---
title: "Osvědčené postupy pro používání řetězců v .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d187096fee5119a22d886029cd63173e4ca1c8ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="best-practices-for-using-strings-in-net"></a>Osvědčené postupy pro používání řetězců v .NET
<a name="top"></a>.NET poskytuje rozsáhlou podporu pro vývoj lokalizovaných a globálních aplikací a umožňuje snadno použít konvence aktuální jazykové verze nebo konkrétní jazykové verze při provádění běžných operací, jako je například řazení a zobrazování řetězců. Ale řazení a porovnávání řetězců není vždy operace zohledňující jazykovou verzi. Například řetězce, které jsou používány interně aplikaci obvykle zpracování stejně jako všechny jazykové verze. Pokud jazykově nezávislá řetězcová data, jako je například XML značky HTML značky, uživatelská jména, cesty k souborům a názvy objektů systému jsou interpretovány, jako kdyby byly zohledňující jazykovou verzi, může jemně chyb, nízký výkon a v některých případech může být kód aplikace problémy se zabezpečením.  
  
 Toto téma zkoumá řazení řetězce, porovnání a metody velká a malá písmena v rozhraní .NET, uvede doporučení pro výběr odpovídající metody zpracování řetězců a poskytuje další informace o metodách zpracování řetězců. Také zkontroluje jak formátovaných dat, jako je například číselná data a data a času, používá k zobrazení a pro úložiště.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Doporučení pro používání řetězců](#recommendations_for_string_usage)  
  
-   [Určení explicitního porovnávání řetězců](#specifying_string_comparisons_explicitly)  
  
-   [Podrobnosti o porovnání řetězců](#the_details_of_string_comparison)  
  
-   [Výběr člena StringComparison pro vaše volání metody](#choosing_a_stringcomparison_member_for_your_method_call)  
  
-   [Běžné metody porovnávání řetězců v rozhraní .NET](#common_string_comparison_methods_in_the_net_framework)  
  
-   [Metody, které nepřímo provést porovnání řetězců](#methods_that_perform_string_comparison_indirectly)  
  
-   [Zobrazení a zachování formátovaných dat](#Formatted)  
  
<a name="recommendations_for_string_usage"></a>   
## <a name="recommendations-for-string-usage"></a>Doporučení pro používání řetězců  
 Při vývoji v rozhraní .NET postupujte podle následujících jednoduchých doporučení pro používání řetězců:  
  
-   Použijte přetížení, která explicitně zadáte pravidla porovnávání pro operace s řetězci. To obvykle zahrnuje volání přetížení metody, která má parametr typu <xref:System.StringComparison>.  
  
-   Použití <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro porovnání jako výchozí bezpečnou pro porovnávání řetězců bez ohledu na jazykové verzi.  
  
-   Použití porovnávání s <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro dosažení vyššího výkonu.  
  
-   Pomocí operace s řetězci, které jsou založeny na <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> při zobrazení výstupu pro uživatele.  
  
-   Použití jazyce, <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> podle hodnoty místo operace s řetězci <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> po jazykově důležité porovnání (například symbolické).  
  
-   Použití <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> metoda místo <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> metoda při normalizujte řetězce pro porovnání.  
  
-   Použijte přetížení <xref:System.String.Equals%2A?displayProperty=nameWithType> metodu k ověření, zda jsou dva řetězce stejné.  
  
-   Použití <xref:System.String.Compare%2A?displayProperty=nameWithType> a <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody pro řazení řetězců, není pro kontrolu rovnosti.  
  
-   Použijte formátování zohledňující jazykovou verzi pro zobrazení dat jiné než řetězec, například čísel a dat, v uživatelském rozhraní. Formátování s neutrální jazykovou verzi použijte k uchování dat jiné než řetězec ve formátu řetězce.  
  
 Následující postupy předejít, když používáte řetězce:  
  
-   Nepoužívejte přetížení, které explicitně nebo implicitně zadejte pravidla pro porovnávání řetězců pro operace s řetězci.  
  
-   Nepoužívejte na základě operace s řetězci <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> ve většině případů. Jedním z několika výjimkami je, když uchováváte data, která ale jazykově smysluplný.  
  
-   Nepoužívejte přetížení <xref:System.String.Compare%2A?displayProperty=nameWithType> nebo <xref:System.String.CompareTo%2A> metoda a testování návratová hodnota nula. Chcete-li zjistit, zda jsou dva řetězce stejné.  
  
-   Nepoužívejte formátování jazykové udržení číselná data nebo data datum a čas ve formátu řetězce.  
  
 [Zpět na začátek](#top)  
  
<a name="specifying_string_comparisons_explicitly"></a>   
## <a name="specifying-string-comparisons-explicitly"></a>Určení explicitního porovnávání řetězců  
 Většinu metod manipulace s řetězci v .NET jsou přetížený. Jeden nebo více přetížení obvykle přijmout výchozí nastavení, zatímco ostatní přijměte žádné výchozí hodnoty a místo toho definují přesný způsob, kterým jsou porovnávány a s nimi manipulovat, řetězce. Většina z metody, které nespoléhejte na výchozím nastavení zahrnuje parametr typu <xref:System.StringComparison>, které je výčet, který explicitně určuje pravidla pro porovnání řetězců jazykovou verzi a případu. V následující tabulce jsou popsány <xref:System.StringComparison> členy výčtu.  
  
|Člen StringComparison|Popis|  
|-----------------------------|-----------------|  
|<xref:System.StringComparison.CurrentCulture>|Provádí malá a velká písmena porovnání s použitím aktuální jazykové verze.|  
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|Provede porovnávání s využitím aktuální jazykové verze.|  
|<xref:System.StringComparison.InvariantCulture>|Provádí malá a velká písmena porovnání s použitím neutrální jazykovou verzi.|  
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|Provádí velká a malá písmena porovnání s použitím neutrální jazykovou verzi.|  
|<xref:System.StringComparison.Ordinal>|Provede porovnávání podle pořadového čísla.|  
|<xref:System.StringComparison.OrdinalIgnoreCase>|Provede porovnávání řadových číslovek.|  
  
 Například <xref:System.String.IndexOf%2A> metoda, která vrátí index podřetězce v <xref:System.String> objekt, který odpovídá znak nebo řetězec, obsahuje devět přetížení:  
  
-   <xref:System.String.IndexOf%28System.Char%29>, <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29>, a <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>, který ve výchozím nastavení provádí pořadovém místě (malá a velká písmena a na jazykové verzi) vyhledávání znaku v řetězci.  
  
-   <xref:System.String.IndexOf%28System.String%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>, a <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>, který ve výchozím nastavení provádí velká a malá písmena a jazykovou vyhledávání podřetězce v řetězci.  
  
-   <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>, a <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29>, mezi které patří parametr typu <xref:System.StringComparison> umožňuje formu porovnání zadat.  
  
 Doporučujeme vám, že jste vybrali přetížení, které nepoužívá výchozí hodnoty z následujících důvodů:  
  
-   Některé přetížení s výchozí parametry (ty, které hledají <xref:System.Char> v instanci řetězce) provést ordinální porovnávání, zatímco ostatní (ty, které hledají řetězce v instanci řetězce) jsou závislé na jazykové verzi. Je obtížné mějte na paměti, která metoda používá danou výchozí hodnotu a snadno zaměnit přetížení.  
  
-   Záměr kód, který je založen na výchozí hodnoty pro volání metody není jasné. V následujícím příkladu, které závisí na výchozí hodnoty, je obtížné zjistit, zda se na vývojáře ve skutečnosti určené pořadí nebo lingvistické porovnání dvou řetězců nebo zda případu rozdíl mezi `protocol` a "http" může dojít k testování rovnosti Chcete-li vrátit `false`.  
  
     [!code-csharp[Conceptual.Strings.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]  
  
 Obecně doporučujeme volat metodu, která není závislý na výchozí hodnoty, protože umožňuje jednoznačným záměr kódu. Pak díky kód čitelnější a snazší ladit a údržbu. Následující příklad adresy otázky i o předchozí příklad. Umožňuje vymazat to pořadí porovnání se používá a že rozdíly v případě jsou ignorovány.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
 [!code-vb[Conceptual.Strings.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]  
  
 [Zpět na začátek](#top)  
  
<a name="the_details_of_string_comparison"></a>   
## <a name="the-details-of-string-comparison"></a>Podrobnosti o porovnání řetězců  
 Porovnání řetězců jsou srdcem mnoho řetězec operace související, zejména řazení a testování rovnosti. Řazení řetězců v určené pořadí: Pokud "Moje" se zobrazuje před "řetězec" v seřazený seznam řetězců, "my" musí porovnat menší než nebo rovno "řetězec". Kromě toho porovnání implicitně definuje rovnosti. Operace porovnání vrátí pro řetězce, které se považuje za rovné nule. Dobrý výkladu je, že ani řetězec není menší než druhý. Většina smysluplných operací zahrnujících řetězce obsahuje jednu nebo obě tyto postupy: porovnávání s jiným řetězcem a provádění operace dobře definovaný řazení.  
  
 Však vyhodnocení dva řetězce pro rovnosti nebo pořadí řazení nepřinese jeden správný výsledek. Výsledek závisí na kritéria použitá pro porovnání řetězců. Porovnání řetězců, které jsou pořadí nebo které jsou založeny na malá a velká písmena a řazení konvence aktuální jazykové verze nebo neutrální jazykovou verzi (bez ohledu na národním prostředí jazykovou verzi na základě v anglickém jazyce), mohou mít různé výsledky.  
  
<a name="current_culture"></a>   
### <a name="string-comparisons-that-use-the-current-culture"></a>Porovnání řetězců, které používají aktuální jazykové verze  
 Jedno kritérium zahrnuje pomocí konvencí aktuální jazykové verze, pokud porovnávání řetězců. Porovnání, které jsou založeny na aktuální jazykové verze použít aktuální jazykovou verzi vlákna nebo národní prostředí. Pokud jazyková verze není nastavená uživatelem, nastaví se jako výchozí nastavení **místní nastavení** okno v Ovládacích panelech. Vždy byste měli používat porovnání, které jsou založeny na aktuální jazykové verze, když jazykově relevantní data a odráží interakci s uživatelem zohledňující jazykovou verzi.  
  
 Chování při porovnání a velká a malá písmena v rozhraní .NET však změní při změně jazykové verze. To se stane, když je aplikace spuštěna v počítači, který má jinou jazykovou verzi než počítači, na kterém byla vyvinuta aplikace, nebo při změně provádění vlákna jazykové verze. Toto chování je záměrné, ale pořád není zřejmé celá řada vývojářů. Následující příklad ilustruje rozdíly v řazení mezi USA Angličtina ("en US") a švédská jazykové verze ("sv-SE"). Všimněte si, že slova "ångström", "Systém Windows" a "Visual Studio" se objeví na různých místech v polích seřazené řetězec.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
 [!code-vb[Conceptual.Strings.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]  
  
 Porovnávání, které používají aktuální jazykovou verzi jsou stejné jako Porovnání zohledňující jazykovou verzi, s tím rozdílem, že ignorují velikost písmen, protože závisí na aktuální jazykovou verzi vlákna. Toto chování může projevit v také pořadí řazení.  
  
 Porovnání, které používají sémantiku aktuální jazykové verze jsou výchozí hodnoty pro následující metody:  
  
-   <xref:System.String.Compare%2A?displayProperty=nameWithType>přetížení, které neobsahují <xref:System.StringComparison> parametr.  
  
-   <xref:System.String.CompareTo%2A?displayProperty=nameWithType>přetížení.  
  
-   Výchozí hodnota <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> metody a <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda s `null` <xref:System.Globalization.CultureInfo> parametr.  
  
-   Výchozí hodnota <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> metody a <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda s `null` <xref:System.Globalization.CultureInfo> parametr.  
  
-   <xref:System.String.IndexOf%2A?displayProperty=nameWithType>přetížení, které přijímají <xref:System.String> jako vyhledávání parametr a které nemají <xref:System.StringComparison> parametr.  
  
-   <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>přetížení, které přijímají <xref:System.String> jako vyhledávání parametr a které nemají <xref:System.StringComparison> parametr.  
  
 V každém případě doporučujeme volat přetížení, která má <xref:System.StringComparison> parametr, aby byl záměr metody volání zrušte.  
  
 Jemně a méně choulostivé chyby můžou vznikat, když data mimo jazykových řetězce interpretována jazykově, nebo když řetězcovými daty z konkrétní jazykové verze interpretována pomocí konvencí jiné jazykové verze. Kanonický příklad je turečtina-I problém.  
  
 Pro téměř všechny abeced latinky, včetně USA Angličtina, znak "i" (\u0069) je malá verzi znak "I" (\u0049). Toto pravidlo velikosti se výchozí někomu programování v takovéto jazykové verzi. Ale abecedy turečtina ("tr-TR") obsahuje "I s tečkou" znak "İ" (\u0130), což je velká verze z "i". Turečtina také obsahuje znak malá "i bez tečky", "ı" (\u0131), jehož velká "I". K tomuto chování dochází v také culture Ázerbájdžánština (az").  
  
 Proto předpokladům o psaní velkých písmen "i" nebo předpoklady "I" nejsou platné pro všechny jazykové verze. Pokud používáte výchozí přetížení rutin pro porovnávání řetězců, budou se odchylka mezi jazykové verze. Pokud data, která mají být porovnána mimo jazykových, použití výchozích přetížení může způsobit nežádoucí výsledky, protože následující pokus o provedení velká a malá písmena porovnání řetězce "soubor" a "Soubor" znázorňuje.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
 [!code-vb[Conceptual.Strings.BestPractices#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]  
  
 Toto porovnání může způsobit významné problémy, pokud se nastavení citlivé na zabezpečení, jako v následujícím příkladu nechtěně používá jazykovou verzi. Volání metody, jako například `IsFileURI("file:")` vrátí `true` Pokud aktuální jazyková verze Angličtina, ale `false` Pokud turečtinu aktuální jazykovou verzi. Proto v tureckém systémech někdo mohl obejít bezpečnostní opatření, která blokují přístup k velká a malá písmena URI, které začínají řetězcem "souboru:".  
  
 [!code-csharp[Conceptual.Strings.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
 [!code-vb[Conceptual.Strings.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]  
  
 V takovém případě protože "souboru:" je určená interpretovat jako mimo jazykových nezávislé na jazykových identifikátor, kód by měl být zapsán jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
 [!code-vb[Conceptual.Strings.BestPractices#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]  
  
### <a name="ordinal-string-operations"></a>Ordinální operace s řetězci  
 Určení <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> hodnota ve volání metody znamená-lingvistické porovnání, ve kterém jsou ignorovány vlastnosti přirozeného jazyka. Metody, které jsou vyvolány pomocí těchto <xref:System.StringComparison> hodnoty rozhodovat řetězec operaci na porovnání jednotlivých bajtů místo velká a malá písmena nebo ekvivalenční tabulek, které jsou parametry podle jazykové verze. Ve většině případů se tento přístup nejlépe odpovídá zamýšlenému výkladu řetězce při vytváření kódu rychlejší a spolehlivější.  
  
 Ordinální porovnávání jsou porovnání řetězců, ve kterých se porovná každý byte řetězce bez lingvistické interpretace. například "systém windows" neodpovídá "Systém Windows". Toto je v podstatě volání C runtime `strcmp` funkce. Toto porovnání použijte, pokud kontext stanoví, že řetězce by si měly odpovídat přesně nebo požadavků konzervativní odpovídající zásady. Kromě toho porovnávání pořadového čísla je nejrychlejší operace porovnání, protože žádná lingvistické pravidla platí při určování výsledku.  
  
 Řetězců v .NET může obsahovat vložené znaky null. Jedním z nejjednoznačnějším rozdílů mezi pořadí a jazykovou porovnání (včetně porovnání, které používají neutrální jazykovou verzi) se týká zpracování vložené znaky null v řetězci. Tyto znaky jsou ignorovány, při použití <xref:System.String.Compare%2A?displayProperty=nameWithType> a <xref:System.String.Equals%2A?displayProperty=nameWithType> metody k provádění porovnávání zohledňující jazykovou verzi (včetně porovnání, které používají neutrální jazykovou verzi). V důsledku toho v porovnávání jazykovou řetězce, které obsahují vložené znaky null lze považovat za rovna řetězce, které nepodporují.  
  
> [!IMPORTANT]
>  I když metody porovnávání řetězců nezohledňují vložené znaky null, string vyhledávací metody, jako <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.EndsWith%2A?displayProperty=nameWithType>, <xref:System.String.IndexOf%2A?displayProperty=nameWithType>, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>, a <xref:System.String.StartsWith%2A?displayProperty=nameWithType> nepodporují.  
  
 Následující příklad provede porovnání zohledňující jazykovou verzi řetězec "Aa" se podobně jako řetězec, který obsahuje několik vložených znaků null mezi "A" a "a" a ukazuje, jak dva řetězce jsou považovány za shodné.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]  
  
 Ale řetězce nejsou považovány za shodné při použití pořadí porovnání, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
 [!code-vb[Conceptual.Strings.BestPractices#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]  
  
 Porovnávání bez pořadí jsou další nejvíce konzervativní přístup. Tato porovnání ignorovat většina velká a malá písmena; například "systém windows" odpovídá "Systém Windows". Při zpracovávání znaků ASCII, tato zásada je ekvivalentní <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>, s tím rozdílem, že ignorují obvyklé velikosti znaků ASCII. Proto libovolný znak v [A, Z] (\u0041-\u005A) odpovídá odpovídající znaku v [a, z] (\u0061-\007A). Velká a malá písmena mimo rozsah ASCII používá tabulky neutrální jazykovou verzi. Proto na toto porovnání:  
  
 [!code-csharp[Conceptual.Strings.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
 [!code-vb[Conceptual.Strings.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]  
  
 je ekvivalentní (ale rychlejší než) Toto porovnání:  
  
 [!code-csharp[Conceptual.Strings.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
 [!code-vb[Conceptual.Strings.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]  
  
 Tato porovnání jsou stále velmi rychle.  
  
> [!NOTE]
>  Řetězec chování systému souborů, klíčů registru a hodnoty a proměnné prostředí je reprezentována nejlépe <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>.  
  
 Obě <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> a <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> přímo použít binární hodnoty a jsou nejvhodnější pro párování. Pokud si nejste jisti o porovnání nastavení, použijte jednu z těchto dvou hodnot. Ale protože provádějí porovnání bajtové byte, neposkytují řazení lingvistické řazení (například anglický slovník), ale binární řazení. Výsledky vypadat nevhodně ve většině případů, pokud se zobrazí uživatelům.  
  
 Ordinální sémantika je výchozí nastavení pro <xref:System.String.Equals%2A?displayProperty=nameWithType> přetížení, které neobsahují <xref:System.StringComparison> argument (včetně operátor rovnosti). V každém případě doporučujeme volat přetížení, která má <xref:System.StringComparison> parametr.  
  
### <a name="string-operations-that-use-the-invariant-culture"></a>Operace s řetězci, které používají neutrální jazykovou verzi  
 Porovnání s použitím neutrální jazykovou verzi <xref:System.Globalization.CultureInfo.CompareInfo%2A> vlastnost vrácený statických <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost. Toto chování je stejné ve všech systémech. převádí všechny znaky mimo daný rozsah na které považuje za odpovídající invariantní znaky. Tato zásada může být užitečná pro údržbu jednu sadu řetězec chování napříč jazykové verze, ale často poskytuje neočekávané výsledky.  
  
 Porovnávání s neutrální jazykovou verzi používá statickou <xref:System.Globalization.CultureInfo.CompareInfo%2A> vlastnost vrácený statických <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost pro informace o porovnávání. Případné případu rozdíly mezi těmito přeloženými znaky jsou ignorovány.  
  
 Porovnání, které používají <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> a <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> pracovní stejně jako u řetězců ASCII. Ale <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> uskutečňuje lingvistické rozhodnutí, která nemusí být vhodné pro řetězce, které mají být interpretovat jako sada bajtů. `CultureInfo.InvariantCulture.CompareInfo` Objektu díky <xref:System.String.Compare%2A> metoda interpretovat určité sady znaků jako ekvivalentní. Například následující ekvivalence je platný v rámci neutrální jazykovou verzi:  
  
 InvariantCulture: + ̊ =  
  
 LATINSKÁ malé písmeno A znak "(\u0061), pokud je vedle KOMBINOVÁNÍ PRSTENEC výše znak" + "̊" (\u030a), se interpretují jako LATIN malé písmeno A s PRSTENEC výše znak "å" (\u00e5). Jak ukazuje následující příklad, toto chování se liší od pořadí porovnání.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
 [!code-vb[Conceptual.Strings.BestPractices#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]  
  
 Při interpretaci názvy souborů, soubory cookie nebo cokoliv jiného, kde se může vyskytovat kombinaci jako je například "å", pořadí porovnání stále nabízí nejvíce transparentní a nejvhodnější chování.  
  
 Neutrální jazykovou verzi na balance, má jen několik vlastností, které jsou užitečné pro porovnání. Provede porovnání jazykově relevantním způsobem, který zabraňuje v jeho zaručení plné ekvivalence, ale není volbou pro zobrazení v libovolné jazykové verzi. Jedním z několika důvodů používat <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> pro porovnání je zachování seřazených dat pro ve všech jazykových verzích stejné zobrazení. Například pokud soubor velkého množství dat, který obsahuje seznam seřazený identifikátory pro zobrazení doprovází aplikace, přidání do tohoto seznamu vyžadovat vložení pomocí stylu neutrální řazení.  
  
 [Zpět na začátek](#top)  
  
<a name="choosing_a_stringcomparison_member_for_your_method_call"></a>   
## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Výběr člena StringComparison pro vaše volání metody  
 Následující tabulka popisuje mapování ze sémantického kontext, který má <xref:System.StringComparison> – člen výčtu.  
  
|Data|Chování|Odpovídající System.StringComparison<br /><br /> value|  
|----------|--------------|-----------------------------------------------------|  
|Interní identifikátory malá a velká písmena.<br /><br /> Malá a velká písmena identifikátory v standardy, jako je soubor XML a HTTP.<br /><br /> Malá a velká písmena nastavení související se zabezpečením.|Identifikátor jazyce, kde se přesně shodují bajtů.|<xref:System.StringComparison.Ordinal>|  
|Interní identifikátory velká a malá písmena.<br /><br /> Velká a malá písmena identifikátory v standardy, jako je soubor XML a HTTP.<br /><br /> Cesty k souborům.<br /><br /> Klíče registru a hodnoty.<br /><br /> Proměnné prostředí.<br /><br /> Identifikátory prostředků (například názvy popisovač).<br /><br /> Velká a malá písmena nastavení související se zabezpečením.|Identifikátor mimo jazykových, kde je případ důležité; zejména data uložená v většina služeb systému Windows.|<xref:System.StringComparison.OrdinalIgnoreCase>|  
|Některé trvalé, jazykově relevantní data.<br /><br /> Zobrazení lingvistické data, která vyžaduje pevnou řazení.|Která data, která je jazykově relevantní.|<xref:System.StringComparison.InvariantCulture><br /><br /> -nebo-<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|  
|Data zobrazená pro uživatele.<br /><br /> Většina vstupu uživatele.|Data, která vyžaduje místní lingvistické.|<xref:System.StringComparison.CurrentCulture><br /><br /> -nebo-<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|  
  
 [Zpět na začátek](#top)  
  
<a name="common_string_comparison_methods_in_the_net_framework"></a>   
## <a name="common-string-comparison-methods-in-net"></a>Běžné metody porovnávání řetězců v rozhraní .NET  
 Následující části popisují metody, které se běžně používají pro porovnání řetězců.  
  
### <a name="stringcompare"></a>String.Compare  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Jako operace nejvíce zaměřují na interpretaci řetězce by měl všech instancí těchto volání metod prověřit, abyste zjistili, jestli řetězců by měla být interpretovat v souladu aktuální jazykové verze, nebo zrušit její přidružení z jazykové verze (symbolicky). Obvykle je k tomu a <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> porovnání by měl být místo toho použít.  
  
 <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> Třídy, která je vrácený <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> také obsahuje vlastnosti, <xref:System.Globalization.CompareInfo.Compare%2A> metoda, která poskytuje velký počet odpovídajících možnosti (pořadí, ignoruje prázdné znaky, znaky abeced kana bude ignorována typ a tak dále) prostřednictvím <xref:System.Globalization.CompareOptions> příznak výčet.  
  
### <a name="stringcompareto"></a>String.CompareTo  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Tato metoda aktuálně nenabízí přetížení, které určuje <xref:System.StringComparison> typu. Obvykle je možné převést tuto metodu doporučené <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> formuláře.  
  
 Typy, které implementují <xref:System.IComparable> a <xref:System.IComparable%601> tuto metodu implementovat rozhraní. Protože nenabízí možnost <xref:System.StringComparison> parametr typy implementace často umožní uživateli zadat <xref:System.StringComparer> v jejich konstruktoru. V následujícím příkladu definuje `FileName` třídy, jejichž konstruktor třídy zahrnuje <xref:System.StringComparer> parametr. To <xref:System.StringComparer> objekt je pak použit v `FileName.CompareTo` metoda.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
 [!code-vb[Conceptual.Strings.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]  
  
### <a name="stringequals"></a>String.Equals  
 Výchozí interpretaci: <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.  
  
 <xref:System.String> Třída umožňuje testovat rovnost voláním buď statického nebo instanci <xref:System.String.Equals%2A> přetížení metody, nebo pomocí statického operátoru rovnosti. Ve výchozím nastavení používá přetížení a operátor porovnání pořadí. Však doporučujeme volat přetížení, které explicitně určuje <xref:System.StringComparison> typ i v případě, že chcete provést porovnávání podle pořadového čísla; to usnadňuje vyhledávání kódu pro určitých interpretací řetězce.  
  
### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper a String.ToLower  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Byste měli být opatrní při používání těchto metod, protože vynucení řetězce na velká nebo malá se často používá jako malá normalizace pro porovnávání řetězců bez ohledu na případ. Pokud ano, zvažte použití porovnávání.  
  
 <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> a <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> metody jsou také k dispozici. <xref:System.String.ToUpperInvariant%2A>je standardní způsob, jak normalizování velikosti písmen. Porovnání pomocí <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> jsou složení dvou volání: volání metody <xref:System.String.ToUpperInvariant%2A> na oba argumenty řetězce a provedení porovnání s použitím <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.  
  
 Přetížení jsou také k dispozici pro převod na velká a malá písmena v konkrétní jazykové verzi, předáním <xref:System.Globalization.CultureInfo> objekt, který představuje tuto jazykovou verzi metodě.  
  
### <a name="chartoupper-and-chartolower"></a>Char.ToUpper a Char.ToLower  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Tyto metody fungují podobně jako <xref:System.String.ToUpper%2A?displayProperty=nameWithType> a <xref:System.String.ToLower%2A?displayProperty=nameWithType> metody popsané v předchozí části.  
  
### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith a String.EndsWith  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Ve výchozím nastavení proveďte obě tyto metody porovnání zohledňující jazykovou verzi.  
  
### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf a String.LastIndexOf  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Není k dispozici souvisí s nedostatečnou konzistencí v tom, jak výchozí přetížení těchto metod provést porovnání. Všechny <xref:System.String.IndexOf%2A?displayProperty=nameWithType> a <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> metody, které zahrnují <xref:System.Char> parametr provést ordinální porovnávání, ale výchozí <xref:System.String.IndexOf%2A?displayProperty=nameWithType> a <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> metody, které zahrnují <xref:System.String> parametr provést zohledňující jazykovou verzi porovnání.  
  
 Při volání <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> nebo <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> metoda a předejte ji řetězec pro vyhledání v aktuální instanci, doporučujeme volat přetížení, které explicitně určuje <xref:System.StringComparison> typu. Přetížení, které obsahují <xref:System.Char> argument neumožňuje zadat <xref:System.StringComparison> typu.  
  
 [Zpět na začátek](#top)  
  
<a name="methods_that_perform_string_comparison_indirectly"></a>   
## <a name="methods-that-perform-string-comparison-indirectly"></a>Metody, které nepřímo provést porovnání řetězců  
 Některé metody jiné než řetězec, které mají porovnávání řetězců jako centrální operaci používají <xref:System.StringComparer> typu. <xref:System.StringComparer> Třída obsahuje šest statické vlastnosti, které vracejí <xref:System.StringComparer> instance, jehož <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> metody provést následující typy porovnávání řetězců:  
  
-   Porovnání řetězců pomocí aktuální jazykové verze. To <xref:System.StringComparer> objekt je vrácen rutinou <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType> vlastnost.  
  
-   Porovnávání s využitím aktuální jazykové verze. To <xref:System.StringComparer> objekt je vrácen rutinou <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType> vlastnost.  
  
-   Nezávislé na jazykových porovnání pomocí pravidel porovnávání slov neutrální jazykovou verzi. To <xref:System.StringComparer> objekt je vrácen rutinou <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType> vlastnost.  
  
-   Porovnání velká a malá písmena a nezávislé na jazykových pomocí pravidel porovnávání slov neutrální jazykovou verzi. To <xref:System.StringComparer> objekt je vrácen rutinou <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType> vlastnost.  
  
-   Porovnání podle pořadového čísla. To <xref:System.StringComparer> objekt je vrácen rutinou <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType> vlastnost.  
  
-   Porovnávání řadových číslovek. To <xref:System.StringComparer> objekt je vrácen rutinou <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> vlastnost.  
  
### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort a Array.BinarySearch  
 Výchozí interpretaci: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.  
  
 Při ukládání dat v kolekci nebo číst trvalou data ze souboru nebo databáze do kolekce, mohou zneplatnit přepínání aktuální jazykové verze výstupních podmínek v kolekci. <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> Metoda předpokládá, že jsou již seřazeny prvků v poli má proběhnout. Seřadit libovolný prvek řetězce v poli <xref:System.Array.Sort%2A?displayProperty=nameWithType> volání metod <xref:System.String.Compare%2A?displayProperty=nameWithType> metoda pořadí jednotlivých prvků. Pomocí porovnávače zohledňující jazykovou verzi může být nebezpečné, pokud budou prohledávány jazykovou verzi změny mezi časem seřazených pole a její obsah. Například následující kód, ukládání a načítání pracovat porovnávače, která je k dispozici implicitně `Thread.CurrentThread.CurrentCulture` vlastnost. Pokud jazykovou verzi můžete změnit mezi voláním `StoreNames` a `DoesNameExist`, a zejména v případě, že je obsah pole trvalý někde mezi volání dvě metody, binární vyhledávání se pravděpodobně nezdaří.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]  
  
 V následujícím příkladu, který používá stejnou metodu pořadí (na jazykové verzi) porovnání řazení a hledání pole se zobrazí doporučená variace. Změna kódu se projeví na řádcích označených `Line A` a `Line B` v obou příkladech.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
 [!code-vb[Conceptual.Strings.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]  
  
 Pokud tato data je trvalá a přesunuta mezi jazykové verze, a řazení se používá k zobrazení těchto dat uživatele, můžete zvážit použití <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>, který funguje jazykově pro lepší uživatelský výstup, ale je ovlivněna změnami v jazykovou verzi. Následující příklad změní dva předchozí příklady použití neutrální jazykovou verzi pro řazení a vyhledávání pole.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
 [!code-vb[Conceptual.Strings.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]  
  
### <a name="collections-example-hashtable-constructor"></a>Příklad kolekcí: konstruktor zatřiďovací tabulky  
 Řetězce hash poskytují v druhém příkladu operace, která je ovlivněna způsobem ve kterém jsou porovnávány řetězce.  
  
 Následující příklad vytvoří <xref:System.Collections.Hashtable> objekt předáním ho <xref:System.StringComparer> objekt, který je vrácený <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> vlastnost. Protože třída <xref:System.StringComparer> je odvozena z <xref:System.StringComparer> implementuje <xref:System.Collections.IEqualityComparer> rozhraní, jeho <xref:System.Collections.IEqualityComparer.GetHashCode%2A> metoda se používá k výpočtu hash řetězců v zatřiďovací tabulce.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
 [!code-vb[Conceptual.Strings.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]  
  
 [Zpět na začátek](#top)  
  
<a name="Formatted"></a>   
## <a name="displaying-and-persisting-formatted-data"></a>Zobrazení a uchování formátovaných dat  
 Pokud má uživatelům zobrazit jiné než řetězec data, jako jsou čísla a data a časy, formátu je pomocí nastavení jazykové verze uživatele. Ve výchozím nastavení <xref:System.String.Format%2A?displayProperty=nameWithType> metoda a `ToString` metody číselnými typy a typy data a času použít pro formátování operations jazykové verze aktuálního vlákna. K explicitnímu zadání že formátování metoda by měla používat aktuální jazykovou verzi, můžete volat přetížení formátování metodu, která má `provider` parametr, například <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> nebo <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType>, možností a předejte ji <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost.  
  
 Jiné než řetězec dat můžete zachovat jako binární data, nebo jako formátovaná data. Pokud zvolíte možnost Uložit jako formátovaných dat, by měly volat formátování přetížení metody, která zahrnuje `provider` parametr a předejte ji <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost. Neutrální jazykovou verzi poskytuje konzistentní formát pro formátovaných dat, která je nezávislá jazykovou verzi a počítače. Naproti tomu zachování dat, který je naformátovaný pomocí jazykové verze než neutrální jazykovou verzi má několik omezení:  
  
-   Data jsou pravděpodobně nebude možné použít, pokud načtením v systému, který má jinou jazykovou verzi, nebo pokud je uživatel v aktuálním systému změní aktuální jazykovou verzi a pokusí se načíst data.  
  
-   Vlastnosti culture na konkrétním počítači se může lišit od standardních hodnot. Kdykoli může uživatel přizpůsobit zobrazení jazykové nastavení. Z toho důvodu formátovaných dat, který je uložený v systému nemusí být po čitelné uživatel upravuje nastavení jazykové verze. Přenositelnost formátovaných dat mezi počítači je pravděpodobně i omezenější.  
  
-   Mezinárodní, regionální nebo národní standardy, které řídí formátování čísel nebo data a časy časem změnit a tyto změny jsou součástí aktualizací operačního systému Windows. Při změně konvence formátování, může přestat data, která byla formátována pomocí předchozí konvence nečitelná.  
  
 Následující příklad ilustruje omezenou přenositelnost, která je výsledkem použití formátování jazykové uchovávat data. Příklad uloží do souboru pole hodnoty data a času. Tyto jsou formátovaná pomocí konvencí jazykové verze Angličtina (Spojené státy). Po aplikaci změní jazykové verze aktuálního vlákna francouzština (Švýcarska), se pokusí načíst uložené hodnoty pomocí konvencí formátování aktuální jazykovou verzi. Pokus o čtení dat dvě položky vyvolává <xref:System.FormatException> výjimka a pole data teď obsahuje dvě nesprávné prvky, které se rovnají <xref:System.DateTime.MinValue>.  
  
 [!code-csharp[Conceptual.Strings.BestPractices#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
 [!code-vb[Conceptual.Strings.BestPractices#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]  
  
 Ale pokud nahradíte <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnost s <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> v volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> a <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, trvalou datum a čas data úspěšně obnovena, jak ukazuje následující výstup.  
  
```  
06.05.1758 21:26  
05.05.1818 07:19  
22.04.1870 23:54  
08.09.1890 06:47  
18.02.1905 15:12  
```  
  
## <a name="see-also"></a>Viz také  
 [Manipulace s řetězci](../../../docs/standard/base-types/manipulating-strings.md)
