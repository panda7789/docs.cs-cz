---
title: Doporučené postupy pro regulární výrazy v rozhraní .NET
description: Naučte se vytvářet efektivní a efektivní regulární výrazy v rozhraní .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, best practices
- regular expressions, best practices
ms.assetid: 618e5afb-3a97-440d-831a-70e4c526a51c
ms.openlocfilehash: ff04b4950f48f2ba06f60b65cc3a46f1295711f3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243151"
---
# <a name="best-practices-for-regular-expressions-in-net"></a>Doporučené postupy pro regulární výrazy v rozhraní .NET

Modul regulárních výrazů v rozhraní .NET je výkonný, plně vybavený nástroj, který zpracovává text na základě shody vzorku, nikoli na porovnávání a porovnávání doslovného textu. Ve většině případů provádí porovnání vzorů rychle a efektivně. V některých případech se však může zdát, že je modul regulárních výrazů velmi pomalý. V extrémních případech se může dokonce zdát, že přestal při zpracování relativně malého vstupu odpovídat po dobu hodin nebo dokonce dní.

Toto téma nastiňuje některé osvědčené postupy, které si mohou vývojáři osvojit za účelem dosažení optimálního výkonu regulárních výrazů.

## <a name="consider-the-input-source"></a>Zvažte vstupní zdroj

Regulární výrazy mohou většinou přijmout dva typy vstupů: vstupy s omezením a vstupy bez omezení. Vstup s omezením je text, který pochází ze známého nebo ověřeného zdroje a odpovídá předdefinovanému formátu. Vstup bez omezení je text, který pochází z neověřeného zdroje, jako je například uživatel webu, a nemusí odpovídat předdefinovanému nebo očekávanému formátu.

Vzory regulárních výrazů jsou obvykle napsány tak, aby odpovídaly platnému vstupu. Vývojáři totiž prozkoumají text, který chtějí porovnat, a následně napíšou vzor regulárního výrazu, který mu odpovídá. Vývojáři následně určí, zda tento vzor vyžaduje korekci nebo další zpracování testováním pomocí většího množství platných vstupních položek. Pokud vzor odpovídá všem předpokládaným platným vstupům, je možné jej uvést do produkce a může být vložen do vydané aplikace. To znamená, že vzor regulárního výrazu je vhodný pro porovnávání se vstupem s omezením. Neznamená to však, že je vhodný pro porovnávání se vstupem bez omezení.

Aby mohl regulární výraz odpovídat vstupu bez omezení, musí být schopen efektivně zpracovat tři druhy textu:

- Text, který odpovídá vzoru regulárního výrazu.

- Text, který neodpovídá vzoru regulárního výrazu.

- Text, který téměř odpovídá vzoru regulárního výrazu.

Poslední typ je zvláště problematický pro regulární výrazy, které jsou napsány tak, aby zpracovávaly vstup s omezením. Pokud tento regulární výraz také závisí na [rozsáhlém navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md), modul regulárních výrazů může strávit nadměrné množství času (v některých případech mnoho hodin nebo dní) zpracovánízdánlivě neškodného textu.

> [!WARNING]
> V následujícím příkladu je použit regulární výraz, který je náchylný na časté používání mechanismu zpětného navracení a který pravděpodobně zamítne platné e-mailové adresy. Neměl by být používán v rutině ověřování e-mailové adresy. Pokud chcete regulární výraz, který ověřuje e-mailové adresy, [přečtěte si postup: Ověření, zda jsou řetězce v platném formátu e-mailu](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).

Předpokládejme například velmi často používaný, ale extrémně problematický regulární výraz pro ověřování aliasu e-mailové adresy. Regulární `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` výraz je zapsán ke zpracování platné e-mailové adresy, která se skládá z alfanumerického znaku následovaného nulou nebo více znaky, které mohou být alfanumerické, tečky nebo pomlčky. Regulární výraz musí končit alfanumerickým znakem. Ačkoli tento regulární výraz snadno zpracovává platný vstup, je velmi neefektivní při zpracování téměř platného vstupu, jak vyplývá z následujícího příkladu.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/design2.cs#1)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/design2.vb#1)]

Jak znázorňuje výstup v příkladu, zpracovává modul regulárních výrazů platný alias e-mailové adresy zhruba stejnou dobu bez ohledu na délku. Na druhou stranu platí, že pokud téměř platná e-mailová adresa obsahuje více než pět znaků, čas zpracování se po přidání každého dalšího znaku do řetězce přibližně zdvojnásobí. To znamená, že zpracování téměř platného osmadvacetiznakového řetězce může trvat více než hodinu a zpracování téměř platného třiatřicetiznakového řetězce bude trvat skoro celý den.

