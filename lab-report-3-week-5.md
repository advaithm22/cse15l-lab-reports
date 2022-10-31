# Advaith Modali - Lab Report 3 Week 5

## Command 1: `grep`

```
grep -o -b "embassy" chapter-2.txt

72640:embassy
75456:embassy
77516:embassy
78248:embassy
78783:embassy
78816:embassy
78972:embassy
```

Here, we are using the -o and -b modifications to the `grep` command, enabling it to show the specific position of a match in a certain line of a file that we provide. We provided the arguments of "embassy" and chapter-2.txt to designate the pattern and file we want to perform the operation on, and in turn we are presented with some numbers that show the matches. This is useful, because if we would like to know how prevalent a certain word is in a document, we will be given access to its position and can navigate to explore the context of the word in that specific position within the document.

```
grep -m5 "mice" rr74.txt

        using mice that are deficient in NOS isoforms.
        vascular tone. Studies using knockout mice for each of
        hypertension in mice that lack eNOS [ 9, 12]. In the
        present study we exposed wild-type mice to severe hypobaric
          ME, USA) mice at age 6 weeks.
```

Here, we are placing a constraint on how many matches are displayed (in this case we want the screen to show a maximum of 5 occurences of the word "mice" in the rr74.txt file). This helpful because the results could narrow down what specific usages of mice we're looking for, hence allowing us to gain a better understanding of how relevant the word is to what we're trying to find in the file.

```
grep -i "proposition" water_fees.txt

under Proposition 218, a process Tulare County Water Works       
```
In this situation the -i we added to grep stands for ignore case, and it essential ignores any case sensitivity that previously existed for grep. Here we want to use it on "proposition" in the water_fees.txt file, so it returns an instance where the word is capitalized. This is useful in many scenarios because we can be unsure if a certain word we want to find is capitalized or not. 

## Command 2: `find`

```
find government -name "RoanokeTimes.txt"

government/Media/RoanokeTimes.txt       
```

Here we utilize -name to look for a specific fil, in this case called RoanokeTimes.txt . This is helpful because in many cases we can be unsure of which subdirectory a certain file is in. By using this command, we essentialy solve that issue and are provided the relative path of the file we want to access.

```
find . -type d -name "Media"

./government/Media       
```
In this example, we provide . to indicate the current folder, technical, and use d to indicate that we want to find a directory and not a certain file. We get the relative path to the name of the directory we pass in as an argument. This is beneficial since we can check if something truly is a directory or not. 

```
find plos -not -name "*.txt"

plos       
```
Here, we use -not to see if there are any files that don't have the "txt" extension. In this case, we get just the directory name itself, plos. This is beneficial if we want to separate the types of extensions within a certain folder and identify if there are any files that can be run locally instead of just read.

## Command 3: `less`

```
less -N rr73.txt

1
      2
      3
      4
      5         Introduction
      6         Three-dimensional (3D) collagen gel culture has been
      7         used as an
      8         in vitro model of
      9         in vivo tissue contraction, a common
     10         feature of fibrosis, as well as the resolution of
     11         granulation tissue that characterizes repair [ 1, 2].
     12         Short-term co-cultures of monocytes with fibroblasts result
     13         in the inhibition of collagen gel contraction [ 3], while
     14         co-cultures of fibroblasts with neutrophils, or with
     15         neutrophil elastase (NE), augment contraction [ 4].
     16         Results in the linked study [ 5] demonstrated that 3D
     17         collagen gel contraction was augmented in extended
     18         co-cultures of fibroblasts and monocytes. Since MMPs play a
     19         prominent role in connective tissue degradation [ 6, 7, 8],
     20         the current study, an extension of this linked study, was
     21         designed to explore the potential role of MMPs in this
     22         process.
     23
     24
rr73.txt      
```
Here, we utilize find along with the -N option that shows each line number. We performed the operation on the rr73.txt file within the biomed folder, and got the indicated output. The purpose of this is so that we can easily see which lines correspond to which line number, making it easier for us to reference where a certain feature of the file might be located. 

```
less +20 pmed.0020281.txt

from the scientific community and whose incomplete findings cause injury; and
        pharmaceuticals that are detailed to physicians, not to save lives or necessarily improve
        the health or welfare of the recipients, but to make money.
        In the lonely and, at times, discouraging world of whistleblowing, we whistleblowers are
        passionate, and often successful, because our efforts have a different goal than the
        corporations and political interests whose operations we occasionally challenge. Our goal
        is to tell the truth. That honest effort is the source of any ethical difference we can or
        might make. Truth is the basis for the power of a whistleblower, one that can withstand the
        assault of unprecedented odds against being heard put forth by that sum of political power,
        expediency, and money.
        A whistleblower's success depends upon competent and articulate media. The debate to
        improve the status quo—be it in pharmaceutical marketing or managed-care decision
        making—cannot proceed or flourish without it.
        Ralph Waldo Emerson, American essayist and philosopher (1803–1882), commpmed.0020281.txt   
```

Here we added the +20 to display the output of the files from line 20 onwards. This is beneficial if we want to control the output and also if we expect more important in a certain range of the file.

```
less -pFDNY chapter-9.txt

ork (FDNY) were
                hampered by the inability of its radios to function in buildings as large as the
                Twin Towers. The 911 emergency call system was overwhelmed. The general evacuation
                of the towers' occupants via the stairwells took more than four hours.

            Several small groups of people who were physically unable to descend the stairs were
                evacuated from the roof of the South Tower by New York Police Department (NYPD)
                helicopters. At least one person was lifted from the North Tower
 roof by the NYPD in
                a dangerous helicopter rappel operation- 15 hours after the bomb
ing. General
                knowledge that these air rescues had occurred appears to have le
ft a number of
                civilians who worked in the Twin Towers with the false impressio
n that helicopter
                rescues were part of the WTC evacuation plan and that rescue fro
m the roof was a
                viable, if not favored, option for those who worked on upper flo
ors. Although they 
```

Here we utilize the -p command, whose purpose is to take the user to the specific portion of the file that starts with the string we add on to it without any spaces. This is beneficial because once we execute the command, we can use the right arrow to go to any other portion of the file where the same word exists.

