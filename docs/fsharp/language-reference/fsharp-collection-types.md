---
title: Typy kolekcí F#
description: 'Další informace o typy kolekcí F # a jak se liší od typy kolekcí v rozhraní .NET Framework.'
ms.date: 05/16/2016
ms.openlocfilehash: a3cfc3f06582c31a79dce43b583eca39f69ddf1e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43864758"
---
# <a name="f-collection-types"></a>Typy kolekcí F#

V tomto tématu můžete určit, které typ jazyka F # kolekce nejlepší vyhovuje konkrétní požadavky. Tyto typy kolekcí se liší od typy kolekcí v rozhraní .NET Framework, jako například sítě na `System.Collections.Generic` obor názvů, v tom, že typy kolekcí F # jsou navržené tak z hlediska funkčního programování, nikoli objektově orientované perspektivy. Přesněji řečeno pouze kolekce pole má proměnlivé elementy. Proto při úpravě kolekce, vytvořit instanci upravené kolekce, místo aby se změna původní kolekci.

Typy kolekcí se liší v typu datové struktury, ve kterém jsou uložené objekty. Datové struktury, například zatřiďovacích tabulek, propojené seznamy a pole mají jiné výkonové charakteristiky a jinou množinu dostupných operací.

## <a name="f-collection-types"></a>Typy kolekcí F#

V následující tabulce jsou uvedeny typy kolekcí F #.

