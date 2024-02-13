# Lab Report 3 - Isaac Robles
---
The bug I am choosing from the week 4 lab will be shown down below.

```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];

    }
    return arr;
  }
```

---

Down below is a test that passes. Notice that we are testing on an empty array `arr` in order for the test to pass because of the how the bug affects the program. The way the program works currently the method will always return 0 for the first element.  

```
  @Test 
  public void testReversedWithoutFailure() {
    int[] inputArray = {};
    assertArrayEquals(new int[]{}, ArrayExamples.reversed(inputArray));
  }
```
```
$ java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
.
Time: 0.007

OK (1 test)
```

When we write another test that is supposed to pass if the method works as intended, we can see that it fails and instead of the the expected return for the first element being the last element of the original array `arr` (because it should be reversed) we just get 0 for that first element. This lets us pinpoint the bug to how elements are being assigned. 

```
$ java -cp ".;lib/junit-4.13.2.jar;lib/hamcrest-core-1.3.jar" org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
.E.
Time: 0.01
There was 1 failure:
1) testReversedWithFailure(ArrayTests)
arrays first differed at element [0]; expected:<5> but was:<0>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReversedWithFailure(ArrayTests.java:8)
        ... 32 trimmed
Caused by: java.lang.AssertionError: expected:<5> but was:<0>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)    
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 38 more

FAILURES!!!
Tests run: 2,  Failures: 1
```
So in order to fix this we must change how the method is assigning elements and down below is how we will do so.

```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    newArray[arr.length - i - 1] = arr[i];
  }
  return newArray;
}
```

This is able to fix the bug in the method because it is no longer grabbing elements from the already empty array `newArray` and rewriting the elements onto our original array `arr`. Instead it grabs the elements from `arr` starting from the end (reversed order) and rewrites said elements onto the array `newArray`. This will allow for a reversed version of our orignal array `arr` to be created through the array `newArray` and returned back to us corretly reversing everything.

---
# `less` 

The less command is allows one to view the contents of text files and has many options built it providing that allow you navigate said file or search for specific patterns.

## `-N` Displaying Line Numbers ##

### Two examples: ###
```
      defin@BOOK-NGRBMV3GI4 MINGW64 ~/OneDrive/Desktop/cse15L/docsearch-main/docsearch-main/technical/government/Alcohol_Problems
      $ less -N Session2-PDF.txt
```

```
      1
      2
      3
      4
      5 Session 2.
      6 Identifying ED Patients with Alcohol Problems
      7
      8 Robert Woolard, MD
      9 Many patients in the emergency department (ED) have alcohol
     10 problems, and they can be identified.1 Research on techniques used
     11 to identify these patients has been conducted, but several areas of
     12 interest should be addressed by further research. We need to
     13 further examine and refine alcohol-screening questionnaires in the
     14 ED. We need to determine the sequence and combination of questions
     15 and tests that constitute the best screening process. We need to
     16 study barriers to screening, identify factors that promote
     17 screening implementation, and demonstrate the impact of a screening
     18 program in the ED. The final aim of screening must be improved
     19 outcomes through referral and counseling. Identification is only
     20 the first step in a process of care.
     21 Alcohol problems defined
     22 Alcohol problems designate a spectrum from risk behavior to
     23 illness, and from problematic consumption to alcohol use disorder.
     24 We must be careful when interpreting the results of studies, and in
     25 our own design of screening procedures, that we are clear about the
     26 endpoints we are measuring. Clinicians in the ED are interested in
Session2-PDF.txt
```

```
      defin@BOOK-NGRBMV3GI4 MINGW64 ~/OneDrive/Desktop/cse15L/docsearch-main/docsearch-main/technical/government/Alcohol_Problems
      $ less -N Session3-PDF.txt
```

```
      1
      2
      3
      4
      5 Session 3.
      6 Intervening with Alcohol Problems
      7 in Emergency Settings
      8
      9 Carlo C. DiClemente, PhD* Carl Soderstrom, MD
     10 Excessive alcohol consumption plays an important role in many of
     11 the medical conditions, accidents, and injuries that cause visits
     12 to emergency departments and trauma centers. Many studies have
     13 documented the presence of alcohol among patients admitted to
     14 emergency depart-ment1-5 and trauma center6,7 settings. Other
     15 studies have demonstrated that even blood alcohol concentration
     16 (BAC) determinations under-estimate the extent of alcohol problems
     17 among the patients who are triaged and treated in emergency
     18 settings.4,7 The prevalence of this co-factor to the emergency
     19 admission, and the fact that alcohol is a risk factor both for the
     20 first visit and for a return visit to the emergency setting, have
     21 occasioned a call for an effective method of intervening with
     22 alcohol problems in these settings.8-12 Although there are problems
     23 with and barriers to intervening in these settings, a number of
     24 studies and a few controlled trials indicate that interventions
     25 focused on patients' drinking can reduce the amount of drinking as
     26 well as injury episodes, including repeat re-admission for injury
Session3-PDF.txt
```

