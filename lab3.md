# Lab 3 #
### Grace Ortiz ###
## Part 1 - Bugs##

From the Week 4 Lab, I chose the reversedInPlace bug in ArrayExamples.java.   

A failure inducing input: 
```
@Test
  public void testReverseInPlace2() {
    int[] input = {1, 2, 3};
    ArrayExamples.reverseInPlace(input); 
    assertArrayEquals(new int[]{3, 2, 1}, input);
  }
```

An input that doesn't induce failure:
```
@Test
  public void testReverseInPlace3() {
    int[] input = {1, 2, 1};
    ArrayExamples.reverseInPlace(input); 
    assertArrayEquals(new int[]{1, 2, 1}, input);
  }
```   

The symptom:
![JUnit debug](junit-debug.png)   

The bug, before: 
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```   

The bug, fixed:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < (arr.length/2); i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }
```

The fix addresses the issue because before, the method did not save the initial value of arr[i] and it got replaced and its value lost. It also traversed the whole array, overwriting swapping back valued that were already reversed. By changing the condition in the for loop to arr.length/2 it ensures that only half of the array is traversed, not re-swapping any already reversed data. By creating the temp variable, it saves the value of arr[i] so it can be reassigned and swapped effectively.   

## Part 2 - Researching Commands ##
4 command line options for **grep**:
- grep -i. (n.d). Ignore case. Manual page. Retrieved from the terminal.
    ```
    [user@sahara ~/docsearch/technical/biomed]$ grep -i phosphatase 1471-2105-3-22.txt 
          Phosphatase in Activated Cells )
    ```
    - -i ignores the case of matching lines, so even though we are searching for "phosphatase", it matches with the line containing "Phosphatase" as well since we are ignoring the case change of the 'p'.
    ```
    [user@sahara ~/docsearch/technical/911report]$ grep -i california chapter-7.txt 
            FIRST ARRIVALS IN CALIFORNIA
            Why Hazmi and Mihdhar came to California, we do not know for certain. Khalid Sheikh
                Mohammed (KSM), the organizer of the planes operation, explains that California was
                that al Qaeda had any agents in Southern California. We do not credit this
                California, so that they could begin pilot training as soon as possible. KSM claims
                Culver City, one of the most prominent mosques in Southern California.
                fellow inmates at a California prison in September- October 2003 that he had known
                rest of his time in California, until mid-December; he would then leave for Arizona
                Translating between English and Arabic, he assisted them in obtaining California
                of California declined to prosecute him on charges arising out of his alleged
                impression is that soon after arriving in California, Hazmi and Mihdhar sought out
                child arrived, he could stand life in California no longer. In late May and early
                California, and Arizona; and he briefly started at a couple of them before returning
                an English as a second language program in Oakland, California, which he had
    ```
    - This example shows how -i works for identifying many lines just how regular grep does. It has a lot of importance for searching for words as words at the start of the sentence are capitalized while some words in the middle of a sentence are not, so searching for a word while ignoring case will output every single instance of that word, which is how the search tool works for most computers. 
- grep -o. (n.d). Only matching. Manual page. Retrieved from the terminal.
    ```
    [user@sahara ~/docsearch/technical]$ grep -ro biomed
    biomed/1472-6807-1-1.txt:biomed
    biomed/1472-6920-2-3.txt:biomed
    biomed/1471-2105-3-17.txt:biomed
    biomed/1471-2164-3-18.txt:biomed
    biomed/1471-2202-2-8.txt:biomed
    biomed/1472-6947-3-8.txt:biomed
    biomed/1472-6947-3-8.txt:biomed
    biomed/1472-6882-3-3.txt:biomed
    biomed/1472-6882-3-3.txt:biomed
    biomed/1472-6882-3-3.txt:biomed
    biomed/1472-6882-3-3.txt:biomed
    biomed/1472-6882-3-3.txt:biomed
    biomed/1472-6882-3-3.txt:biomed
    biomed/1471-2474-2-3.txt:biomed
    biomed/1472-6947-3-5.txt:biomed
    biomed/1472-6882-1-12.txt:biomed
    biomed/1471-2202-2-9.txt:biomed
    biomed/1471-2164-3-7.txt:biomed
    biomed/1471-2105-3-16.txt:biomed
    ```
    - -o prints only the matching part of the line. In this example, we see all the files that have biomed in them, without being flooded by the content on the line containing biomed. 
    ```
    [user@sahara ~/docsearch/technical/911report]$ grep -o Mohammed chapter-5.txt 
    Mohammed
    Mohammed
    Mohammed
    Mohammed
    Mohammed
    Mohammed
    Mohammed
    ```
    - In this example where we are only searching within a file, it shows only the matching text, not even the line number. This demonstrates that -o is typically more useful in conjunction with other commands, as it does not provide much other information on its own. 
