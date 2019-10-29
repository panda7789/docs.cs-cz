---
title: Osvědčené postupy pro regulární výrazy v .NET
description: Naučte se vytvářet efektivní a efektivní regulární výrazy v .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, best practices
- regular expressions, best practices
ms.assetid: 618e5afb-3a97-440d-831a-70e4c526a51c
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 89585ff97183912feb9b9af0bd326041b7381bfb
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774309"
---
# <a name="best-practices-for-regular-expressions-in-net"></a>Osvědčené postupy pro regulární výrazy v .NET

Modul regulárních výrazů v rozhraní .NET je účinný, plně funkční nástroj, který zpracovává text na základě porovnávání vzorů, nikoli porovnávání a porovnávání literálního textu. Ve většině případů provádí porovnání vzorů rychle a efektivně. V některých případech se však může zdát, že je modul regulárních výrazů velmi pomalý. V extrémních případech se může dokonce zdát, že přestal při zpracování relativně malého vstupu odpovídat po dobu hodin nebo dokonce dní.

Toto téma nastiňuje některé osvědčené postupy, které si mohou vývojáři osvojit za účelem dosažení optimálního výkonu regulárních výrazů.

## <a name="consider-the-input-source"></a>Vezměte v úvahu vstupní zdroj

Regulární výrazy mohou většinou přijmout dva typy vstupů: vstupy s omezením a vstupy bez omezení. Vstup s omezením je text, který pochází ze známého nebo ověřeného zdroje a odpovídá předdefinovanému formátu. Vstup bez omezení je text, který pochází z neověřeného zdroje, jako je například uživatel webu, a nemusí odpovídat předdefinovanému nebo očekávanému formátu.

Vzory regulárních výrazů jsou obvykle napsány tak, aby odpovídaly platnému vstupu. Vývojáři totiž prozkoumají text, který chtějí porovnat, a následně napíšou vzor regulárního výrazu, který mu odpovídá. Vývojáři následně určí, zda tento vzor vyžaduje korekci nebo další zpracování testováním pomocí většího množství platných vstupních položek. Pokud vzor odpovídá všem předpokládaným platným vstupům, je možné jej uvést do produkce a může být vložen do vydané aplikace. To znamená, že vzor regulárního výrazu je vhodný pro porovnávání se vstupem s omezením. Neznamená to však, že je vhodný pro porovnávání se vstupem bez omezení.

Aby mohl regulární výraz odpovídat vstupu bez omezení, musí být schopen efektivně zpracovat tři druhy textu:

- Text, který odpovídá vzoru regulárního výrazu.

- Text, který neodpovídá vzoru regulárního výrazu.

- Text, který téměř odpovídá vzoru regulárního výrazu.

Poslední typ je zvláště problematický pro regulární výrazy, které jsou napsány tak, aby zpracovávaly vstup s omezením. Pokud tento regulární výraz také spoléhá na rozsáhlé [zpětné navrácení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md), modul regulárních výrazů může strávit nadměrné množství času (v některých případech mnoho hodin nebo dnů) a zpracovává zdánlivě neškodného text.

> [!WARNING]
> V následujícím příkladu je použit regulární výraz, který je náchylný na časté používání mechanismu zpětného navracení a který pravděpodobně zamítne platné e-mailové adresy. Neměl by být používán v rutině ověřování e-mailové adresy. Chcete-li regulární výraz, který ověřuje e-mailové adresy, přečtěte si téma [How to: Ověřte, že jsou řetězce v platném formátu e-mailu](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).

Předpokládejme například velmi často používaný, ale extrémně problematický regulární výraz pro ověřování aliasu e-mailové adresy. Regulární výraz `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` je zapsán pro zpracování toho, co je považováno za platnou e-mailovou adresu, která se skládá z alfanumerického znaku následovaných žádným nebo více znaky, které mohou být alfanumerické, tečky nebo spojovníky. Regulární výraz musí končit alfanumerickým znakem. Ačkoli tento regulární výraz snadno zpracovává platný vstup, je velmi neefektivní při zpracování téměř platného vstupu, jak vyplývá z následujícího příkladu.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/design2.cs#1)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/design2.vb#1)]