`-N` is useful because it can show you specific line numbers. This can be useful when you want to use a specific number from a txt file. In the examples above we see it being used on two different txt files. `Session3-PDF.txt` and `Session2-PDF.TXT`

---
## `+` Starting at a specific line number ##

### Two examples: ###
```
defin@BOOK-NGRBMV3GI4 MINGW64 ~/OneDrive/Desktop/cse15L/docsearch-main/docsearch-main/technical/government/Alcohol_Problems  
$ less +100 Session3-PDF.txt
```
```
treatment after discharge. Gentilello and colleagues conducted a
pilot intervention at a Houston emergency department that consisted
of a substance abuse counselor mobilizing the family, and at times
the employer, to intervene with the patient's drinking and to
arrange for immediate entry to a residential substance abuse
treatment program after discharge. This program appeared to be
successful in getting problem-drinking patients to treatment, but
only with families who could be engaged and for patients who had
resources or insurance.21 This and other seminal studies encouraged
many professionals to call for some type of consultation service or
brief intervention to be employed with patients in emergency rooms
or trauma settings.13,22-25
Many of the early studies that documented the efficacy of
interventions with problem drinkers in emergency settings were
evaluations and not controlled studies. Nevertheless, the
documented outcomes have been impressive. Several studies have
examined the outcomes achieved by substance abuse counselors or
alcohol workers intervening with problem drinkers. A brief
intervention in an emergency department by alcohol health workers
demonstrated a mean reduction in drinking of 43% for a subset of
patients who were enrolled in the study.26 The pilot
program in Texas described above demonstrated a 100% successful
referral to alcoholism treatment for patients and families who
agreed to be in the program.21 A substance abuse consultation team
in a trauma center reported acceptance of referral for drug or
alcohol treatment in 62% of the 100 consecutive cases
Session3-PDF.txt
```

```
defin@BOOK-NGRBMV3GI4 MINGW64 ~/OneDrive/Desktop/cse15L/docsearch-main/docsearch-main/technical/government/Alcohol_Problems  
$ less +150 Session3-PDF.txt
```
```
by Sommers and colleagues15 involving two trauma centers, patients
who were injured in vehicular crashes and had a positive BAC were
asked, "To what extent do you believe your alcohol consumption was
responsible for this injury?" Overall, 62% attributed being injured
either "somewhat" (24%) or "mostly" or "totally" (38%) to be the
result of drinking. This attribution may be less endorsed with
medical conditions such as liver disease or pancreatitis.
Whether this awareness is viewed as a "hitting bottom"
phenomenon or in more traditional motivational terms, there does
seem to be a connection between readiness to change and recognition
that negative consequences can be directly linked to a behavior.17
Reports from emergency staff and anecdotal descriptions of some
interventions support the results of the above studies, indicating
heightened motivation in the initial period of time in the
emergency setting. However, it is not clear how long this initial
openness to change lasts. There are also reports that after a
couple of days, spurred by concerns about legal responsibility,
family member advice, or rationalizations, patient openness to
discuss drinking and other problem behaviors decreases
dramatically.
We do know that alcohol consumption changes for many problem
drinkers after their visit to an emergency setting. Several studies
have documented consumption changes not only in the intervention
condition but also in the minimal intervention control groups.18,19
However, changes in alcohol consumption are often not sustained
among participants in control conditions. After the emergency
Session3-PDF.txt
```


In the examples above, we can see that the output starts at the number specificed after the `+` in the command ran on the the txt filec `Session3-PDF.txt`. This is useful when you want to only see certain parts of a text file. In the examples above, we can see it being used to start the outputs on line 100 and line 150 of the txt file mentioned prior.

---

## `-S` No line wrapping ##

### Two examples: ###
```
defin@BOOK-NGRBMV3GI4 MINGW64 ~/OneDrive/Desktop/cse15L/docsearch-main/docsearch-main/technical/government/Alcohol_Problems  
$ less -S Session3-PDF.txt
```

```
Session 3.
Intervening with Alcohol Problems
in Emergency Settings

Carlo C. DiClemente, PhD* Carl Soderstrom, MD
Excessive alcohol consumption plays an important role in many of
the medical conditions, accidents, and injuries that cause visits
to emergency departments and trauma centers. Many studies have
documented the presence of alcohol among patients admitted to
emergency depart-ment1-5 and trauma center6,7 settings. Other
studies have demonstrated that even blood alcohol concentration
(BAC) determinations under-estimate the extent of alcohol problems
among the patients who are triaged and treated in emergency
settings.4,7 The prevalence of this co-factor to the emergency
admission, and the fact that alcohol is a risk factor both for the
first visit and for a return visit to the emergency setting, have
occasioned a call for an effective method of intervening with
alcohol problems in these settings.8-12 Although there are problems
with and barriers to intervening in these settings, a number of
studies and a few controlled trials indicate that interventions
focused on patients' drinking can reduce the amount of drinking as
well as injury episodes, including repeat re-admission for injury
Session3-PDF.txt
```