- grep -v. (n.d). Invert. Manual page. Retrieved from the terminal.
    ```
    [user@sahara ~/docsearch/technical/911report]$ grep -v e preface.txt 

    
        
            PREFACE
                27, 2002).
                accountability.
        

    ```
    - -v outputs the lines that do not match. This example shows that it outputs all the lines that do not contain "e", including lines that are completely empty (like the first 3 blank lines and the last 2), and lines that contain "E" but not "e", because we have not used "grep -iv". 
   ```
   [user@sahara ~/docsearch/technical/911report]$ grep -v '\.' preface.txt 

    
        
            PREFACE
            We present the narrative of this report and the recommendations that flow from it to
                the President of the United States, the United States Congress, and the American
                Democrats chosen by elected leaders from our nation's capital at a time of great
                September 11, 2001, was a day of unprecedented shock and suffering in the history of
                avoid such tragedy again?
            To answer these questions, the Congress and the President created the National
                Commission on Terrorist Attacks Upon the United States (Public Law 107-306, November
                relating to the terrorist attacks of September 11, 2001," including those relating
                to intelligence agencies, law enforcement agencies, diplomacy, immigration issues
                and border control, the flow of assets to terrorist organizations, commercial
                aviation, the role of congressional oversight and resource allocation, and other
                current and previous administrations who had responsibility for topics covered in
                From the outset, we have been committed to share as much of our investigation as we
                fullest possible account of the events surrounding 9/11 and to identify lessons
                enemy rallies broad support in the Arab and Muslim world by demanding redress of
                purpose is to rid the world of religious and political pluralism, the plebiscite,
            We learned that the institutions charged with protecting our borders, civil aviation,
                and national security did not understand how grave this threat could be, and did not
                fault lines within our government-between foreign and domestic intelligence, and
                sharing information across a large and unwieldy government that had been built in a
                We hope that the terrible losses chronicled in this report can create something
                the long haul, to attack terrorists and prevent their ranks from swelling while at
                agencies that prevailed in the great struggles of the twentieth century must work
                Congress needs dramatic change as well to strengthen oversight and focus
            As we complete our final report, we want to begin by thanking our fellow
                together over every page, and the report has benefited from this remarkable
                Philip Zelikow, has contributed innumerable hours to the completion of this report,
                They have conducted the exacting investigative work upon which the Commission has
                officials, past and present, who were generous with their time and provided us with
                Inspectors General at the Department of Justice and the CIA provided great
                of several previous Commissions, and we thank the Congressional Joint Inquiry, whose
            We conclude this list of thanks by coming full circle: We thank the families of 9/11,
                This final report is only a summary of what we have done, citing only a fraction of
            We have listened to scores of overwhelming personal tragedies and astounding acts of
                have admired their determination to do their best to prevent another tragedy while
                enormous sympathy for the victims and their loved ones, and with enhanced respect
                pause, reflect, and sometimes change our minds as we studied these problems and
        
    ```
   - In this example, it outputs every line that doesn't have a period. The '.' character is reserved and if it was used alone it would be a stand in for any character and would have an output of a blank line. We must use '\.' to search for the period character itself. 
- grep -r. (n.d). Recursive. Manual page. Retrieved from the terminal.
  - recursively searches through all subdirectories
    ```
    [user@sahara ~/docsearch/technical]$ grep -r narrative 911report/
    911report/preface.txt:            We present the narrative of this report and the recommendations that flow from it to
    911report/chapter-11.txt:            In composing this narrative, we have tried to remember that we write with the benefit
    911report/chapter-11.txt:            Before concluding our narrative, we offer a reminder, and an explanation, of the one
    ```
    - -r recurcursively searches through all subdirectories and files and returns matching lines. Int his example, we search through all files in 911report/ to find all matches for the word "narrative", demonstarating its recursive capabilites. 
    ```
    [user@sahara ~/docsearch/technical]$ grep -r narrative
    biomed/1472-6882-3-1.txt:        Several narrative reviews of the literature on the
    biomed/1472-6963-3-6.txt:          combination of both coded and narrative fields. The AMRS
    biomed/1471-2407-3-18.txt:            them into short narratives, and learning and
    biomed/1471-2407-3-18.txt:            story in a two to three page narrative prior to the
    biomed/1471-2407-3-18.txt:            narrative were encouraged to write one half to one page
    biomed/1471-2407-3-18.txt:            sessions and formulated a narrative together that
    biomed/1471-2407-3-18.txt:            approaches provided a narrative that could be presented
    911report/preface.txt:            We present the narrative of this report and the recommendations that flow from it to
    911report/chapter-11.txt:            In composing this narrative, we have tried to remember that we write with the benefit
    911report/chapter-11.txt:            Before concluding our narrative, we offer a reminder, and an explanation, of the one
    ```
    - Similar to the previous example, we recursively search for the word narrative, but this time, without specifying a directory. grep -r will recursively search all subdriectoryies and files within the working directory, resulting in far more matches, and demonstrating its capability to traverse multiple directories.
   
(All sources cited in APA format in line)
