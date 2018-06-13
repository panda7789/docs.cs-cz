---
title: Typy kolekcí F#
description: 'Další informace o typy kolekcí F # a jak se liší od typy kolekcí v rozhraní .NET Framework.'
ms.date: 05/16/2016
ms.openlocfilehash: a94dc300d984ca31baf1eb7d1073e23b51ebd030
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566844"
---
# <a name="f-collection-types"></a>Typy kolekcí F#

V tomto tématu můžete určit, které F # – typ kolekce nejlepší vyhovuje konkrétní požadavky. Tyto typy kolekcí se liší od typy kolekcí v rozhraní .NET Framework, jako jsou ty v `System.Collections.Generic` obor názvů, v tom, že typy kolekcí F # jsou navržené tak z hlediska funkčnosti programování, nikoli objektově orientované perspektivy. Přesněji řečeno jenom u pole kolekce je měnitelný elementy. Proto když upravíte kolekce, vytvořit instanci upravené kolekce, místo aby se změna původní kolekci.

Typy kolekcí se také liší z hlediska typu datová struktura, v níž jsou uloženy objekty. Datové struktury například zatřiďovacích tabulkách, propojené seznamy a pole mají různé výkonové charakteristiky a jinou sadu dostupné operace.


## <a name="f-collection-types"></a>Typy kolekcí F#
V následující tabulce jsou uvedeny typy kolekcí F #.



