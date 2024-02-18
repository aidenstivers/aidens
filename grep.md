# Grep Documentation

I downloaded two different `.bib` files. The first one included ten articles, and I used it to follow along with this week's lecture and demonstration. 
The second file included 17 articles, and I performed the same functions without the same level of guidance. 

<img width="858" alt="Screen Shot 2024-02-17 at 3 24 22 PM" src="https://github.com/aidenstivers/aidens/assets/157851343/f813744b-6bf5-48e3-bfb8-5e2ed2911fcf">

Above was my successful attempt at getting my `scopus.bib` file on my gcloud. It took several tries.
I saw on Element that other people were having the same problem, so I did the alternative method by using the `wget` command.

<img width="519" alt="Screen Shot 2024-02-17 at 3 51 12 PM" src="https://github.com/aidenstivers/aidens/assets/157851343/2ba1de1f-45a2-45aa-8344-fe1cd136d46a">

After that, I played around with the `grep` command. In this command, I was following the video instructions.
`grep` is used to find specific data in a file.

The command in the picture was `grep -Eio "^@(A|B)[A-Z]*" scopus.bib | sort`

`grep` is the command. `-E` extends grep's regular expression engine, `-i` ignores case, and `-o` returns only matching results.
The quotes signify the result being searched for.
`^` marks the beginning of the line. `@` is the first character in the line. So this means I was searching for lines that began with `@`.
The next part narrows down what comes after the `@`. Since there were only Articles and Books in this `.bib` file, it was narrowed down to only show results that began with an @ and were followed by either an A or a B. The `[A-Z]` signifies that any letters can come after the initial A or B and the `*` tells it that the previous character(s) can be repeated any number of times.
Following that is the name of the file, `scopus.bib`.
Finally, there is a pipe `|` which signifies that the first command is finished and should be run in full before what comes after the pipe, which should be run within the results of the first command. In this instance, it says to sort the results of the initial command.

<img width="1016" alt="Screen Shot 2024-02-17 at 4 10 03 PM" src="https://github.com/aidenstivers/aidens/assets/157851343/19950b34-c117-4991-8bc8-f07041b651a6">

Above is the command `grep -o "Cited by: [0-9]*" scopus.bib | awk -F":" 'BEGIN { printf "Total Citations: "} {sum += $2; }END {print sum}'`

This command sums together the number of times each resource has been cited.
The field in the data that marks the numbers I wanted to calculate was "Cited by:", so the command `-o "Cited by: [0-9]*" grabs the data from fields that begin with the words "Cited by:" followed by a number 0-9 which might be followed by other numbers. This is followed by the file name.
`awk` is a programming language helpful for finding and sorting data. In this instance, it's being used as a command to help sum together the number of citations each resource has.

<img width="485" alt="Screen Shot 2024-02-17 at 4 46 00 PM" src="https://github.com/aidenstivers/aidens/assets/157851343/edaa2458-032a-49d1-ae21-fd51bc486ad5">

I did the same command on my second `.bib` file.

<img width="642" alt="Screen Shot 2024-02-17 at 6 45 43 PM" src="https://github.com/aidenstivers/aidens/assets/157851343/0fc6cbec-3dc4-49b3-8b9a-dae3c4a78ef3">

This was my attempts to sort the types of resources returned in my second `.bib` file. Initially, I had run this using `grep -Eio "(A|CC)[A-Z]*" plants.bib` but I realized it returned an unwanted instance. `@cam` was unrelated to the types of resources, so I had to get more specific.
I ended up using two different commands which worked. One specified the whole words following the `@` and the other specified `@(A|CO)[A-Z]*` which also worked.

I used similar commands to the ones I outlined above to sort by author, article title, journal, etc.

This week was definitely more challenging for me than last week. I am getting the hang of running the commands and feel great about following the instructions in the videos, but I lose confidence when I explore on my own. 