Vzhledem k tomu, že tento regulární řetězec byl vytvořen pouze za předpokladu, že formát vstupu se bude shodovat, nebere v potaz vstup, který neodpovídá vzoru. Tato skutečnost pak může vést k tomu, že vstup bez omezení, který téměř odpovídá vzoru regulárního výrazu, významně sníží výkon.

Chcete-li tento problém vyřešit, proveďte následující akce:

- Při vytváření vzoru je třeba zvážit, jakým způsobem mechanismus zpětného navracení může ovlivnit výkon modulu regulárních výrazů, především tehdy, pokud je regulární výraz navržen pro zpracování vstupu bez omezení. Další informace naleznete v části [Převzít zpětnosné navracení.](#take-charge-of-backtracking)

- Regulární výraz je nutné důkladně odzkoušet pomocí neplatných vstupů, téměř platných vstupů a také platných vstupů. Chcete-li generovat vstup pro konkrétní regulární výraz náhodně, můžete použít [Rex](https://www.microsoft.com/research/project/rex-regular-expression-exploration/), což je nástroj pro průzkum regulárních výrazů z microsoft research.

## <a name="handle-object-instantiation-appropriately"></a>Správně popisovat vytvoření instance objektu

V srdci . NET je objektový model <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> regulárního výrazu třída, která představuje modul regulárních výrazů. Často jeden největší faktor, který ovlivňuje výkon regulárních výrazů je způsob, jakým <xref:System.Text.RegularExpressions.Regex> je použit modul. Definování regulárního výrazu zahrnuje pevné párování modulu regulárních výrazů se vzorem regulárního výrazu. Tento proces párování, zda zahrnuje vytvoření <xref:System.Text.RegularExpressions.Regex> instance objektu předáním jeho konstruktoru vzor regulárního výrazu nebo volání statické metody předáním vzor regulárního výrazu spolu s řetězcem, který má být analyzován, je z nutnosti nákladné jeden.

> [!NOTE]
> Podrobnější informace o dopadech použití interpretovaných a kompilovaných regulárních výrazů na výkon výkonu interpretace, [část II: Převzetí zpětného navracení](https://docs.microsoft.com/archive/blogs/bclteam/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha) v blogu týmu BCL.

Modul regulárních výrazů lze spárovat s konkrétním vzorem regulárního výrazu a následně modul použít pro porovnání textu několika různými způsoby:

- Můžete volat statickou metodu porovnávání <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>vzorů, například . Tato akce nevyžaduje vytvoření instance objektu regulárních výrazů.

- Můžete vytvořit instanci <xref:System.Text.RegularExpressions.Regex> objektu a volat metodu porovnávání vzorů instance interpretovaného regulárního výrazu. Toto je výchozí metoda pro vytvoření vazby modulu regulárních výrazů se vzorem regulárního výrazu. Výsledkem je, <xref:System.Text.RegularExpressions.Regex> když je objekt `options` vytvořena bez <xref:System.Text.RegularExpressions.RegexOptions.Compiled> argumentu, který obsahuje příznak.

- Můžete vytvořit instanci <xref:System.Text.RegularExpressions.Regex> objektu a volat metodu porovnávání vzorů instance zkompilovaného regulárního výrazu. Objekty regulárních výrazů <xref:System.Text.RegularExpressions.Regex> představují kompilované vzorky, když je objekt instanci s argumentem, `options` který obsahuje <xref:System.Text.RegularExpressions.RegexOptions.Compiled> příznak.

- Můžete vytvořit objekt pro <xref:System.Text.RegularExpressions.Regex> speciální účely, který je pevně spojen s určitým vzorem regulárního výrazu, zkompilovat jej a uložit do samostatného sestavení. Provést voláním <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metody.

Způsob, jakým budou metody porovnávání regulárních výrazů volány, může mít zásadní vliv na vaši aplikaci. V následujících částech jsou probírány způsoby volání statických metod, interpretovaných regulárních výrazů a zkompilovaných regulárních výrazů za účelem zvýšení výkonu aplikace.

> [!IMPORTANT]
> Způsob volání metod (statické, interpretované, zkompilované) ovlivňuje výkon, pokud pro volání metod použijete stejný regulární výraz, nebo pokud aplikace příliš často používá objekty regulárních výrazů.

### <a name="static-regular-expressions"></a>Statické regulární výrazy

Statické metody regulárních výrazů jsou vhodnou alternativou k opakovanému vytváření instancí objektů regulárních výrazů se stejným regulárním výrazem. Na rozdíl od vzorů regulárních výrazů používaných objekty regulárních výrazů jsou kódy operací nebo zkompilovaný zprostředkující jazyk Microsoftu (MSIL) ze vzorků používaných ve volání chodu statické metody interně ukládádo mezipaměti modulu regulárních výrazů.

Například pro ověření uživatelského vstupu volá obslužná rutina události často jinou metodu. To se projeví v následujícím kódu, ve kterém se událost ovládacího <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> prvku používá k volání metody s názvem `IsValidCurrency`, která kontroluje, zda uživatel zadal symbol měny následovaný alespoň jednou desetinnou číslicí.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#2)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#2)]

Velmi neefektivní implementace `IsValidCurrency` metody je uvedena v následujícím příkladu. Všimněte si, že každá metoda <xref:System.Text.RegularExpressions.Regex> volání reinstantiates objekt se stejným vzorem. To znamená, že vzor regulárního výrazu musí být při každém dalším volání metody znovu zkompilován.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#3)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#3)]

Tento neefektivní kód byste měli nahradit <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> voláním statické metody. To eliminuje potřebu vytvořit instanci <xref:System.Text.RegularExpressions.Regex> objektu pokaždé, když chcete volat metodu porovnávání vzorů, a umožňuje modulu regulárních výrazů načíst z kompilované verze regulárního výrazu z mezipaměti.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static2.cs#4)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static2.vb#4)]

Ve výchozím nastavení je v mezipaměti uloženo posledních 15 použitých vzorů regulárních výrazů. U aplikací, které vyžadují větší počet statických regulárních výrazů v mezipaměti, lze velikost mezipaměti upravit nastavením vlastnosti. <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType>

Regulární `\p{Sc}+\s*\d+` výraz, který se používá v tomto příkladu, ověří, zda se vstupní řetězec skládá ze symbolu měny a alespoň jedné desetinné číslice. Vzor je definován tak, jak je uvedeno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`\p{Sc}+`|Porovná jeden nebo více znaků z kategorie měn a symbolů Unicode.|
|`\s*`|Porovná žádný nebo více prázdných znaků.|
|`\d+`|Porovná jednu nebo více desítkových číslic.|

### <a name="interpreted-vs-compiled-regular-expressions"></a>Interpretováno vs. kompilované regulární výrazy

Jsou interpretovány vzory regulárních výrazů, které <xref:System.Text.RegularExpressions.RegexOptions.Compiled> nejsou vázány na modul regulárních výrazů prostřednictvím specifikace možnosti. Po vytvoření instance objektu regulárního výrazu převede modul regulárních výrazů regulární výraz na množinu kódů operací. Po zavolání metody instance jsou operační kódy převedeny do jazyka MSIL a provedeny kompilátorem JIT. Obdobně platí, že pokud zavoláte statickou metodu regulárních výrazů a regulární výraz nelze nalézt v mezipaměti, modul regulárních výrazů převede regulární výraz na množinu operačních kódů a uloží je do mezipaměti. Poté jsou tyto operační kódy převedeny do jazyka MSIL, aby je mohl kompilátor JIT provést. U interpretovaných regulárních výrazů je čas spuštění zkrácen na úkor delšího času provádění. Z tohoto důvodu je nejvhodnější je používat tehdy, pokud je regulární výraz použit v nízkém počtu volání metod, nebo pokud přesný počet volání metod regulárních výrazů není znám, ale očekává se, že bude nízký. S rostoucím počtem volání metod je výkonový zisk plynoucí z kratší doby spouštění kompenzován nižší rychlostí provádění.

Jsou kompilovány vzory regulárních výrazů, <xref:System.Text.RegularExpressions.RegexOptions.Compiled> které jsou vázány na modul regulárních výrazů prostřednictvím specifikace možnosti. To znamená, že když vytvoříte instanci objektu regulárního výrazu nebo když voláte statickou metodu regulárních výrazů a regulární výraz zároveň nelze nalézt v mezipaměti, modul regulárních výrazů převede regulární výraz na mezilehlou množinu operačních kódů, které jsou následně převedeny do jazyka MSIL. Jakmile metodu zavoláte, kompilátor JIT provede kód MSIL. Na rozdíl od interpretovaných regulárních výrazů mají zkompilované regulární výrazy delší dobu spouštění, jednotlivé metody porovnávání se však provádí rychleji. Ve výsledku se výkonový zisk plynoucí z kompilování regulárního výrazu zvyšuje s počtem regulárních výrazů, které metoda volá.

Shrnutí: V případě, že metody regulárních výrazů s konkrétním regulárním výrazem nebudou volány tak často, doporučujeme vám, abyste použili interpretované regulární výrazy. Pokud metody regulárních výrazů s konkrétním regulárním výrazem voláte relativně často, měli byste použít zkompilované regulární výrazy. Je těžké stanovit přesný práh, kdy delší doba provádění interpretovaných regulárních výrazů převyšuje výkonový zisk plynoucí z kratší doby provádění, nebo práh, kdy kratší doba spouštění zkompilovaných regulárních výrazů převyšuje výkonový zisk plynoucí z kratší doby provádění. Tato možnost závisí na různých faktorech, mezi které patří složitost regulárního výrazu a konkrétní data, která jsou zpracovávána. Chcete-li zjistit, zda interpretované nebo zkompilované regulární výrazy <xref:System.Diagnostics.Stopwatch> nabízejí nejlepší výkon pro konkrétní scénář aplikace, můžete použít třídu porovnat jejich doby provádění.

Následující příklad porovnává výkon kompilovaných a interpretovaných regulárních výrazů při čtení prvních deseti vět a při čtení všech vět v textu Theodora Dreisera *Finančník*. Jak znázorňuje výstup uvedený v příkladu, interpretovaný regulární výraz nabízí lepší výkon než zkompilovaný regulární výraz pouze tehdy, pokud je provedeno pouze deset volání metody porovnávání regulárních výrazů. Zkompilovaný regulární výraz však nabízí lepší výkon, pokud je proveden větší počet volání (v tomto případě 13 000).

[!code-csharp[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compare1.cs#5)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compare1.vb#5)]

Vzor regulárního výrazu `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`použitý v příkladu , je definován tak, jak je znázorněno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`\b`|Začne porovnání na hranici slova.|
|`\w+`|Porovná jeden nebo více znaků slova.|
|<code>(\r?\n)&#124;,?\s)</code>|Porovná buď žádný, nebo jeden návratový znak následovaný znakem nového řádku, nebo žádnou či jednou čárkou následovanou prázdným znakem.|
|<code>(\w+((\r?\n)&#124;,?\s))*</code>|Porovná žádný nebo více výskytů jednoho nebo více znaků slova následovaných žádným nebo jedním návratovým znakem a znakem nového řádku, nebo žádnou či jednou čárkou následovanou prázdným znakem.|
|`\w+`|Porovná jeden nebo více znaků slova.|
|`[.?:;!]`|Porovná tečku, otazník, dvojtečku, středník nebo vykřičník.|

### <a name="regular-expressions-compiled-to-an-assembly"></a>Regulární výrazy: Zkompilován do sestavení

Rozhraní .NET také umožňuje vytvořit sestavení, které obsahuje kompilované regulární výrazy. Tím dojde k přesunu výkonnosti regulárního výrazu z doby spuštění do doby návrhu. Tato akce však zahrnuje další úkony: musíte předem definovat regulární výrazy a zkompilovat je do sestavení. Kompilátor může poté odkazovat na toto sestavení při kompilaci zdrojového kódu, který používá regulární výrazy sestavení. Každý zkompilovaný regulární výraz v sestavení <xref:System.Text.RegularExpressions.Regex>je reprezentován třídou, která je odvozena z aplikace .

Chcete-li zkompilovat regulární <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%28System.Text.RegularExpressions.RegexCompilationInfo%5B%5D%2CSystem.Reflection.AssemblyName%29?displayProperty=nameWithType> výrazy do sestavení, zavolejte metodu a předejte ji pole <xref:System.Text.RegularExpressions.RegexCompilationInfo> objektů, které představují regulární výrazy, které mají být kompilovány, a <xref:System.Reflection.AssemblyName> objekt, který obsahuje informace o sestavení, které má být vytvořeno.

Kompilaci regulárních výrazů do sestavení doporučujeme provádět v následujících situacích:

- Pokud pracujete jako vývojář komponent a chcete vytvořit knihovnu znovupoužitelných regulárních výrazů.

- Pokud očekáváte, že metody porovnávání se vzorem regulárních výrazů budou mít neurčitý počet volání – v rozsahu od jednoho nebo dvou do tisíců nebo desítek tisíců volání. Na rozdíl od zkompilovaných nebo interpretovaných regulárních výrazů nabízejí regulární výrazy, které jsou zkompilovány do samostatných sestavení, výkon, který je konzistentní bez ohledu na počet volání metod.

Pokud jsou pro optimalizaci výkonu použity kompilované regulární výrazy, neměla by pro vytvoření sestavení, načtení modulu regulárních výrazů a provedení metod porovnávání se vzorem být použita reflexe. Tato akce vyžaduje vynechání dynamického sestavování vzorů regulárních výrazů a zadání možnosti nastavení porovnávání se vzorem (jako je například porovnávání s rozlišováním velkých a malých čísel) během vytváření sestavení. Vyžaduje také oddělení kódu, který vytváří sestavení, od kódu, který používá regulární výraz.

Následující příklad znázorňuje způsob vytvoření sestavení, které obsahuje zkompilovaný regulární výraz. Vytvoří sestavení s `RegexLib.dll` názvem s jednou `SentencePattern`třídou regulárního výrazu , která obsahuje vzor regulárního výrazu odpovídající větě použitý v části [Interpretované vs. kompilované regulární výrazy.](#interpreted-vs-compiled-regular-expressions)

[!code-csharp[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile1.cs#6)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile1.vb#6)]

Když je příklad zkompilován do spustitelného souboru a spuštěn, vytvoří sestavení s názvem `RegexLib.dll`. Regulární výraz je reprezentován třídou s názvem `Utilities.RegularExpressions.SentencePattern` , která je odvozena od . <xref:System.Text.RegularExpressions.Regex> Následující příklad pak používá zkompilovaný regulární výraz k extrahování vět z textu Theodora Dreisera *The Financier*.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile2.cs#7)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile2.vb#7)]

## <a name="take-charge-of-backtracking"></a>Převzít backtracking

Pro posouvání ve vstupním řetězci a porovnání řetězce se vzorem regulárního výrazu používá regulární výraz většinou lineární posloupnost. Pokud se však neurčité kvantifikátory, například `*`, `+`a `?` používají ve vzoru regulárních výrazů, může se modul regulárních výrazů vzdát části úspěšných částečných shod a vrátit se do dříve uloženého stavu, aby vyhledal úspěšnou shodu pro celý vzorek. Tento proces se označuje jako zpětné navracení.

> [!NOTE]
> Další informace o navracení naleznete [v tématu Podrobnosti o chování regulárních výrazů](../../../docs/standard/base-types/details-of-regular-expression-behavior.md) a [navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md). Podrobnou diskusi o navracení najdete v [tématu Optimalizace výkonu regulárních výrazů, část II: Převzetí zpětného navracení](https://docs.microsoft.com/archive/blogs/bclteam/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha) v blogu týmu BCL.

Podpora zpětného navracení zajišťuje regulárním výrazům výkon a flexibilitu. Zároveň přenáší odpovědnost za řízení provozu modulu regulárních výrazů do rukou vývojáře regulárních výrazů. Vzhledem k tomu, že vývojáři si často tuto odpovědnost neuvědomují, jejich špatný způsob používání mechanismu navracení nebo přílišné používání tohoto mechanismu hraje nejdůležitější roli při snížení výkonu regulárních výrazů. V nejhorším případě se doba provádění může s každým dalším znakem ve vstupním řetězci zdvojnásobit. Přílišným používáním mechanismu navracení je vlastně velmi snadné vytvořit programový ekvivalent nekonečné smyčky, pokud se vstup téměř shoduje se vzorem regulárního výrazů; modulu regulárních výrazů může trvat hodiny, nebo dokonce dny, než zpracuje relativně krátký vstupní řetězec.

Aplikace často platí daň za snížený výkon při používání zpětného navracení navzdory skutečnosti, že mechanismus zpětného navracení není pro shodu klíčový. Například regulární `\b\p{Lu}\w*\b` výraz odpovídá všem slovům, která začínají znakem velkých písmen, jak ukazuje následující tabulka.

|Vzor|Popis|
|-|-|
|`\b`|Začne porovnání na hranici slova.|
|`\p{Lu}`|Porovná znak velkého písmena.|
|`\w*`|Porovná žádný nebo více znaků slova.|
|`\b`|Ukončí porovnání na hranici slova.|

Vzhledem k tomu, že hranice slova se neshoduje s hranicí znaku slova ani není jeho podmnožinou, nemá modul regulárních výrazů žádnou možnost při porovnávání znaků překročit hranici slova. To znamená, že pro tento regulární výraz nemůže mechanismus zpětného navracení nikdy přispět k celkovému úspěšnému vyhledání jakékoli shody – může pouze snížit výkon, protože modul regulárních výrazů je nucen uložit stav pro každou předběžně úspěšnou shodu znaku slova.

Pokud zjistíte, že navracení není nutné, můžete `(?>subexpression)` jej zakázat pomocí elementu jazyka, známého jako atomická skupina. Následující příklad analyzuje vstupní řetězec pomocí dvou regulárních výrazů. První , `\b\p{Lu}\w*\b`spoléhá na navracení. Druhý , `\b\p{Lu}(?>\w*)\b`zakáže navracení. Jak znázorňuje výstup z příkladu, vytvoří oba výrazy stejný výsledek.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack2.cs#10)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack2.vb#10)]

V mnoha případech je zpětné navracení pro porovnávání vzorů regulárních výrazů se vstupním textem nezbytné. Přílišné používání mechanismu navracení však může zásadním způsobem snížit výkon a vytvořit dojem, že aplikace přestala odpovídat. K této situaci dochází především tehdy, pokud jsou kvalifikátory vnořené a text, který se shoduje s vnějším dílčím výrazem, je podmnožinou textu, který se shoduje s vnějším dílčím výrazem.

> [!WARNING]
> Kromě toho, že byste mechanismus navracení neměli často používat, byste také měli použít funkci časového limitu, aby přílišné používání zpětného navracení nezpůsobovalo zásadní snížení výkonu regulárních výrazů. Další informace naleznete v části [Použití hodnot časového času.](#use-time-out-values)

Například vzor `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` regulárního výrazu je určen tak, aby odpovídal číslu dílu, který se skládá alespoň z jednoho alfanumerického znaku. Mezi dalšími znaky může být alfanumerický znak, spojovník, podtržítko nebo tečka, poslední znak však musí být alfanumerický. Znak dolaru ukončuje číslo součásti. V některých případech může tento vzor regulárního výrazu vykazovat extrémně nízký `[0-9A-Z]` výkon, protože kvantifikátory jsou vnořeny a protože dílčí výraz je podmnožinou dílčího výrazu `[-.\w]*`.

V těchto případech lze výkon regulárních výrazů optimalizovat odebráním vnořených kvantifikátorů a nahrazením vnějšího dílčího výrazu kontrolním výrazem dopředného nebo zpětného vyhledávání s nulovou šířkou. Kontrolní výrazy dopředného a zpětného vyhledávání fungují jako kotvy: neposouvají ukazatele ve vstupním řetězci, ale prohledávají směrem dopředu nebo dozadu a ověřují, zda byla splněna konkrétní podmínka. Regulární výraz číslo dílu lze `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`například přepsat jako . Tento vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`^`|Zahájí porovnávání na začátku vstupního řetězce.|
|`[0-9A-Z]`|Porovná alfanumerický znak. Číslo součásti musí obsahovat alespoň tento znak.|
|`[-.\w]*`|Porovná žádný nebo více výskytů znaku slova, spojovníku nebo tečky.|
|`\$`|Porovná znak dolaru.|
|`(?<=[0-9A-Z])`|Vyhledá směrem dopředu znak dolaru a ověří, zda je předchozí znak alfanumerický.|
|`$`|Ukončí porovnávání na konci vstupního řetězce.|

Následující příklad znázorňuje používání tohoto regulárního výrazu pro porovnání pole obsahujícího pravděpodobná čísla součástí.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack4.cs#11)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack4.vb#11)]

Jazyk regulárních výrazů v rozhraní .NET obsahuje následující prvky jazyka, které můžete použít k odstranění vnořených kvantifikátorů. Další informace naleznete v [tématu Seskupování konstrukcí](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

|Prvek jazyka|Popis|
|----------------------|-----------------|
|`(?=` `subexpression` `)`|Pozitivní dopředné vyhledávání s nulovou šířkou. Podívejte se před aktuální pozici `subexpression` k určení, zda odpovídá vstupní řetězec.|
|`(?!` `subexpression` `)`|Negativní dopředné vyhledávání s nulovou šířkou. Podívejte se dopředu aktuální pozici `subexpression` k určení, zda neodpovídá vstupní řetězec.|
|`(?<=` `subexpression` `)`|Pozitivní zpětné vyhledávání s nulovou šířkou. Podívejte se za aktuální `subexpression` pozici k určení, zda odpovídá vstupní řetězec.|
|`(?<!` `subexpression` `)`|Negativní zpětné vyhledávání s nulovou šířkou. Podívejte se za aktuální `subexpression` pozici k určení, zda neodpovídá vstupní řetězec.|

## <a name="use-time-out-values"></a>Použití hodnot časového času

Pokud regulární výraz zpracovává vstup, který téměř odpovídá vzoru regulárního výrazu, může se často spoléhat na přílišné používání zpětného navracení, což má velký dopad na výkon. Kromě pečlivého zvážení používání mechanismu zpětného navracení a ověřování regulárního výrazu s téměř shodným vstupem byste měli nastavit hodnotu časového limitu, který minimalizuje vliv přílišného používání mechanismu zpětného navracení, pokud k němu dojde.

Časový interval regulárního výrazu definuje časové období, po které bude modul regulárních výrazů hledat jednu shodu před časovým intervalem. Výchozí časový limit je <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType>, což znamená, že regulární výraz nebude časový limit. Tuto hodnotu můžete přepsat a definovat interval časového intervalu následujícím způsobem:

- Poskytnutím hodnoty časového času při vytváření instancí objektu <xref:System.Text.RegularExpressions.Regex> voláním konstruktoru. <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29>

- Voláním statické metody porovnávání <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> vzorů, například nebo <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>, která obsahuje `matchTimeout` parametr.

- Pro zkompilované regulární výrazy, které jsou vytvořeny voláním <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metody <xref:System.TimeSpan>voláním konstruktoru, který má parametr typu .

Pokud jste definovali časový interval a shoda nebyla nalezena na konci tohoto intervalu, metoda regulárního výrazu vyvolá výjimku. <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> V obslužné rutině výjimek můžete zadat nové vyhledávání shody s delším intervalem časového limitu, zrušit pokus o vyhledání shody a předpokládat, že shoda neexistuje, nebo zrušit pokus o vyhledání shody a vytvořit protokol s informacemi o výjimce pro další analýzu.

Následující příklad definuje `GetWordData` metodu, která inkonaluje regulární výraz s časovým intervalem 350 milisekund pro výpočet počtu slov a průměrného počtu znaků ve slově v textovém dokumentu. Pokud časový interval odpovídající operace je časový interval zvýšen o 350 <xref:System.Text.RegularExpressions.Regex> milisekund a objekt je re-instanceed. Pokud nový interval časového limitu překročí 1 sekundu, metoda opětovně vyvolá výjimku pro volajícího.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/timeout1.cs#12)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/timeout1.vb#12)]

## <a name="capture-only-when-necessary"></a>Zachyťte pouze v případě potřeby

Regulární výrazy v rozhraní .NET podporují řadu seskupovacích konstrukcí, které umožňují seskupit vzorek regulárního výrazu do jednoho nebo více podvýrazů. Nejčastěji používané `(`seskupovací konstrukce v jazyce regulárních výrazů .NET jsou `(?<` *podvýraz*`)`, který definuje číslovanou zachytávající skupinu, a*podvýraz*`)` *názvu*`>`, který definuje pojmenovanou zachytávající skupinu. Seskupovací konstrukce jsou nezbytné pro vytváření a definování dílčího výrazu, pro který je použit kvantifikátor.

Používání těchto prvků jazyka však má svou cenu. Způsobí, <xref:System.Text.RegularExpressions.GroupCollection> že objekt <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vrácený vlastností má být naplněn nejnovějšími nepojmenovanými nebo pojmenovanými zachyceními a pokud jedna konstrukce seskupení zachytila více podřetězců ve vstupním řetězci, naplní také <xref:System.Text.RegularExpressions.CaptureCollection> objekt vrácený <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastností určité zachytávající skupiny více <xref:System.Text.RegularExpressions.Capture> objekty.

Seskupovací konstrukce se v regulárních výrazech používají pouze proto, aby na ně mohly být aplikovány kvantifikátory a aby skupiny zachycené těmito dílčími výrazy nebyly poté používány. Regulární výraz `\b(\w+[;,]?\s?)+[.?!]` je například určen k zachycení celé věty. Následující tabulka popisuje prvky jazyka v tomto vzoru <xref:System.Text.RegularExpressions.Match> regulárních <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> výrazů a jejich vliv na objekt a kolekce.

|Vzor|Popis|
|-------------|-----------------|
|`\b`|Začne porovnání na hranici slova.|
|`\w+`|Porovná jeden nebo více znaků slova.|
|`[;,]?`|Porovná žádnou nebo jednu čárku či středník.|
|`\s?`|Porovná žádný nebo jeden prázdný znak.|
|`(\w+[;,]?\s?)+`|Porovná jeden nebo několik výskytů znaků slova následovaných nepovinnou čárkou nebo středníkem, za kterými následuje nepovinný prázdný znak. Tím je definována první zachytávající skupina, která je nezbytná k tomu, aby kombinace více znaků slova (neboli slovo) následovaná nepovinným interpunkčním symbolem opakovala, dokud modul regulárních výrazů nedosáhne konce věty.|
|`[.?!]`|Porovná tečku, otazník nebo vykřičník.|

Jak ukazuje následující příklad, při nalezení shody jsou <xref:System.Text.RegularExpressions.GroupCollection> objekty i <xref:System.Text.RegularExpressions.CaptureCollection> objekty naplněny zachyceními ze shody. V tomto případě zachytávající skupina `(\w+[;,]?\s?)` `+` existuje tak, aby kvantifikátor mohl být použit na něj, což umožňuje, aby vzor regulárního výrazu odpovídal každému slovu ve větě. V opačném případě může odpovídat poslednímu slovu ve větě.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group1.cs#8)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group1.vb#8)]

Pokud použijete dílčí výrazy pouze proto, abyste mohli použít kvantifikátor a zachycený text pro vás není podstatný, měli byste skupinové zachytávání zakázat. Například element `(?:subexpression)` jazyka zabraňuje skupině, na kterou se vztahuje, zachytit odpovídající podřetězce. V následujícím příkladu se změní vzor regulárního výrazu z předchozího příkladu na `\b(?:\w+[;,]?\s?)+[.?!]`. Jak ukazuje výstup, zabrání modulu regulárních výrazů v vyplnění kolekce <xref:System.Text.RegularExpressions.GroupCollection> a. <xref:System.Text.RegularExpressions.CaptureCollection>

[!code-csharp[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group2.cs#9)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group2.vb#9)]

Zachytávání lze zakázat jedním z následujících způsobů:

- Použijte `(?:subexpression)` prvek jazyka. Tento prvek zabraňuje v zachytávání shodných podřetězců ve skupině, pro kterou se používá. Nezakazuje zachytávání podřetězců v jakékoli vnořené skupině.

- Použijte <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> tuto možnost. Zakazuje všechna nepojmenovaná nebo implicitní zachycení ve vzoru regulárního výrazu. Při použití této možnosti lze zachytit pouze podřetězce, které odpovídají pojmenovaným skupinám definovaným s elementem `(?<name>subexpression)` jazyka. Příznak <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> může být předán `options` parametru <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo <xref:System.Text.RegularExpressions.Regex> parametru `options` statické odpovídající metody.

- Použijte `n` možnost v `(?imnsx)` elementu jazyka. Tato možnost zakazuje všechna nepojmenovaná nebo implicitní zachycení z bodu ve vzoru regulárního výrazu, ve kterém se prvek objeví. Zachycení jsou zakázány buď do konce vzoru `(-n)` nebo dokud možnost povolí nepojmenované nebo implicitní zachycení. Další informace naleznete v tématu [Různé konstrukce](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md).

- Použijte `n` možnost v `(?imnsx:subexpression)` elementu jazyka. Tato možnost zakáže všechna nepojmenovaná nebo implicitní zachycení v programu `subexpression`. Zachycení nepojmenovanou nebo implicitní vnořenou zachytávající skupinou jsou rovněž zakázána.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Podrobnosti k chování regulárních výrazů](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|Zkoumá implementaci modulu regulárních výrazů v rozhraní .NET. Téma se zaměřuje na flexibilitu regulárních výrazů a objasňuje odpovědnost vývojáře za zajištění efektivity a výkonnosti modulu regulárních výrazů.|
|[Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Vysvětluje princip zpětného navracení a vliv tohoto mechanismu na výkon regulárních výrazů a zkoumá prvky jazyka, které nabízí alternativu zpětného navracení.|
|[Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Popisuje prvky jazyka regulárních výrazů v rozhraní .NET a obsahuje odkazy na podrobnou dokumentaci pro každý element jazyka.|
