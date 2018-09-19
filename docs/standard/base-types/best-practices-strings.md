---
title: Osvědčené postupy pro používání řetězců v .NET
ms.date: 09/13/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework],searching
- best practices,string comparison and sorting
- strings [.NET Framework],best practices
- strings [.NET Framework],basic string operations
- sorting strings
- strings [.NET Framework],sorting
- string comparison [.NET Framework],best practices
- string sorting
- comparing strings
- strings [.NET Framework],comparing
ms.assetid: b9f0bf53-e2de-4116-8ce9-d4f91a1df4f7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6114553c6bcdac8521c80c10f470d4c38b15e738
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45988735"
---
# <a name="best-practices-for-using-strings-in-net"></a>Osvědčené postupy pro používání řetězců v .NET
<a name="top"></a> .NET poskytuje rozsáhlou podporu pro vývoj globalizovaných a lokalizovaných aplikací a umožňuje snadno použít konvence aktuální jazykové verze nebo specifické jazykové verze při provádění běžných operací, jako je například řazení a zobrazení řetězce. Ale řazení a porovnávání řetězců není vždy operace zohledňující jazykovou verzi. Například by řetězců, které se používají interně aplikace obvykle zpracovává stejně jako všechny jazykové verze. Pokud jazykově nezávislá řetězec dat, jako jsou XML značky HTML značky, uživatelská jména, cesty k souborům a názvy systémové objekty, jsou interpretovány, jako by byly zohledňující jazykovou verzi, v souladu s drobné chyby, nízký výkon a v některých případech může být kód aplikace problémy se zabezpečením.  
  
 Toto téma prozkoumá řazení řetězců, porovnání a metody malých a velkých písmen v .NET, nabízí doporučení pro výběr příslušné metody zpracování řetězců a poskytuje další informace o metodách zpracování řetězce. Také zkontroluje jak formátovaných dat, jako je například číselná data a data a času, se zpracovává k zobrazení a pro úložiště.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Doporučení pro používání řetězců](#recommendations_for_string_usage)  
  
-   [Odstranit explicitním zadáním porovnávání řetězců](#specifying_string_comparisons_explicitly)  
  
-   [Podrobnosti o porovnání řetězců](#the_details_of_string_comparison)  
  
-   [Výběr člena StringComparison, který vaše volání metody](#choosing_a_stringcomparison_member_for_your_method_call)  
  
-   [Běžné metody pro porovnávání řetězců v .NET](#common_string_comparison_methods_in_the_net_framework)  
  
-   [Metody, které nepřímo provést porovnání řetězců](#methods_that_perform_string_comparison_indirectly)  
  
-   [Zobrazení a uchování formátovaných dat](#Formatted)  
  
<a name="recommendations_for_string_usage"></a>   
## <a name="recommendations-for-string-usage"></a>Doporučení pro používání řetězců  
 Při vývoji pomocí .NET, postupujte podle těchto jednoduchých doporučení, při použití řetězce:  
  
-   Použijte přetížení, která explicitně zadáte pravidel pro porovnávání řetězců pro operace s řetězci. Obvykle to zahrnuje volání přetížení metody, která má parametr typu <xref:System.StringComparison>.  
  
-   Použití <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro porovnání jako výchozí bezpečnou pro porovnávání řetězců nezávislá na jazykové verzi.  
  
-   Použít porovnávání s <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro zajištění lepšího výkonu.  
  
-   Pomocí operace s řetězci, které jsou založeny na <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> při zobrazení výstupu uživateli.  
  
-   Použít nejazykové <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> podle hodnoty místo operace s řetězci <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> při porovnání lingvistických bezvýznamná (například symbolických).  
  
-   Použití <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> metoda místo <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> metoda při normalizujte řetězce pro porovnání.  
  
-   Použijte přetížení <xref:System.String.Equals%2A?displayProperty=nameWithType> metodu k ověření, zda jsou dva řetězce rovny.  
  
-   Použití <xref:System.String.Compare%2A?displayProperty=nameWithType> a <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody pro řazení řetězců, ne pro kontrolu rovnosti.  
  
-   Formátování zohledňující jazykovou verzi použijte k zobrazení neřetězcová data, jako je například čísla a kalendářní data, v uživatelském rozhraní. Použití formátování pomocí neutrální jazykové verze k uchování neřetězcová data ve formátu řetězce.  
  
 Nepoužívejte následující postupy pro používání řetězců:  
  
-   Nepoužívejte přetížení, které explicitně nebo implicitně zadat pravidla pro porovnávání řetězců pro operace s řetězci.  
  
-   Nepoužívejte operace s řetězci závislé na základě <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> ve většině případů. Jednou z několika výjimkami je uchováváte data, která ale lingvistických smysluplné.  
  
-   Nepoužívejte přetížení <xref:System.String.Compare%2A?displayProperty=nameWithType> nebo <xref:System.String.CompareTo%2A> metoda a testování pro návratovou hodnotu nula, která určí, zda jsou dva řetězce stejné.  
  
-   Nepoužívejte formátování zohledňující jazykovou verzi se zachovat číselná data nebo data pro datum a čas ve formátu řetězce.  
  
 [Zpět na začátek](#top)  
  
<a name="specifying_string_comparisons_explicitly"></a>   
## <a name="specifying-string-comparisons-explicitly"></a>Odstranit explicitním zadáním porovnávání řetězců  
 Většina metod manipulace s řetězci v .NET jsou přetížené. Jeden nebo více přetížení obvykle přijmout výchozí nastavení, zatímco ostatní přijměte žádné výchozí hodnoty a místo toho určit přesné způsob, jakým jsou řetězce k porovnání nebo s nimi pracovat. Většina metod, které nespoléhejte na výchozím nastavení zahrnují parametr typu <xref:System.StringComparison>, což je výčet, který explicitně určuje pravidla pro porovnání řetězců podle jazykové verze a případ. V následující tabulce jsou popsány <xref:System.StringComparison> členy výčtu.  
  
|Člen StringComparison|Popis|  
|-----------------------------|-----------------|  
|<xref:System.StringComparison.CurrentCulture>|Provádí velká a malá písmena porovnání použitím aktuální jazykové verze.|  
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|Provádí porovnávání bez použitím aktuální jazykové verze.|  
|<xref:System.StringComparison.InvariantCulture>|Provádí porovnání velká a malá písmena pomocí neutrální jazykové verze.|  
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|Provádí porovnávání pomocí neutrální jazykové verze.|  
|<xref:System.StringComparison.Ordinal>|Provádí řadové porovnání.|  
|<xref:System.StringComparison.OrdinalIgnoreCase>|Provádí pořadové porovnávání.|  
  
 Například <xref:System.String.IndexOf%2A> metodu, která vrátí index podřetězce v <xref:System.String> objekt, který odpovídá znaku nebo řetězec, obsahuje devět přetížení:  
  
-   <xref:System.String.IndexOf%28System.Char%29>, <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29>, a <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>, která ve výchozím nastavení provádí ordinální vyhledávání (malá a velká písmena a nezávislé na jazykové verzi) pro znak v řetězci.  
  
-   <xref:System.String.IndexOf%28System.String%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>, a <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>, která ve výchozím nastavení provádí velká a malá písmena a zohledňující jazykovou verzi vyhledávání podřetězce v řetězci.  
  
-   <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>, a <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29>, které obsahují parametr typu <xref:System.StringComparison> , která umožňuje formu porovnání zadání.  
  
 Doporučujeme vám, že vyberete přetížení, která nepoužívá výchozí hodnoty z následujících důvodů:  
  
-   Některá přetížení s výchozími parametry (těch, které hledají <xref:System.Char> v instanci string) provádět pořadové porovnávání, zatímco jiné (těch, které hledají řetězce v instanci string) jsou závislé na jazykové verzi. Je obtížné mějte na paměti, která metoda používá které výchozí hodnotu a snadno zaměnit přetížení.  
  
-   Záměr kódu, který závisí na výchozí hodnoty pro volání metody není jasný. V následujícím příkladu, který závisí na výchozí hodnoty, je obtížné zjistit, jestli vývojář skutečně určený ordinální číslo nebo jazykové porovnání dvou řetězců nebo zda případu rozdíl mezi `protocol` a "http" může způsobit, že testování rovnosti Chcete-li vrátit `false`.  
  
     [!code-csharp[Conceptual.Strings.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]  
  
 Obecně platí doporučujeme volání metody, který není závislý na výchozí hodnoty, protože záměr kód je jednoznačný. Díky tomu kód lépe čitelný a snadněji vyladit a udržovat. V následujícím příkladu řeší otázky o z předchozího příkladu. Umožňuje vymazat to ordinálního porovnání se používá a že rozdíly v případě jsou ignorovány.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
 [!code-vb[Conceptual.Strings.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]  
  
 [Zpět na začátek](#top)  
  
<a name="the_details_of_string_comparison"></a>   
## <a name="the-details-of-string-comparison"></a>Podrobnosti o porovnání řetězců  
 Porovnání řetězců je srdcem mnoho řetězec operací souvisejících se zabezpečením, zejména řazení a testování rovnosti. V určeném pořadí řazení řetězců: Pokud "my" před "string" v seřazený seznam řetězců, "my" musí porovnat menší než nebo rovno "string". Kromě toho porovnání implicitně definuje rovnosti. Operace porovnání vrátí hodnotu 0 pro řetězce, které považuje za stejné. Dobré výkladu je, že žádný řetězec není menší než ten druhý. Smysluplných operací zahrnujících řetězce obsahuje jedno nebo obě z následujících postupů: Výsledkem porovnání s jiným řetězcem a provádění operace jasně definované řazení.  

> [!NOTE]
> Můžete stáhnout [řazení váhy tabulky](https://www.microsoft.com/en-us/download/details.aspx?id=10921), sadu textové soubory, které obsahují informace o tom váhy znaků použitých v operacích řazení a porovnávání pro operační systémy Windows, a [výchozí kódování Unicode Kolace elementu Table](https://www.unicode.org/Public/UCA/latest/allkeys.txt), nejnovější verze tabulky váhy řazení pro systémy Linux a macOS. Konkrétní verze tabulky váhy řazení v Linuxu a macOS závisí na verzi [mezinárodní součásti pro kódování Unicode](http://site.icu-project.org/) knihovny nainstalované v systému. Informace o verzích ICU a Unicode verze, které implementují najdete v tématu [stahování ICU](http://site.icu-project.org/download).

 Však vaše rozhodnutí vyzkoušet dva řetězce pro rovnost nebo pořadí řazení nevydává jeden správný výsledek. Výsledek závisí na kritéria použitá pro porovnání řetězců. Zejména porovnávání řetězců, které jsou podle pořadového čísla nebo které jsou založeny malých a velkých písmen a řazení konvence aktuální jazykové verze nebo neutrální jazykové verze (národní prostředí bez ohledu na jazykovou verzi na základě v anglickém jazyce) mohou mít různé výsledky.  

Porovnání řetězců pomocí různých verzí rozhraní .NET nebo pomocí rozhraní .NET na různé operační systémy nebo verze operačního systému kromě toho může vrátit různé výsledky. Další informace najdete v tématu [řetězce a standardu Unicode](xref:System.String#Unicode). 

<a name="current_culture"></a>   
### <a name="string-comparisons-that-use-the-current-culture"></a>Porovnávání řetězců, které používají aktuální jazykovou verzi  
 Jedno kritérium zahrnuje při porovnávání řetězců pomocí konvencí aktuální jazykové verze. Porovnání, které jsou založeny na aktuální jazykovou verzi pomocí aktuální jazykové verze vlákna nebo národní prostředí. Pokud uživatel není nastavena jazyková verze, použije se výchozí nastavení **místní nastavení** okno v Ovládacích panelech. Vždy byste měli použít porovnávání, které jsou založeny na aktuální jazykové verze, pokud jsou jazykově relevantní data a odráží interakci s uživatelem zohledňující jazykovou verzi.  
  
 Chování porovnání a malých a velkých písmen v .NET změny však po změně jazykové verze. To se stane, když je aplikace spuštěna v počítači, který má jinou jazykovou verzi, než počítač, na kterém byla vyvinuta aplikace nebo při změně spuštěné vlákno jeho jazykovou verzi. Toto chování je záměrné, ale zůstane není zřejmé celá řada vývojářů. Následující příklad ukazuje rozdíly v řazení mezi USA Angličtina ("en US") a švédština jazykové verze ("sv-SE"). Všimněte si, že na různých místech v polích seřazený řetězec nezobrazí slova "ångström", "Windows" a "Sada Visual Studio".  
  
 [!code-csharp[Conceptual.Strings.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
 [!code-vb[Conceptual.Strings.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]  
  
 Porovnávání, které používají aktuální jazykovou verzi jsou stejné jako Porovnání zohledňující jazykovou verzi, s tím rozdílem, že ignorovat velikost písmen podle aktuální jazykové verze vlákna. Toto chování se může projevit v pořadí řazení i.  
  
 Porovnání, která používají sémantiku aktuální jazykové verze se na výchozí hodnoty pro následující metody:  
  
-   <xref:System.String.Compare%2A?displayProperty=nameWithType> přetížení, které nejsou zahrnuté <xref:System.StringComparison> parametru.  
  
-   <xref:System.String.CompareTo%2A?displayProperty=nameWithType> přetížení.  
  
-   Výchozí hodnota <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> metoda a <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metodou `null` <xref:System.Globalization.CultureInfo> parametr.  
  
-   Výchozí hodnota <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> metoda a <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metodou `null` <xref:System.Globalization.CultureInfo> parametr.  
  
-   <xref:System.String.IndexOf%2A?displayProperty=nameWithType> přetížení, které přijímají <xref:System.String> jako hledání parametr a které nemají <xref:System.StringComparison> parametru.  
  
-   <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> přetížení, které přijímají <xref:System.String> jako hledání parametr a které nemají <xref:System.StringComparison> parametru.  
  
 V každém případě doporučujeme volat přetížení, která má <xref:System.StringComparison> parametr, chcete záměr metody jasný volání.  
  
 Jednoduchý a proto drobné chyby můžete objeví, když data nejazykové řetězec je interpretován lingvistických, nebo když řetězcovými daty z konkrétní jazykové verze je interpretován pomocí konvencí jinou jazykovou verzi. Canonical příkladu je turečtina-jsem problém.  
  
 Pro téměř všechna latinky písmena abecedy, včetně USA Angličtina, znak "i" (\u0069) je malá verze znaku "I" (\u0049). Toto pravidlo malých a velkých písmen rychle stane výchozí někdo programování v těchto jazykovou verzi. Ale obsahuje abecedy turečtina ("tr-TR") "I s tečkou" znak "İ" (\u0130), což je velká verze z "i". Turečtina také obsahuje znak malé písmeno "i bez tečky", "ı" (\u0131), jehož velká "I". K tomuto chování dochází v jazykové verzi Ázerbájdžánština ("az") i.  
  
 Proto předpoklady o "i" na velká písmena nebo předpoklady "I" nejsou platné pro všechny jazykové verze. Pokud používáte výchozí přetížení rutin pro porovnávání řetězců, budou platit odchylky mezi jazykové verze. Pokud jsou data k porovnání nejazykové, pomocí přetížení výchozí může způsobit nežádoucí výsledky, jako je následující pokus o provádění porovnávání řetězců "file" a ukazuje "FILE".  
  
 [!code-csharp[Conceptual.Strings.BestPractices#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
 [!code-vb[Conceptual.Strings.BestPractices#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]  
  
 Toto porovnání může způsobit významné problémy, pokud citlivá nastavení zabezpečení, jako v následujícím příkladu neúmyslně používané jazykové verze. Volání metody, jako `IsFileURI("file:")` vrátí `true` Pokud je aktuální jazyková verze Angličtina, ale `false` Pokud je aktuální jazyková verze turečtinu. Proto v turecké systémech někdo mohl obejít bezpečnostních opatření, které blokují přístup k malá a velká písmena identifikátorů URI, který začíná pod "souboru:".  
  
 [!code-csharp[Conceptual.Strings.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
 [!code-vb[Conceptual.Strings.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]  
  
 V tomto případě protože "souboru:" je určená, je interpretován jako identifikátor nejazykové, nezávislých na jazykové verzi, kód by měl místo zapsání jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
 [!code-vb[Conceptual.Strings.BestPractices#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]  
  
### <a name="ordinal-string-operations"></a>Ordinální operace s řetězci  
 Zadání <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> hodnotu ve volání metody označuje nejazykové porovnání, ve kterém jsou ignorovány funkcí přirozeného jazyka. Metody, které jsou vyvolány pomocí těchto <xref:System.StringComparison> hodnoty základní řetězec operace rozhodnutí o porovnání jednoduché bajtů namísto malých a velkých písmen nebo ekvivalence tabulek, které jsou parametrizovány podle jazykové verze. Ve většině případů se tento přístup nejlépe odpovídá určené interpretace řetězce při provádění kódu rychlejší a spolehlivější.  
  
 Ordinální porovnání jsou porovnávání řetězců, ve kterých každý bajt každého řetězce je porovnán bez lingvistické interpretace. například "windows" neodpovídá "Windows". Toto je v podstatě volání modulu C Runtime `strcmp` funkce. Porovnání použijte, pokud kontext určuje, že by řetězců přesně odpovídat nebo požadavků konzervativní odpovídající zásady. Kromě toho řadové porovnání je nejrychlejší operace porovnání, protože žádná jazyková pravidla platí při stanovení výsledku.  
  
 Řetězců v .NET může obsahovat vložené znaky null. Jedním z s nejjednoznačnějším rozdílů mezi porovnání podle pořadového čísla a zohledňující jazykovou verzi (včetně porovnání, která používají invariantní jazyková verze) se týká zpracování vložené znaky null v řetězci. Tyto znaky jsou ignorovány, pokud použijete <xref:System.String.Compare%2A?displayProperty=nameWithType> a <xref:System.String.Equals%2A?displayProperty=nameWithType> metody k provádění porovnání zohledňující jazykovou verzi (včetně porovnání, která používají invariantní jazyková verze). V důsledku toho v porovnání zohledňující jazykovou verzi, řetězce obsahující vložené znaky null lze považovat za rovno řetězci, které nepodporují.  
  
> [!IMPORTANT]
>  I když metod pro porovnávání řetězců ignorovat vložené znaky null, řetězec hledání metody jako <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.EndsWith%2A?displayProperty=nameWithType>, <xref:System.String.IndexOf%2A?displayProperty=nameWithType>, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>, a <xref:System.String.StartsWith%2A?displayProperty=nameWithType> nepodporují.  
  
 Následující příklad provádí porovnání zohledňující jazykovou verzi řetězec "Aa" podobně jako řetězec, který obsahuje několik vložené znaky null mezi "A" a "a" a ukazuje, jak dva řetězce považovány za shodné.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]  
  
 Ale řetězce nejsou považovány za shodné při použít řadové porovnání, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
 [!code-vb[Conceptual.Strings.BestPractices#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]  
  
 Ordinální porovnání velká a malá písmena jsou další nejrestriktivnější přístup. Tato porovnání ignorovat většina malých a velkých písmen; například "windows" odpovídá "Windows". Při zpracování komplexnějších znaky ASCII, tato zásada je ekvivalentní <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>, s tím rozdílem, že je ignorován obvykle ASCII velká a malá písmena. Proto jakémukoliv znaku v [A, Z] (\u0041-\u005A) odpovídá na odpovídající znak v [, z] (\u0061-\007A). Velká a malá písmena mimo rozsah ASCII používá invariantní jazyková verze tabulky. Proto se na toto porovnání:  
  
 [!code-csharp[Conceptual.Strings.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
 [!code-vb[Conceptual.Strings.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]  
  
 je ekvivalentní k (ale rychlejší než) Toto porovnání:  
  
 [!code-csharp[Conceptual.Strings.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
 [!code-vb[Conceptual.Strings.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]  
  
 Tato porovnání jsou stále velmi rychle.  
  
> [!NOTE]
>  Řetězec chování systému souborů, klíčů registru a hodnoty a proměnné prostředí je reprezentována nejlépe <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>.  
  
 Obě <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> a <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> přímo použít binární hodnoty a jsou nejvhodnější pro porovnání. Pokud si nejste jisti o porovnání nastavení, použijte jednu z těchto dvou hodnot. Ale protože provádějí porovnání bajt po bajtu, neposkytují řazení lingvistické řazení (např. angličtinu slovník), ale binární řazení. Ve většině případů, pokud se zobrazí uživatelům může připadat výsledky.  
  
 Ordinální sémantika je výchozí nastavení pro <xref:System.String.Equals%2A?displayProperty=nameWithType> přetížení, které nejsou zahrnuté <xref:System.StringComparison> argument (včetně operátor rovnosti). V každém případě doporučujeme volat přetížení, která má <xref:System.StringComparison> parametru.  
  
### <a name="string-operations-that-use-the-invariant-culture"></a>Operace s řetězci, které používají neutrální jazykovou verzi  
 Porovnávání pomocí neutrální jazykové verze <xref:System.Globalization.CultureInfo.CompareInfo%2A> vrácené statickou vlastnost <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost. Toto chování je stejné ve všech systémech. převádí všechny znaky mimo rozsah na co považuje za ekvivalentní invariantní znaků. Tato zásada může být užitečné pro zachování jednu sadu řetězec chování mezi jazykové verze, ale často poskytuje neočekávané výsledky.  
  
 Porovnávání pomocí neutrální jazykové verze používá statickou <xref:System.Globalization.CultureInfo.CompareInfo%2A> vrácené statickou vlastnost <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost pro informace o porovnávání. Všechny velikosti písmen rozdíly mezi těmito přeloženými znaky se ignorují.  
  
 Porovnání, která používají <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> a <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> pracovat stejně jako na řetězce ASCII. Ale <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> díky lingvistické rozhodnutí, které nemusí být vhodný pro řetězce, které mají být vykládány jako řadu bajtů. `CultureInfo.InvariantCulture.CompareInfo` Objektu provede <xref:System.String.Compare%2A> metoda interpretovat jako ekvivalentní určité sady znaků. Například následující rovnost je platný pro invariantní jazykovou verzi:  
  
 InvariantCulture: + ̊ =  
  
 LATIN malé písmeno A znak "a" (\u0061), když je vedle KOMBINOVÁNÍ KROUŽKEM znak "+"̊"(\u030a), je interpretován jako LATINCE malé písmeno s KROUŽKEM znak"å"(\u00e5). Jak ukazuje následující příklad, toto chování se liší od ordinálního porovnání.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
 [!code-vb[Conceptual.Strings.BestPractices#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]  
  
 Při interpretaci názvů souborů, souborů cookie nebo cokoli jiného, kde se mohou objevit kombinaci, jako je například "å", pořadové porovnávání stále nabízet chování nejtransparentnější a nejvhodnější.  
  
 Neutrální jazykovou verzi na zůstatek, má jen několik vlastností, které jsou užitečné pro porovnání. Provede porovnání lingvistických relevantní způsobem, který brání jeho zaručení plné ekvivalence, ale není to volbou pro zobrazení v žádné jazykové verze. Jeden z několika důvodů, proč používat <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> pro porovnání je pro trvalé ukládání seřazený napříč kulturami stejné zobrazení. Například pokud soubor velkých objemů dat, který obsahuje seznam seřazený identifikátory pro zobrazení doprovází aplikace, přidání do tohoto seznamu vyžadovat vložení pomocí řazení ve stylu invariantní.  
  
 [Zpět na začátek](#top)  
  
<a name="choosing_a_stringcomparison_member_for_your_method_call"></a>   
## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Výběr člena StringComparison, který vaše volání metody  
 Následující tabulka uvádí mapování z kontextu sémantického <xref:System.StringComparison> člena výčtu.  
  
|Data|Chování|Odpovídající System.StringComparison<br /><br /> value|  
|----------|--------------|-----------------------------------------------------|  
|Malá a velká písmena identifikátorů interní.<br /><br /> Malá a velká písmena identifikátorů standardů, jako jsou XML a HTTP.<br /><br /> Malá a velká písmena nastavení související se zabezpečením.|Nejazykové identifikátor, kde se přesně shodují bajtů.|<xref:System.StringComparison.Ordinal>|  
|Malá a velká písmena identifikátorů interní.<br /><br /> Malá a velká písmena identifikátorů standardů, jako jsou XML a HTTP.<br /><br /> Cesty k souborům.<br /><br /> Klíče registru a hodnoty.<br /><br /> Proměnné prostředí.<br /><br /> Identifikátory prostředků (například názvy popisovač).<br /><br /> Malá a velká písmena nastavení související se zabezpečením.|Nejazykové identifikátor, kde je bezvýznamná; případ zejména data uložená v většina služeb systému Windows.|<xref:System.StringComparison.OrdinalIgnoreCase>|  
|Trvalé, lingvistických relevantní data.<br /><br /> Zobrazit údaje o jazyku, který vyžaduje pořadí opravené seřadit.|Jazykově nezávislá data, která je stále lingvistických relevantní.|<xref:System.StringComparison.InvariantCulture><br /><br /> -nebo-<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|  
|Data zobrazená pro uživatele.<br /><br /> Většina vstupu uživatele.|Data, která vyžaduje místní lingvistické.|<xref:System.StringComparison.CurrentCulture><br /><br /> -nebo-<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|  
  
 [Zpět na začátek](#top)  
  
<a name="common_string_comparison_methods_in_the_net_framework"></a>   
## <a name="common-string-comparison-methods-in-net"></a>Běžné metody pro porovnávání řetězců v .NET  
 Následující části popisují metody, které se nejčastěji používají pro porovnání řetězců.  
  
### <a name="stringcompare"></a>String.Compare  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Jako většina centrální k interpretaci řetězec operace by měla být prozkoumána všech instancí těchto volání metod určit, zda řetězce by měla být interpretováno podle aktuální jazykové verze nebo oddělen od jazykovou verzi (symbolicky). Obvykle je ten a <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> porovnání by místo toho používat.  
  
 <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> Třída, která je vrácena <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> také obsahuje vlastnosti, <xref:System.Globalization.CompareInfo.Compare%2A> metodu, která obsahuje velký počet odpovídající možnosti (řádové, ignorování prázdných znaků, typu ignoruje kana a tak dále) prostřednictvím <xref:System.Globalization.CompareOptions> příznak výčet.  
  
### <a name="stringcompareto"></a>String.CompareTo  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Tato metoda aktuálně nenabízí přetížení, která určuje <xref:System.StringComparison> typu. Obvykle je možné převést tuto metodu na doporučenou <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> formuláře.  
  
 Typy, které implementují <xref:System.IComparable> a <xref:System.IComparable%601> tuto metodu implementovat rozhraní. Vzhledem k tomu, že nenabízí možnost <xref:System.StringComparison> parametr, implementace typy často umožní uživateli zadat <xref:System.StringComparer> v jejich konstruktoru. Následující příklad definuje `FileName` třídy, jejíž konstruktor třídy zahrnuje <xref:System.StringComparer> parametru. To <xref:System.StringComparer> objekt se pak použije v `FileName.CompareTo` metody.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
 [!code-vb[Conceptual.Strings.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]  
  
### <a name="stringequals"></a>String.Equals  
 Výchozí interpretaci: <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.  
  
 <xref:System.String> Třída umožňuje testovat rovnost voláním buď statické, nebo instanci <xref:System.String.Equals%2A> přetížení metody, nebo pomocí operátoru rovnosti statické. Přetížení a operátor použít řadové porovnání ve výchozím nastavení. Ale doporučujeme, že můžete volat přetížení, které explicitně určuje <xref:System.StringComparison> typ i v případě, že chcete provést řadové porovnání; to usnadňuje vyhledávání kódu pro určité interpretace řetězce.  
  
### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper a String.ToLower  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Měli byste být opatrní při použití těchto metod, protože vynucení řetězec na velká nebo malá písmena se často používá jako malé normalizace pro porovnávání řetězců bez ohledu na malá. V takovém případě zvažte použití porovnávání.  
  
 <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> a <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> metody jsou také k dispozici. <xref:System.String.ToUpperInvariant%2A> je standardní způsob, jak normalizovat případ. Porovnání pomocí <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> jsou složením dvě volání: volání <xref:System.String.ToUpperInvariant%2A> na řetězcové argumenty a to v porovnání s použitím <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.  
  
 Přetížení jsou také k dispozici pro převod na velká a malá písmena v konkrétní jazykovou verzi, tím, že předáte <xref:System.Globalization.CultureInfo> objekt, který představuje tuto jazykovou verzi k metodě.  
  
### <a name="chartoupper-and-chartolower"></a>Char.ToUpper – a Char.ToLower  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Tyto metody fungují podobně jako <xref:System.String.ToUpper%2A?displayProperty=nameWithType> a <xref:System.String.ToLower%2A?displayProperty=nameWithType> metod popsaných v předchozí části.  
  
### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith a String.EndsWith  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Ve výchozím nastavení obě tyto metody provádět porovnání zohledňující jazykovou verzi.  
  
### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf a String.LastIndexOf  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Existuje souvisí s nedostatečnou konzistencí v jak výchozím přetížením metod provést porovnání. Všechny <xref:System.String.IndexOf%2A?displayProperty=nameWithType> a <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> metody, které patří <xref:System.Char> parametru provede pořadové porovnávání, ale výchozí <xref:System.String.IndexOf%2A?displayProperty=nameWithType> a <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> metody, které obsahují <xref:System.String> parametru provede zohledňující jazykovou verzi porovnání.  
  
 Při volání <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> nebo <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> metoda a předejte jí řetězec pro vyhledání v aktuální instanci aplikace, doporučujeme vám, že můžete volat přetížení, které explicitně určuje <xref:System.StringComparison> typu. Přetížení, které obsahují <xref:System.Char> argument neumožňuje zadat <xref:System.StringComparison> typu.  
  
 [Zpět na začátek](#top)  
  
<a name="methods_that_perform_string_comparison_indirectly"></a>   
## <a name="methods-that-perform-string-comparison-indirectly"></a>Metody, které nepřímo provést porovnání řetězců  
 Některé neřetězcové metody, které mají porovnání řetězců jako použití centrální operaci <xref:System.StringComparer> typu. <xref:System.StringComparer> Třída obsahuje šest statické vlastnosti, které vracejí <xref:System.StringComparer> instance, jejíž <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> metody provádět následující typy porovnávání řetězců:  
  
-   Porovnání řetězců zohledňující jazykovou verzi pomocí aktuální jazykové verze. To <xref:System.StringComparer> objekt je vrácen rutinou <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType> vlastnost.  
  
-   Malá a velká písmena porovnání použitím aktuální jazykové verze. To <xref:System.StringComparer> objekt je vrácen rutinou <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType> vlastnost.  
  
-   Porovnání nezávislá na jazykové verzi pomocí pravidel pro slova porovnání invariantní jazykovou verzi. To <xref:System.StringComparer> objekt je vrácen rutinou <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType> vlastnost.  
  
-   Porovnání velká a malá písmena a nezávislé na jazykové verzi pomocí pravidel pro slova porovnání invariantní jazykovou verzi. To <xref:System.StringComparer> objekt je vrácen rutinou <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType> vlastnost.  
  
-   Ordinálního porovnání. To <xref:System.StringComparer> objekt je vrácen rutinou <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType> vlastnost.  
  
-   Malá a velká písmena ordinálního porovnání. To <xref:System.StringComparer> objekt je vrácen rutinou <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> vlastnost.  
  
### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort a Array.BinarySearch  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Při ukládání dat v kolekci, nebo přečíst trvalá data ze souboru nebo databáze do kolekce, mohou zneplatnit přepínání aktuální jazykové verze výstupních podmínek v kolekci. <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> Metoda předpokládá, že jsou již seřazeny prvků v poli pro hledání. Řazení libovolný prvek řetězce v poli, <xref:System.Array.Sort%2A?displayProperty=nameWithType> volání metod <xref:System.String.Compare%2A?displayProperty=nameWithType> metody pro řazení jednotlivých prvků. Použití porovnávání zohledňující jazykovou verzi může být nebezpečné, pokud jsou prohledávány změny jazykové verze mezi časem, který je seřazen pole a jeho obsah. Například v následujícím kódu, ukládání a načítání provádět porovnávací metody, která je k dispozici implicitně `Thread.CurrentThread.CurrentCulture` vlastnost. Pokud jazykovou verzi může změnit mezi volání `StoreNames` a `DoesNameExist`, a zejména v případě, že je obsah pole jsou trvalé někde mezi dvěma voláními, binární vyhledávání může selhat.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]  
  
 V následujícím příkladu, který používá stejné metody porovnání podle pořadového čísla (nezávislých na jazykové verzi), řazení a vyhledávání pole se zobrazí doporučená varianta. Změna kódu se projeví v řádcích označené `Line A` a `Line B` v obou příkladech.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
 [!code-vb[Conceptual.Strings.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]  
  
 Pokud tato data je trvalá a přesouvat mezi jazykové verze a řazení se používá k zobrazení těchto dat pro uživatele, můžete zvážit použití <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>, jež pracuje lingvistických pro lepší uživatelský výstup je ale nebudou výpadkem ovlivněny změnami v jazykové verzi. Následující příklad upravuje tyto dva příklady předchozí použití invariantní jazykovou verzi pro řazení a vyhledávání pole.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
 [!code-vb[Conceptual.Strings.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]  
  
### <a name="collections-example-hashtable-constructor"></a>Příklad kolekcí: konstruktor zatřiďovací tabulky  
 Druhý příklad: operace, která je tím ovlivněná tím, jak ve kterém jsou řetězce porovnány algoritmu hash řetězců poskytuje.  
  
 Následující příklad vytvoří <xref:System.Collections.Hashtable> objekt ji <xref:System.StringComparer> objekt, který je vrácený <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> vlastnost. Protože třída <xref:System.StringComparer> , která je odvozena od <xref:System.StringComparer> implementuje <xref:System.Collections.IEqualityComparer> rozhraní, jeho <xref:System.Collections.IEqualityComparer.GetHashCode%2A> metoda se používá k výpočtu kódů hash řetězců v zatřiďovací tabulce.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
 [!code-vb[Conceptual.Strings.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]  
  
 [Zpět na začátek](#top)  
  
<a name="Formatted"></a>   
## <a name="displaying-and-persisting-formatted-data"></a>Zobrazení a uchování formátovaných dat  
 Při zobrazení neřetězcová data, jako je například čísla a kalendářní data a časy pro uživatele, naformátujte s použitím nastavení jazykové verze uživatele. Ve výchozím nastavení <xref:System.String.Format%2A?displayProperty=nameWithType> metoda a `ToString` metody číselné typy a typy data a času používají aktuální jazykovou verzi vlákna pro operace formátování. Explicitně určit, že metoda formátování používejte aktuální jazykovou verzi, můžete volat přetížení metody pro formátování, který má `provider` parametr, například <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> nebo <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType>a předat ji <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost.  
  
 Jako binární data nebo jako formátovaná data je možné zachovat neřetězcová data. Pokud se rozhodnete ji uložit jako formátovaných dat, měli byste zavolat formátování přetížení metody, která zahrnuje `provider` parametr a předat ji <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost. Neutrální jazykové verze poskytuje konzistentní formát pro formátovaných dat, který je nezávislý na jazykové verzi a počítače. Naproti tomu zachovává data, který je naformátovaný pomocí jazykové verze než neutrální jazykové verze má několik omezení:  
  
-   Data jsou pravděpodobně nebude možné použít, pokud je načten v systému, který má jinou jazykovou verzi, nebo pokud uživatel aktuálního systému změní aktuální jazykovou verzi a pokusí se načíst data.  
  
-   Vlastnosti v určitém počítači jazykové verze se může lišit od standardních hodnot. V každém okamžiku může uživatel přizpůsobit nastavení zobrazení zohledňující jazykovou verzi. Z tohoto důvodu nemusí být formátovaná data, která je uložena v systému čitelné po uživatel upraví nastavení jazykové verze. Přenositelnost formátovaných dat mezi počítači by mohla být ještě více omezit.  
  
-   Mezinárodní, místní nebo národní standardy, které řídí formátování čísla nebo kalendářní data a časy v průběhu času měnit a tyto změny jsou součástí aktualizací operačního systému Windows. Při změně konvence formátování, může stává se nečitelnou dat, který se naformátoval pomocí předchozí konvencí.  
  
 Následující příklad ukazuje omezené přenositelnost, která je výsledkem použití formátování zohledňující jazykovou verzi uchovávat data. Příklad uloží do souboru pole hodnoty data a času. Tyto jsou formátovány pomocí úmluv jazykové verze Angličtina (Spojené státy). Po aplikaci se změní aktuální jazykovou verzi vlákna na Francouzština (Švýcarsko), pokusí se načíst uložené hodnoty pomocí formátovacích úmluv aktuální jazykové verze. Pokus o čtení dat dvě položky, vyvolá výjimku <xref:System.FormatException> výjimky a pole data nyní obsahuje dva nesprávné elementy, které se rovná <xref:System.DateTime.MinValue>.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
 [!code-vb[Conceptual.Strings.BestPractices#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]  
  
 Ale pokud nahradíte <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost s <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> ve volání do <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> a <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, trvalý datum a čas, data se úspěšně obnovila, jak ukazuje následující výstup.  
  
```  
06.05.1758 21:26  
05.05.1818 07:19  
22.04.1870 23:54  
08.09.1890 06:47  
18.02.1905 15:12  
```  
  
## <a name="see-also"></a>Viz také:

- [Práce s řetězci](../../../docs/standard/base-types/manipulating-strings.md)
