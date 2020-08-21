---
title: Typy kolekcí
description: 'Přečtěte si o typech kolekcí F # a o tom, jak se liší od kolekcí typu .NET.'
ms.date: 08/14/2020
ms.openlocfilehash: 394f6bbaf58e7e8607abc3a0c20bbc2b1c9c3c8d
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656902"
---
# <a name="f-collection-types"></a>Typy kolekcí F#

Projděte si toto téma, kde můžete určit, který typ kolekce F # nejlépe vyhovuje konkrétní potřebě. Tyto typy kolekcí se liší od typů kolekce v rozhraní .NET, jako jsou například v `System.Collections.Generic` oboru názvů, v tom, že typy kolekce F # jsou navržené z perspektivy funkčního programování, nikoli z hlediska objektu orientovaného na objekt. Přesněji řečeno, pouze kolekce Array mají proměnlivé prvky. Proto když upravíte kolekci, vytvoříte instanci upravené kolekce namísto změny původní kolekce.

Typy kolekce se také liší v typu struktury dat, ve kterých jsou objekty uloženy. Datové struktury, jako jsou zatřiďovací tabulky, propojené seznamy a pole, mají různé charakteristiky výkonu a jinou sadu dostupných operací.

## <a name="f-collection-types"></a>Typy kolekcí F#

V následující tabulce jsou uvedeny typy kolekcí F #.

|Typ|Popis|Související odkazy|
|----|-----------|-------------|
|[Seznam](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-fsharplist-1.html)|Seřazená, neproměnlivá řada prvků stejného typu. Implementováno jako propojený seznam.|[Seznamy](lists.md)<br /><br />[Seznam modulů](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)|
|[Skupin](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-array-1.html)|Pevná velikost, která je založená na nule, proměnlivá kolekce po sobě jdoucích datových prvků, které jsou všechny stejného typu.|[Pole](arrays.md)<br /><br />[Modul pole](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html)<br /><br />[Přidaný modul](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html)<br /><br />[Modul Array3D](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array3dmodule.html)|
|[SEQ](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seq-1.html)|Logická řada prvků, které jsou všechny jednoho typu. Sekvence jsou zvláště užitečné v případě, že máte rozsáhlou uspořádanou kolekci dat, ale nemusí nutně očekávat použití všech prvků. Jednotlivé prvky sekvence jsou vypočítány pouze jako povinné, takže sekvence může být využívána lépe než seznam, pokud nejsou použity všechny prvky. Sekvence jsou reprezentovány `seq<'T>` typem, který je aliasem pro `IEnumerable<T>` . Proto může být jakýkoli typ .NET Framework, který implementuje, `System.Collections.Generic.IEnumerable<'T>` použit jako sekvence.|[Sekvence](sequences.md)<br /><br />[SEQ – modul](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html)|
|[Mapa](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-fsharpmap-2.html)|Neproměnlivý slovník prvků. K prvkům se používá klíč.|[Mapový modul](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-mapmodule.html)|
|[Set](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-fsharpset-1.html)|Neproměnlivá sada, která je založena na binárních stromech, kde porovnání je funkce strukturálního porovnání F #, která potenciálně používá implementace `System.IComparable` rozhraní u klíčových hodnot.|[Nastavit modul](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-setmodule.html)|

### <a name="table-of-functions"></a>Tabulka funkcí

Tato část porovnává funkce, které jsou k dispozici v typech kolekcí F #. Výpočet složitosti funkce je uveden, kde N je velikost první kolekce a M je velikost druhé kolekce, pokud existuje. Pomlčka (-) označuje, že tato funkce není v kolekci k dispozici. Vzhledem k tomu, že sekvence jsou vyhodnoceny jako laxně vytvářená, funkce, jako je například Seq. DISTINCT, může být O (1), protože se okamžitě vrátí, i když stále ovlivňuje výkon sekvence při vytváření výčtu.

