---
title: Typy kolekcí
description: Přečtěte F# si o typech kolekcí a o tom, jak se liší od typů kolekcí v .NET Framework.
ms.date: 05/16/2016
ms.openlocfilehash: e5735efbffb1010f3886f3b32800a61e2d3b0d36
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344572"
---
# <a name="f-collection-types"></a>Typy kolekcí F#

Projděte si toto téma, kde můžete určit F# , který typ kolekce nejlépe vyhovuje konkrétní potřebě. Tyto typy kolekcí se liší od typů kolekce v .NET Framework, jako jsou například v oboru názvů `System.Collections.Generic`, v tom, že F# typy kolekce jsou navrženy z pohledu funkčního programování, nikoli z hlediska objektu orientovaného na objekt. Přesněji řečeno, pouze kolekce Array mají proměnlivé prvky. Proto když upravíte kolekci, vytvoříte instanci upravené kolekce namísto změny původní kolekce.

Typy kolekce se také liší v typu struktury dat, ve kterých jsou objekty uloženy. Datové struktury, jako jsou zatřiďovací tabulky, propojené seznamy a pole, mají různé charakteristiky výkonu a jinou sadu dostupných operací.

## <a name="f-collection-types"></a>Typy kolekcí F#

V následující tabulce jsou F# uvedeny typy kolekcí.

