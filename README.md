<h1>Free Food</h1>

To edit, fork and submit a pull request please!

![screenshot](https://github.com/yemistar/FreeFood/blob/master/freefood_app.png)

<h2>Contributing to email dataset</h2>

Adding sample emails to the dataset requires a specific process. Simply copying and pasting will not work.

The general form should be as such:
```
[
  {
    "subject": "La te da I am the subject",
    "date": "Oct 4, 2018, 2:58 PM",
    "body": "Body text excluding the signature"
  }
]
```
When coping your body text, save it to a file temporarily as is.
Then, type:
```
sed -E ':a;N;$!ba;s/\r{0,1}\n/\\n/g' file.txt > value.js
```
in Linux to convert the text to json format (replacing new lines by new line characters ( \n )). You can also use:

https://codebeautify.org/json-escape-unescape

to achieve the same thing.

<h2>Contributing to food sentences dataset</h2>

Pick a <b>singular</b> and <b>plural</b> form of a food word. A food word is a noun that describes a physcial thing you can eat. 
Acceptable words: snack, pizza, soda, burger, bread<br/>
Unacceptable words: lunch, dinner, breakfast

Use a site like http://sentence.yourdictionary.com/ or http://sentencedict.com/ to generate sentences with the food word you want. Make sure that the sentence is using the word you picked in the form that was intended for the definition. For instance, 'soda' could be used for 'baking soda' and 'pop' could be used as a verb.

Copy sentences to a new file in Atom. Hit "Ctrl-F" and make sure the the regular expression grabbing is activated. (it's an option in the top-right hand corner of the ctrl-f popup).

Shape the sentences so that there are in proper JSON format:<br/>
    all double quotes in the sentence are escaped (\")<br/>
    there is a double quote at the beginning and end of the sentence<br/>
    there is a comma at the end of the sentence after the double quote<br/>

Example:<br/>
<em>"I just put a pizza in the oven.",</em>

Common regular expressions for doing this quickly:<br/>
    ^\d+.\s  -->  removes digit numbering at the beginning of the sentence. EX: 32.<br/>
    ^|$      -->  Grabs the beginning and ending of each new line. Replace All with a double quote<br/>
    $        -->  Grabs the end of each new line. Replace All with a comma<br/>
    ^\n      -->  Selects a line which is simply a new line. Replace All with nothing<br/>
    
Finally, add the sentences to food_sentences.json. Make sure that when you copy and paste it in that the file is still in proper JSON form!!



