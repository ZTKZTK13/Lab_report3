# **Several Useful options for `grep` Command**
When using various commands in bash, there are a lot of different options to choose to generate outputs meeting different specific requirement. In this lab, there are several useful options for the command `grep`, which can search the contexts in files with different demands. (Using `man grep` command in bash, it will give all specific information about this command including all options that can be used)
* `-i`: this is an option for `grep` to search a certain text regardless of the case of the contents. In other words, this option will give an output containing the required texts of both upper case and lower case. For example, if I search the word "clinical" in `./technical/biomed/1468-6708-3-1.txt`, it will return all lines containing the word "clinical" without examing the case.
  
  ```
  # input
  $ grep -i "clinical" ./technical/biomed/1468-6708-3-1.txt
  # output
        decreased mortality. Clinical trials powered to detect
        whom risk factors, subclinical disease, and morbidity are
           baseline. Clinical covariates include hypertension,
         significantly greater than zero. A clinical trial of a
           Implications for clinical trials
          YHL, but not YOL. Clinical trials of weight modification
          found for underweight older adults. Clinical trials whose
          outcome measure. Both YOL and YHL would be clinically
        YHL as the outcome measure in clinical trials involving
  ```
  
  Another example is that if I search "allhat" in `./technical/biomed/1468-6708-3-10.txt`, it will return all lines containing "ALLHAT" because this is an abbreviation and it only appears as all upper case.
  
  ```
  # input
  $ grep -i "allhat" ./technical/biomed/1468-6708-3-10.txt
  # output
        Prevent Heart Attack Trial (ALLHAT) is a randomized,
          The rationale and design of ALLHAT are described in
          1. Did HF cases meet ALLHAT diagnostic criteria?
          were reviewed at the ALLHAT Clinical Trials Center (CTC)
          ALLHAT Endpoints Subcommittee; for these cases additional
          The ALLHAT definition of HF, used previously in the
        created a dilemma for ALLHAT. Since the trial was not
        ALLHAT criteria for HF were equivalently met in the two
        HF reports reviewed by the ALLHAT Endpoints Subcommittee
        reported in the ALLHAT events that were reviewed, the
        smaller and difficult to detect even in a trial of ALLHAT's
        as ALLHAT has potential limitations. Built into a structure
        number of endpoints, resources available to ALLHAT
        according to ALLHAT criteria. Some discharge summaries and
        documentation for 2% of ALLHAT event reports.
        developed for ALLHAT, specifically for HF events. This
        2) The ALLHAT Manual of Operations provides for
        3) The ALLHAT follow-up form allows for reporting of
  ```

* `-w`: this command for `grep` will return only the text that searched as an independent word in a file. For example, if I search the word "it" in `./technical/biomed/1468-6708-3-1.txt`, it will return only the line containing the word "it" instead of the lines containing words such as "additional" or "longitude".

  ```
  # input
  $ grep -w "it" ./technical/biomed/1468-6708-3-1.txt
  # output
            it does not distinguish between fair or poor health and
  ```
  
  Here is another example of using `-w` to search texts, in which I searched the word "set" in `./technical/biomed/1468-6708-3-1.txt`, and it returned all lines containing only the word "set" instead of "subset", "sets", or "offset".
  
  ```
  # input
  $ grep -w "set" ./technical/biomed/1468-6708-3-1.txt
  # output
        after adjustment for the entire set of health-related
        also adjusted for the entire set of covariates (columns 2
  ```
  
* `-n`: this comand can be used to find the line number of the searching result, and consequently helping to nevigate to the specific part of a file which contains the target lines. For example, in the same target file, `./technical/biomed/1468-6708-3-1.txt`, if "overweight" is the target word, using `grep` with `-n` will return the lines containing the target word with the line number of each.

  ```
  # input
  $ grep -n "overweight" ./technical/biomed/1468-6708-3-1.txt
  # output
  7:        even though there is little evidence that overweight is
  70:          BMI of 18.5 to 24.9; overweight as 25 to 29.9; and
  259:        classified as normal, overweight or obese all had about the
  262:        women and men. Women who were normal or overweight averaged
  268:        women than for men in the normal and overweight groups, but
  291:        underweight category. The effect size comparing overweight
  303:        overweight (for men or women) or obese (for men) affects
  315:          Optimal weight and overweight
  322:          overweight (as opposed to the obese) are no different
  338:          interventions for older adults who were merely overweight
  394:          differences between the overweight and normal weight
  410:        'overweight' by the NHLBI guidelines. This suggests using
  413:        that address older adults who are merely overweight.
  ```
  
  This command option can be used in almost all files to locate the target word. If I search the word "ALLHAT" in `./technical/biomed/1468-6708-3-10.txt`: 
  
  ```
  # input
  $ grep -n "ALLHAT" ./technical/biomed/1468-6708-3-10.txt
  # output
  7:        Prevent Heart Attack Trial (ALLHAT) is a randomized,
  72:          The rationale and design of ALLHAT are described in
  96:          1. Did HF cases meet ALLHAT diagnostic criteria?
  117:          were reviewed at the ALLHAT Clinical Trials Center (CTC)
  124:          ALLHAT Endpoints Subcommittee; for these cases additional
  147:          The ALLHAT definition of HF, used previously in the
  379:        created a dilemma for ALLHAT. Since the trial was not
  405:        ALLHAT criteria for HF were equivalently met in the two
  407:        HF reports reviewed by the ALLHAT Endpoints Subcommittee
  419:        reported in the ALLHAT events that were reviewed, the
  449:        smaller and difficult to detect even in a trial of ALLHAT's
  459:        as ALLHAT has potential limitations. Built into a structure
  464:        number of endpoints, resources available to ALLHAT
  472:        according to ALLHAT criteria. Some discharge summaries and
  476:        documentation for 2% of ALLHAT event reports.
  485:        developed for ALLHAT, specifically for HF events. This
  518:        2) The ALLHAT Manual of Operations provides for
  527:        3) The ALLHAT follow-up form allows for reporting of
  ```
  
* `-c`: this command option will calculate how many time a target word appears in a file. Using `grep` with `-c`, instead of returning all lines containing the word, it will return only a number indicating the count of the number of times the word of search appears. For instance, if I use `-c` as the option to the same examples of `-n`, it will just return a number of count.

  ```
  # input
  $ grep -c "overweight" ./technical/biomed/1468-6708-3-1.txt
  # output
  13
  ```
  
  ```
  # input
  $ grep -c "ALLHAT" ./technical/biomed/1468-6708-3-10.txt
  # output
  18
  ```
  
Other than these four options, there are a lot of other options that can be added after `grep` as additional requirements of searching. When using `grep` to search contents, more than one options can be used as limitation to the search. For example, you can use `grep -i -w` to search the target text. Last but not least, if `man` is a very useful tool to give all relevant information including different options and patterns about `grep`.

(The command options mentioned in this report refers to the information given by `man grep`)