|Typ|Popis|Související odkazy|
|----|-----------|-------------|
|[seznam](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|Seřazený, neměnné řada elementů stejného typu. Implementovaný jako odkazovaného seznamu.|[Seznamy](lists.md)<br /><br />[List – modul](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[Pole](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|Pevné velikosti, počítáno od nuly, měnitelnou kolekci po sobě jdoucích datové prvky, které jsou všechny stejného typu.|[Pole](arrays.md)<br /><br />[Array – modul](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Array2d – modul](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Array3d – modul](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[SEQ](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|Logické řadu prvky, které jsou všechny jednoho typu. Pořadí jsou zvláště užitečné, když máte velký, seřazené shromažďování dat, ale nejsou nezbytně očekávat používat všechny elementy. Jednotlivé pořadí, které elementy se vypočítávají pouze jako povinné, tak můžete lépe než seznam provádět sekvenci, není-li se používají všechny elementy. Pořadí jsou reprezentované pomocí `seq<'T>` typu, který je alias pro `IEnumerable<T>`. Proto žádný typ rozhraní .NET Framework, který implementuje `System.Collections.Generic.IEnumerable<'T>` lze použít jako sekvenci.|[Sekvence](sequences.md)<br /><br />[SEQ – modul](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[mapy](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|Neměnné slovník elementů. Elementy jsou dostupné přes klíč.|[Map – modul](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[nastavení](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|Neměnné sadu, která je založená na binární stromy, kde porovnání je F # strukturální porovnání, který používá potenciálně implementace `System.IComparable` rozhraní na klíčové hodnoty.|[Set – modul](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>Tabulka funkcí
Tato část obsahuje porovnání funkcí, které jsou k dispozici na typy kolekcí F #. Výpočetní složitost funkce není uveden, kde N je velikost první kolekce a M je velikost druhé kolekci, pokud existuje. Pomlčkou (-) označuje, že tato funkce není k dispozici v kolekci. Protože vyhodnocují líné pořadí, funkce, jako je například SEQ.DISTINCT – pravděpodobně o(1), která vrátí okamžitě, i když stále ovlivňuje výkon pořadí při výčtu.



|Funkce|Pole|Seznam|Pořadí|mapy|nastavení|Popis|
|--------|-----|----|--------|---|---|-----------|
|Připojit|O(M)|O(N)|O(N)|-|-|Vrátí novou kolekci, která obsahuje elementy první kolekce, za nímž následuje elementy druhé kolekci.|
|add|-|-|-|O (protokol N)|O (protokol N)|Vrátí novou kolekci s elementu přidány.|
|Průměr|O(N)|O(N)|O(N)|-|-|Vrátí průměr elementů v kolekci.|
|averageby –|O(N)|O(N)|O(N)|-|-|Vrátí průměr výsledky zadaná funkce pro každý prvek použít.|
|blit|O(N)|-|-|-|-|Zkopíruje oddíl pole.|
|mezipaměť|-|-|O(N)|-|-|Vypočítá a uloží elementy pořadí.|
|přetypování|-|-|O(N)|-|-|Převede elementy zadaného typu.|
|Zvolte|O(N)|O(N)|O(N)|-|-|Platí danou funkci `f` na každý element `x` seznamu. Vrátí seznam, který obsahuje výsledky pro každý element, kde funkce vrátí hodnotu `Some(f(x))`.|
|shromažďování|O(N)|O(N)|O(N)|-|-|Platí pro každý prvek kolekce danou funkci, zřetězí všechny výsledky a vrátí součet seznamu.|
|comparewith –|-|-|O(N)|-|-|Porovná dvě pořadí pomocí funkci porovnání daného elementu pomocí elementu.|
|concat|O(N)|O(N)|O(N)|-|-|Kombinuje dané – výčet z – výčty jako jeden zřetězených výčtu.|
|obsahuje|-|-|-|-|O (protokol N)|Vrátí hodnotu true Pokud sada obsahuje zadaný element.|
|containsKey|-|-|-|O (protokol N)|-|Ověřuje, zda je element v doméně mapy.|
|count|-|-|-|-|O(N)|Vrátí počet prvků v objektu set.|
|countby –|-|-|O(N)|-|-|Funkce generování klíče se vztahuje na každý prvek pořadí a vrátí sekvenci, která vypočítá jedinečné klíče a jejich počet výskytů na původní pořadí.|
|copy|O(N)|-|O(N)|-|-|Kopíruje kolekci.|
|vytvoření|O(N)|-|-|-|-|Vytvoří pole celou elementů, které jsou všechny původně předané hodnoty.|
|Zpoždění|-|-|O(1), KTERÁ|-|-|Vrátí sekvenci, která vychází z daného zpožděné specifikaci pořadí.|
|rozdíl|-|-|-|-|O (M &#42; protokolu N)|Vrátí novou sadu, kdy elementy druhé sadě odebrány z první sady.|
|Odlišné|||O(1), KTERÁ&AMP;#42;|||Vrátí pořadí, které obsahuje neobsahoval duplicitní položky podle obecné porovnání rovnosti a hodnotu hash na položky. Pokud element vyskytuje opakovaně v pořadí, novější události se zahodí.|
|distinctby –|||O(1), KTERÁ&AMP;#42;|||Vrátí pořadí, které obsahuje neobsahoval duplicitní položky podle obecné porovnání hodnoty hash a rovnosti na klíčů, které vrátí danou funkci generování klíče. Pokud element vyskytuje opakovaně v pořadí, novější události se zahodí.|
|empty|O(1), KTERÁ|O(1), KTERÁ|O(1), KTERÁ|O(1), KTERÁ|O(1), KTERÁ|Vytvoří prázdnou kolekci.|
|existuje|O(N)|O(N)|O(N)|O (protokol N)|O (protokol N)|Ověřuje, zda libovolný element pořadí splňuje daného predikátu.|
|exists2 –|O(min(N,M))|-|O(min(N,M))|||Ověřuje, zda žádném páru odpovídající elementů vstupních sekvencí splňuje daného predikátu.|
|fill|O(N)|||||Nastaví rozsah elementy pole na zadanou hodnotu.|
|filtrování|O(N)|O(N)|O(N)|O(N)|O(N)|Vrátí novou kolekci, která obsahuje pouze elementy kolekce, pro který daného predikátu vrátí `true`.|
|find|O(N)|O(N)|O(N)|O (protokol N)|-|Vrátí první prvek, pro který dané funkce vrátí `true`. Vrátí `System.Collections.Generic.KeyNotFoundException` Pokud neexistuje žádný takový prvek.|
|findIndex|O(N)|O(N)|O(N)|-|-|Vrátí index první prvek v poli, která splňuje daného predikátu. Vyvolá `System.Collections.Generic.KeyNotFoundException` Pokud žádný element splňuje predikátu.|
|findKey –|-|-|-|O (protokol N)|-|Vyhodnotí funkce na každý mapování v kolekci a vrátí klíč pro první mapování, kde funkce vrátí hodnotu `true`. Pokud žádný takový prvek existuje, tato funkce vyvolá `System.Collections.Generic.KeyNotFoundException`.|
|fold –|O(N)|O(N)|O(N)|O(N)|O(N)|Funkce se vztahuje na každý prvek kolekce, dělení na vlákna argument akumulátorová prostřednictvím výpočet. Pokud je vstupní funkce f a elementy jsou i0... v, tato funkce vypočítá f (... (f s i0)...) v.|
|fold2 –|O(N)|O(N)|-|-|-|Funkce se vztahuje na odpovídající elementy dvě kolekce, dělení na vlákna argument akumulátorová prostřednictvím výpočet. Kolekce musí mít identické velikosti. Pokud je vstupní funkce f a elementy jsou i0... v a j0 –... jN, tato funkce vypočítá f (... (j0 – f s i0)...) v jN.|
|foldBack|O(N)|O(N)|-|O(N)|O(N)|Funkce se vztahuje na každý prvek kolekce, dělení na vlákna argument akumulátorová prostřednictvím výpočet. Pokud je vstupní funkce f a elementy jsou i0... v, tato funkce vypočítá f i0 (... (f za s)).|
|foldback2 –|O(N)|O(N)|-|-|-|Funkce se vztahuje na odpovídající elementy dvě kolekce, dělení na vlákna argument akumulátorová prostřednictvím výpočet. Kolekce musí mít identické velikosti. Pokud je vstupní funkce f a elementy jsou i0... v a j0 –... jN, tato funkce vypočítá j0 – f i0 (... (f v jN s)).|
|ForAll|O(N)|O(N)|O(N)|O(N)|O(N)|Ověřuje, zda všechny elementy kolekce uspokojení daného predikátu.|
|forall2 –|O(N)|O(N)|O(N)|-|-|Ověřuje, zda všechny odpovídající elementy kolekce ukládání uspokojení daného predikátu.|
|získat / n-tou|O(1), KTERÁ|O(N)|O(N)|-|-|Vrátí element z kolekce danou její index.|
|HEAD|-|O(1), KTERÁ|O(1), KTERÁ|-|-|Vrátí první prvek kolekce.|
|Init –|O(N)|O(N)|O(1), KTERÁ|-|-|Vytvoří kolekci daného dimenze a generátor funkce pro výpočet elementy.|
|initinfinite –|-|-|O(1), KTERÁ|-|-|Generuje pořadí, pokud vstupní, vrátí následných elementy voláním danou funkci.|
|Intersect|-|-|-|-|O (protokolu N &#42; protokolu M)|Vypočítá průnik dvou sad.|
|intersectmany –|-|-|-|-|O (N1 &AMP;#42; N2...)|Vypočítá průnik pořadí sad. Pořadí nesmí být prázdný.|
|IsEmpty –|O(1), KTERÁ|O(1), KTERÁ|O(1), KTERÁ|O(1), KTERÁ|-|Vrátí `true` Pokud kolekce je prázdná.|
|ispropersubset –|-|-|-|-|O (M &#42; protokolu N)|Vrátí `true` Pokud jsou všechny elementy z první sady v druhé sadě a alespoň jeden element druhé sadě není v první sady.|
|ispropersuperset –|-|-|-|-|O (M &#42; protokolu N)|Vrátí `true` Pokud všechny elementy druhé sady jsou v sadě první a alespoň jeden prvek z první sady není v druhé sadě.|
|issubset –|-|-|-|-|O (M &#42; protokolu N)|Vrátí `true` Pokud jsou všechny elementy z první sady v druhé sadě.|
|issuperset –|-|-|-|-|O (M &#42; protokolu N)|Vrátí `true` Pokud všechny elementy druhé sady jsou v sadě první.|
|ITER –|O(N)|O(N)|O(N)|O(N)|O(N)|Každý prvek kolekce se týká danou funkci.|
|iteri –|O(N)|O(N)|O(N)|-|-|Každý prvek kolekce se týká danou funkci. Celé číslo, které je předaný funkci značí index elementu.|
|iteri2 –|O(N)|O(N)|-|-|-|Dané funkce se vztahuje na pár prvky, které jsou vykreslovány z odpovídající indexy v dvěma poli. Celé číslo, které je předaný funkci značí index elementů. Tato dvě pole musí mít stejnou délku.|
|iter2 –|O(N)|O(N)|O(N)|-|-|Dané funkce se vztahuje na pár prvky, které jsou vykreslovány z odpovídající indexy v dvěma poli. Tato dvě pole musí mít stejnou délku.|
|length|O(1), KTERÁ|O(N)|O(N)|-|-|Vrátí počet prvků v kolekci.|
|map|O(N)|O(N)|O(1), KTERÁ|-|-|Sestaví kolekci, jehož elementy jsou výsledky použití danou funkci pro každý element pole.|
|map2 –|O(N)|O(N)|O(1), KTERÁ|-|-|Sestaví kolekci, jehož elementy jsou výsledky ukládání použitím dané funkce pro odpovídající elementy dvě kolekce. Dvě vstupní pole musí mít stejnou délku.|
|map3 –|-|O(N)|-|-|-|Sestaví kolekci, jehož elementy jsou výsledky použitím dané funkce pro odpovídající elementy tři kolekcí současně.|
|MAPI|O(N)|O(N)|O(N)|-|-|Sestaví pole jehož elementy jsou výsledky použití danou funkci pro každý element pole. Celočíselný index, který je předán do funkce značí index elementu, který je prováděna transformace.|
|mapi2 –|O(N)|O(N)|-|-|-|Sestaví kolekci, jehož elementy jsou výsledky použitím dané funkce pro odpovídající elementy dvě kolekce pairwise, také předávání index elementů. Dvě vstupní pole musí mít stejnou délku.|
|max|O(N)|O(N)|O(N)|-|-|Vrátí nejvyšší element v kolekci, ve srovnání s použitím [maximální](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) operátor.|
|maxby –|O(N)|O(N)|O(N)|-|-|Vrátí nejvyšší element v kolekci, ve srovnání s použitím [maximální](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) u výsledku funkce.|
|maxelement –|-|-|-|-|O (protokol N)|Vrátí největší prvek v sadě podle pořadí, který se používá pro sadu.|
|min|O(N)|O(N)|O(N)|-|-|Vrátí nejmenší element v kolekci, ve srovnání s použitím [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) operátor.|
|minby –|O(N)|O(N)|O(N)|-|-|Vrátí nejmenší element v kolekci, ve srovnání s použitím [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) operátor u výsledku funkce.|
|minelement –|-|-|-|-|O (protokol N)|Vrátí nejnižší prvek v sadě podle pořadí, který se používá pro sadu.|
|ofarray –|-|O(N)|O(1), KTERÁ|O(N)|O(N)|Vytvoří kolekci, která obsahuje stejné prvky jako daném poli.|
|oflist –|O(N)|-|O(1), KTERÁ|O(N)|O(N)|Vytvoří kolekci, která obsahuje stejné prvky jako daného seznamu.|
|ofseq –|O(N)|O(N)|-|O(N)|O(N)|Vytvoří kolekci, která obsahuje stejné prvky jako daného pořadí.|
|ukládání|-|-|O(N)|-|-|Vrátí pořadí jednotlivých prvků vstupní pořadí a jeho předchůdce s výjimkou první prvek, který je vrácen pouze jako předchůdcem druhý prvkem.|
|partition|O(N)|O(N)|-|O(N)|O(N)|Rozdělí kolekci do dvě kolekce. První kolekce obsahuje prvky, pro které se vrátí daného predikátu `true`, a druhá kolekce obsahuje prvky, pro které se vrátí daného predikátu `false`.|
|permute –|O(N)|O(N)|-|-|-|Vrátí pole s všechny elementy podle zadaného Permutace permutovanou funkci.|
|Vyberte|O(N)|O(N)|O(N)|O (protokol N)|-|Dané funkce se vztahuje na následných elementy, vrátí první výsledek, kde některé funkce vrátí. Pokud některé funkce nikdy vrátí `System.Collections.Generic.KeyNotFoundException` je vyvolána.|
|readonly|-|-|O(N)|-|-|Vytvoří objekt pořadí, která deleguje pro objekt daného pořadí. Tato operace zajišťuje, že nelze přetypování opakované zjišťování a mutovat původní pořadí. Například pokud zadané pole, vrácený pořadí vrátí elementy pole, ale nelze převést objekt vrácený sekvence na pole.|
|snížení|O(N)|O(N)|O(N)|-|-|Funkce se vztahuje na každý prvek kolekce, dělení na vlákna argument akumulátorová prostřednictvím výpočet. Tato funkce spustí použitím funkce na první dva elementy, předá tento výsledek do funkce společně s třetí elementu a tak dále. Funkce vrátí konečný výsledek.|
|reduceback –|O(N)|O(N)|-|-|-|Funkce se vztahuje na každý prvek kolekce, dělení na vlákna argument akumulátorová prostřednictvím výpočet. Pokud je vstupní funkce f a elementy jsou i0... v, tato funkce vypočítá f i0 (... (f v 1 v)).|
|remove|-|-|-|O (protokol N)|O (protokol N)|Odebere element z domény mapy. Pokud element není k dispozici, je vyvolána žádná výjimka.|
|replikace|-|O(N)|-|-|-|Vytvoří seznam zadané délky se každý element nastavit na zadanou hodnotu.|
|rev|O(N)|O(N)|-|-|-|Vrátí nový seznam s elementy v obráceném pořadí.|
|Kontrola|O(N)|O(N)|O(N)|-|-|Funkce se vztahuje na každý prvek kolekce, dělení na vlákna argument akumulátorová prostřednictvím výpočet. Tato operace platí funkce pro druhý argument a první prvek seznamu. Operaci poté předá tento výsledek do funkce společně s druhý prvkem a tak dále. Nakonec operaci vrátí seznam mezilehlých výsledků a konečný výsledek.|
|scanback –|O(N)|O(N)|-|-|-|Podobá foldBack operaci, ale vrací zprostředkující a finální výsledky.|
|singleton|-|-|O(1), KTERÁ|-|O(1), KTERÁ|Vrátí pořadí, které poskytuje jen jednu položku.|
|set|O(1), KTERÁ|-|-|-|-|Element pole se nastaví na zadanou hodnotu.|
|Přeskočit|-|-|O(N)|-|-|Vrátí pořadí, které přeskočí N prvků základní pořadí a pak vypočítá zbývající elementy sekvence.|
|SkipWhile|-|-|O(N)|-|-|Vrátí pořadí, že pokud vstupní, přeskočí elementy základní pořadí při daném predikátu vrátí `true` a pak vypočítá zbývající elementy sekvence.|
|sort|Průměr O (protokol N N)<br /><br />Nejhorším případě O(N^2)|O (protokol N N)|O (protokol N N)|-|-|Kolekce jsou řazeny podle hodnota elementu. Elementy jsou porovnávány pomocí [porovnat](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortBy|Průměr O (protokol N N)<br /><br />Nejhorším případě O(N^2)|O (protokol N N)|O (protokol N N)|-|-|Zadaný seznam jsou pomocí klíče, které poskytuje daný projekce. Klíče jsou porovnávány pomocí [porovnat](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortinplace –|Průměr O (protokol N N)<br /><br />Nejhorším případě O(N^2)|-|-|-|-|Prvky pole jsou řazeny podle mutace na místě a pomocí funkce dané porovnání. Elementy jsou porovnávány s použitím [porovnat](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortinplaceby –|Průměr O (protokol N N)<br /><br />Nejhorším případě O(N^2)|-|-|-|-|Prvky pole jsou řazeny podle mutace na místě a pomocí dané projekci pro klíče. Elementy jsou porovnávány s použitím [porovnat](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortinplacewith –|Průměr O (protokol N N)<br /><br />Nejhorším případě O(N^2)|-|-|-|-|Prvky pole jsou řazeny podle mutace na místě a pomocí funkce dané porovnání jako pořadí.|
|sortwith –|Průměr O (protokol N N)<br /><br />Nejhorším případě O(N^2)|O (protokol N N)|-|-|-|Seřadí prvky kolekce, pomocí funkce dané porovnání jako pořadí a vrátí novou kolekci.|
|Sub –|O(N)|-|-|-|-|Sestaví pole obsahující danou Podoblast sady, která je zadána od indexu a délky.|
|Součet|O(N)|O(N)|O(N)|-|-|Vrátí součet elementů v kolekci.|
|sumby –|O(N)|O(N)|O(N)|-|-|Vrátí součet výsledky, které jsou generovány použitím funkce na každý prvek kolekce.|
|Tail|-|O(1), KTERÁ|-|-|-|Vrátí seznam bez jeho první prvek.|
|proveďte|-|-|O(N)|-|-|Vrátí pořadí až s určeným počtem elementů.|
|TakeWhile|-|-|O(1), KTERÁ|-|-|Vrátí pořadí, že pokud vstupní, jsou elementy základní sekvence při daném predikátu vrátí `true` a vrátí žádné další prvky.|
|ToArray|-|O(N)|O(N)|O(N)|O(N)|Pole se vytvoří z dané kolekce.|
|ToList|O(N)|-|O(N)|O(N)|O(N)|Vytvoří seznam z dané kolekce.|
|toseq –|O(1), KTERÁ|O(1), KTERÁ|-|O(1), KTERÁ|O(1), KTERÁ|Posloupnost vytvoří z dané kolekce.|
|zkrácení|-|-|O(1), KTERÁ|-|-|Vrátí sekvenci, pokud uvedené, vrátí víc než N prvků.|
|tryfind –|O(N)|O(N)|O(N)|O (protokol N)|-|Vyhledá element, který splňuje daného predikátu.|
|tryfindindex –|O(N)|O(N)|O(N)|-|-|Vyhledá první prvek, který splňuje daného predikátu a vrátí index odpovídající element nebo `None` Pokud neexistuje žádný takový prvek.|
|tryfindkey –|-|-|-|O (protokol N)|-|Vrátí první mapování klíč v kolekci, která splňuje daného predikátu nebo vrátí `None` Pokud neexistuje žádný takový prvek.|
|trypick –|O(N)|O(N)|O(N)|O (protokol N)|-|Dané funkce se vztahuje na následných elementy, vrátí první výsledek, kde funkce vrátí hodnotu `Some` pro určitou hodnotu. Pokud žádný takový prvek existuje, vrátí operaci `None`.|
|unfold –|-|-|O(N)|-|-|Vrátí pořadí, které obsahuje prvky, které generuje dané výpočet.|
|sjednocení|-|-|-|-|O (M &#42; protokolu N)|Vypočítá sjednocení dvou sad.|
|unionmany –|-|-|-|-|O (N1 &AMP;#42; N2...)|Vypočítá sjednocení pořadí sad.|
|Rozbalte|O(N)|O(N)|O(N)|-|-|Seznam párů rozdělí na dva seznamy.|
|unzip3 –|O(N)|O(N)|O(N)|-|-|Rozdělí seznam triples na tři seznamy.|
|oddílové|-|-|O(N)|-|-|Vrátí pořadí, které dává posuvné windows z obsahující prvky, které jsou vykreslovány z vstupní pořadí. Každé okno se vrátí jako novou pole.|
|ZIP|O(N)|O(N)|O(N)|-|-|Kombinuje dvě kolekce do seznamu párů. Dva seznamy musí mít stejnou délku.|
|zip3 –|O(N)|O(N)|O(N)|-|-|Kombinuje tři kolekce do seznamu triples. Seznamy musí mít stejnou délku.|

## <a name="see-also"></a>Viz také
[Typy F#](fsharp-types.md)

[Referenční dokumentace jazyka F#](index.md)

