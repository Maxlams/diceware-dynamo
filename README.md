# Diceware Dynamo
[Diceware](http://world.std.com/~reinhold/diceware.html) is a method of generating (almost) truly random passphrases using dice. The method entails rolling a dice (many times), indexing numbers to a large word list, and appending them together. It allows for an easy way to make secure passwords that are still relatively easy to remember, such as
```shell
amigo helpful south dirt
```

[Diceware Dynamo](https://maxlambda.github.io/diceware-dynamo/) does all this dice rolling and indexing for you. It builds passphrases of customizable length by generating pseudo-random 5 digit length numbers (with each digit being "dice roll" numbers from 1-6), and mapping them to text from a [word list](http://world.std.com/~reinhold/diceware.wordlist.asc). Here is an example from the word list:
```shell
...
53256 sears
53261 season
53262 seat
53263 sec
53264 secant
53265 sect
53266 sedan
...
```

## Approach
To simulate dice rolls, pseudo-random numbers are generated to index a string list containing **7776** entries.

Diceware is secure because of this; if one word is chosen from this list, an attacker would have a one in 7776 chance of guessing your chosen word the first try. This might seem low, as the attacker may be able to correctly find your word after about 3888 tries (half of the list). However...

If you add another word to your passphrase, the attacker's chances decrease to a one in 7776<sup>2</sup> = 60466176 chance of finding your word the first try, and would keep decreasing the more words are added.

Essentially, by adding more and more words, you are creating *entropy*, or *randomness*, to ensure that your password is hack-proof. For example, if you use Diceware Dynamo to generate the ten-word string
```shell
spay ascend cycle mabel gould alga wonder dramatic glaze greek
```
then you've created a passphrase with over 97 bits of entropy. This is very, *very* secure: compare this to the average-looking password
```shell
Tr0ub4dor&3
```
as shown below. This passphrase only has about 28 bits of entropy - over **3 times less** than the previous one! Now, you should start [generating passwords with Diceware](https://maxlambda.github.io/diceware-dynamo/)! - Max 

> learn more about **entropy** [here](https://www.pleacher.com/mp/mlessons/algebra/entropy.html)


![Entropy Image](https://imgs.xkcd.com/comics/password_strength.png)

(image from [xkcd](https://xkcd.com/936/))
