# Amplitude and Parameters

As well as allowing you to control which note to play or which sample to trigger, Sonic Pi provides a whole range of parameters to craft and control the sounds. We'll be covering many of these in this tutorial and there's extensive documentation for each in the help system. However, for now we'll cover introduce of the most useful: *amplitude*.  First, let's look at what parameters actually are.


## Parameters

Sonic Pi supports the notion of parameters for its synths and samples. Paramters are controls you pass to `play` or `sample` which modify and control aspects of the sound you hear. Each synth has its own set of parameters for finely tuning its sound. However there are common sets of paramters shared by many sounds such as `amp:` and envelop parameters (covered in another section).

Parameters have to major parts, their name (the name of the control) and their value (the value you want to set the control at). For example, you might have a paramter called `cheese:` and want to set it with a value of `1`.

Parameters are passed to calls to `play` and `sample` by using a comma `,` and then the name of the param such as `amp:` (don't forget the colon `:`) and then a space and the value of the parameter. For example:

```
play 50, cheese: 1
```

(Note that `cheese:` isn't a valid parameter we're just using it as an example).

You can pass multiple parameters by separating them with a comma: 

```
play 50, cheese: 1, beans: 0.5
```

The order of the parameters doesn't matter, so the following is identical:

```
play 50, beans: 0.5, cheese: 1
```

Parameters that aren't recognised by the synth are just ignored (like `cheese` and `beans` which are clearly ridiculous param names!). 

If you accidentally use the same parameter twice with different values, the last one wins. For example, `beans:` will have the value 2 rather than 0.5:

```
play 50, beans: 0.5, cheese: 3, eggs: 0.1, beans: 2
```

Many things in Sonic Pi accept parameters, so just spend a little time learning how to use them and you'll be set! Let's play with our first parameter: `amp:`.

## Amplitude

Amplitude is a computer representation of the loudness of a sound. A *high amplitude produces a loud sound* and a *low amplitude produces a quiet sound*. Just as Sonic Pi uses numbers to represent time and notes, it uses numbers to represent amplitude. An amplitude of 0 is silent (you'll hear nothing) whereas an amplitude of 1 is normal volume. You can even crank up the amplitude higher to 2, 10, 100. However, you should note that when the overall amplitude of all the sounds gets too high, Sonic Pi uses what's called a compressor to squash them all to make sure things aren't too loud for your ears. This can often make the sound muddy and strange. So try to use low amplitudes i.e. in the range 0 to 0.5 to avoid compression.



## Amp it up

To change the amplitude of a sound, you can use the `amp:` parameter. For example, to play at half amplitude pass 0.5:

```
play 60, amp: 0.5
```

To play at double amplitude pass 2:

```
play 60, amp: 2
```

The `amp:` param only modifies the call to `play` it's associated with. So, in this example, the first call to play is at half volume and the second is back to the default (1):

```
play 60, amp: 0.5
sleep 0.5
play 65
```

Of course, you can use different `amp:` values for each call to play:

```
play 50, amp: 0.1
sleep 0.25
play 55, amp: 0.2
sleep 0.25
play 57, amp: 0.4
sleep 0.25
play 62, amp: 1
```

## Amping samples

You can also change the amplitude of samples with the same approach:

```
sample :ambi_lunar_land, amp: 0.5
```

Now, go and have fun changing the amplitude of your sounds!