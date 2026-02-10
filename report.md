### Write Up

## 1: Baseline:

Output based on 500 tokens: 
```
BUCKINGHAM:
3 KING HENRY VI:
Beve you not before amont.

Firstst your subjust have the
sirtch not turnisly onather. GoO, love flove
Tustread than thas
I go yone sin is good curs.

BOMHERCR:
Whym ortward. you whoug many his mestent:
3 II, nou more suce
Prauged suded, not then unter some.
Was done, I advieyhtraw? Cair no apprough.

CAPUPULET:
Which is me, 'twere a my sack, grave. Well we'll ress parthom in'd I and not
I markly be ast this woorth it the your
jevanters.

MENEN ELIZA:
How fulless for


```
### Analysis:
- This is the basis of how the model works. It successfully learned the format the plays given as input to the model. It generated almost coherent 
and recognizable text. At first glance it looks like english, but if you try and read it, it is not quite english. A lot of the words are nonsensical 
or grammatically incorrect. This suggests that the model learned character patterns, but not semantic meaning. It did capture short words correctly. 
This is probably from high frequency patterns. 


## 2: Changing Max Iters

### Max at: 100

Output of same 500 tokens: 
```
B; eelane.
O3 thule b?Akhy tyd ve witinorirOn.
Gry f ngoKt fasltou ine,
Ave t hte eerd
Bir cUAnrld .
Cisenookpe w I't Ohol SeIoZo picuetowed emand e
Sore ofouno sis is ith y ue
T ne hed C fad ym o thanetiy cowy be menOn lluthith t:
3 thed thamor, herenondurenceadedMeng l mFn uUes gs y areased piEne adriey keawhe a;
Sn: aputou ourel hadd ne y, d slireveke c$st da mers, y, g 'se. he bhesore rere pan.
&e f Lwheraowo snof marollthig he -Yir woorowait ty wy:
Jr hpr dk slle fofuouee mowtoeqfu ce se l 


```

### Max at: 300

Output of same 500 tokens: 
```

B; emlant kl that his lomy ay bet witin,
Ard I Gramo ngo m fasstou sue,
Ave t hteres dfour chand d penis tookaave I't Onol bed Zo prinet,
Cd amand was
Theof hay sis is if hy de
Tmne hed Canfo ym o thand iy cowy be mand hrlomed hat:
3 thed thamor, surend dshencst ad,
Borl man unest s youreass
This ceadr:
Iher whe ainon: aput u ourel ladd'n.

Wld slireveke chst da my pas thad se. he bous.


ERCN panChot f Larerand m jof marovencs a't thif wherthait t coy:
Or her de slle fofud
Ast ENtobqut ceman t

```


### Max at: 1000

Output of same 500 tokens: 
```
If helle? Dll miblait, not and tho gomme, taigh an meshord.
I and have druesswe , nomn ane wind set!

Dow'd I whay to thot deirs my as berord Youllseer:
Yoll of slepl fich and goth me weare sgoon,
To la manfutse to hie with, hindy myy shronerker
Aks conde ifime thill it it shis bousplood,
That to mupongh son heracleg, yere a knould aphours,
Tish gun in Donord enp; me Gnove no. Yoouy cordsand, hastlior?

Cere; dencorther, grup thainks you'e thou soby to Rich, that jradoble'd,
Is I ilf yould his t
```

### Analysis: 
- Overall each output was worse. Since the model was only allowed to train for the set max iterations the model was not able to improve to the point 
that the 5000 default max iterations was. With each of the increase in max iterations, the appearance of words increased, but the words were 
still giberish. At 100 iterations the model did not understand the usuage of puncuation and showed it barely understood character patterns.
At 300 iterations it created more word like structures, but they were still not real words. By 1000 iterations the model was able to create 
more word like structures between many basic real words such as "and", "to", "my", "have" in addition to a better understanding of 
punctuation. However, the model still did not understand the meaning of the words and created many giberish words. 

## 3: Chaning the Dataset

### Output with 1000 iterations and showing 500 characters: 
```

"I any strided Harry slidn't hood boffechers of Duckelby dind the do fons." 

"It muse yean. 

"I wethe'd got. them dothe fow nere the dome beeasiore an fair this lousseed boofemitgs Go shemsped and and tap hulfap. How fong, DAffe you, wou--Xe Ronged gringw." Harry abe wecked fay. 

"Looze.." 

"Sou's towakind owll flor," Hally Rumedney 

"Whix. He meppetthith mening on te on were at theirs ofe his clookt?" 

He loked Pocle srop, conged any fulle and in antout thim."" 

"What, petle be Loursed h
```



### Analysis:
 - The model was able to learn the style of the Harry Potter dataset and compared to the shakespeare dataset it was able to understand the structure of a 
 book vs the play style that shakespeare used. The dataset is completly different and the model does not store the previous learnings from the shakespeare 
 dataset, so the output style will be completely different. The word and puncuation structure is also differnent because of a totally new dataset. Considering also when the datasets were written, the puncutation and word structure is different. The model was able to learn the new dataset and create a similar style of writing, but it still did not understand the meaning of the words and created many giberish words. The longer the word, the more likely it is to be giberish. 



 ## 4: Change the Tokenizer (4 Points)
 