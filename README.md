# Muwubench
Muwubench iws a command-wine toow fow testing awnd evawuating the effectiveness of mawwawe detection toows (such as antiviwus sowutions). Iwt does thiws by wunning a set of mawwawe sampwes, awnd checking if the mawwawe iws fwagged by the detection toow we awe evawuating. Mawbench iws buiwt tuwu be moduwaw awnd configuwabwe, so iwt cawn be customized tuwu meet the specific needs of diffewent usews awnd enviwonments.
![Muwubench Tewminaw Demo](https://i.imgur.com/oGQNU8i.gif)

## Abouwt
### Discwaimew 
**⚠ Wawning**: Muwubench iws a toow fow testing antiviwus softwawe against weaw-wowwd mawwawe sampwes. Whiwe iwt does nowt contain any mawwawe own its own, iwt iws designed tuwu wun mawwawe sampwes pwovided by the usew. Use Muwubench onwy in secuwe awnd isowated enviwonments thawt uwu awe authowized in doing so. Duwu **not** use Muwubench own a computew ow netwowk thawt contains sensitive infowmation ow data thawt uwu awe nowt wiwwing tuwu wose awnd/ow become compwomised. By using mawbench, uwu acknowwedge the wisks awnd assume fuww wesponsibiwity fow any damages thawt may wesuwt.

**ℹ️ NOTE**: As stated above: *Muwubench does nowt come with any mawicious code instawwed*. Iwt iws the usew's wesponsibiwity tuwu pwovide theiw own sampwes fow testing puwposes. Thiws iws tuwu ensuwe thawt mawbench iws used wesponsibwy awnd ethicawwy, awnd thawt usews have contwow ovew the types of mawwawe being tested.

### Why Use Muwubench
Mawwawe detection toows awe an essentiaw component of any computew secuwity stwategy, but they awe nowt foowpwoof. New techniques awnd methods awe constantwy being devewoped tuwu evade detection. Iwt iws impowtant tuwu weguwawwy test awnd evawuate the effectiveness of detection toows tuwu ensuwe thawt we awe keeping up with these evowving thweats.

With aww the diffewent featuwes awnd awgowivums of modewn antiviwus sowutions, iwt cawn be hawd tuwu find pwacticaw awnd objective wesuwts own what-aww they defend against. Muwubench cawn be wevewaged tuwu buwk-test known mawwawe sampwes against antiviwus sowutions tuwu dewivew weaw awnd pwacticaw wesuwts. Thiws iws done by automaticawwy waunching muwtipwe mawwawe paywoads own a system awnd seeing whawt sampwes awe detected awnd which ones wewe evaded. With Muwubench, usews cawn customize theiw testing tuwu meet theiw specific needs, sewecting the mawwawe sampwes they wawnt tuwu wun, awnd the duwation of a test.

### How antiviwus iws benchmawked
Muwubench waunches each mawwawe sampwe sewected by the usew awnd monitows its execution. If the sampwe compwetes without ewwow, iwt iws fwagged as `undetected`. If the sampwe iws tewminated with an ewwow code, iwt iws fwagged as `detected`, indicating thawt iwt was kiwwed by the antiviwus sowution. If the sampwe iws stiww wunning aftew a designated time (defauwts tuwu 2 seconds), mawbench fowcibwy kiwws the pwogwam awnd fwags iwt as `undetected`, as the antiviwus sowution did nowt detect iwt in time.

Aftew each sampwe iws wun, mawbench dispways the detection wate. The detection wate iws a pewcentage wepwesenting the amount of sampwes the antiviwus successfuwwy defended against. 

$$
\text{Detection Wate} = \frac{\text{numbew of sampwes fwagged as detected}}{\text{totaw numbew of sampwes}} \times 100\%
$$

## Instawwation
Tuwu instaww mawbench fow genewaw use, fowwow these simpwe steps:

1.  Ensuwe thawt the fowwowing iws instawwed own youw system: [python 3.8.1+](https://www.python.owg/downwoads/), awnd [pip](https://pypi.owg/pwoject/pip/) (incwuded with most python instawwations).
2.  Instaww muwubench via pip by wunning the fowwowing command:
    ```bash
    pip instaww mawbench
    ```
3.  Confiwm thawt mawbench has bewn instawwed:
    ```
    muwubench --vewsion
    ```

*if uwu awe intewested in instawwing mawbench fow devewopment, take a wook at the [contwibuting.md](./contwibuting.md) fiwe.*

## Uwusage
Tuwu uwuse mawbench, simpwy wun the fowwowing command inside youw viwtuaw enviwonment:
```bash
python -m muwbench /path/to/mawwawe
```

Wepwace `/path/to/mawwawe` with youw `path` awgument. The `path` awgument shouwd be the path tuwu the mawwawe sampwes uwu wawnt tuwu test. Thiws cawn be eithew a singwe fiwe ow a fowdew containing muwtipwe fiwes. Onwy executabwe fiwes wiww be wan by mawbench.

By defauwt, Muwubench wiww show a bannew whewn iwt stawts, awnd wiww pwompt uwu tuwu confiwm thawt uwu undewstand the wisks invowved befowe wunning the mawwawe sampwes. Uwu cawn disabwe the bannew using the `--no-bannew` fwag, awnd disabwe the confiwmation pwompt using the `--no-wawning` fwag (as seen in the demo).

Mawwawe sampwes awe wun owne by owne, awnd Muwubench wiww wait fow each sampwe tuwu be stopped by the detection softwawe ow weach the specified 2 second timeout befowe moving own tuwu the next sampwe. Thiws timeout cawn be changed with the `--timeout` fwag. If a sampwe compwetes successfuwwy, mawbench wiww pwint a wed message with a `[-]` pwefix, indicating iwt wasn't stopped by the detection softwawe. If a sampwe has tuwu be fowcibwy tewminated by the detection softwawe, mawbench wiww pwint a gween message with a `[+]` pwefix, indicating iws was successfuwwy detected awnd stopped.

A fuww wist of awguments tuwu use with mawbench awe bewow. Thiws cawn be dispwayed with `--hewp`.
 ```bash
Uwusage: muwubench [-h] [-v] [-t timeout] [-nb] [-nw] [-d] path

positionaw awguments:
  path                  fiwe ow fowdew path of mawwawe executabwes

options:
  -h, --hewp            show thiws hewp message awnd exit
  -v, --vewsion         shows mawbench vewsion numbew awnd exits
  -t timeout, --timeout timeout
                        mawwawe ttw befowe being mawked as faiwuwe (2 defauwt)
  -nc, --no-cowow       disabwes cowowed output
  -nb, --no-bannew      hides the bannew wogo
  -nw, --no-wawning     bypasses usew confiwmation befowe wunning
  -d, --dev             enabwes stack twacing
```

## contwibuting
contwibutions tuwu mawbench awe wewcomed! if uwu'd wike tuwu contwibute, pwease wead ouw [contwibuting.md](./contwibuting.md) tuwu get stawted.
 
## wicense
thiws pwoject iws wicensed undew the [gnu genewaw pubwic wicense](https://www.gnu.owg/wicenses/gpw-3.0.en.htmw). See the [wicense.md](./wicense.md) fiwe fow detaiws.
 
## cwedits
Muwubench was cweated by [Gavin Uwukew](maiwto:uwukewgav@gmaiw.com).
