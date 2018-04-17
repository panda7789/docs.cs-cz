---
title: Osvědčené postupy pro regulární výrazy v rozhraní .NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, best practices
- regular expressions, best practices
ms.assetid: 618e5afb-3a97-440d-831a-70e4c526a51c
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 59ec9ead0fd010baccaadb1eda0f469b7b4dcb46
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="best-practices-for-regular-expressions-in-net"></a>Osvědčené postupy pro regulární výrazy v rozhraní .NET
<a name="top"></a> Modul regulárních výrazů v .NET je výkonný, plně vybavený nástroj, který zpracuje text na základě vzor odpovídá nikoli na shodu literálu text a porovnání. Ve většině případů provádí porovnání vzorů rychle a efektivně. V některých případech se však může zdát, že je modul regulárních výrazů velmi pomalý. V extrémních případech se může dokonce zdát, že přestal při zpracování relativně malého vstupu odpovídat po dobu hodin nebo dokonce dní.  
  
 Toto téma nastiňuje některé osvědčené postupy, které si mohou vývojáři osvojit za účelem dosažení optimálního výkonu regulárních výrazů. Obsahuje následující oddíly:  
  
-   [Vezměte v úvahu vstupního zdroje](#InputSource)  
  
-   [Vytvoření instance objektu správně zpracovat](#ObjectInstantiation)  
  
-   [Převzetí zpětné navracení](#Backtracking)  
  
-   [Použijte hodnoty časového limitu](#Timeouts)  
  
-   [Zaznamenat pouze v případě potřeby](#Capture)  
  
-   [Související témata](#RelatedTopics)  
  
<a name="InputSource"></a>   
## <a name="consider-the-input-source"></a>Výběr vstupního zdroje  
 Regulární výrazy mohou většinou přijmout dva typy vstupů: vstupy s omezením a vstupy bez omezení. Vstup s omezením je text, který pochází ze známého nebo ověřeného zdroje a odpovídá předdefinovanému formátu. Vstup bez omezení je text, který pochází z neověřeného zdroje, jako je například uživatel webu, a nemusí odpovídat předdefinovanému nebo očekávanému formátu.  
  
 Vzory regulárních výrazů jsou obvykle napsány tak, aby odpovídaly platnému vstupu. Vývojáři totiž prozkoumají text, který chtějí porovnat, a následně napíšou vzor regulárního výrazu, který mu odpovídá. Vývojáři následně určí, zda tento vzor vyžaduje korekci nebo další zpracování testováním pomocí většího množství platných vstupních položek. Pokud vzor odpovídá všem předpokládaným platným vstupům, je možné jej uvést do produkce a může být vložen do vydané aplikace. To znamená, že vzor regulárního výrazu je vhodný pro porovnávání se vstupem s omezením. Neznamená to však, že je vhodný pro porovnávání se vstupem bez omezení.  
  
 Aby mohl regulární výraz odpovídat vstupu bez omezení, musí být schopen efektivně zpracovat tři druhy textu:  
  
-   Text, který odpovídá vzoru regulárního výrazu.  
  
-   Text, který neodpovídá vzoru regulárního výrazu.  
  
-   Text, který téměř odpovídá vzoru regulárního výrazu.  
  
 Poslední typ je zvláště problematický pro regulární výrazy, které jsou napsány tak, aby zpracovávaly vstup s omezením. Pokud tento regulární výraz také závisí na rozsáhlé [zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md), modul regulárních výrazů může trávit nadměrné množství času (v některých případech mnoha hodin nebo dnů) zpracování zdánlivě nepatrná text.  
  
> [!WARNING]
>  V následujícím příkladu je použit regulární výraz, který je náchylný na časté používání mechanismu zpětného navracení a který pravděpodobně zamítne platné e-mailové adresy. Neměl by být používán v rutině ověřování e-mailové adresy. Pokud chcete regulární výraz, který ověří e-mailových adres, přečtěte si téma [postup: Ověřte, zda jsou řetězce v platném formátu e-mailu](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
 Předpokládejme například velmi často používaný, ale extrémně problematický regulární výraz pro ověřování aliasu e-mailové adresy. Regulární výraz `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` je zapsán do zpracovat, co se považuje za platnou e-mailovou adresu, která se skládá z alfanumerický znak, za nímž následuje nula nebo více znaků, které mohou být alfanumerické znaky, tečky a pomlčky. Regulární výraz musí končit alfanumerickým znakem. Ačkoli tento regulární výraz snadno zpracovává platný vstup, je velmi neefektivní při zpracování téměř platného vstupu, jak vyplývá z následujícího příkladu.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/design2.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/design2.vb#1)]  
  
 Jak znázorňuje výstup v příkladu, zpracovává modul regulárních výrazů platný alias e-mailové adresy zhruba stejnou dobu bez ohledu na délku. Na druhou stranu platí, že pokud téměř platná e-mailová adresa obsahuje více než pět znaků, čas zpracování se po přidání každého dalšího znaku do řetězce přibližně zdvojnásobí. To znamená, že zpracování téměř platného osmadvacetiznakového řetězce může trvat více než hodinu a zpracování téměř platného třiatřicetiznakového řetězce bude trvat skoro celý den.  
  
 Vzhledem k tomu, že tento regulární řetězec byl vytvořen pouze za předpokladu, že formát vstupu se bude shodovat, nebere v potaz vstup, který neodpovídá vzoru. Tato skutečnost pak může vést k tomu, že vstup bez omezení, který téměř odpovídá vzoru regulárního výrazu, významně sníží výkon.  
  
 Chcete-li tento problém vyřešit, proveďte následující akce:  
  
-   Při vytváření vzoru je třeba zvážit, jakým způsobem mechanismus zpětného navracení může ovlivnit výkon modulu regulárních výrazů, především tehdy, pokud je regulární výraz navržen pro zpracování vstupu bez omezení. Další informace najdete v tématu [trvat poplatků z zpětné navracení](#Backtracking) části.  
  
-   Regulární výraz je nutné důkladně odzkoušet pomocí neplatných vstupů, téměř platných vstupů a také platných vstupů. Chcete-li vygenerovat náhodně vstup pro konkrétní regulární výraz, můžete použít [Rex](https://www.microsoft.com/en-us/research/project/rex-regular-expression-exploration/), což je nástroj zkoumání regulární výraz z Microsoft Research.  
  
 [Zpět na začátek](#top)  
  
<a name="ObjectInstantiation"></a>   
## <a name="handle-object-instantiation-appropriately"></a>Vhodné vytváření instancí objektu  
 Jádrem. Model objektu regulárního výrazu na NET je <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> třídy, která představuje modul regulárních výrazů. Často jeden největší faktor, který ovlivňuje výkon regulární výraz je způsob, ve kterém <xref:System.Text.RegularExpressions.Regex> modul se používá. Definování regulárního výrazu zahrnuje pevné párování modulu regulárních výrazů se vzorem regulárního výrazu. Aby spojovacích procesu, jestli se týká vytváření instancí <xref:System.Text.RegularExpressions.Regex> objektu předáním jeho konstruktoru vzor regulárního výrazu nebo volání statickou metodu předáním vzor regulárního výrazu společně s řetězec, který má být analyzován, je nezbytné nákladné jedné.  
  
> [!NOTE]
>  Podrobnější informace o výkonu důsledky použití interpretovaný a kompilované regulární výrazy, najdete v části [optimalizace výkonu regulární výraz, část II: pořízení poplatků z zpětné navracení](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) v blogu týmu BCL.  
  
 Modul regulárních výrazů lze spárovat s konkrétním vzorem regulárního výrazu a následně modul použít pro porovnání textu několika různými způsoby:  
  
-   Můžete například volat statickou metodu porovnávání <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>. Tato akce nevyžaduje vytvoření instance objektu regulárních výrazů.  
  
-   Můžete vytvořit instanci <xref:System.Text.RegularExpressions.Regex> objektu a volání metody porovnávání instance interpretovaný regulárního výrazu. Toto je výchozí metoda pro vytvoření vazby modulu regulárních výrazů se vzorem regulárního výrazu. Ho výsledky při <xref:System.Text.RegularExpressions.Regex> bez vytvoření instance objektu `options` argument, který obsahuje <xref:System.Text.RegularExpressions.RegexOptions.Compiled> příznak.  
  
-   Můžete vytvořit instanci <xref:System.Text.RegularExpressions.Regex> objektu a volání metody porovnávání instance kompilované regulárního výrazu. Regulární výraz objekty vzory představují kompilovat, kdy <xref:System.Text.RegularExpressions.Regex> vytvořit instanci objektu s `options` argument, který zahrnuje <xref:System.Text.RegularExpressions.RegexOptions.Compiled> příznak.  
  
-   Můžete vytvořit zvláštní účely <xref:System.Text.RegularExpressions.Regex> objekt, který je úzce spojeny s vzor regulárního výrazu konkrétní jej zkompilovat a uložte jej do samostatné sestavení. To provedete pomocí volání <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metoda.  
  
 Způsob, jakým budou metody porovnávání regulárních výrazů volány, může mít zásadní vliv na vaši aplikaci. V následujících částech jsou probírány způsoby volání statických metod, interpretovaných regulárních výrazů a zkompilovaných regulárních výrazů za účelem zvýšení výkonu aplikace.  
  
> [!IMPORTANT]
>  Způsob volání metod (statické, interpretované, zkompilované) ovlivňuje výkon, pokud pro volání metod použijete stejný regulární výraz, nebo pokud aplikace příliš často používá objekty regulárních výrazů.  
  
### <a name="static-regular-expressions"></a>Statické regulární výrazy  
 Statické metody regulárních výrazů jsou vhodnou alternativou k opakovanému vytváření instancí objektů regulárních výrazů se stejným regulárním výrazem. Na rozdíl od vzorů regulárních výrazů používaných objekty regulárních výrazů jsou kódy operací nebo zkompilovaný kód MSIL (Microsoft intermediate language) ze vzorů používaných pro volání metod instance interně ukládány do mezipaměti pomocí modulu regulárních výrazů.  
  
 Například pro ověření uživatelského vstupu volá obslužná rutina události často jinou metodu. To se projeví v následujícím kódu, ve kterém <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> událostí se používá k volání metody s názvem `IsValidCurrency`, která kontroluje, zda uživatel zadal symbolu měny, za nímž následuje alespoň jednu číslici desítkové soustavy.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#2)]  
  
 Velmi neefektivní provádění `IsValidCurrency` metoda je znázorněno v následujícím příkladu. Všimněte si, že každé volání metody reinstantiates <xref:System.Text.RegularExpressions.Regex> objekt se stejným vzorkem. To znamená, že vzor regulárního výrazu musí být při každém dalším volání metody znovu zkompilován.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#3)]  
  
 Tento neefektivní kód by měl nahraďte volání statických <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda. Tím se eliminuje potřeba k vytváření instancí <xref:System.Text.RegularExpressions.Regex> objekt pokaždé, když chcete volat metodu porovnávání a umožňuje modulu regulární výraz k načtení kompilované verze regulárního výrazu ze své mezipaměti.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static2.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static2.vb#4)]  
  
 Ve výchozím nastavení je v mezipaměti uloženo posledních 15 použitých vzorů regulárních výrazů. Pro aplikace, které vyžadují větší počet statických regulárních výrazů v mezipaměti, můžete upravit velikost mezipaměti nastavením <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> vlastnost.  
  
 Regulární výraz `\p{Sc}+\s*\d+` používané v tomto příkladu ověřuje, že vstupní řetězec obsahuje symbolu měny a alespoň jeden desítková číslice. Vzor je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\p{Sc}+`|Porovná jeden nebo více znaků z kategorie měn a symbolů Unicode.|  
|`\s*`|Porovná žádný nebo více prázdných znaků.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
  
<a name="Interpreted"></a>   
### <a name="interpreted-vs-compiled-regular-expressions"></a>Interpretovaný vs. Kompilované regulární výrazy  
 Regulární výraz vzorů, které nejsou vázány na modul regulárních výrazů prostřednictvím specifikaci <xref:System.Text.RegularExpressions.RegexOptions.Compiled> se interpretují možnost. Po vytvoření instance objektu regulárního výrazu převede modul regulárních výrazů regulární výraz na množinu kódů operací. Po zavolání metody instance jsou operační kódy převedeny do jazyka MSIL a provedeny kompilátorem JIT. Obdobně platí, že pokud zavoláte statickou metodu regulárních výrazů a regulární výraz nelze nalézt v mezipaměti, modul regulárních výrazů převede regulární výraz na množinu operačních kódů a uloží je do mezipaměti. Poté jsou tyto operační kódy převedeny do jazyka MSIL, aby je mohl kompilátor JIT provést. U interpretovaných regulárních výrazů je čas spuštění zkrácen na úkor delšího času provádění. Z tohoto důvodu je nejvhodnější je používat tehdy, pokud je regulární výraz použit v nízkém počtu volání metod, nebo pokud přesný počet volání metod regulárních výrazů není znám, ale očekává se, že bude nízký. S rostoucím počtem volání metod je výkonový zisk plynoucí z kratší doby spouštění kompenzován nižší rychlostí provádění.  
  
 Vzory regulárních výrazů, které jsou vázány na modul regulárních výrazů prostřednictvím specifikaci <xref:System.Text.RegularExpressions.RegexOptions.Compiled> kompilované možnost. To znamená, že když vytvoříte instanci objektu regulárního výrazu nebo když voláte statickou metodu regulárních výrazů a regulární výraz zároveň nelze nalézt v mezipaměti, modul regulárních výrazů převede regulární výraz na mezilehlou množinu operačních kódů, které jsou následně převedeny do jazyka MSIL. Jakmile metodu zavoláte, kompilátor JIT provede kód MSIL. Na rozdíl od interpretovaných regulárních výrazů mají zkompilované regulární výrazy delší dobu spouštění, jednotlivé metody porovnávání se však provádí rychleji. Ve výsledku se výkonový zisk plynoucí z kompilování regulárního výrazu zvyšuje s počtem regulárních výrazů, které metoda volá.  
  
 Shrnutí: V případě, že metody regulárních výrazů s konkrétním regulárním výrazem nebudou volány tak často, doporučujeme vám, abyste použili interpretované regulární výrazy. Pokud metody regulárních výrazů s konkrétním regulárním výrazem voláte relativně často, měli byste použít zkompilované regulární výrazy. Je těžké stanovit přesný práh, kdy delší doba provádění interpretovaných regulárních výrazů převyšuje výkonový zisk plynoucí z kratší doby provádění, nebo práh, kdy kratší doba spouštění zkompilovaných regulárních výrazů převyšuje výkonový zisk plynoucí z kratší doby provádění. Tato možnost závisí na různých faktorech, mezi které patří složitost regulárního výrazu a konkrétní data, která jsou zpracovávána. K určení, zda interpretovat nebo kompilované regulární výrazy nabízejí nejlepší výkon pro váš scénář konkrétní aplikaci, můžete použít <xref:System.Diagnostics.Stopwatch> třída k porovnání časy jejich provádění.  
  
 Následující příklad porovnání výkonu kompilované a interpretovaný regulární výrazy při čtení prvních deset věty a při čtení všechny věty v textu Theodore Dreiser *Financier*. Jak znázorňuje výstup uvedený v příkladu, interpretovaný regulární výraz nabízí lepší výkon než zkompilovaný regulární výraz pouze tehdy, pokud je provedeno pouze deset volání metody porovnávání regulárních výrazů. Zkompilovaný regulární výraz však nabízí lepší výkon, pokud je proveden větší počet volání (v tomto případě 13 000).  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compare1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compare1.vb#5)]  
  
 Vzor regulárního výrazu používaný v příkladu `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|<code>(\r?\n)&#124;,?\s)</code>|Porovná buď žádný, nebo jeden návratový znak následovaný znakem nového řádku, nebo žádnou či jednou čárkou následovanou prázdným znakem.|  
|<code>(\w+((\r?\n)&#124;,?\s))*</code>|Porovná žádný nebo více výskytů jednoho nebo více znaků slova následovaných žádným nebo jedním návratovým znakem a znakem nového řádku, nebo žádnou či jednou čárkou následovanou prázdným znakem.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`[.?:;!]`|Porovná tečku, otazník, dvojtečku, středník nebo vykřičník.|  
  
### <a name="regular-expressions-compiled-to-an-assembly"></a>Regulární výrazy: kompilace do sestavení  
 Rozhraní .NET můžete také vytvořit sestavení, které kompilované regulární výrazy obsahuje. Tím dojde k přesunu výkonnosti regulárního výrazu z doby spuštění do doby návrhu. Tato akce však zahrnuje další úkony: musíte předem definovat regulární výrazy a zkompilovat je do sestavení. Kompilátor může poté odkazovat na toto sestavení při kompilaci zdrojového kódu, který používá regulární výrazy sestavení. Každý kompilované regulárnímu výrazu v sestavení je reprezentována třídu odvozenou z <xref:System.Text.RegularExpressions.Regex>.  
  
 Kompilace regulární výrazy k sestavení, zavoláte <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%28System.Text.RegularExpressions.RegexCompilationInfo%5B%5D%2CSystem.Reflection.AssemblyName%29?displayProperty=nameWithType> metoda a předejte ji pole <xref:System.Text.RegularExpressions.RegexCompilationInfo> objekty, které představují regulární výrazy sestavují, a <xref:System.Reflection.AssemblyName> objekt, který obsahuje informace o sestavení, které má být vytvořit.  
  
 Kompilaci regulárních výrazů do sestavení doporučujeme provádět v následujících situacích:  
  
-   Pokud pracujete jako vývojář komponent a chcete vytvořit knihovnu znovupoužitelných regulárních výrazů.  
  
-   Pokud očekáváte, že metody porovnávání se vzorem regulárních výrazů budou mít neurčitý počet volání – v rozsahu od jednoho nebo dvou do tisíců nebo desítek tisíců volání. Na rozdíl od zkompilovaných nebo interpretovaných regulárních výrazů nabízejí regulární výrazy, které jsou zkompilovány do samostatných sestavení, výkon, který je konzistentní bez ohledu na počet volání metod.  
  
 Pokud jsou pro optimalizaci výkonu použity kompilované regulární výrazy, neměla by pro vytvoření sestavení, načtení modulu regulárních výrazů a provedení metod porovnávání se vzorem být použita reflexe. Tato akce vyžaduje vynechání dynamického sestavování vzorů regulárních výrazů a zadání možnosti nastavení porovnávání se vzorem (jako je například porovnávání s rozlišováním velkých a malých čísel) během vytváření sestavení. Vyžaduje také oddělení kódu, který vytváří sestavení, od kódu, který používá regulární výraz.  
  
 Následující příklad znázorňuje způsob vytvoření sestavení, které obsahuje zkompilovaný regulární výraz. Vytvoří sestavení s názvem `RegexLib.dll` s třídou jeden regulární výraz, `SentencePattern`, který obsahuje větu odpovídající regulárnímu výrazu způsobem používaným v [interpretovat vs. Kompilované regulární výrazy](#Interpreted) části.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile1.vb#6)]  
  
 Když v příkladu kompiluje na spustitelný soubor a spustit, vytvoří se sestavení s názvem `RegexLib.dll`. Regulární výraz je reprezentována třídy s názvem `Utilities.RegularExpressions.SentencePattern` je odvozena z <xref:System.Text.RegularExpressions.Regex>. Následující příklad použije kompilované regulární výraz k extrakci věty z textu Theodore Dreiser *Financier*.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile2.cs#7)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile2.vb#7)]  
  
 [Zpět na začátek](#top)  
  
<a name="Backtracking"></a>   
## <a name="take-charge-of-backtracking"></a>Dohled nad zpětným navracením  
 Pro posouvání ve vstupním řetězci a porovnání řetězce se vzorem regulárního výrazu používá regulární výraz většinou lineární posloupnost. Ale když neurčitém kvantifikátory jako `*`, `+`, a `?` se používají v vzor regulárního výrazu může modul regulárních výrazů uvolňovat část úspěšné shodují jen částečně a vrátit do předchozího uloženého stavu Chcete-li vyhledat úspěšné shoda pro celý vzor. Tento proces se označuje jako zpětné navracení.  
  
> [!NOTE]
>  Další informace o zpětné navracení najdete v tématu [podrobnosti o regulární výraz chování](../../../docs/standard/base-types/details-of-regular-expression-behavior.md) a [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md). Podrobnou diskuzi o zpětné navracení, najdete v části [optimalizace výkonu regulární výraz, část II: pořízení poplatků z zpětné navracení](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) v blogu týmu BCL.  
  
 Podpora zpětného navracení zajišťuje regulárním výrazům výkon a flexibilitu. Zároveň přenáší odpovědnost za řízení provozu modulu regulárních výrazů do rukou vývojáře regulárních výrazů. Vzhledem k tomu, že vývojáři si často tuto odpovědnost neuvědomují, jejich špatný způsob používání mechanismu navracení nebo přílišné používání tohoto mechanismu hraje nejdůležitější roli při snížení výkonu regulárních výrazů. V nejhorším případě se doba provádění může s každým dalším znakem ve vstupním řetězci zdvojnásobit. Přílišným používáním mechanismu navracení je vlastně velmi snadné vytvořit programový ekvivalent nekonečné smyčky, pokud se vstup téměř shoduje se vzorem regulárního výrazů; modulu regulárních výrazů může trvat hodiny, nebo dokonce dny, než zpracuje relativně krátký vstupní řetězec.  
  
 Aplikace často platí daň za snížený výkon při používání zpětného navracení navzdory skutečnosti, že mechanismus zpětného navracení není pro shodu klíčový. Například regulární výraz `\b\p{Lu}\w*\b` odpovídá všechna slova, která začínají velké písmeno, jak ukazuje následující tabulka.  
  
|Vzor|Popis|  
|-|-|  
|`\b`|Začne porovnání na hranici slova.|  
|`\p{Lu}`|Porovná znak velkého písmena.|  
|`\w*`|Porovná žádný nebo více znaků slova.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzhledem k tomu, že hranice slova se neshoduje s hranicí znaku slova ani není jeho podmnožinou, nemá modul regulárních výrazů žádnou možnost při porovnávání znaků překročit hranici slova. To znamená, že pro tento regulární výraz nemůže mechanismus zpětného navracení nikdy přispět k celkovému úspěšnému vyhledání jakékoli shody – může pouze snížit výkon, protože modul regulárních výrazů je nucen uložit stav pro každou předběžně úspěšnou shodu znaku slova.  
  
 Pokud zjistíte, že zpětné navracení není nutné, můžete ji zakázat pomocí `(?>``subexpression``)` element jazyka. Následující příklad analyzuje vstupní řetězec pomocí dvou regulárních výrazů. První, `\b\p{Lu}\w*\b`, spoléhá na zpětné navracení. Druhá s názvem `\b\p{Lu}(?>\w*)\b`, zakáže zpětné navracení. Jak znázorňuje výstup z příkladu, vytvoří oba výrazy stejný výsledek.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack2.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack2.vb#10)]  
  
 V mnoha případech je zpětné navracení pro porovnávání vzorů regulárních výrazů se vstupním textem nezbytné. Přílišné používání mechanismu navracení však může zásadním způsobem snížit výkon a vytvořit dojem, že aplikace přestala odpovídat. K této situaci dochází především tehdy, pokud jsou kvalifikátory vnořené a text, který se shoduje s vnějším dílčím výrazem, je podmnožinou textu, který se shoduje s vnějším dílčím výrazem.  
  
> [!WARNING]
>  Kromě toho, že byste mechanismus navracení neměli často používat, byste také měli použít funkci časového limitu, aby přílišné používání zpětného navracení nezpůsobovalo zásadní snížení výkonu regulárních výrazů. Další informace najdete v tématu [hodnoty časového limitu použití](#Timeouts) části.  
  
 Například vzor regulárního výrazu `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` se má shodovat s počtem část, která se skládá z nejméně jeden alfanumerický znak. Mezi dalšími znaky může být alfanumerický znak, spojovník, podtržítko nebo tečka, poslední znak však musí být alfanumerický. Znak dolaru ukončuje číslo součásti. V některých případech se tento vzor regulárního výrazu vykazovat velmi nízký výkon, protože jsou vnořeny Kvantifikátory a protože dílčí výraz `[0-9A-Z]` je podmnožinou dílčí výraz `[-.\w]*`.  
  
 V těchto případech lze výkon regulárních výrazů optimalizovat odebráním vnořených kvantifikátorů a nahrazením vnějšího dílčího výrazu kontrolním výrazem dopředného nebo zpětného vyhledávání s nulovou šířkou. Kontrolní výrazy dopředného a zpětného vyhledávání fungují jako kotvy: neposouvají ukazatele ve vstupním řetězci, ale prohledávají směrem dopředu nebo dozadu a ověřují, zda byla splněna konkrétní podmínka. Například část číslo regulární výraz může být přepsán jako `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`. Tento vzor regulárního výrazu je definován tak, jak je uvedeno v následující tabulce.  
  
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
  
 Jazyk regulárních výrazů v .NET obsahuje následující prvky jazyka, které můžete použít k vyloučení vnořené kvantifikátory. Další informace najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
|Prvek jazyka|Popis|  
|----------------------|-----------------|  
|`(?=` `subexpression` `)`|Pozitivní dopředné vyhledávání s nulovou šířkou. Podívejte se před aktuální pozici k určení zda `subexpression` odpovídá vstupní řetězec.|  
|`(?!` `subexpression` `)`|Negativní dopředné vyhledávání s nulovou šířkou. Podívejte se před aktuální pozici k určení zda `subexpression` neodpovídá vstupní řetězec.|  
|`(?<=` `subexpression` `)`|Pozitivní zpětné vyhledávání s nulovou šířkou. Podívejte se za aktuální pozici k určení zda `subexpression` odpovídá vstupní řetězec.|  
|`(?<!` `subexpression` `)`|Negativní zpětné vyhledávání s nulovou šířkou. Podívejte se za aktuální pozici k určení zda `subexpression` neodpovídá vstupní řetězec.|  
  
 [Zpět na začátek](#top)  
  
<a name="Timeouts"></a>   
## <a name="use-time-out-values"></a>Používání hodnot časového limitu  
 Pokud regulární výraz zpracovává vstup, který téměř odpovídá vzoru regulárního výrazu, může se často spoléhat na přílišné používání zpětného navracení, což má velký dopad na výkon. Kromě pečlivého zvážení používání mechanismu zpětného navracení a ověřování regulárního výrazu s téměř shodným vstupem byste měli nastavit hodnotu časového limitu, který minimalizuje vliv přílišného používání mechanismu zpětného navracení, pokud k němu dojde.  
  
 Interval časového limitu regulárního výrazu definuje časové období, během kterého bude modul regulárních výrazů vyhledávat jediný výskyt shody před vypršením časového limitu. Je výchozí interval časového limitu <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType>, což znamená, že se regulární výraz není vypršení časového limitu. Tuto hodnotu lze přepsat a definovat vlastní časový limit následujícím způsobem:  
  
-   Zadáním hodnoty časového limitu při instanci můžete vytvořit <xref:System.Text.RegularExpressions.Regex> objekt voláním <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> konstruktor.  
  
-   Voláním statické vzor odpovídající metoda, jako například <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>, který obsahuje `matchTimeout` parametr.  
  
-   Pro kompilované regulární výrazy, které jsou vytvořené pomocí volání <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metoda voláním konstruktor, který má parametr typu <xref:System.TimeSpan>.  
  
 Pokud jste definovali interval časového limitu a na konci tohoto intervalu není nalezena shoda, vyvolá metoda regulární výraz <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> výjimka. V obslužné rutině výjimek můžete zadat nové vyhledávání shody s delším intervalem časového limitu, zrušit pokus o vyhledání shody a předpokládat, že shoda neexistuje, nebo zrušit pokus o vyhledání shody a vytvořit protokol s informacemi o výjimce pro další analýzu.  
  
 V následujícím příkladu definuje `GetWordData` metoda, která vytvoří instanci regulární výraz pomocí interval časového limitu 350 časový interval v milisekundách vypočítat počet slov a průměrný počet znaků v textovém v textový dokument. Pokud odpovídající operaci vyprší časový limit, časový limit je zvýšen 350 milisekundách a <xref:System.Text.RegularExpressions.Regex> se znovu vytvořenou instanci objektu. Pokud nový interval časového limitu překročí 1 sekundu, metoda opětovně vyvolá výjimku pro volajícího.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/timeout1.cs#12)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/timeout1.vb#12)]  
  
 [Zpět na začátek](#top)  
  
<a name="Capture"></a>   
## <a name="capture-only-when-necessary"></a>Zachycení pouze v případě potřeby  
 Regulární výrazy v rozhraní .NET podporovat počet seskupovací konstrukce, které umožňují skupiny vzor regulárního výrazu na jeden nebo více podvýrazy. Jsou nejčastěji používané seskupovací konstrukce v jazyk regulárních výrazů .NET `(` *dílčím výrazu*`)`, která definuje skupinu číslovaných zachycení a `(?<` *název* `>` *dílčím výrazu*`)`, která definuje pojmenovanou skupinu zaznamenávání. Seskupovací konstrukce jsou nezbytné pro vytváření a definování dílčího výrazu, pro který je použit kvantifikátor.  
  
 Používání těchto prvků jazyka však má svou cenu. Způsobí <xref:System.Text.RegularExpressions.GroupCollection> objekt vrácený <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost být vyplněny nejnovější nepojmenovaný nebo s názvem zachycení a v případě více dílčích řetězců ve vstupním řetězci má zaznamenat jeden seskupovací konstrukce, také naplnit <xref:System.Text.RegularExpressions.CaptureCollection>objekt vrácený <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastnost určité zaznamenávání skupiny s více <xref:System.Text.RegularExpressions.Capture> objekty.  
  
 Seskupovací konstrukce se v regulárních výrazech používají pouze proto, aby na ně mohly být aplikovány kvantifikátory a aby skupiny zachycené těmito dílčími výrazy nebyly poté používány. Například regulární výraz `\b(\w+[;,]?\s?)+[.?!]` slouží k zaznamenání celé věty. Následující tabulka popisuje prvky jazyka v tomto vzoru regulárního výrazu a jejich vliv na <xref:System.Text.RegularExpressions.Match> objektu <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> kolekce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`[;,]?`|Porovná žádnou nebo jednu čárku či středník.|  
|`\s?`|Porovná žádný nebo jeden prázdný znak.|  
|`(\w+[;,]?\s?)+`|Porovná jeden nebo několik výskytů znaků slova následovaných nepovinnou čárkou nebo středníkem, za kterými následuje nepovinný prázdný znak. Tím je definována první zachytávající skupina, která je nezbytná k tomu, aby kombinace více znaků slova (neboli slovo) následovaná nepovinným interpunkčním symbolem opakovala, dokud modul regulárních výrazů nedosáhne konce věty.|  
|`[.?!]`|Porovná tečku, otazník nebo vykřičník.|  
  
 Jak ukazuje následující příklad, pokud je nalezena shoda, i <xref:System.Text.RegularExpressions.GroupCollection> a <xref:System.Text.RegularExpressions.CaptureCollection> objekty se naplní obrazovek z shody. V takovém případě se skupinou zachycení `(\w+[;,]?\s?)` existuje tak, aby `+` kvantifikátoru lze použít, která umožňuje vzor regulárního výrazu tak, aby odpovídaly jednotlivých slov ve větě. V opačném případě může odpovídat poslednímu slovu ve větě.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group1.cs#8)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group1.vb#8)]  
  
 Pokud použijete dílčí výrazy pouze proto, abyste mohli použít kvantifikátor a zachycený text pro vás není podstatný, měli byste skupinové zachytávání zakázat. Například `(?:``subexpression``)` jazyk element brání skupiny, které se od zaznamenání odpovídající dílčích řetězců. V následujícím příkladu vzor regulárního výrazu z předchozího příkladu se změní na `\b(?:\w+[;,]?\s?)+[.?!]`. Jak ukazuje výstup zabrání naplnění modul regulárních výrazů <xref:System.Text.RegularExpressions.GroupCollection> a <xref:System.Text.RegularExpressions.CaptureCollection> kolekce.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group2.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group2.vb#9)]  
  
 Zachytávání lze zakázat jedním z následujících způsobů:  
  
-   Použití `(?:``subexpression``)` element jazyka. Tento prvek zabraňuje v zachytávání shodných podřetězců ve skupině, pro kterou se používá. Nezakazuje zachytávání podřetězců v jakékoli vnořené skupině.  
  
-   Použití <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> možnost. Zakazuje všechna nepojmenovaná nebo implicitní zachycení ve vzoru regulárního výrazu. Pokud použijete tuto možnost, pouze podřetězce které odpovídají definované s skupiny s názvem `(?<``name``>``subexpression``)` element jazyk, se dají zachytit. <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> Příznak se dá předat do `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo `options` parametr <xref:System.Text.RegularExpressions.Regex> statickou odpovídající metodu.  
  
-   Použití `n` možnost `(?imnsx)` element jazyka. Tato možnost zakazuje všechna nepojmenovaná nebo implicitní zachycení z bodu ve vzoru regulárního výrazu, ve kterém se prvek objeví. Záznamy jsou zakázány buď až do konce vzoru, nebo dokud se `(-n)` možnost umožňuje nepojmenovaný nebo implicitní zachycení. Další informace najdete v tématu [různé vytvoří](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md).  
  
-   Použití `n` možnost `(?imnsx:``subexpression``)` element jazyka. Tato možnost zakáže všechny nepojmenované nebo implicitní zachycení v `subexpression`. Zachycení nepojmenovanou nebo implicitní vnořenou zachytávající skupinou jsou rovněž zakázána.  
  
 [Zpět na začátek](#top)  
  
<a name="RelatedTopics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Podrobnosti k chování regulárních výrazů](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|Prozkoumá implementace modul regulárních výrazů v .NET. Téma se zaměřuje na flexibilitu regulárních výrazů a objasňuje odpovědnost vývojáře za zajištění efektivity a výkonnosti modulu regulárních výrazů.|  
|[Zpětné navracení](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Vysvětluje princip zpětného navracení a vliv tohoto mechanismu na výkon regulárních výrazů a zkoumá prvky jazyka, které nabízí alternativu zpětného navracení.|  
|[Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Popisuje elementy jazyk regulárních výrazů v .NET a poskytuje odkazy na podrobná dokumentace pro jednotlivé elementy jazyka.|