The use of `-S` can be useful because it gets rid of line wrapping and shows very long lines as is. This can make \
ridicuoulsly long lines easier to read \
as they \
aren't split \
up into \
multiple \
lines. 

---


---
## `-m` Display Percentage  ##

### Two examples: ###
```
$ less -m Session3-PDF.txt
```

```
Session 3.
Intervening with Alcohol Problems
in Emergency Settings

Carlo C. DiClemente, PhD* Carl Soderstrom, MD
Excessive alcohol consumption plays an important role in many of
the medical conditions, accidents, and injuries that cause visits
to emergency departments and trauma centers. Many studies have
documented the presence of alcohol among patients admitted to
emergency depart-ment1-5 and trauma center6,7 settings. Other
studies have demonstrated that even blood alcohol concentration
(BAC) determinations under-estimate the extent of alcohol problems
among the patients who are triaged and treated in emergency
settings.4,7 The prevalence of this co-factor to the emergency
admission, and the fact that alcohol is a risk factor both for the
first visit and for a return visit to the emergency setting, have
occasioned a call for an effective method of intervening with
alcohol problems in these settings.8-12 Although there are problems
with and barriers to intervening in these settings, a number of
studies and a few controlled trials indicate that interventions
focused on patients' drinking can reduce the amount of drinking as
well as injury episodes, including repeat re-admission for injury
and other negative consequences of drinking. This review will
examine the rationale for intervening, types of interventions and
interveners, and barriers and concerns that need to be addressed.
Then we will offer suggestions for research and practice related to
intervening effectively with alcohol problems in emergency
settings.
Motivational considerations
The rationale for interventions in the emergency setting is that
the medical condition or injury prompting admission provides a
"window of opportunity" when the individual may be more vulnerable
and more open to seeing the connection between current consequences
and his or her drinking or drug abuse and may be more motivated to
change.13-15
* Presenter
The presence of an adverse consequence that can be linked to
drinking-such as gastrointestinal, vascular, renal, or other
medical problem; an automobile crash; unintentional injury; or
involvement in a violent incident-facilitates intervention among
patients with alcohol problems encountered in the emergency
setting. In an emergency department (ED) study of injured crash
victims who had been drinking, Cherpitel found that more than
one-third linked their drinking to being injured and thus were
deemed good candidates for "brief intervention."16 In another study
by Sommers and colleagues15 involving two trauma centers, patients
who were injured in vehicular crashes and had a positive BAC were
asked, "To what extent do you believe your alcohol consumption was
responsible for this injury?" Overall, 62% attributed being injured
3%
```

```
defin@BOOK-NGRBMV3GI4 MINGW64 ~/OneDrive/Desktop/cse15L/docsearch-main/docsearch-main/technical/government/Alcohol_Problems  
$ less -m Session2-PDF.txt
```

```
Session 2.
Identifying ED Patients with Alcohol Problems

Robert Woolard, MD
Many patients in the emergency department (ED) have alcohol
problems, and they can be identified.1 Research on techniques used
to identify these patients has been conducted, but several areas of
interest should be addressed by further research. We need to
further examine and refine alcohol-screening questionnaires in the
ED. We need to determine the sequence and combination of questions
and tests that constitute the best screening process. We need to
study barriers to screening, identify factors that promote
screening implementation, and demonstrate the impact of a screening
program in the ED. The final aim of screening must be improved
outcomes through referral and counseling. Identification is only
the first step in a process of care.
Alcohol problems defined
Alcohol problems designate a spectrum from risk behavior to
illness, and from problematic consumption to alcohol use disorder.
We must be careful when interpreting the results of studies, and in
our own design of screening procedures, that we are clear about the
endpoints we are measuring. Clinicians in the ED are interested in
screening for several alcohol endpoints. Acute intoxication is of
concern to emergency physicians. Intoxication in a driver would
certainly be considered an "alcohol problem." The blood or breath
4%

```
Above we can see two examples of `-m` being used on the files `Session3-PDF.txt` and `Session2-PDF.txt` This allows for a percentage to be displayed at the bottom of how much the user has gone through the file. In the examples below we can see different percetanges being displayed as each time we hit `enter` on our keyboard the terminal goes further through the txt file and so we are getting a higher percentage of completion in regards to how much we've gone through said file.  

---

Sources used: `man less`