|Type|Popis|Související odkazy|
|----|-----------|-------------|
|[Seznam](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|Seřazená, neproměnlivá řada prvků stejného typu. Implementováno jako propojený seznam.|[Seznamy](lists.md)<br /><br />[Seznam modulů](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[Pole](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|Pevná velikost, která je založená na nule, proměnlivá kolekce po sobě jdoucích datových prvků, které jsou všechny stejného typu.|[Pole](arrays.md)<br /><br />[Modul pole](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Přidaný modul](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Modul Array3D](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[SEQ](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|Logická řada prvků, které jsou všechny jednoho typu. Sekvence jsou zvláště užitečné v případě, že máte rozsáhlou uspořádanou kolekci dat, ale nemusí nutně očekávat použití všech prvků. Jednotlivé prvky sekvence jsou vypočítány pouze jako povinné, takže sekvence může být využívána lépe než seznam, pokud nejsou použity všechny prvky. Sekvence jsou reprezentovány typem `seq<'T>`, který je aliasem pro `IEnumerable<T>`. Proto může být jakýkoli typ .NET Framework, který implementuje `System.Collections.Generic.IEnumerable<'T>`, použit jako sekvence.|[Sekvence](sequences.md)<br /><br />[SEQ – modul](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[Mapa](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|Neproměnlivý slovník prvků. K prvkům se používá klíč.|[Mapový modul](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[Stanovenými](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|Neproměnlivá sada, která je založena na binárních stromech, kde F# porovnání je strukturální relační funkce, která potenciálně používá implementace `System.IComparable` rozhraní na klíčových hodnotách.|[Nastavit modul](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>Tabulka funkcí

Tato část porovnává funkce, které jsou k F# dispozici pro typy kolekcí. Výpočet složitosti funkce je uveden, kde N je velikost první kolekce a M je velikost druhé kolekce, pokud existuje. Pomlčka (-) označuje, že tato funkce není v kolekci k dispozici. Vzhledem k tomu, že sekvence jsou vyhodnoceny jako laxně vytvářená, funkce, jako je například Seq. DISTINCT, může být O (1), protože se okamžitě vrátí, i když stále ovlivňuje výkon sekvence při vytváření výčtu.

|Funkce|Array|Seznam|Sequence|Mapa|Nastavit|Popis|
|--------|-----|----|--------|---|---|-----------|
|příloh|O (M)|O (N)|O (N)|-|-|Vrátí novou kolekci, která obsahuje prvky první kolekce následované elementy druhé kolekce.|
|add|-|-|-|O (protokol N)|O (protokol N)|Vrátí novou kolekci s přidaným elementem.|
|průměr|O (N)|O (N)|O (N)|-|-|Vrátí průměr z prvků v kolekci.|
|averageBy –|O (N)|O (N)|O (N)|-|-|Vrátí průměr výsledků zadané funkce použité pro každý prvek.|
|blit –|O (N)|-|-|-|-|Zkopíruje část pole.|
|mezipaměť|-|-|O (N)|-|-|Vypočítá a ukládá prvky sekvence.|
|přetypování|-|-|O (N)|-|-|Převede elementy na zadaný typ.|
|zvolte|O (N)|O (N)|O (N)|-|-|Použije danou funkci `f` pro každý prvek `x` seznamu. Vrátí seznam obsahující výsledky pro každý prvek, kde funkce vrátí `Some(f(x))`.|
|shromažďovat|O (N)|O (N)|O (N)|-|-|Použije danou funkci na každý prvek kolekce, zřetězí všechny výsledky a vrátí kombinovaný seznam.|
|compareWith –|-|-|O (N)|-|-|Porovná dvě sekvence pomocí dané funkce porovnání, elementu po prvku.|
|concat|O (N)|O (N)|O (N)|-|-|Kombinuje dané výčtové výčty jako jeden zřetězený výčet.|
|obsahuje|-|-|-|-|O (protokol N)|Vrátí hodnotu true, pokud sada obsahuje zadaný element.|
|containsKey|-|-|-|O (protokol N)|-|Testuje, zda je prvek v doméně mapy.|
|počet|-|-|-|-|O (N)|Vrátí počet prvků v objektu set.|
|CountBy –|-|-|O (N)|-|-|Aplikuje funkci generování klíčů na každý prvek sekvence a vrátí sekvenci, která poskytuje jedinečné klíče a jejich počet výskytů v původní sekvenci.|
|copy|O (N)|-|O (N)|-|-|Zkopíruje kolekci.|
|vytvoření|O (N)|-|-|-|-|Vytvoří pole celých prvků, které jsou původně danou hodnotou.|
|delay|-|-|O(1)|-|-|Vrací sekvenci, která je sestavena z dané zpožděné specifikace sekvence.|
|rozdíl|-|-|-|-|O (M &#42; protokol N)|Vrátí novou sadu s prvky druhé sady odebrané z první sady.|
|distinct|||O (1)&#42;|||Vrátí sekvenci, která neobsahuje žádné duplicitní položky na základě porovnání obecného algoritmu hash a rovnosti položek. Pokud v sekvenci dojde vícekrát k elementu, další výskyty se zahodí.|
|distinctBy –|||O (1)&#42;|||Vrátí sekvenci, která neobsahuje žádné duplicitní položky podle obecného porovnání hodnoty hash a rovnosti u klíčů, které vrací daná funkce generování klíčů. Pokud v sekvenci dojde vícekrát k elementu, další výskyty se zahodí.|
|empty|O(1)|O(1)|O(1)|O(1)|O(1)|Vytvoří prázdnou kolekci.|
|neexistuje|O (N)|O (N)|O (N)|O (protokol N)|O (protokol N)|Testuje, zda jakýkoliv prvek sekvence splňuje daný predikát.|
|exists2 –|O(min(N,M))|-|O(min(N,M))|||Testuje, zda některé páry odpovídajících prvků vstupních sekvencí splní daný predikát.|
|fill|O (N)|||||Nastaví rozsah prvků pole na danou hodnotu.|
|Filter|O (N)|O (N)|O (N)|O (N)|O (N)|Vrátí novou kolekci, která obsahuje pouze prvky kolekce, pro které daný predikát vrací `true`.|
|find|O (N)|O (N)|O (N)|O (protokol N)|-|Vrátí první prvek, pro který vrátí daná funkce `true`. Vrátí `System.Collections.Generic.KeyNotFoundException`, pokud žádný takový prvek neexistuje.|
|findIndex|O (N)|O (N)|O (N)|-|-|Vrátí index prvního prvku v poli, který splňuje daný predikát. Vyvolá `System.Collections.Generic.KeyNotFoundException`, pokud žádný prvek nesplňuje predikát.|
|FindKey –|-|-|-|O (protokol N)|-|Vyhodnotí funkci u každého mapování v kolekci a vrátí klíč pro první mapování, kde funkce vrátí `true`. Pokud žádný takový prvek neexistuje, tato funkce vyvolá `System.Collections.Generic.KeyNotFoundException`.|
|sklopit|O (N)|O (N)|O (N)|O (N)|O (N)|Použije funkci na každý prvek kolekce a podvláknuje argument Akumulovaná pomocí výpočtu. Je-li vstupní funkce f a prvky jsou I0... Tato funkce v nástroji počítá f (... (f s I0)...) pro.|
|fold2 –|O (N)|O (N)|-|-|-|Aplikuje funkci na odpovídající prvky dvou kolekcí, zřetězení argumentu Akumulovaná prostřednictvím výpočtu. Kolekce musí mít stejné velikosti. Je-li vstupní funkce f a prvky jsou I0... v a J0... jN, tato funkce vypočítá f (... (f s I0 J0)...) v jN.|
|foldBack –|O (N)|O (N)|-|O (N)|O (N)|Použije funkci na každý prvek kolekce a podvláknuje argument Akumulovaná pomocí výpočtu. Je-li vstupní funkce f a prvky jsou I0... Tato funkce v nástroji počítá f I0 (... (f v s)).|
|Foldback2 –|O (N)|O (N)|-|-|-|Aplikuje funkci na odpovídající prvky dvou kolekcí, zřetězení argumentu Akumulovaná prostřednictvím výpočtu. Kolekce musí mít stejné velikosti. Je-li vstupní funkce f a prvky jsou I0... v a J0... jN, tato funkce vypočítá f I0 J0 (... (f v jN s)).|
|ForAll|O (N)|O (N)|O (N)|O (N)|O (N)|Testuje, zda všechny prvky kolekce odpovídají danému predikátu.|
|forall2 –|O (N)|O (N)|O (N)|-|-|Testuje, zda všechny odpovídající prvky kolekce odpovídají danému predikátu párový.|
|získat na n-tý|O(1)|O (N)|O (N)|-|-|Vrátí prvek z kolekce s daným indexem.|
|záhlaví|-|O(1)|O(1)|-|-|Vrátí první prvek kolekce.|
|init|O (N)|O (N)|O(1)|-|-|Vytvoří kolekci pro výpočet prvků v dimenzi a funkci generátoru.|
|initInfinite –|-|-|O(1)|-|-|Generuje sekvenci, která při iteraci vrátí úspěšné prvky voláním dané funkce.|
|Krývají|-|-|-|-|O (log N &#42; log M)|Vypočítá průnik dvou sad.|
|intersectMany|-|-|-|-|O (N1 &#42; N2...)|Vypočítá průnik sekvencí sad. Sekvence nesmí být prázdná.|
|isEmpty|O(1)|O(1)|O(1)|O(1)|-|Vrátí `true`, pokud je kolekce prázdná.|
|isProperSubset|-|-|-|-|O (M &#42; protokol N)|Vrátí `true`, pokud jsou všechny prvky první sady ve druhé sadě a alespoň jeden prvek druhé sady není v první sadě.|
|isProperSuperset|-|-|-|-|O (M &#42; protokol N)|Vrátí `true`, pokud jsou všechny prvky druhé sady v první sadě a alespoň jeden prvek první sady není ve druhé sadě.|
|isSubset –|-|-|-|-|O (M &#42; protokol N)|Vrátí `true`, pokud jsou všechny prvky první sady ve druhé sadě.|
|isSuperset –|-|-|-|-|O (M &#42; protokol N)|Vrátí `true`, pokud jsou všechny prvky druhé sady v první sadě.|
|ITER|O (N)|O (N)|O (N)|O (N)|O (N)|Použije danou funkci na každý prvek kolekce.|
|iteri –|O (N)|O (N)|O (N)|-|-|Použije danou funkci na každý prvek kolekce. Celé číslo, které je předáno funkci, označuje index elementu.|
|iteri2 –|O (N)|O (N)|-|-|-|Aplikuje danou funkci na dvojici prvků, které jsou vykresleny z porovnávacích indexů ve dvou polích. Celé číslo, které je předáno funkci, označuje index prvků. Obě pole musí mít stejnou délku.|
|iter2 –|O (N)|O (N)|O (N)|-|-|Aplikuje danou funkci na dvojici prvků, které jsou vykresleny z porovnávacích indexů ve dvou polích. Obě pole musí mít stejnou délku.|
|poslední|O(1)|O (N)|O (N)|-|-|Vrátí poslední položku v příslušné kolekci.|
|length|O(1)|O (N)|O (N)|-|-|Vrátí počet prvků v kolekci.|
|map|O (N)|O (N)|O(1)|-|-|Vytvoří kolekci, jejíž prvky jsou výsledkem použití dané funkce na každý prvek pole.|
|MAP2 –|O (N)|O (N)|O(1)|-|-|Vytvoří kolekci, jejíž prvky jsou výsledkem použití dané funkce na odpovídající prvky dvou kolekcí. Dvě vstupní pole musí mít stejnou délku.|
|map3 –|-|O (N)|-|-|-|Vytvoří kolekci, jejíž prvky jsou výsledkem použití dané funkce na odpovídající prvky tří kolekcí současně.|
|MAPI|O (N)|O (N)|O (N)|-|-|Vytvoří pole, jehož prvky jsou výsledkem použití dané funkce na každý prvek pole. Celočíselný index předaný funkci označuje index elementu, který je transformován.|
|mapi2 –|O (N)|O (N)|-|-|-|Sestaví kolekci, jejíž prvky jsou výsledkem použití dané funkce na odpovídající prvky dvou kolekcí, a také předání indexu prvků. Dvě vstupní pole musí mít stejnou délku.|
|max|O (N)|O (N)|O (N)|-|-|Vrátí největší prvek v kolekci v porovnání s použitím operátoru [Max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) .|
|maxBy –|O (N)|O (N)|O (N)|-|-|Vrátí největší prvek v kolekci ve srovnání s použitím [Max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) na výsledku funkce.|
|MaxElement –|-|-|-|-|O (protokol N)|Vrátí největší prvek v sadě podle řazení, které se používá pro sadu.|
|min|O (N)|O (N)|O (N)|-|-|Vrátí prvek, který je nejméně v kolekci, v porovnání s použitím operátoru [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) .|
|minBy –|O (N)|O (N)|O (N)|-|-|Vrátí prvek, který je nejméně v kolekci, v porovnání s použitím operátoru [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) na výsledku funkce.|
|MinElement –|-|-|-|-|O (protokol N)|Vrátí nejnižší prvek v sadě podle řazení, které se používá pro sadu.|
|ofArray –|-|O (N)|O(1)|O (N)|O (N)|Vytvoří kolekci, která obsahuje stejné prvky jako dané pole.|
|ofList –|O (N)|-|O(1)|O (N)|O (N)|Vytvoří kolekci, která obsahuje stejné prvky jako daný seznam.|
|ofSeq –|O (N)|O (N)|-|O (N)|O (N)|Vytvoří kolekci, která obsahuje stejné prvky jako daná sekvence.|
|dvojic|-|-|O (N)|-|-|Vrací sekvenci každého prvku ve vstupní sekvenci a jeho předchůdce s výjimkou prvního prvku, který je vrácen pouze jako předchůdce druhého prvku.|
|partition|O (N)|O (N)|-|O (N)|O (N)|Rozdělí kolekci do dvou kolekcí. První kolekce obsahuje prvky, pro které daný predikát vrací `true`a druhá kolekce obsahuje prvky, pro které daný predikát vrátí `false`.|
|permute|O (N)|O (N)|-|-|-|Vrátí pole se všemi elementy permuted podle zadané permutace.|
|zrad|O (N)|O (N)|O (N)|O (protokol N)|-|Použije danou funkci na po sobě jdoucí prvky a vrátí první výsledek, kde funkce vrátí některé. Pokud funkce žádné nevrátí, `System.Collections.Generic.KeyNotFoundException` je vyvolána.|
|readonly|-|-|O (N)|-|-|Vytvoří objekt sekvence, který se deleguje k danému objektu sekvence. Tato operace zajišťuje, že přetypování typu nemůže znovu zjistit a postoupit původní sekvenci. Například pokud je zadáno pole, vrácená sekvence vrátí prvky pole, ale nelze přetypovat vrácený objekt sekvence na pole.|
|úrovně|O (N)|O (N)|O (N)|-|-|Použije funkci na každý prvek kolekce a podvláknuje argument Akumulovaná pomocí výpočtu. Tato funkce se spouští použitím funkce na první dva prvky, předává tento výsledek do funkce společně s třetím prvkem a tak dále. Funkce vrátí konečný výsledek.|
|reduceBack –|O (N)|O (N)|-|-|-|Použije funkci na každý prvek kolekce a podvláknuje argument Akumulovaná pomocí výpočtu. Je-li vstupní funkce f a prvky jsou I0... Tato funkce v nástroji počítá f I0 (... (f iN-1 v)).|
|remove|-|-|-|O (protokol N)|O (protokol N)|Odebere prvek z domény mapy. Není-li prvek přítomen, není vyvolána žádná výjimka.|
|probíhá|-|O (N)|-|-|-|Vytvoří seznam zadané délky s každým prvkem nastaveným na danou hodnotu.|
|obrácen|O (N)|O (N)|-|-|-|Vrátí nový seznam s prvky v obráceném pořadí.|
|skenuje|O (N)|O (N)|O (N)|-|-|Použije funkci na každý prvek kolekce a podvláknuje argument Akumulovaná pomocí výpočtu. Tato operace použije funkci na druhý argument a první prvek v seznamu. Tato operace pak předá tento výsledek do funkce společně s druhým prvkem a tak dále. Nakonec operace vrátí seznam mezilehlých výsledků a konečný výsledek.|
|ScanBack –|O (N)|O (N)|-|-|-|Se podobá operaci foldBack –, ale vrací mezilehlé i konečné výsledky.|
|singleton|-|-|O(1)|-|O(1)|Vrátí sekvenci, která poskytuje jenom jednu položku.|
|set|O(1)|-|-|-|-|Nastaví prvek pole na zadanou hodnotu.|
|Přeskočit|-|-|O (N)|-|-|Vrací sekvenci, která přeskočí elementy v podkladové sekvenci a následně vrátí zbývající prvky sekvence.|
|SkipWhile –|-|-|O (N)|-|-|Vrací sekvenci, která při iteraci přeskočí prvky podkladové sekvence, zatímco daný predikát vrátí `true` a následně vrátí zbývající prvky sekvence.|
|sort|Průměr O (N protokol n)<br /><br />O (N ^ 2) nejhorší případ|O (N protokol N)|O (N protokol N)|-|-|Seřadí kolekci podle hodnoty elementu. Prvky jsou porovnávány pomocí [Compare](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortBy|Průměr O (N protokol n)<br /><br />O (N ^ 2) nejhorší případ|O (N protokol N)|O (N protokol N)|-|-|Seřadí daný seznam pomocí klíčů, které poskytuje daná projekce. Klíče se porovnávají pomocí [porovnání](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlace –|Průměr O (N protokol n)<br /><br />O (N ^ 2) nejhorší případ|-|-|-|-|Seřadí prvky pole podle jeho použití na místě a pomocí dané funkce porovnání. Prvky jsou porovnány pomocí [porovnání](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceBy –|Průměr O (N protokol n)<br /><br />O (N ^ 2) nejhorší případ|-|-|-|-|Seřadí prvky pole podle jeho použití na místě a pomocí dané projekce pro tyto klíče. Prvky jsou porovnány pomocí [porovnání](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortInPlaceWith|Průměr O (N protokol n)<br /><br />O (N ^ 2) nejhorší případ|-|-|-|-|Seřadí prvky pole podle jeho použití na místě a použitím dané funkce porovnání jako pořadí.|
|sortWith –|Průměr O (N protokol n)<br /><br />O (N ^ 2) nejhorší případ|O (N protokol N)|-|-|-|Seřadí prvky kolekce pomocí dané funkce porovnání jako pořadí a vrátí novou kolekci.|
|sub|O (N)|-|-|-|-|Vytvoří pole, které obsahuje daný dílčí rozsah určený počáteční index a délkou.|
|Součet|O (N)|O (N)|O (N)|-|-|Vrátí součet prvků v kolekci.|
|sumBy –|O (N)|O (N)|O (N)|-|-|Vrátí součet výsledků, které jsou generovány použitím funkce na každý prvek kolekce.|
|kompatibilní|-|O(1)|-|-|-|Vrátí seznam bez jeho prvního prvku.|
|nezbytná|-|-|O (N)|-|-|Vrátí prvky sekvence až do zadaného počtu.|
|TakeWhile –|-|-|O(1)|-|-|Vrací sekvenci, která při iteraci vrátí prvky podkladové sekvence, zatímco daný predikát vrátí `true` a pak nevrátí žádné další prvky.|
|ToArray –|-|O (N)|O (N)|O (N)|O (N)|Vytvoří pole ze zadané kolekce.|
|ToList –|O (N)|-|O (N)|O (N)|O (N)|Vytvoří seznam ze zadané kolekce.|
|toSeq –|O(1)|O(1)|-|O(1)|O(1)|Vytvoří sekvenci ze zadané kolekce.|
|zkrátit|-|-|O(1)|-|-|Vrací sekvenci, která při výčtu nevrátí více než N prvků.|
|tryFind –|O (N)|O (N)|O (N)|O (protokol N)|-|Vyhledá prvek, který splňuje daný predikát.|
|tryFindIndex|O (N)|O (N)|O (N)|-|-|Vyhledá první prvek, který splňuje daný predikát, vrátí index odpovídajícího prvku nebo `None`, pokud žádný takový prvek neexistuje.|
|tryFindKey|-|-|-|O (protokol N)|-|Vrátí klíč prvního mapování v kolekci, který splňuje daný predikát, nebo vrátí hodnotu `None`, pokud žádný takový prvek neexistuje.|
|tryPick –|O (N)|O (N)|O (N)|O (protokol N)|-|Použije danou funkci na po sobě jdoucí prvky a vrátí první výsledek, kde funkce vrátí `Some` pro určitou hodnotu. Pokud žádný takový prvek neexistuje, operace vrátí `None`.|
|unfold|-|-|O (N)|-|-|Vrátí sekvenci, která obsahuje prvky, které vygeneruje daný výpočet.|
|sjednocení|-|-|-|-|O (M &#42; protokol N)|Vypočítá sjednocení dvou sad.|
|UnionMany –|-|-|-|-|O (N1 &#42; N2...)|Vypočítá sjednocení posloupnosti sad.|
|Komprimovat|O (N)|O (N)|O (N)|-|-|Rozdělí seznam párů na dva seznamy.|
|unzip3 –|O (N)|O (N)|O (N)|-|-|Rozdělí seznam trojitých na tři seznamy.|
|oddílové|-|-|O (N)|-|-|Vrací sekvenci, která poskytuje posuvná okna obsahující prvky, které jsou vykresleny ze vstupní sekvence. Každé okno je vráceno jako nové pole.|
|zip|O (N)|O (N)|O (N)|-|-|Kombinuje dvě kolekce do seznamu párů. Dva seznamy musí mít stejné délky.|
|zip3|O (N)|O (N)|O (N)|-|-|Kombinuje tři kolekce do seznamu trojí. Seznamy musí mít stejnou délku.|

## <a name="see-also"></a>Viz také:

- [Typy F#](fsharp-types.md)
- [Referenční dokumentace jazyka F#](index.md)