|Funkce|Pole|Seznam|Sequence|Mapa|Nastavit|Popis|
|--------|-----|----|--------|---|---|-----------|
|příloh|O (N)|O (N)|O (N)|-|-|Vrátí novou kolekci, která obsahuje prvky první kolekce následované elementy druhé kolekce.|
|add|-|-|-|O (protokol (N))|O (protokol (N))|Vrátí novou kolekci s přidaným elementem.|
|Průměr|O (N)|O (N)|O (N)|-|-|Vrátí průměr z prvků v kolekci.|
|averageBy –|O (N)|O (N)|O (N)|-|-|Vrátí průměr výsledků zadané funkce použité pro každý prvek.|
|blit –|O (N)|-|-|-|-|Zkopíruje část pole.|
|cache|-|-|O (N)|-|-|Vypočítá a ukládá prvky sekvence.|
|přetypování|-|-|O (N)|-|-|Převede elementy na zadaný typ.|
|výběrem|O (N)|O (N)|O (N)|-|-|Použije danou funkci `f` na každý prvek `x` seznamu. Vrátí seznam obsahující výsledky pro každý prvek, kde funkce vrátí `Some(f(x))` .|
|shromáždění|O (N)|O (N)|O (N)|-|-|Použije danou funkci na každý prvek kolekce, zřetězí všechny výsledky a vrátí kombinovaný seznam.|
|compareWith –|-|-|O (N)|-|-|Porovná dvě sekvence pomocí dané funkce porovnání, elementu po prvku.|
|concat|O (N)|O (N)|O (N)|-|-|Kombinuje dané výčtové výčty jako jeden zřetězený výčet.|
|obsahuje|-|-|-|-|O (protokol (N))|Vrátí hodnotu true, pokud sada obsahuje zadaný element.|
|ContainsKey –|-|-|-|O (protokol (N))|-|Testuje, zda je prvek v doméně mapy.|
|count|-|-|-|-|O (N)|Vrátí počet prvků v objektu set.|
|CountBy –|-|-|O (N)|-|-|Aplikuje funkci generování klíčů na každý prvek sekvence a vrátí sekvenci, která poskytuje jedinečné klíče a jejich počet výskytů v původní sekvenci.|
|kopírování|O (N)|-|O (N)|-|-|Zkopíruje kolekci.|
|vytvoření|O (N)|-|-|-|-|Vytvoří pole celých prvků, které jsou původně danou hodnotou.|
|způsobené|-|-|O (1)|-|-|Vrací sekvenci, která je sestavena z dané zpožděné specifikace sekvence.|
|rozdíl|-|-|-|-|O ( \* protokol M (N))|Vrátí novou sadu s prvky druhé sady odebrané z první sady.|
|distinct|||O (1)\*|||Vrátí sekvenci, která neobsahuje žádné duplicitní položky na základě porovnání obecného algoritmu hash a rovnosti položek. Pokud v sekvenci dojde vícekrát k elementu, další výskyty se zahodí.|
|distinctBy –|||O (1)\*|||Vrátí sekvenci, která neobsahuje žádné duplicitní položky podle obecného porovnání hodnoty hash a rovnosti u klíčů, které vrací daná funkce generování klíčů. Pokud v sekvenci dojde vícekrát k elementu, další výskyty se zahodí.|
|empty|O (1)|O (1)|O (1)|O (1)|O (1)|Vytvoří prázdnou kolekci.|
|neexistuje|O (N)|O (N)|O (N)|O (protokol (N))|O (protokol (N))|Testuje, zda jakýkoliv prvek sekvence splňuje daný predikát.|
|exists2 –|O (min (N, M))|-|O (min (N, M))|||Testuje, zda některé páry odpovídajících prvků vstupních sekvencí splní daný predikát.|
|fill|O (N)|||||Nastaví rozsah prvků pole na danou hodnotu.|
|filtrování|O (N)|O (N)|O (N)|O (N)|O (N)|Vrátí novou kolekci, která obsahuje pouze prvky kolekce, pro které se daný predikát vrátí `true` .|
|find|O (N)|O (N)|O (N)|O (protokol (N))|-|Vrátí první prvek, pro který vrátí daná funkce `true` . Vrátí, `System.Collections.Generic.KeyNotFoundException` Pokud žádný takový prvek neexistuje.|
|FindIndex –|O (N)|O (N)|O (N)|-|-|Vrátí index prvního prvku v poli, který splňuje daný predikát. Vyvolá `System.Collections.Generic.KeyNotFoundException` , pokud predikát nevyhovuje žádnému elementu.|
|FindKey –|-|-|-|O (protokol (N))|-|Vyhodnotí funkci u každého mapování v kolekci a vrátí klíč pro první mapování, kde funkce vrátí `true` . Pokud žádný takový prvek neexistuje, tato funkce vyvolá `System.Collections.Generic.KeyNotFoundException` .|
|nahoře|O (N)|O (N)|O (N)|O (N)|O (N)|Použije funkci na každý prvek kolekce a podvláknuje argument Akumulovaná pomocí výpočtu. Je-li vstupní funkce f a prvky jsou I0... Tato funkce v nástroji počítá f (... (f s I0)...) pro.|
|fold2 –|O (N)|O (N)|-|-|-|Aplikuje funkci na odpovídající prvky dvou kolekcí, zřetězení argumentu Akumulovaná prostřednictvím výpočtu. Kolekce musí mít stejné velikosti. Je-li vstupní funkce f a prvky jsou I0... v a J0... jN, tato funkce vypočítá f (... (f s I0 J0)...) v jN.|
|foldBack –|O (N)|O (N)|-|O (N)|O (N)|Použije funkci na každý prvek kolekce a podvláknuje argument Akumulovaná pomocí výpočtu. Je-li vstupní funkce f a prvky jsou I0... Tato funkce v nástroji počítá f I0 (... (f v s)).|
|Foldback2 –|O (N)|O (N)|-|-|-|Aplikuje funkci na odpovídající prvky dvou kolekcí, zřetězení argumentu Akumulovaná prostřednictvím výpočtu. Kolekce musí mít stejné velikosti. Je-li vstupní funkce f a prvky jsou I0... v a J0... jN, tato funkce vypočítá f I0 J0 (... (f v jN s)).|
|ForAll|O (N)|O (N)|O (N)|O (N)|O (N)|Testuje, zda všechny prvky kolekce odpovídají danému predikátu.|
|forall2 –|O (N)|O (N)|O (N)|-|-|Testuje, zda všechny odpovídající prvky kolekce odpovídají danému predikátu párový.|
|získat na n-tý|O (1)|O (N)|O (N)|-|-|Vrátí prvek z kolekce s daným indexem.|
|záhlaví|-|O (1)|O (1)|-|-|Vrátí první prvek kolekce.|
|init|O (N)|O (N)|O (1)|-|-|Vytvoří kolekci pro výpočet prvků v dimenzi a funkci generátoru.|
|initInfinite –|-|-|O (1)|-|-|Generuje sekvenci, která při iteraci vrátí úspěšné prvky voláním dané funkce.|
|intersect|-|-|-|-|O (protokol (N) \* protokol (M))|Vypočítá průnik dvou sad.|
|intersectMany –|-|-|-|-|O (N1 \* N2...)|Vypočítá průnik sekvencí sad. Sekvence nesmí být prázdná.|
|isEmpty|O (1)|O (1)|O (1)|O (1)|-|Vrátí, `true` zda je kolekce prázdná.|
|IsProperSubset –|-|-|-|-|O ( \* protokol M (N))|Vrátí `true` , zda jsou všechny prvky první sady ve druhé sadě a alespoň jeden prvek druhé sady není v první sadě.|
|IsProperSuperset –|-|-|-|-|O ( \* protokol M (N))|Vrátí `true` , zda jsou všechny prvky druhé sady v první sadě a alespoň jeden prvek první sady není ve druhé sadě.|
|isSubset –|-|-|-|-|O ( \* protokol M (N))|Vrátí, `true` zda jsou všechny prvky první sady ve druhé sadě.|
|isSuperset –|-|-|-|-|O ( \* protokol M (N))|Vrátí, `true` zda jsou všechny prvky druhé sady v první sadě.|
|ITER|O (N)|O (N)|O (N)|O (N)|O (N)|Použije danou funkci na každý prvek kolekce.|
|iteri –|O (N)|O (N)|O (N)|-|-|Použije danou funkci na každý prvek kolekce. Celé číslo, které je předáno funkci, označuje index elementu.|
|iteri2 –|O (N)|O (N)|-|-|-|Aplikuje danou funkci na dvojici prvků, které jsou vykresleny z porovnávacích indexů ve dvou polích. Celé číslo, které je předáno funkci, označuje index prvků. Obě pole musí mít stejnou délku.|
|iter2 –|O (N)|O (N)|O (N)|-|-|Aplikuje danou funkci na dvojici prvků, které jsou vykresleny z porovnávacích indexů ve dvou polích. Obě pole musí mít stejnou délku.|
|poslední|O (1)|O (N)|O (N)|-|-|Vrátí poslední položku v příslušné kolekci.|
|length|O (1)|O (N)|O (N)|-|-|Vrátí počet prvků v kolekci.|
|mapa|O (N)|O (N)|O (1)|-|-|Vytvoří kolekci, jejíž prvky jsou výsledkem použití dané funkce na každý prvek pole.|
|MAP2 –|O (N)|O (N)|O (1)|-|-|Vytvoří kolekci, jejíž prvky jsou výsledkem použití dané funkce na odpovídající prvky dvou kolekcí. Dvě vstupní pole musí mít stejnou délku.|
|map3 –|-|O (N)|-|-|-|Vytvoří kolekci, jejíž prvky jsou výsledkem použití dané funkce na odpovídající prvky tří kolekcí současně.|
|MAPI|O (N)|O (N)|O (N)|-|-|Vytvoří pole, jehož prvky jsou výsledkem použití dané funkce na každý prvek pole. Celočíselný index předaný funkci označuje index elementu, který je transformován.|
|mapi2 –|O (N)|O (N)|-|-|-|Sestaví kolekci, jejíž prvky jsou výsledkem použití dané funkce na odpovídající prvky dvou kolekcí, a také předání indexu prvků. Dvě vstupní pole musí mít stejnou délku.|
|max|O (N)|O (N)|O (N)|-|-|Vrátí největší prvek v kolekci v porovnání s použitím operátoru [Max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) .|
|maxBy –|O (N)|O (N)|O (N)|-|-|Vrátí největší prvek v kolekci ve srovnání s použitím [Max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) na výsledku funkce.|
|MaxElement –|-|-|-|-|O (protokol (N))|Vrátí největší prvek v sadě podle řazení, které se používá pro sadu.|
|min|O (N)|O (N)|O (N)|-|-|Vrátí prvek, který je nejméně v kolekci, v porovnání s použitím operátoru [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) .|
|minBy –|O (N)|O (N)|O (N)|-|-|Vrátí prvek, který je nejméně v kolekci, v porovnání s použitím operátoru [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) na výsledku funkce.|
|MinElement –|-|-|-|-|O (protokol (N))|Vrátí nejnižší prvek v sadě podle řazení, které se používá pro sadu.|
|ofArray –|-|O (N)|O (1)|O (N)|O (N)|Vytvoří kolekci, která obsahuje stejné prvky jako dané pole.|
|ofList –|O (N)|-|O (1)|O (N)|O (N)|Vytvoří kolekci, která obsahuje stejné prvky jako daný seznam.|
|ofSeq –|O (N)|O (N)|-|O (N)|O (N)|Vytvoří kolekci, která obsahuje stejné prvky jako daná sekvence.|
|dvojic|-|-|O (N)|-|-|Vrací sekvenci každého prvku ve vstupní sekvenci a jeho předchůdce s výjimkou prvního prvku, který je vrácen pouze jako předchůdce druhého prvku.|
|partition|O (N)|O (N)|-|O (N)|O (N)|Rozdělí kolekci do dvou kolekcí. První kolekce obsahuje prvky, pro které se daný predikát vrátí `true` , a druhá kolekce obsahuje prvky, pro které se daný predikát vrátí `false` .|
|permute|O (N)|O (N)|-|-|-|Vrátí pole se všemi elementy permuted podle zadané permutace.|
|zrad|O (N)|O (N)|O (N)|O (protokol (N))|-|Použije danou funkci na po sobě jdoucí prvky a vrátí první výsledek, kde funkce vrátí některé. Pokud funkce žádného nevrátí, `System.Collections.Generic.KeyNotFoundException` je vyvolána.|
|readonly|-|-|O (N)|-|-|Vytvoří objekt sekvence, který se deleguje k danému objektu sekvence. Tato operace zajišťuje, že přetypování typu nemůže znovu zjistit a postoupit původní sekvenci. Například pokud je zadáno pole, vrácená sekvence vrátí prvky pole, ale nelze přetypovat vrácený objekt sekvence na pole.|
|úrovně|O (N)|O (N)|O (N)|-|-|Použije funkci na každý prvek kolekce a podvláknuje argument Akumulovaná pomocí výpočtu. Tato funkce se spouští použitím funkce na první dva prvky, předává tento výsledek do funkce společně s třetím prvkem a tak dále. Funkce vrátí konečný výsledek.|
|reduceBack –|O (N)|O (N)|-|-|-|Použije funkci na každý prvek kolekce a podvláknuje argument Akumulovaná pomocí výpočtu. Je-li vstupní funkce f a prvky jsou I0... Tato funkce v nástroji počítá f I0 (... (f iN-1 v)).|
|remove|-|-|-|O (protokol (N))|O (protokol (N))|Odebere prvek z domény mapy. Není-li prvek přítomen, není vyvolána žádná výjimka.|
|probíhá|-|O (N)|-|-|-|Vytvoří seznam zadané délky s každým prvkem nastaveným na danou hodnotu.|
|obrácen|O (N)|O (N)|-|-|-|Vrátí nový seznam s prvky v obráceném pořadí.|
|skenuje|O (N)|O (N)|O (N)|-|-|Použije funkci na každý prvek kolekce a podvláknuje argument Akumulovaná pomocí výpočtu. Tato operace použije funkci na druhý argument a první prvek v seznamu. Tato operace pak předá tento výsledek do funkce společně s druhým prvkem a tak dále. Nakonec operace vrátí seznam mezilehlých výsledků a konečný výsledek.|
|ScanBack –|O (N)|O (N)|-|-|-|Se podobá operaci foldBack –, ale vrací mezilehlé i konečné výsledky.|
|singleton|-|-|O (1)|-|O (1)|Vrátí sekvenci, která poskytuje jenom jednu položku.|
|set|O (1)|-|-|-|-|Nastaví prvek pole na zadanou hodnotu.|
|Přeskočit|-|-|O (N)|-|-|Vrací sekvenci, která přeskočí elementy v podkladové sekvenci a následně vrátí zbývající prvky sekvence.|
|SkipWhile –|-|-|O (N)|-|-|Vrací sekvenci, která při iteraci přeskočí prvky podkladové sekvence, zatímco daný predikát vrátí `true` a následně vrátí zbývající prvky sekvence.|
|sort|Průměr v (N \* log (n))<br /><br />O (N ^ 2) nejhorší případ|O (N \* protokol (n))|O (N \* protokol (n))|-|-|Seřadí kolekci podle hodnoty elementu. Prvky jsou porovnávány pomocí [Compare](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortBy|Průměr v (N \* log (n))<br /><br />O (N ^ 2) nejhorší případ|O (N \* protokol (n))|O (N \* protokol (n))|-|-|Seřadí daný seznam pomocí klíčů, které poskytuje daná projekce. Klíče se porovnávají pomocí [porovnání](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlace –|Průměr v (N \* log (n))<br /><br />O (N ^ 2) nejhorší případ|-|-|-|-|Seřadí prvky pole podle jeho použití na místě a pomocí dané funkce porovnání. Prvky jsou porovnány pomocí [porovnání](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceBy –|Průměr v (N \* log (n))<br /><br />O (N ^ 2) nejhorší případ|-|-|-|-|Seřadí prvky pole podle jeho použití na místě a pomocí dané projekce pro tyto klíče. Prvky jsou porovnány pomocí [porovnání](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceWith –|Průměr v (N \* log (n))<br /><br />O (N ^ 2) nejhorší případ|-|-|-|-|Seřadí prvky pole podle jeho použití na místě a použitím dané funkce porovnání jako pořadí.|
|sortWith –|Průměr v (N \* log (n))<br /><br />O (N ^ 2) nejhorší případ|O (N \* protokol (n))|-|-|-|Seřadí prvky kolekce pomocí dané funkce porovnání jako pořadí a vrátí novou kolekci.|
|jednotk|O (N)|-|-|-|-|Vytvoří pole, které obsahuje daný dílčí rozsah určený počáteční index a délkou.|
|Součet|O (N)|O (N)|O (N)|-|-|Vrátí součet prvků v kolekci.|
|sumBy –|O (N)|O (N)|O (N)|-|-|Vrátí součet výsledků, které jsou generovány použitím funkce na každý prvek kolekce.|
|kompatibilní|-|O (1)|-|-|-|Vrátí seznam bez jeho prvního prvku.|
|take|-|-|O (N)|-|-|Vrátí prvky sekvence až do zadaného počtu.|
|TakeWhile –|-|-|O (1)|-|-|Vrací sekvenci, která při iteraci vrátí prvky podkladové sekvence, zatímco daný predikát vrátí `true` a pak nevrátí žádné další prvky.|
|ToArray –|-|O (N)|O (N)|O (N)|O (N)|Vytvoří pole ze zadané kolekce.|
|ToList –|O (N)|-|O (N)|O (N)|O (N)|Vytvoří seznam ze zadané kolekce.|
|toSeq –|O (1)|O (1)|-|O (1)|O (1)|Vytvoří sekvenci ze zadané kolekce.|
|zkrátit|-|-|O (1)|-|-|Vrací sekvenci, která při výčtu nevrátí více než N prvků.|
|tryFind –|O (N)|O (N)|O (N)|O (protokol (N))|-|Vyhledá prvek, který splňuje daný predikát.|
|tryFindIndex –|O (N)|O (N)|O (N)|-|-|Vyhledá první prvek, který splňuje daný predikát, a vrátí index odpovídajícího prvku, nebo `None` Pokud žádný takový prvek neexistuje.|
|TryFindKey –|-|-|-|O (protokol (N))|-|Vrátí klíč prvního mapování v kolekci, který splňuje daný predikát, nebo vrátí, `None` Pokud žádný takový prvek neexistuje.|
|tryPick –|O (N)|O (N)|O (N)|O (protokol (N))|-|Aplikuje danou funkci na po sobě jdoucí elementy a vrátí první výsledek, ve kterém se funkce vrátí `Some` na určitou hodnotu. Pokud žádný takový prvek neexistuje, operace se vrátí `None` .|
|unfold|-|-|O (N)|-|-|Vrátí sekvenci, která obsahuje prvky, které vygeneruje daný výpočet.|
|sjednocení|-|-|-|-|O ( \* protokol M (N))|Vypočítá sjednocení dvou sad.|
|UnionMany –|-|-|-|-|O (N1 \* N2...)|Vypočítá sjednocení posloupnosti sad.|
|Komprimovat|O (N)|O (N)|O (N)|-|-|Rozdělí seznam párů na dva seznamy.|
|unzip3 –|O (N)|O (N)|O (N)|-|-|Rozdělí seznam trojitých na tři seznamy.|
|oddílové|-|-|O (N)|-|-|Vrací sekvenci, která poskytuje posuvná okna obsahující prvky, které jsou vykresleny ze vstupní sekvence. Každé okno je vráceno jako nové pole.|
|věřitel|O (N)|O (N)|O (N)|-|-|Kombinuje dvě kolekce do seznamu párů. Dva seznamy musí mít stejné délky.|
|zip3 –|O (N)|O (N)|O (N)|-|-|Kombinuje tři kolekce do seznamu trojí. Seznamy musí mít stejnou délku.|

## <a name="see-also"></a>Viz také:

- [Typy F#](fsharp-types.md)
- [Referenční dokumentace jazyka F #](index.md)