|Typ|Popis|Související odkazy|
|----|-----------|-------------|
|[Seznam](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|Seřazený, neměnné řadu prvků stejného typu. Implementovat jako propojeného seznamu.|[Seznamy](lists.md)<br /><br />[List – modul](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[Pole](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|Pevné velikosti, založený na nule, proměnlivé kolekce po sobě jdoucích datové prvky, které jsou všechny stejného typu.|[Pole](arrays.md)<br /><br />[Array – modul](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Array2d – modul](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Array3d – modul](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[SEQ](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|Logické řady elementů, které jsou jednoho typu. Sekvence jsou zvlášť užitečné, když máte velké, seřazené kolekce dat, ale Neočekáváme, že nemusí používat všechny prvky. Jednotlivé pořadí, které prvky se zpracovávají pouze jako požadované, takže sekvenci může mít lepší výkon než seznamu, není-li všechny prvky se používají. Sekvence jsou reprezentovány `seq<'T>` typu, což je alias pro `IEnumerable<T>`. Proto libovolný typ rozhraní .NET Framework, který implementuje `System.Collections.Generic.IEnumerable<'T>` může sloužit jako sekvenci.|[Sekvence](sequences.md)<br /><br />[SEQ – modul](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[Mapa](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|Neměnné slovník elementů. Prvky jsou přístupné pomocí klíče.|[Map – modul](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[Nastavit](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|Neměnné sady založené na binárních stromech, kde je porovnáním funkce strukturálního porovnání F #, potenciálně využívající implementace `System.IComparable` rozhraní klíčových hodnot.|[Set – modul](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>Tabulka funkcí

Tato část porovnává funkce, které jsou k dispozici na typy kolekcí F #. Je zadaný výpočetní složitost funkce, kde N je velikost první kolekce, a M je velikost druhá kolekce, pokud existuje. Pomlčkou (-) označuje, že tato funkce není dostupná pro kolekci. Sekvence se vyhodnocují laxně, funkce, jako je například Seq.distinct může být O(1) vzhledem k tomu, že se vrátí okamžitě, ale stále ovlivňuje výkon pořadí při výčtu.

|Funkce|Pole|Seznam|Pořadí|Mapa|Nastavit|Popis|
|--------|-----|----|--------|---|---|-----------|
|Připojení|O(M)|O(N)|O(N)|-|-|Vrátí novou kolekci, která obsahuje elementy první kolekce, za nímž následuje elementy druhé kolekci.|
|add|-|-|-|O (protokolu N)|O (protokolu N)|Vrátí novou kolekci s elementem přidán.|
|Průměr|O(N)|O(N)|O(N)|-|-|Vrátí průměr z prvků v kolekci.|
|averageBy|O(N)|O(N)|O(N)|-|-|Vrátí průměr z výsledků zadaná funkce na každý prvek.|
|blit –|O(N)|-|-|-|-|Zkopíruje část pole.|
|mezipaměť|-|-|O(N)|-|-|Vypočítá a uloží prvky pořadí.|
|přetypování|-|-|O(N)|-|-|Převede prvky zadaného typu.|
|Zvolte|O(N)|O(N)|O(N)|-|-|Použije danou funkci `f` na každý prvek `x` seznamu. Vrátí seznam, který obsahuje výsledky pro každý prvek, kde funkce vrátí `Some(f(x))`.|
|shromažďování|O(N)|O(N)|O(N)|-|-|Použije danou funkci na každý prvek kolekce, všechny výsledky zřetězit a vrátit kombinovaný seznam.|
|comparewith –|-|-|O(N)|-|-|Porovná dvě pořadí pomocí funkce dané porovnání prvek po prvku.|
|concat|O(N)|O(N)|O(N)|-|-|Kombinuje daný výčet sady výčtů jako jeden výčet zřetězených.|
|obsahuje|-|-|-|-|O (protokolu N)|Vrátí true, pokud sada obsahuje specifikovaný element.|
|containsKey|-|-|-|O (protokolu N)|-|Testuje, zda je prvek v doméně objektu map.|
|count|-|-|-|-|O(N)|Vrátí počet prvků v objektu set.|
|countby –|-|-|O(N)|-|-|Funkce generování klíče se vztahuje na každý prvek pořadí a vrátí sekvenci, která poskytuje jedinečné klíče a jejich počet výskytů v původní sekvenci.|
|copy|O(N)|-|O(N)|-|-|Kopíruje kolekci.|
|vytvoření|O(N)|-|-|-|-|Vytvoří pole celé prvky, které jsou všechny původně předané hodnoty.|
|zpoždění|-|-|O(1)|-|-|Vrátí sekvenci, která je vytvořená z daného zpožděné specifikaci pořadí.|
|rozdíl|-|-|-|-|O (M &#42; protokolu N)|Vrátí novou sadu, kdy elementy druhé sadě odebrány z první sady.|
|DISTINCT|||O(1)&AMP;#42;|||Vrátí sekvenci, která neobsahuje žádné duplicitní položky podle obecného porovnání rovnosti a hodnotu hash na položky. Pokud element dojde k více než jednou v sekvenci, novější výskytů se zahodí.|
|distinctby –|||O(1)&AMP;#42;|||Vrátí sekvenci, která neobsahuje žádné duplicitní položky podle obecného porovnání rovnosti a hodnotu hash na klíče, které vrátí danou funkci generování klíče. Pokud element dojde k více než jednou v sekvenci, novější výskytů se zahodí.|
|empty|O(1)|O(1)|O(1)|O(1)|O(1)|Vytvoří prázdnou kolekci.|
|Existuje|O(N)|O(N)|O(N)|O (protokolu N)|O (protokolu N)|Ověřuje, zda některý z sekvenci prvků splňuje daného predikátu.|
|exists2 –|O(min(N,M))|-|O(min(N,M))|||Testuje, jestli nějaká dvojice prvků odpovídající vstupní sekvence splňuje daného predikátu.|
|fill|O(N)|||||Nastaví rozsah prvků pole na zadanou hodnotu.|
|filtrování|O(N)|O(N)|O(N)|O(N)|O(N)|Vrátí novou kolekci, která obsahuje pouze elementy v kolekci, pro které daný predikát vrátí `true`.|
|find|O(N)|O(N)|O(N)|O (protokolu N)|-|Vrátí první prvek, pro kterou jsou dané funkce vrátí `true`. Vrátí `System.Collections.Generic.KeyNotFoundException` Pokud žádný takový prvek neexistuje.|
|findindex –|O(N)|O(N)|O(N)|-|-|Vrátí index prvního prvku v poli, která splňuje daného predikátu. Vyvolá `System.Collections.Generic.KeyNotFoundException` když žádný element nesplňuje predikát.|
|findKey|-|-|-|O (protokolu N)|-|Vyhodnocuje funkci na každý mapování v kolekci a vrátí klíč pro první mapování, kde funkce vrátí `true`. Pokud žádný takový prvek neexistuje, tato funkce vyvolá `System.Collections.Generic.KeyNotFoundException`.|
|fold|O(N)|O(N)|O(N)|O(N)|O(N)|Funkce se vztahuje na každý prvek kolekce dělení na vlákna argument akumulátor prostřednictvím výpočtu. Pokud je vstupní funkce f a prvky jsou i0... v, tato funkce vypočítá f (...) (f s i0)...) v.|
|fold2 –|O(N)|O(N)|-|-|-|Funkce se vztahuje na odpovídající prvky dvou kolekcí, práce s vlákny argument akumulátor prostřednictvím výpočtu. Kolekce musí mít stejné velikosti. Pokud je vstupní funkce f a prvky jsou i0... v a... j0 – jN, tato funkce vypočítá f (...) (j0 – f s i0)...) v jN.|
|foldback –|O(N)|O(N)|-|O(N)|O(N)|Funkce se vztahuje na každý prvek kolekce dělení na vlákna argument akumulátor prostřednictvím výpočtu. Pokud je vstupní funkce f a prvky jsou i0... v, tato funkce vypočítá f i0 (...) (f v s)).|
|foldback2 –|O(N)|O(N)|-|-|-|Funkce se vztahuje na odpovídající prvky dvou kolekcí, práce s vlákny argument akumulátor prostřednictvím výpočtu. Kolekce musí mít stejné velikosti. Pokud je vstupní funkce f a prvky jsou i0... v a... j0 – jN, tato funkce vypočítá j0 – i0 f (...) (f v jN s)).|
|ForAll|O(N)|O(N)|O(N)|O(N)|O(N)|Testuje, jestli splňují všechny elementy z kolekce daného predikátu.|
|forall2 –|O(N)|O(N)|O(N)|-|-|Ověřuje, zda všechny odpovídající elementy kolekce ukládání splňují daného predikátu.|
|získat / n-tý|O(1)|O(N)|O(N)|-|-|Vrátí element z kolekce uveden jeho index.|
|hlavní|-|O(1)|O(1)|-|-|Vrátí první prvek kolekce.|
|Inicializace|O(N)|O(N)|O(1)|-|-|Vytvoří kolekci pomocí dimenze a generátoru funkcí pro výpočet prvků.|
|initinfinite –|-|-|O(1)|-|-|Generuje posloupnost, která, pokud provést iteraci, vrátí po sobě jdoucí prvky pomocí volání dané funkce.|
|Intersect|-|-|-|-|O (protokolu N &#42; protokolu M)|Vypočítá průnik dvou sad.|
|intersectmany –|-|-|-|-|O (N1 &AMP;#42; N2...)|Vypočítá průnik posloupnost sady. Pořadí nesmí být prázdný.|
|IsEmpty|O(1)|O(1)|O(1)|O(1)|-|Vrátí `true` Pokud kolekce je prázdná.|
|ispropersubset –|-|-|-|-|O (M &#42; protokolu N)|Vrátí `true` Pokud jsou všechny prvky první sady ve druhé sadě a alespoň jeden prvek druhé sady není v sadě první.|
|ispropersuperset –|-|-|-|-|O (M &#42; protokolu N)|Vrátí `true` Pokud jsou všechny prvky druhé sady v první sadě a alespoň jeden prvek první sady není v druhé sadě.|
|issubset –|-|-|-|-|O (M &#42; protokolu N)|Vrátí `true` Pokud jsou všechny prvky první sady ve druhé sadě.|
|issuperset –|-|-|-|-|O (M &#42; protokolu N)|Vrátí `true` Pokud jsou všechny prvky druhé sady v první sadě.|
|ITER|O(N)|O(N)|O(N)|O(N)|O(N)|Použije danou funkci na každý prvek kolekce.|
|iteri –|O(N)|O(N)|O(N)|-|-|Použije danou funkci na každý prvek kolekce. Celé číslo, který je předán funkci označuje index prvku.|
|iteri2 –|O(N)|O(N)|-|-|-|Použije danou funkci na dvojici prvků, které jsou vykreslovány vedle z odpovídajících indexů ve dvou polích. Celé číslo, který je předán funkci označuje index prvků. Dvě pole musí mít stejnou délku.|
|iter2 –|O(N)|O(N)|O(N)|-|-|Použije danou funkci na dvojici prvků, které jsou vykreslovány vedle z odpovídajících indexů ve dvou polích. Dvě pole musí mít stejnou délku.|
|length|O(1)|O(N)|O(N)|-|-|Vrátí počet prvků v kolekci.|
|map|O(N)|O(N)|O(1)|-|-|Sestaví kolekci, jehož prvky jsou výsledkem použití dané funkce na každý prvek pole.|
|map2 –|O(N)|O(N)|O(1)|-|-|Sestaví kolekci, jehož prvky jsou výsledkem použití dané funkce na odpovídající prvky dvou kolekcí ukládání. Dvě vstupní pole musí mít stejnou délku.|
|map3 –|-|O(N)|-|-|-|Sestaví kolekci, jehož prvky jsou výsledkem použití dané funkce na odpovídající elementy z těchto tří kolekcí současně.|
|rozhraní MAPI|O(N)|O(N)|O(N)|-|-|Vytvoří pole, jehož prvky jsou výsledkem použití dané funkce na každý prvek pole. Celočíselný index předaný funkci označuje index prvku, který je prováděna transformace.|
|mapi2 –|O(N)|O(N)|-|-|-|Sestaví kolekci, jehož prvky jsou výsledkem použití dané funkce na odpovídající prvky dvou kolekcí pairwise také předá index prvků. Dvě vstupní pole musí mít stejnou délku.|
|max|O(N)|O(N)|O(N)|-|-|Vrátí nejvyšší prvek v kolekci, ve srovnání s použitím [maximální](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) operátor.|
|maxby –|O(N)|O(N)|O(N)|-|-|Vrátí nejvyšší prvek v kolekci, ve srovnání s použitím [maximální](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) na výsledek funkce.|
|maxelement –|-|-|-|-|O (protokolu N)|Vrátí nejvyšší prvek v sadě podle řazení, který se používá pro sadu.|
|min|O(N)|O(N)|O(N)|-|-|Vrátí nejnižší prvek v kolekci, ve srovnání s použitím [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) operátor.|
|minby –|O(N)|O(N)|O(N)|-|-|Vrátí nejnižší prvek v kolekci, ve srovnání s použitím [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) operátor na výsledek funkce.|
|minelement –|-|-|-|-|O (protokolu N)|Vrátí nejnižší prvek v sadě podle řazení používaného pro sadu.|
|ofarray –|-|O(N)|O(1)|O(N)|O(N)|Vytvoří kolekci, která obsahuje stejný prvek jako daného pole.|
|oflist –|O(N)|-|O(1)|O(N)|O(N)|Vytvoří kolekci, která obsahuje stejný prvek jako předaném seznamu.|
|ofseq –|O(N)|O(N)|-|O(N)|O(N)|Vytvoří kolekci, která obsahuje stejný prvek jako dané sekvence.|
|ukládání|-|-|O(N)|-|-|Vrátí sekvenci každý prvek ve vstupní sekvence a jeho předchůdcem s výjimkou prvního prvku, který je vrácen pouze jako předchůdce druhý prvek.|
|partition|O(N)|O(N)|-|O(N)|O(N)|Rozdělí kolekci na dvě kolekce. První kolekce obsahuje prvky, pro které daný predikát vrátí `true`, a druhá kolekce obsahuje prvky, pro které daný predikát vrátí `false`.|
|permute –|O(N)|O(N)|-|-|-|Vrátí pole obsahující všechny prvky permutovanou funkci podle zadaného permutaci.|
|Výběr|O(N)|O(N)|O(N)|O (protokolu N)|-|Použije danou funkci na po sobě jdoucí prvky vrací první výsledek, kde funkce vrátí některé. Pokud funkce vrátí nikdy některé, `System.Collections.Generic.KeyNotFoundException` je vyvolána.|
|readonly|-|-|O(N)|-|-|Vytvoří objekt sekvence, která deleguje daný objekt sekvence. Tato operace zajistí, že nelze přetypování opětovné zjištění a mutovat původní pořadí. Například pole směru, je-li vrácená sekvence vrátí prvky pole, ale nelze přetypovat objekt vrácený sekvence na pole.|
|snížení|O(N)|O(N)|O(N)|-|-|Funkce se vztahuje na každý prvek kolekce dělení na vlákna argument akumulátor prostřednictvím výpočtu. Tato funkce spustí použitím funkce do první dva prvky, předá tento výsledek do funkce spolu s třetí elementu a tak dále. Funkce vrátí konečný výsledek.|
|reduceback –|O(N)|O(N)|-|-|-|Funkce se vztahuje na každý prvek kolekce dělení na vlákna argument akumulátor prostřednictvím výpočtu. Pokud je vstupní funkce f a prvky jsou i0... v, tato funkce vypočítá f i0 (...) (f v 1 v)).|
|remove|-|-|-|O (protokolu N)|O (protokolu N)|Odebere element z domény na mapě. Pokud element není k dispozici, je vyvolána žádná výjimka.|
|Replikace|-|O(N)|-|-|-|Vytvoří seznam zadané délky se každý prvek nastavit na zadanou hodnotu.|
|rev|O(N)|O(N)|-|-|-|Vrátí nový seznam s prvky v obráceném pořadí.|
|Kontrola|O(N)|O(N)|O(N)|-|-|Funkce se vztahuje na každý prvek kolekce dělení na vlákna argument akumulátor prostřednictvím výpočtu. Tato operace použije funkci na druhý argument a první prvek v seznamu. Operace pak předá tento výsledek do funkce spolu s druhý element a tak dále. Nakonec se operace vrátí seznam mezilehlých výsledků a konečný výsledek.|
|scanback –|O(N)|O(N)|-|-|-|Operace foldback – se podobá, ale vrací pomocných a finální výsledky.|
|singleton|-|-|O(1)|-|O(1)|Vrátí sekvenci, která vrací pouze jednu položku.|
|set|O(1)|-|-|-|-|Nastaví prvek pole se zadanou hodnotou.|
|Přeskočit|-|-|O(N)|-|-|Vrátí sekvenci, který přeskočí N prvků základní pořadí a pak vrací zbývající prvky pořadí.|
|SkipWhile –|-|-|O(N)|-|-|Vrátí pořadí, že když provést iteraci, přeskočí prvků základní pořadí a daný predikát vrátí `true` a pak vrací zbývající prvky pořadí.|
|sort|Průměr O (protokolu N N)<br /><br />Nejhorším případě O(N^2)|O (protokolu N N)|O (protokolu N N)|-|-|Kolekce jsou řazeny podle hodnoty prvku. Prvky jsou porovnány pomocí [porovnání](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortBy|Průměr O (protokolu N N)<br /><br />Nejhorším případě O(N^2)|O (protokolu N N)|O (protokolu N N)|-|-|Seřadí dané seznamu s použitím klíče, které poskytuje zadané projekce. Klíče jsou porovnány pomocí [porovnání](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortinplace –|Průměr O (protokolu N N)<br /><br />Nejhorším případě O(N^2)|-|-|-|-|Seřadí prvky pole mutace na místě a pomocí funkce dané porovnání. Prvky jsou porovnány pomocí [porovnání](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortinplaceby –|Průměr O (protokolu N N)<br /><br />Nejhorším případě O(N^2)|-|-|-|-|Seřadí prvky pole podle mutace na místě a pomocí zadané projekce pro klíče. Prvky jsou porovnány pomocí [porovnání](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortinplacewith –|Průměr O (protokolu N N)<br /><br />Nejhorším případě O(N^2)|-|-|-|-|Seřadí prvky pole mutace na místě a pomocí funkce porovnání daného jako pořadí.|
|sortwith –|Průměr O (protokolu N N)<br /><br />Nejhorším případě O(N^2)|O (protokolu N N)|-|-|-|Seřadí prvky kolekce, pomocí funkce porovnání daného jako pořadí a vrátí novou kolekci.|
|Sub|O(N)|-|-|-|-|Sestavení obsahující daný dílčí sadu, která je zadána počáteční index a délka pole.|
|Součet|O(N)|O(N)|O(N)|-|-|Vrátí součet položek v kolekci.|
|sumBy|O(N)|O(N)|O(N)|-|-|Vrátí součet výsledky, které jsou generovány použitím funkce na každý prvek kolekce.|
|Funkce Tail|-|O(1)|-|-|-|Vrátí seznam bez jeho první prvek.|
|Take|-|-|O(N)|-|-|Vrátí elementy pořadí až do zadaného počtu.|
|TakeWhile –|-|-|O(1)|-|-|Vrátí pořadí, že když provést iteraci, výnosů prvků základní pořadí a daný predikát vrátí `true` a vrátí žádné další prvky.|
|ToArray –|-|O(N)|O(N)|O(N)|O(N)|Vytvoří pole ze zadané kolekce.|
|ToList –|O(N)|-|O(N)|O(N)|O(N)|Vytvoří seznam ze zadané kolekce.|
|toseq –|O(1)|O(1)|-|O(1)|O(1)|Vytvoří posloupnost ze zadané kolekce.|
|zkrátit|-|-|O(1)|-|-|Vrátí sekvenci, která při výčtu, vrátí více než N prvků.|
|tryfind –|O(N)|O(N)|O(N)|O (protokolu N)|-|Vyhledá prvek, který splňuje daného predikátu.|
|tryfindindex –|O(N)|O(N)|O(N)|-|-|Vyhledá první prvek, který splňuje daného predikátu. potom vrátí index elementu odpovídající nebo `None` Pokud žádný takový prvek neexistuje.|
|tryfindkey –|-|-|-|O (protokolu N)|-|Vrátí klíč první mapování v kolekci, která splňuje daného predikátu nebo vrátí `None` Pokud žádný takový prvek neexistuje.|
|trypick –|O(N)|O(N)|O(N)|O (protokolu N)|-|Použije danou funkci po sobě jdoucí prvky vrací první výsledek, kde funkce vrátí `Some` pro některá z hodnot. Pokud žádný takový prvek neexistuje, operace vrátí `None`.|
|Rozbalit|-|-|O(N)|-|-|Vrátí sekvenci, která obsahuje elementy, které generuje daný výpočet.|
|sjednocení|-|-|-|-|O (M &#42; protokolu N)|Vypočítá sjednocení dvou sad.|
|unionmany –|-|-|-|-|O (N1 &AMP;#42; N2...)|Vypočítá sjednocení posloupnost sady.|
|Rozbalte|O(N)|O(N)|O(N)|-|-|Seznam dvojic, přičemž se rozdělí na dva seznamy.|
|unzip3 –|O(N)|O(N)|O(N)|-|-|Rozdělí seznam trojic do tří seznamy.|
|oddílové|-|-|O(N)|-|-|Vrátí sekvenci, která vrací posuvného okna obsahující prvky, které jsou zpracovány ze vstupní sekvence. Každé okno se vrátí jako nové pole.|
|PSČ|O(N)|O(N)|O(N)|-|-|Kombinuje dvě kolekce do seznamu párů. Dva seznamy musí mít stejnou délku.|
|zip3 –|O(N)|O(N)|O(N)|-|-|Kombinací těchto tří kolekcí trojic do seznamu. Seznamy musí mít stejnou délku.|

## <a name="see-also"></a>Viz také:

- [Typy F#](fsharp-types.md)
- [Referenční dokumentace jazyka F#](index.md)
