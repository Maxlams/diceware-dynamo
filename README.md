# Diceware Dynamo
[Diceware](http://world.std.com/~reinhold/diceware.html) is a method of generating passphrases using dice. It allows for an easy way to make secure passwords that are still (relatively) easy to remember, such as
```shell
amigo helpful south dirt
```

[Diceware Dynamo](https://maxlambda.github.io/diceware-dynamo/) builds passphrases of customizable length by generating pseudo-random "dice roll" numbers from 1-6, appending 5 of those numbers together, and mapping them to text from a [word list](http://world.std.com/~reinhold/diceware.wordlist.asc). Here is an example from the word list:
```shell
53256 sears
53261 season
53262 seat
53263 sec
53264 secant
53265 sect
53266 sedan
```

## Approach
To simulate dice rolls, pseudo-random numbers are generated to index a string list containing **7776** entries.

Diceware is secure because of this; if one word is chosen from this list, an attack would have a one in 7776 chance of guessing your chosen word the first try. This might seem low, as the attacker may be able to correctly find your word after about 3888 tries (half of the list).

Now, add another word to your passphrase. The attacker's chances decrease to a one in 7776<sup>2</sup> = 60466176 chance of finding your word the first try, and would keep decreasing the more words are added. (unfinished)

![Entropy Image](https://imgs.xkcd.com/comics/password_strength.png)
(image from [xkcd](https://xkcd.com/936/))