Jak znázorňuje výstup v příkladu, zpracovává modul regulárních výrazů platný alias e-mailové adresy zhruba stejnou dobu bez ohledu na délku. Na druhou stranu platí, že pokud téměř platná e-mailová adresa obsahuje více než pět znaků, čas zpracování se po přidání každého dalšího znaku do řetězce přibližně zdvojnásobí. To znamená, že zpracování téměř platného osmadvacetiznakového řetězce může trvat více než hodinu a zpracování téměř platného třiatřicetiznakového řetězce bude trvat skoro celý den.

Vzhledem k tomu, že tento regulární řetězec byl vytvořen pouze za předpokladu, že formát vstupu se bude shodovat, nebere v potaz vstup, který neodpovídá vzoru. Tato skutečnost pak může vést k tomu, že vstup bez omezení, který téměř odpovídá vzoru regulárního výrazu, významně sníží výkon.

Chcete-li tento problém vyřešit, proveďte následující akce:

- Při vytváření vzoru je třeba zvážit, jakým způsobem mechanismus zpětného navracení může ovlivnit výkon modulu regulárních výrazů, především tehdy, pokud je regulární výraz navržen pro zpracování vstupu bez omezení. Další informace najdete v části [převzetí zpětného navrácení](#take-charge-of-backtracking) .

- Regulární výraz je nutné důkladně odzkoušet pomocí neplatných vstupů, téměř platných vstupů a také platných vstupů. K náhodnému vygenerování vstupu pro konkrétní regulární výraz lze použít [Rex](https://www.microsoft.com/research/project/rex-regular-expression-exploration/), což je nástroj pro zkoumání regulárních výrazů od společnosti Microsoft Research.

## <a name="handle-object-instantiation-appropriately"></a>Vhodně zpracovat vytváření instancí objektu

Srdce. Model objektu regulárního výrazu netto je třída <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>, která představuje modul regulárních výrazů. Jediný největší faktor, který ovlivňuje výkon regulárních výrazů, je často způsob, jakým se používá modul <xref:System.Text.RegularExpressions.Regex>. Definování regulárního výrazu zahrnuje pevné párování modulu regulárních výrazů se vzorem regulárního výrazu. Tento spojovací proces, ať už zahrnuje vytvoření instance objektu <xref:System.Text.RegularExpressions.Regex> předáním jeho konstruktoru vzor regulárního výrazu nebo voláním statické metody předáním vzoru regulárního výrazu společně s řetězcem, který má být analyzován, je nutností finančně jedna.

> [!NOTE]
> Podrobnější diskuzi o vlivech na výkon použití interpretovaných a zkompilovaných regulárních výrazů naleznete v tématu [optimalizace výkonu regulárních výrazů, část II: Přebírání zpětného navrácení](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) na blogu týmu BCL.

Modul regulárních výrazů lze spárovat s konkrétním vzorem regulárního výrazu a následně modul použít pro porovnání textu několika různými způsoby:

- Můžete zavolat statickou metodu porovnávání vzorů, například <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>. Tato akce nevyžaduje vytvoření instance objektu regulárních výrazů.

- Můžete vytvořit instanci objektu <xref:System.Text.RegularExpressions.Regex> a volat metodu porovnávání vzorů pro interpretovaný regulární výraz. Toto je výchozí metoda pro vytvoření vazby modulu regulárních výrazů se vzorem regulárního výrazu. Dojde k tomu při vytváření instance <xref:System.Text.RegularExpressions.Regex>ho objektu bez argumentu `options`, který obsahuje příznak <xref:System.Text.RegularExpressions.RegexOptions.Compiled>.

- Můžete vytvořit instanci objektu <xref:System.Text.RegularExpressions.Regex> a volat metodu instance porovnávání vzorů zkompilovaného regulárního výrazu. Objekty regulárních výrazů reprezentují zkompilované vzory, když je vytvořena instance objektu <xref:System.Text.RegularExpressions.Regex> s argumentem `options`, který obsahuje příznak <xref:System.Text.RegularExpressions.RegexOptions.Compiled>.

- Můžete vytvořit objekt <xref:System.Text.RegularExpressions.Regex> pro zvláštní účely, který je úzce spojen s konkrétním vzorem regulárního výrazu, zkompilovat jej a Uložit do samostatného sestavení. Provedete to tak, že zavoláte metodu <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType>.

Způsob, jakým budou metody porovnávání regulárních výrazů volány, může mít zásadní vliv na vaši aplikaci. V následujících částech jsou probírány způsoby volání statických metod, interpretovaných regulárních výrazů a zkompilovaných regulárních výrazů za účelem zvýšení výkonu aplikace.

> [!IMPORTANT]
> Způsob volání metod (statické, interpretované, zkompilované) ovlivňuje výkon, pokud pro volání metod použijete stejný regulární výraz, nebo pokud aplikace příliš často používá objekty regulárních výrazů.

### <a name="static-regular-expressions"></a>Statické regulární výrazy

Statické metody regulárních výrazů jsou vhodnou alternativou k opakovanému vytváření instancí objektů regulárních výrazů se stejným regulárním výrazem. Na rozdíl od vzorů regulárních výrazů používaných objekty regulárních výrazů, jsou kódy operací nebo zkompilovaný jazyk MSIL (Microsoft Intermediate Language) ze vzorů používaných ve statických voláních metod ukládány do mezipaměti interně modulem regulárních výrazů.

Například pro ověření uživatelského vstupu volá obslužná rutina události často jinou metodu. To se odrazí v následujícím kódu, ve kterém se <xref:System.Windows.Forms.Control.Click> událost <xref:System.Windows.Forms.Button> ovládacího prvku používá k volání metody s názvem `IsValidCurrency`, která kontroluje, zda uživatel zadal symbol měny následovaný alespoň jednou desítkovou číslicí.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#2)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#2)]

V následujícím příkladu je uvedena velmi neefektivní implementace metody `IsValidCurrency`. Všimněte si, že všechny volání metody znovu vytvoří instanci objektu <xref:System.Text.RegularExpressions.Regex> se stejným vzorem. To znamená, že vzor regulárního výrazu musí být při každém dalším volání metody znovu zkompilován.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#3)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#3)]

Tento neefektivní kód byste měli nahradit voláním metody static <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType>. To eliminuje nutnost vytvoření instance <xref:System.Text.RegularExpressions.Regex> objektu pokaždé, když chcete zavolat metodu porovnávání se vzorem, a umožňuje modulu regulárních výrazů načíst zkompilovanou verzi regulárního výrazu z jeho mezipaměti.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static2.cs#4)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static2.vb#4)]

Ve výchozím nastavení je v mezipaměti uloženo posledních 15 použitých vzorů regulárních výrazů. U aplikací, které vyžadují větší počet statických regulárních výrazů uložených v mezipaměti, lze velikost mezipaměti upravit nastavením vlastnosti <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType>.

Regulární výraz `\p{Sc}+\s*\d+`, který je použit v tomto příkladu ověřuje, zda vstupní řetězec obsahuje symbol měny a alespoň jednu desítkovou číslici. Vzor je definován tak, jak je uvedeno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`\p{Sc}+`|Porovná jeden nebo více znaků z kategorie měn a symbolů Unicode.|
|`\s*`|Porovná žádný nebo více prázdných znaků.|
|`\d+`|Porovná jednu nebo více desítkových číslic.|

### <a name="interpreted-vs-compiled-regular-expressions"></a>Interpretované a kompilované regulární výrazy

Vzory regulárních výrazů, které nejsou vázány na modul regulárních výrazů pomocí specifikace možnosti <xref:System.Text.RegularExpressions.RegexOptions.Compiled> jsou interpretovány. Po vytvoření instance objektu regulárního výrazu převede modul regulárních výrazů regulární výraz na množinu kódů operací. Po zavolání metody instance jsou operační kódy převedeny do jazyka MSIL a provedeny kompilátorem JIT. Obdobně platí, že pokud zavoláte statickou metodu regulárních výrazů a regulární výraz nelze nalézt v mezipaměti, modul regulárních výrazů převede regulární výraz na množinu operačních kódů a uloží je do mezipaměti. Poté jsou tyto operační kódy převedeny do jazyka MSIL, aby je mohl kompilátor JIT provést. U interpretovaných regulárních výrazů je čas spuštění zkrácen na úkor delšího času provádění. Z tohoto důvodu je nejvhodnější je používat tehdy, pokud je regulární výraz použit v nízkém počtu volání metod, nebo pokud přesný počet volání metod regulárních výrazů není znám, ale očekává se, že bude nízký. S rostoucím počtem volání metod je výkonový zisk plynoucí z kratší doby spouštění kompenzován nižší rychlostí provádění.

Vzory regulárních výrazů, které jsou vázány na modul regulárních výrazů pomocí specifikace možnosti <xref:System.Text.RegularExpressions.RegexOptions.Compiled> jsou kompilovány. To znamená, že když vytvoříte instanci objektu regulárního výrazu nebo když voláte statickou metodu regulárních výrazů a regulární výraz zároveň nelze nalézt v mezipaměti, modul regulárních výrazů převede regulární výraz na mezilehlou množinu operačních kódů, které jsou následně převedeny do jazyka MSIL. Jakmile metodu zavoláte, kompilátor JIT provede kód MSIL. Na rozdíl od interpretovaných regulárních výrazů mají zkompilované regulární výrazy delší dobu spouštění, jednotlivé metody porovnávání se však provádí rychleji. Ve výsledku se výkonový zisk plynoucí z kompilování regulárního výrazu zvyšuje s počtem regulárních výrazů, které metoda volá.

Shrnutí: V případě, že metody regulárních výrazů s konkrétním regulárním výrazem nebudou volány tak často, doporučujeme vám, abyste použili interpretované regulární výrazy. Pokud metody regulárních výrazů s konkrétním regulárním výrazem voláte relativně často, měli byste použít zkompilované regulární výrazy. Je těžké stanovit přesný práh, kdy delší doba provádění interpretovaných regulárních výrazů převyšuje výkonový zisk plynoucí z kratší doby provádění, nebo práh, kdy kratší doba spouštění zkompilovaných regulárních výrazů převyšuje výkonový zisk plynoucí z kratší doby provádění. Tato možnost závisí na různých faktorech, mezi které patří složitost regulárního výrazu a konkrétní data, která jsou zpracovávána. Chcete-li určit, zda jsou interpretované nebo kompilované regulární výrazy nabízeny co nejlepšího výkonu pro konkrétní scénář aplikace, můžete použít třídu <xref:System.Diagnostics.Stopwatch> pro porovnání časů spuštění.

Následující příklad porovnává výkon kompilovaných a interpretovaných regulárních výrazů při čtení prvních deseti vět a při čtení všech vět v textu Theodora Theodora 's *Dreisera*. Jak znázorňuje výstup uvedený v příkladu, interpretovaný regulární výraz nabízí lepší výkon než zkompilovaný regulární výraz pouze tehdy, pokud je provedeno pouze deset volání metody porovnávání regulárních výrazů. Zkompilovaný regulární výraz však nabízí lepší výkon, pokud je proveden větší počet volání (v tomto případě 13 000).

[!code-csharp[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compare1.cs#5)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compare1.vb#5)]

Vzor regulárního výrazu použitý v příkladu, `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, je definován tak, jak je uvedeno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`\b`|Začne porovnání na hranici slova.|
|`\w+`|Porovná jeden nebo více znaků slova.|
|<code>(\r?\n)&#124;,?\s)</code>|Porovná buď žádný, nebo jeden návratový znak následovaný znakem nového řádku, nebo žádnou či jednou čárkou následovanou prázdným znakem.|
|<code>(\w+((\r?\n)&#124;,?\s))*</code>|Porovná žádný nebo více výskytů jednoho nebo více znaků slova následovaných žádným nebo jedním návratovým znakem a znakem nového řádku, nebo žádnou či jednou čárkou následovanou prázdným znakem.|
|`\w+`|Porovná jeden nebo více znaků slova.|
|`[.?:;!]`|Porovná tečku, otazník, dvojtečku, středník nebo vykřičník.|

### <a name="regular-expressions-compiled-to-an-assembly"></a>Regulární výrazy: Zkompilováno do sestavení

Rozhraní .NET také umožňuje vytvořit sestavení, které obsahuje zkompilované regulární výrazy. Tím dojde k přesunu výkonnosti regulárního výrazu z doby spuštění do doby návrhu. Zahrnuje to ale i další práci: Regulární výrazy musíte definovat předem a kompilovat do sestavení. Kompilátor může poté odkazovat na toto sestavení při kompilaci zdrojového kódu, který používá regulární výrazy sestavení. Každý zkompilovaný regulární výraz v sestavení je reprezentován třídou, která je odvozena z <xref:System.Text.RegularExpressions.Regex>.

Chcete-li kompilovat regulární výrazy do sestavení, zavolejte metodu <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%28System.Text.RegularExpressions.RegexCompilationInfo%5B%5D%2CSystem.Reflection.AssemblyName%29?displayProperty=nameWithType> a předejte jí pole <xref:System.Text.RegularExpressions.RegexCompilationInfo> objektů, které reprezentují regulární výrazy, které mají být zkompilovány, a objekt <xref:System.Reflection.AssemblyName>, který obsahuje informace o sestavení, které má být vytvořeno.

Kompilaci regulárních výrazů do sestavení doporučujeme provádět v následujících situacích:

- Pokud pracujete jako vývojář komponent a chcete vytvořit knihovnu znovupoužitelných regulárních výrazů.

- Pokud očekáváte, že metody porovnávání se vzorem regulárních výrazů budou mít neurčitý počet volání – v rozsahu od jednoho nebo dvou do tisíců nebo desítek tisíců volání. Na rozdíl od zkompilovaných nebo interpretovaných regulárních výrazů nabízejí regulární výrazy, které jsou zkompilovány do samostatných sestavení, výkon, který je konzistentní bez ohledu na počet volání metod.

Pokud jsou pro optimalizaci výkonu použity kompilované regulární výrazy, neměla by pro vytvoření sestavení, načtení modulu regulárních výrazů a provedení metod porovnávání se vzorem být použita reflexe. Tato akce vyžaduje vynechání dynamického sestavování vzorů regulárních výrazů a zadání možnosti nastavení porovnávání se vzorem (jako je například porovnávání s rozlišováním velkých a malých čísel) během vytváření sestavení. Vyžaduje také oddělení kódu, který vytváří sestavení, od kódu, který používá regulární výraz.

Následující příklad znázorňuje způsob vytvoření sestavení, které obsahuje zkompilovaný regulární výraz. Vytvoří sestavení s názvem `RegexLib.dll` s jednou třídou regulárního výrazu, `SentencePattern`, která obsahuje vzor regulárního výrazu odpovídající větě použitým v [interpretované vs. Oddíl kompilovaných regulárních výrazů](#interpreted-vs-compiled-regular-expressions).

[!code-csharp[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile1.cs#6)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile1.vb#6)]

Když je příklad zkompilován pro spustitelný soubor a spuštění, vytvoří sestavení s názvem `RegexLib.dll`. Regulární výraz je reprezentován třídou s názvem `Utilities.RegularExpressions.SentencePattern`, která je odvozena z <xref:System.Text.RegularExpressions.Regex>. Následující příklad poté pomocí kompilovaného regulárního výrazu extrahuje věty z textu Theodora Theodora 's *Dreisera*.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile2.cs#7)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile2.vb#7)]

## <a name="take-charge-of-backtracking"></a>Odúčtujte si zpětné navrácení

Pro posouvání ve vstupním řetězci a porovnání řetězce se vzorem regulárního výrazu používá regulární výraz většinou lineární posloupnost. Pokud se ale ve vzoru regulárního výrazu používají neurčité kvantifikátory, jako jsou `*`, `+`a `?`, může modul regulárních výrazů zadávat část úspěšných částečných shod a vrátit se do dříve uloženého stavu, aby bylo možné je vyhledat. pro úspěšnou shodu pro celý vzor. Tento proces se označuje jako zpětné navracení.

> [!NOTE]
> Další informace o zpětném navrácení najdete v [podrobnostech o chování regulárních výrazů](../../../docs/standard/base-types/details-of-regular-expression-behavior.md) a [zpětném navrácení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md). Podrobné informace o zpětném navrácení najdete v tématu [optimalizace výkonu regulárních výrazů, část II: Přebírání zpětného navrácení](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) na blogu týmu BCL.

Podpora zpětného navracení zajišťuje regulárním výrazům výkon a flexibilitu. Zároveň přenáší odpovědnost za řízení provozu modulu regulárních výrazů do rukou vývojáře regulárních výrazů. Vzhledem k tomu, že vývojáři si často tuto odpovědnost neuvědomují, jejich špatný způsob používání mechanismu navracení nebo přílišné používání tohoto mechanismu hraje nejdůležitější roli při snížení výkonu regulárních výrazů. V nejhorším případě se doba provádění může s každým dalším znakem ve vstupním řetězci zdvojnásobit. Přílišným používáním mechanismu navracení je vlastně velmi snadné vytvořit programový ekvivalent nekonečné smyčky, pokud se vstup téměř shoduje se vzorem regulárního výrazů; modulu regulárních výrazů může trvat hodiny, nebo dokonce dny, než zpracuje relativně krátký vstupní řetězec.

Aplikace často platí daň za snížený výkon při používání zpětného navracení navzdory skutečnosti, že mechanismus zpětného navracení není pro shodu klíčový. Například regulární výraz `\b\p{Lu}\w*\b` odpovídá všem slovům, která začínají velkým znakem, jak je uvedeno v následující tabulce.

|Vzor|Popis|
|-|-|
|`\b`|Začne porovnání na hranici slova.|
|`\p{Lu}`|Porovná znak velkého písmena.|
|`\w*`|Porovná žádný nebo více znaků slova.|
|`\b`|Ukončí porovnání na hranici slova.|

Vzhledem k tomu, že hranice slova se neshoduje s hranicí znaku slova ani není jeho podmnožinou, nemá modul regulárních výrazů žádnou možnost při porovnávání znaků překročit hranici slova. To znamená, že pro tento regulární výraz nemůže mechanismus zpětného navracení nikdy přispět k celkovému úspěšnému vyhledání jakékoli shody – může pouze snížit výkon, protože modul regulárních výrazů je nucen uložit stav pro každou předběžně úspěšnou shodu znaku slova.

Pokud určíte, že zpětné navrácení není nutné, můžete ho zakázat pomocí elementu `(?>subexpression)` jazyka. Následující příklad analyzuje vstupní řetězec pomocí dvou regulárních výrazů. První, `\b\p{Lu}\w*\b`, spoléhá na zpětné navrácení. Druhý `\b\p{Lu}(?>\w*)\b`zakáže navrácení. Jak znázorňuje výstup z příkladu, vytvoří oba výrazy stejný výsledek.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack2.cs#10)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack2.vb#10)]

V mnoha případech je zpětné navracení pro porovnávání vzorů regulárních výrazů se vstupním textem nezbytné. Přílišné používání mechanismu navracení však může zásadním způsobem snížit výkon a vytvořit dojem, že aplikace přestala odpovídat. K této situaci dochází především tehdy, pokud jsou kvalifikátory vnořené a text, který se shoduje s vnějším dílčím výrazem, je podmnožinou textu, který se shoduje s vnějším dílčím výrazem.

> [!WARNING]
> Kromě toho, že byste mechanismus navracení neměli často používat, byste také měli použít funkci časového limitu, aby přílišné používání zpětného navracení nezpůsobovalo zásadní snížení výkonu regulárních výrazů. Další informace najdete v části [použití hodnot časového limitu](#use-time-out-values) .

Například vzor regulárního výrazu `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` má odpovídat číslu součásti, která se skládá alespoň z jednoho alfanumerického znaku. Mezi dalšími znaky může být alfanumerický znak, spojovník, podtržítko nebo tečka, poslední znak však musí být alfanumerický. Znak dolaru ukončuje číslo součásti. V některých případech může tento vzor regulárního výrazu vykazovat extrémně špatný výkon, protože kvantifikátory jsou vnořené a vzhledem k tomu, že dílčí výraz `[0-9A-Z]` je podmnožinou dílčího výrazu `[-.\w]*`.

V těchto případech lze výkon regulárních výrazů optimalizovat odebráním vnořených kvantifikátorů a nahrazením vnějšího dílčího výrazu kontrolním výrazem dopředného nebo zpětného vyhledávání s nulovou šířkou. Kontrolní výrazy dopředného a zpětného vyhledávání fungují jako kotvy: neposouvají ukazatele ve vstupním řetězci, ale prohledávají směrem dopředu nebo dozadu a ověřují, zda byla splněna konkrétní podmínka. Například číslo součásti regulární výraz může být přepsáno jako `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`. Tento vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.

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

Jazyk regulárních výrazů v rozhraní .NET obsahuje následující prvky jazyka, které lze použít k odstranění vnořených kvantifikátorů. Další informace naleznete v tématu [seskupovací konstrukce](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

|Prvek jazyka|Popis|
|----------------------|-----------------|
|`(?=` `subexpression` `)`|Pozitivní dopředné vyhledávání s nulovou šířkou. Prohlédněte si aktuální pozici, abyste zjistili, jestli `subexpression` odpovídat vstupnímu řetězci.|
|`(?!` `subexpression` `)`|Negativní dopředné vyhledávání s nulovou šířkou. Prohlédněte si aktuální pozici, abyste zjistili, zda `subexpression` neodpovídá vstupnímu řetězci.|
|`(?<=` `subexpression` `)`|Pozitivní zpětné vyhledávání s nulovou šířkou. Podívá se za aktuální pozici, abyste zjistili, jestli `subexpression` odpovídat vstupnímu řetězci.|
|`(?<!` `subexpression` `)`|Negativní zpětné vyhledávání s nulovou šířkou. Podívá se za aktuální pozici, aby bylo možné určit, zda `subexpression` neodpovídá vstupnímu řetězci.|

## <a name="use-time-out-values"></a>Použití hodnot časového limitu

Pokud regulární výraz zpracovává vstup, který téměř odpovídá vzoru regulárního výrazu, může se často spoléhat na přílišné používání zpětného navracení, což má velký dopad na výkon. Kromě pečlivého zvážení používání mechanismu zpětného navracení a ověřování regulárního výrazu s téměř shodným vstupem byste měli nastavit hodnotu časového limitu, který minimalizuje vliv přílišného používání mechanismu zpětného navracení, pokud k němu dojde.

Interval časového limitu regulárního výrazu definuje časové období, během kterého bude modul regulárních výrazů vyhledávat jediný výskyt shody před vypršením časového limitu. Výchozí interval časového limitu je <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType>, což znamená, že regulární výraz nebude vyprší časový limit. Tuto hodnotu lze přepsat a definovat vlastní časový limit následujícím způsobem:

- Poskytnutím hodnoty časového limitu při vytváření instance <xref:System.Text.RegularExpressions.Regex>ho objektu voláním konstruktoru <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>.

- Voláním statické metody porovnávání vzorů, jako je například <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>, která obsahuje parametr `matchTimeout`.

- U kompilovaných regulárních výrazů, které jsou vytvořeny voláním metody <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType>, voláním konstruktoru, který má parametr typu <xref:System.TimeSpan>.

Pokud jste definovali časový limit a shoda nebyla na konci tohoto intervalu nalezena, vyvolá metoda regulárního výrazu výjimku <xref:System.Text.RegularExpressions.RegexMatchTimeoutException>. V obslužné rutině výjimek můžete zadat nové vyhledávání shody s delším intervalem časového limitu, zrušit pokus o vyhledání shody a předpokládat, že shoda neexistuje, nebo zrušit pokus o vyhledání shody a vytvořit protokol s informacemi o výjimce pro další analýzu.

Následující příklad definuje metodu `GetWordData`, která vytvoří instanci regulárního výrazu s intervalem časového limitu 350 milisekund pro výpočet počtu slov a průměrného počtu znaků ve slově v textovém dokumentu. Pokud operace porovnání vyprší, časový limit se zvýší o 350 milisekund a znovu se vytvoří instance <xref:System.Text.RegularExpressions.Regex>ho objektu. Pokud nový interval časového limitu překročí 1 sekundu, metoda opětovně vyvolá výjimku pro volajícího.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/timeout1.cs#12)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/timeout1.vb#12)]

## <a name="capture-only-when-necessary"></a>Zachytit pouze v případě potřeby

Regulární výrazy v rozhraní .NET podporují řadu seskupovacích konstrukcí, které umožňují seskupit vzor regulárních výrazů do jednoho nebo více dílčích výrazů. Nejčastěji používané konstrukce seskupení v jazyce regulárních výrazů .NET jsou `(`dílčí *výraz*`)`, který definuje očíslovanou zachytávající skupinu a `(?<`*název*`>`dílčí *výraz*`)`, který definuje pojmenovanou zachytávající skupinu. Seskupovací konstrukce jsou nezbytné pro vytváření a definování dílčího výrazu, pro který je použit kvantifikátor.

Používání těchto prvků jazyka však má svou cenu. Způsobí, že objekt <xref:System.Text.RegularExpressions.GroupCollection> vrácený vlastností <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>, který se má naplnit nejnovějšími nepojmenovanými nebo pojmenovanými zachyceními, a pokud jedna seskupovací konstrukce zachytila více podřetězců ve vstupním řetězci, naplní také objekt <xref:System.Text.RegularExpressions.CaptureCollection>. vráceno vlastností <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> konkrétní zachytávající skupiny s více objekty <xref:System.Text.RegularExpressions.Capture>.

Seskupovací konstrukce se v regulárních výrazech používají pouze proto, aby na ně mohly být aplikovány kvantifikátory a aby skupiny zachycené těmito dílčími výrazy nebyly poté používány. Například regulární výraz `\b(\w+[;,]?\s?)+[.?!]` je navržený tak, aby zachytával celou větu. Následující tabulka popisuje prvky jazyka v tomto vzoru regulárního výrazu a jejich vliv na kolekce <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> objektu <xref:System.Text.RegularExpressions.Match>.

|Vzor|Popis|
|-------------|-----------------|
|`\b`|Začne porovnání na hranici slova.|
|`\w+`|Porovná jeden nebo více znaků slova.|
|`[;,]?`|Porovná žádnou nebo jednu čárku či středník.|
|`\s?`|Porovná žádný nebo jeden prázdný znak.|
|`(\w+[;,]?\s?)+`|Porovná jeden nebo několik výskytů znaků slova následovaných nepovinnou čárkou nebo středníkem, za kterými následuje nepovinný prázdný znak. Tím je definována první zachytávající skupina, která je nezbytná k tomu, aby kombinace více znaků slova (neboli slovo) následovaná nepovinným interpunkčním symbolem opakovala, dokud modul regulárních výrazů nedosáhne konce věty.|
|`[.?!]`|Porovná tečku, otazník nebo vykřičník.|

Jak ukazuje následující příklad, pokud je nalezena shoda, jsou objekty <xref:System.Text.RegularExpressions.GroupCollection> i <xref:System.Text.RegularExpressions.CaptureCollection> naplněny zachycením ze shody. V tomto případě `(\w+[;,]?\s?)`, aby zachytávající skupina existovala, aby se na ni mohl použít kvantifikátor `+`, který umožňuje vzor regulárního výrazu porovnat jednotlivá slova ve větě. V opačném případě může odpovídat poslednímu slovu ve větě.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group1.cs#8)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group1.vb#8)]

Pokud použijete dílčí výrazy pouze proto, abyste mohli použít kvantifikátor a zachycený text pro vás není podstatný, měli byste skupinové zachytávání zakázat. Například prvek jazyka `(?:subexpression)` zabraňuje skupině, na kterou se vztahuje, ze zachytávání odpovídajících podřetězců. V následujícím příkladu je vzor regulárního výrazu z předchozího příkladu změněn na `\b(?:\w+[;,]?\s?)+[.?!]`. Jak ukazuje výstup, zabraňuje modulu regulárních výrazů v naplnění kolekce <xref:System.Text.RegularExpressions.GroupCollection> a <xref:System.Text.RegularExpressions.CaptureCollection>.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group2.cs#9)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group2.vb#9)]

Zachytávání lze zakázat jedním z následujících způsobů:

- Použijte prvek jazyka `(?:subexpression)`. Tento prvek zabraňuje v zachytávání shodných podřetězců ve skupině, pro kterou se používá. Nezakazuje zachytávání podřetězců v jakékoli vnořené skupině.

- Použijte možnost <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>. Zakazuje všechna nepojmenovaná nebo implicitní zachycení ve vzoru regulárního výrazu. Při použití této možnosti mohou být zachyceny pouze podřetězce, které odpovídají pojmenovaným skupinám definovaným pomocí elementu jazyka `(?<name>subexpression)`. Příznak <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> lze předat parametru `options` konstruktoru třídy <xref:System.Text.RegularExpressions.Regex> nebo parametru `options` <xref:System.Text.RegularExpressions.Regex> statické metody pro porovnání.

- Použijte možnost `n` v prvku `(?imnsx)` jazyka. Tato možnost zakazuje všechna nepojmenovaná nebo implicitní zachycení z bodu ve vzoru regulárního výrazu, ve kterém se prvek objeví. Zachycení jsou zakázána do konce vzoru nebo do doby, než možnost `(-n)` povolí Nepojmenovaná nebo implicitní zachycení. Další informace naleznete v tématu [různé konstrukce](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md).

- Použijte možnost `n` v prvku `(?imnsx:subexpression)` jazyka. Tato možnost zakazuje všechna nepojmenovaná nebo implicitní zachycení v `subexpression`. Zachycení nepojmenovanou nebo implicitní vnořenou zachytávající skupinou jsou rovněž zakázána.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Podrobnosti k chování regulárních výrazů](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|Prověřuje implementaci modulu regulárních výrazů v rozhraní .NET. Téma se zaměřuje na flexibilitu regulárních výrazů a objasňuje odpovědnost vývojáře za zajištění efektivity a výkonnosti modulu regulárních výrazů.|
|[Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Vysvětluje princip zpětného navracení a vliv tohoto mechanismu na výkon regulárních výrazů a zkoumá prvky jazyka, které nabízí alternativu zpětného navracení.|
|[Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Popisuje prvky jazyka regulárních výrazů v rozhraní .NET a obsahuje odkazy na podrobnou dokumentaci pro každý prvek jazyka.|
