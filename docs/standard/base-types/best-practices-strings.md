---
title: Osvědčené postupy pro používání řetězců v .NET
description: Naučte se efektivně používat řetězce v aplikacích .NET.
ms.date: 05/01/2019
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
ms.openlocfilehash: c88776ea9d8ba17d86767b704e8b0eaff5b6cb89
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711477"
---
# <a name="best-practices-for-using-strings-in-net"></a>Osvědčené postupy pro používání řetězců v .NET

Rozhraní .NET poskytuje rozsáhlou podporu pro vývoj lokalizovaných a globálních aplikací a usnadňuje použití konvencí pro aktuální jazykovou verzi nebo specifickou jazykovou verzi při provádění běžných operací, jako je například řazení a zobrazování řetězců. Ale řazení nebo porovnávání řetězců není vždy operace zohledňující jazykovou verzi. Například řetězce, které jsou používány interně aplikací, obvykle by měly být zpracovávány stejným způsobem napříč všemi kulturami. V případě, že jazykově nezávislá řetězcová data, jako jsou značky XML, značky HTML, uživatelská jména, cesty k souborům a názvy systémových objektů, jsou interpretovány, jako kdyby byly závislé na jazykové verzi, může být kód aplikace předmětem drobných chyb, sníženého výkonu a, v některých případech problémy se zabezpečením.

Toto téma prověřuje řazení, porovnávání a způsoby používání velkých a malých písmen v rozhraní .NET, prezentuje doporučení pro výběr vhodné metody zpracování řetězců a poskytuje další informace o metodách zpracování řetězců. Kontroluje také, jak jsou formátovaná data, jako jsou číselná data a data a časová data, zpracovaná pro zobrazení a pro úložiště.

## <a name="recommendations-for-string-usage"></a>Doporučení pro použití řetězců

Při vývoji v rozhraní .NET použijte Tato jednoduchá doporučení při použití řetězců:

- Použijte přetížení, která explicitně určují pravidla porovnávání řetězců pro operace s řetězci. Obvykle to zahrnuje volání přetížení metody, která má parametr typu <xref:System.StringComparison>.
- Použijte <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro porovnávání jako výchozí hodnotu pro porovnávání řetězců jazykové verze nezávislá.
- Pro lepší výkon použijte porovnání s <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>.
- Použijte operace s řetězci, které jsou založeny na <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> při zobrazení výstupu uživateli.
- Použijte nelingvistické <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> hodnoty namísto řetězcové operace na základě <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>, pokud je porovnávání lingvisticky irelevantní (například).
- Použijte metodu <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> namísto metody <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType>, pokud normalizete řetězce pro porovnání.
- Použijte přetížení metody <xref:System.String.Equals%2A?displayProperty=nameWithType> k otestování, zda jsou dva řetězce stejné.
- Použijte metody <xref:System.String.Compare%2A?displayProperty=nameWithType> a <xref:System.String.CompareTo%2A?displayProperty=nameWithType> k řazení řetězců, nikoli ke kontrole rovnosti.
- Použijte formátování zohledňující jazykovou verzi pro zobrazení neřetězcových dat, jako jsou čísla a kalendářní data, v uživatelském rozhraní. Použijte formátování s [neutrální jazykovou verzí](xref:System.Globalization.CultureInfo.InvariantCulture) pro zachování dat, která nejsou řetězcová ve formě řetězce.

Při použití řetězců se vyhnete následujícím postupům:

- Nepoužívejte přetížení, která explicitně nebo implicitně neurčují pravidla porovnávání řetězců pro řetězcové operace.
- Nepoužívejte operace s řetězci na základě <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> ve většině případů. Jednou z několika výjimek je, když uchováváte lingvisticky smysluplná, ale kulturní nezávislá data.
- Nepoužívejte přetížení metody <xref:System.String.Compare%2A?displayProperty=nameWithType> nebo <xref:System.String.CompareTo%2A> a testujte návratovou hodnotu nula, aby bylo možné určit, zda jsou dva řetězce stejné.
- Nepoužívejte formátování zohledňující jazykovou verzi k uchovávání číselných dat nebo data a času ve formě řetězce.

## <a name="specifying-string-comparisons-explicitly"></a>Explicitní určení porovnávání řetězců

Většina metod manipulace s řetězci v rozhraní .NET je přetížena. Obvykle jedno nebo více přetížení akceptuje výchozí nastavení, zatímco ostatní nepřijímají žádné výchozí hodnoty a místo toho definují přesný způsob, jakým mají být řetězce porovnány nebo manipulovány. Většina metod, které nezávisí na výchozích hodnotách, zahrnuje parametr typu <xref:System.StringComparison>, což je výčet, který explicitně určuje pravidla pro porovnání řetězců podle jazykové verze a případu. Následující tabulka popisuje <xref:System.StringComparison> členů výčtu.

|Člen StringComparison|Popis|
|-----------------------------|-----------------|
|<xref:System.StringComparison.CurrentCulture>|Provede porovnání rozlišující velká a malá písmena pomocí aktuální jazykové verze.|
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|Provede porovnávání bez rozlišení velkých a malých písmen pomocí aktuální jazykové verze.|
|<xref:System.StringComparison.InvariantCulture>|Provádí porovnání rozlišující velká a malá písmena pomocí neutrální jazykové verze.|
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|Provede porovnávání bez rozlišení velkých a malých písmen pomocí neutrální jazykové verze.|
|<xref:System.StringComparison.Ordinal>|Provede ordinální porovnávání.|
|<xref:System.StringComparison.OrdinalIgnoreCase>|Provede ordinální porovnávání bez rozlišení velkých a malých písmen.|

Například metoda <xref:System.String.IndexOf%2A>, která vrací index podřetězce v objektu <xref:System.String>, který odpovídá znaku nebo řetězci, má devět přetížení:

- <xref:System.String.IndexOf%28System.Char%29>, <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29>a <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>, které ve výchozím nastavení provádějí hledání znaku v řetězci pomocí pořadí (rozlišuje velká a malá písmena a nezávislá na jazykové verzi).
- <xref:System.String.IndexOf%28System.String%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>a <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>, které ve výchozím nastavení provádějí hledání podřetězce v řetězci závislého na velikosti písmen a jazykové verzi.
- <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>a <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29>, které obsahují parametr typu <xref:System.StringComparison>, který umožňuje určení formuláře porovnání.

Doporučujeme, abyste vybrali přetížení, které nepoužívá výchozí hodnoty, z následujících důvodů:

- Některá přetížení s výchozími parametry (ta, která hledají <xref:System.Char> v instanci řetězce) provádějí ordinální porovnávání, zatímco ostatní (ty, které hledají řetězec v instanci řetězce), jsou závislé na jazykové verzi. Je obtížné si pamatovat si, kterou metodu používá tuto výchozí hodnotu a snadno Zaměňujte přetížení.
- Záměr kódu, který závisí na výchozích hodnotách pro volání metody, není jasný. V následujícím příkladu, který závisí na výchozích hodnotách, je obtížné zjistit, zda vývojář skutečně určil ordinální nebo jazykové porovnání dvou řetězců nebo zda rozdíl mezi `protocol` a "http" může způsobit, že test rovnosti vrátí `false`.

     [!code-csharp[Conceptual.Strings.BestPractices#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]

Obecně doporučujeme, abyste volali metodu, která nespoléhá na výchozí hodnoty, protože způsobuje nejednoznačný záměr kódu. To zase usnadňuje čtení kódu a jeho snadnějšímu ladění a údržbě. Následující příklad řeší otázky vyvolané předchozím příkladem. Je tak jasné, že se používá ordinální porovnávání a že rozdíly v případě jsou ignorovány.

[!code-csharp[Conceptual.Strings.BestPractices#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
[!code-vb[Conceptual.Strings.BestPractices#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]

## <a name="the-details-of-string-comparison"></a>Podrobnosti porovnání řetězců

Porovnání řetězců je srdcem mnoha operací souvisejících s řetězci, zejména pro řazení a testování rovnosti. Řetězce se řadí ve stanoveném pořadí: Pokud je "my" zobrazen před řetězcem v setříděném seznamu řetězců, "my" musí porovnat méně než nebo se rovnat "String". Kromě toho porovnání implicitně definuje rovnost. Operace porovnání vrátí nulu pro řetězce, které považuje za shodné. Dobrým výkladem je, že žádný řetězec není menší než druhý. Mezi smysluplné operace zahrnující řetězce patří jeden nebo oba tyto postupy: porovnání s jiným řetězcem a provádění dobře definované operace řazení.

> [!NOTE]
> Můžete si stáhnout [tabulky váhy řazení](https://www.microsoft.com/download/details.aspx?id=10921), sadu textových souborů, které obsahují informace o váhu znaků používaných při operacích řazení a porovnávání pro operační systémy Windows, a [výchozí tabulku prvků kolace sady Unicode](https://www.unicode.org/Public/UCA/latest/allkeys.txt), nejnovější verzi tabulky váhy řazení pro Linux a MacOS. Konkrétní verze tabulky váhy řazení v systému Linux a macOS závisí na verzi [mezinárodní komponenty pro knihovny Unicode](http://site.icu-project.org/) nainstalované v systému. Informace o verzích ICU a verzích Unicode, které implementují, najdete v tématu [stažení ICU](http://site.icu-project.org/download).

Vyhodnocování dvou řetězců pro rovnost nebo řazení ale nepřinese jediný správný výsledek; výsledek závisí na kritériích použitých k porovnání řetězců. Konkrétně porovnávání řetězců, které jsou ordinální nebo které jsou založeny na velikosti písmen a řazení aktuální jazykové verze nebo [invariantní jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture) (jazyková verze nezávislá na základě anglického jazyka), mohou způsobit různé výsledky.

Kromě toho porovnávání řetězců pomocí různých verzí rozhraní .NET nebo použití rozhraní .NET v různých operačních systémech nebo verzích operačního systému může vracet různé výsledky. Další informace najdete v tématu [řetězce a Standard Unicode](xref:System.String#Unicode).

### <a name="string-comparisons-that-use-the-current-culture"></a>Porovnávání řetězců, které používají aktuální jazykovou verzi

Jedno kritérium zahrnuje použití konvencí aktuální jazykové verze při porovnávání řetězců. Porovnání, která jsou založena na aktuální jazykové verzi, používají aktuální jazykovou verzi nebo národní prostředí vlákna. Pokud není jazyková verze nastavená uživatelem, použije se výchozí nastavení v okně **místní možnosti** v Ovládacích panelech. Vždy byste měli používat porovnávání, které jsou založeny na aktuální jazykové verzi, pokud jsou data lingvisticky relevantní a když odráží interakci uživatele zohledňující jazykovou verzi.

Nicméně porovnávání a chování velkých a malých písmen v rozhraní .NET se změní, když se změní jazyková verze. K tomu dochází, když aplikace běží na počítači, který má jinou jazykovou verzi než počítač, ve kterém byla aplikace vyvinutá, nebo když vykonávající vlákno změní svou jazykovou verzi. Toto chování je záměrné, ale zůstává Nezřejmé pro mnoho vývojářů. Následující příklad znázorňuje rozdíly v pořadí řazení mezi kulturami americké angličtiny ("en-US") a švédštinou ("sv-SE"). Všimněte si, že slova "Ångström", "Windows" a "Visual Studio" se zobrazí v různých umístěních v setříděných řetězcích polí.

[!code-csharp[Conceptual.Strings.BestPractices#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
[!code-vb[Conceptual.Strings.BestPractices#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]

Porovnávání bez rozlišení velkých a malých písmen, která používají aktuální jazykovou verzi, jsou stejná jako porovnávání zohledňující jazykovou verzi, s tím rozdílem, že ignorují případ, jak je uvedeno v aktuální jazykové verzi vlákna. Toto chování se může projevit také v pořadí řazení.

Porovnávání, které používají sémantiku aktuální jazykové verze, je výchozí pro následující metody:

- <xref:System.String.Compare%2A?displayProperty=nameWithType> přetížení, které neobsahují parametr <xref:System.StringComparison>.
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType> přetížení.
- Výchozí metoda <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> a metoda <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> s parametrem `null`<xref:System.Globalization.CultureInfo>.
- Výchozí metoda <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> a metoda <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> s parametrem `null`<xref:System.Globalization.CultureInfo>.
- <xref:System.String.IndexOf%2A?displayProperty=nameWithType> přetížení, které přijímají <xref:System.String> jako vyhledávací parametr a které nemají parametr <xref:System.StringComparison>.
- <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> přetížení, které přijímají <xref:System.String> jako vyhledávací parametr a které nemají parametr <xref:System.StringComparison>.

V každém případě doporučujeme, abyste volali přetížení, které má parametr <xref:System.StringComparison> k tomu, aby byl záměr volání metody jasný.

Jemné a nestandardní chyby mohou být vyhodnoceny, pokud jsou nelingvistická data řetězců interpretována lingvisticky nebo když jsou řetězcová data z konkrétní jazykové verze interpretována pomocí konvencí jiné jazykové verze. Kanonický příklad je problém v turečtině.

U téměř všech abeced, včetně americké angličtiny, je znak "i" (\u0069) malými verzemi znaku "I" (\u0049). Toto pravidlo pro velká písmena se rychle nastaví jako výchozí pro někoho, kdo v takové jazykové verzi používá program. Turecká abeceda ("tr-TR") ale obsahuje znak "i s tečkou" (\u0130), což je Velká verze "i". Turečtina obsahuje také malé písmeno "i bez tečky", "ı" (\u0131), které se změní na I. K tomuto chování dochází také v rámci jazykové verze Ázerbájdžánština (AZ).

Proto nejsou předpoklady pro písmena "i" nebo lowercasing "I" platné mezi všemi kulturami. Použijete-li výchozí přetížení pro rutiny porovnávání řetězců, budou předmětem odchylky mezi kulturami. Pokud se data, která mají být porovnána, nelingvistická, může použití výchozích přetížení způsobit nežádoucí výsledky, protože následující pokus o provedení porovnání řetězců "File" a "FILE" v řetězci nerozlišuje malá a velká písmena.

[!code-csharp[Conceptual.Strings.BestPractices#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
[!code-vb[Conceptual.Strings.BestPractices#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]

Toto porovnání může způsobit významné problémy, pokud je jazyková verze neúmyslně používána v nastavení citlivém na zabezpečení, jak je uvedeno v následujícím příkladu. Volání metody, jako je `IsFileURI("file:")`, vrátí `true`, pokud je aktuální jazyková verze U.S. English, ale `false`, pokud je aktuální jazyková verze Tureck. V tureckých systémech by proto někdo mohl obejít bezpečnostní opatření, která blokují přístup k identifikátorům URI bez rozlišení velkých a malých písmen, která začínají na "soubor:".

[!code-csharp[Conceptual.Strings.BestPractices#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
[!code-vb[Conceptual.Strings.BestPractices#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]

V tomto případě, vzhledem k tomu, že "File:" je určeno pro interpretaci jako nelingvistické, nezávisle na jazykové verzi, by měl být kód zapsán, jak je znázorněno v následujícím příkladu:

[!code-csharp[Conceptual.Strings.BestPractices#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
[!code-vb[Conceptual.Strings.BestPractices#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]

### <a name="ordinal-string-operations"></a>Ordinální operace s řetězci

Zadání <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> hodnoty ve volání metody znamená nelingvistické porovnání, ve kterém jsou funkce přirozeného jazyka ignorovány. Metody, které jsou vyvolány pomocí těchto <xref:System.StringComparison> hodnoty základního řetězce operací na základě jednoduchých porovnávání bajtů místo tabulek s velikostí písmen nebo rovnocenných dat, které jsou parametrizované podle jazykové verze. Ve většině případů tento přístup nejlépe odpovídá zamýšlené interpretaci řetězců při rychlejším a spolehlivější provádění kódu.

Ordinální porovnávání jsou porovnávání řetězců, ve kterém každý bajt každého řetězce je porovnán bez jazykového výkladu; například "Windows" neodpovídá "Windows". To je v podstatě volání funkce `strcmp` modulu runtime jazyka C. Toto porovnání použijte, pokud kontext určuje, že by se řetězce měly odpovídat přesně, nebo vyžaduje zásadu vyhovující shodě. Kromě toho je ordinální porovnávání nejrychlejší operace porovnání, protože při určování výsledku nepoužívá žádná jazyková pravidla.

Řetězce v rozhraní .NET můžou obsahovat vložené znaky null. Jeden z jasných rozdílů mezi ordinálním a závislým porovnáním (včetně porovnávání, které používají invariantní jazykovou verzi) se týká zpracování vložených znaků null v řetězci. Tyto znaky jsou ignorovány, pokud použijete metody <xref:System.String.Compare%2A?displayProperty=nameWithType> a <xref:System.String.Equals%2A?displayProperty=nameWithType> k provedení porovnávání závislých na jazykové verzi (včetně porovnávání, která používají invariantní jazykovou verzi). V důsledku toho se v porovnání zohledňující jazykovou verzi mohou řetězce, které obsahují vložené znaky null, považovat za shodné s řetězci, které ne.

> [!IMPORTANT]
> I když metody porovnání řetězců ignorují vložené znaky null, metody vyhledávání řetězců, jako je například <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.EndsWith%2A?displayProperty=nameWithType>, <xref:System.String.IndexOf%2A?displayProperty=nameWithType>, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>a <xref:System.String.StartsWith%2A?displayProperty=nameWithType> ne.

Následující příklad provádí porovnání zohledňující jazykovou verzi řetězce "AA" s podobným řetězcem, který obsahuje několik vložených znaků null mezi "A" a "a" a ukazuje, jak se tyto dva řetězce považují za rovné:

[!code-csharp[Conceptual.Strings.BestPractices#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]

Nicméně řetězce nejsou považovány za stejné při použití ordinálního porovnání, jak ukazuje následující příklad:
  
[!code-csharp[Conceptual.Strings.BestPractices#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
[!code-vb[Conceptual.Strings.BestPractices#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]

Ordinální porovnávání bez rozlišování velkých a malých písmen je další největší konzervativní přístup. Tato porovnávání ignorují většinu velkých a malých písmen. například "Windows" odpovídá "Windows". Při práci se znaky ASCII je tato zásada ekvivalentní <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>, s tím rozdílem, že ignoruje obvyklé velikosti ASCII. Proto jakýkoli znak v [A, Z] (\u0041-\u005A) odpovídá odpovídajícímu znaku v [a, z] (\u0061-\007A). Velikost písmen mimo rozsah ASCII používá tabulky invariantní jazykové verze. Proto následující porovnání:

[!code-csharp[Conceptual.Strings.BestPractices#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
[!code-vb[Conceptual.Strings.BestPractices#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]

je ekvivalentem (ale rychlejší než) Toto porovnání:

[!code-csharp[Conceptual.Strings.BestPractices#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
[!code-vb[Conceptual.Strings.BestPractices#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]

Tato porovnání jsou stále velmi rychlá.

> [!NOTE]
> Chování řetězce systému souborů, klíčů a hodnot registru a proměnných prostředí je nejlépe reprezentované <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>.

<xref:System.StringComparison.Ordinal?displayProperty=nameWithType> i <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> používají binární hodnoty přímo a jsou nejvhodnější pro porovnání. Pokud si nejste jisti nastavením porovnávání, použijte jednu z těchto dvou hodnot. Vzhledem k tomu, že provádí porovnání po bajtech, neprovádí řazení podle jazykového řazení (například anglického slovníku), ale binárním pořadím řazení. V případě, že se zobrazí uživatelům, mohou výsledky vypadat v nejlichých kontextech.

Ordinální sémantika je výchozím nastavením pro <xref:System.String.Equals%2A?displayProperty=nameWithType> přetížení, které nezahrnují <xref:System.StringComparison> argument (včetně operátoru rovnosti). V každém případě doporučujeme volat přetížení, které má parametr <xref:System.StringComparison>.

### <a name="string-operations-that-use-the-invariant-culture"></a>operace s řetězci, které používají invariantní jazykovou verzi

Porovnání s invariantní jazykové verze používají vlastnost <xref:System.Globalization.CultureInfo.CompareInfo%2A> vrácenou vlastností static <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Toto chování je stejné ve všech systémech. převádí všechny znaky mimo svůj rozsah na to, co se považují za neutrální znaky. Tato zásada může být užitečná pro zachování jedné sady řetězcového chování napříč kulturami, ale často poskytuje neočekávané výsledky.

Porovnávání bez rozlišování velkých a malých písmen s neutrální jazykovou verzí používají vlastnost Static <xref:System.Globalization.CultureInfo.CompareInfo%2A> vrácenou vlastností static <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> pro porovnání informací. Rozdíly v případech mezi těmito přeloženými znaky jsou ignorovány.

Porovnávání, které používají <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> a <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> fungují stejně jako řetězce ASCII. <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> však poskytuje lingvistická rozhodnutí, která nemusí být vhodná pro řetězce, které je nutné interpretovat jako sadu bajtů. Objekt `CultureInfo.InvariantCulture.CompareInfo` vytvoří metodu <xref:System.String.Compare%2A> interpretuje některé sady znaků jako ekvivalentní. Například následující ekvivalent je platný v rámci neutrální jazykové verze:

InvariantCulture: a + ̊ =

Malé písmeno latinky znak "A" (\u0061), když je vedle řetězce KOMBINOVÁNí nad znakem "+" ̊ "(\u030a), je interpretováno jako malé písmeno latinky A s KROUŽKem nad znakem" o "(\u00e5). Jak ukazuje následující příklad, toto chování se liší od ordinálního porovnání.

[!code-csharp[Conceptual.Strings.BestPractices#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
[!code-vb[Conceptual.Strings.BestPractices#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]

Při interpretaci názvů souborů, souborů cookie nebo cokoli jiného, kde se může zobrazit kombinace jako ".", ordinální porovnávání stále nabízí nejtransparentní a přizpůsobující chování.

V rovnováze má neutrální jazyková verze velmi málo vlastností, které jsou užitečné pro porovnání. Rozlišuje v lingvisticky relevantním způsobem, který brání v tom, aby zajistily plnou symbolický ekvivalent, ale není volbou pro zobrazení v libovolné jazykové verzi. Jedním z málo důvodů, jak použít <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> pro porovnání, je zachovat seřazená data pro zobrazení identické v různých kulturách. Například pokud velký datový soubor, který obsahuje seznam seřazených identifikátorů pro zobrazení, doprovází aplikaci, přidání do tohoto seznamu by vyžadovalo vložení do invariantního stylu řazení.

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Výběr člena StringComparison pro volání metody

Následující tabulka popisuje mapování z kontextu sémantického řetězce na člen <xref:System.StringComparison> výčtu:

|Datové|Chování|Odpovídající System. StringComparison<br /><br /> hodnotu|
|----------|--------------|-----------------------------------------------------|
|Interní identifikátory s rozlišováním velkých a malých písmen.<br /><br /> Identifikátory citlivé na velká a malá písmena ve standardech, jako je XML a HTTP.<br /><br /> Nastavení související se zabezpečením velkých a malých písmen.|Nelingvistické identifikátory, kde se přesně shodují bajty.|<xref:System.StringComparison.Ordinal>|
|Interní identifikátory bez rozlišení velkých a malých písmen.<br /><br /> Identifikátory bez rozlišení velkých a malých písmen ve standardech, jako je XML a HTTP.<br /><br /> Cesty k souborům.<br /><br /> Klíče a hodnoty registru.<br /><br /> Proměnné prostředí.<br /><br /> Identifikátory prostředků (například názvy popisovačů).<br /><br /> Nastavení týkající se zabezpečení nerozlišuje velká a malá písmena.|Nelingvistické identifikátory, kde Case není důležité; hlavně data uložená ve většině systémových služeb Windows.|<xref:System.StringComparison.OrdinalIgnoreCase>|
|Některá trvalá, lingvisticky relevantní data.<br /><br /> Zobrazení lingvistických dat, která vyžadují pevné pořadí řazení.|Kulturně nezávisláná data, která stále jsou lingvisticky relevantní.|<xref:System.StringComparison.InvariantCulture><br /><br /> -nebo-<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|
|Data zobrazená uživateli<br /><br /> Většina uživatelského vstupu.|Data, která vyžadují místní lingvistické celní úřady.|<xref:System.StringComparison.CurrentCulture><br /><br /> -nebo-<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|

## <a name="common-string-comparison-methods-in-net"></a>Společné metody porovnání řetězců v .NET

V následujících částech jsou popsány metody, které jsou nejčastěji používány pro porovnání řetězců.

### <a name="stringcompare"></a>String. Compare

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Při interpretaci středníku do řetězce je třeba prozkoumat všechny instance těchto volání metod, aby bylo možné určit, zda mají být řetězce interpretovány podle aktuální jazykové verze nebo zrušení přidružení z jazykové verze (symbolického). Obvykle je to ten druhý a místo toho by se mělo použít porovnání <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.

Třída <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>, která je vrácena vlastností <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType>, obsahuje také metodu <xref:System.Globalization.CompareInfo.Compare%2A>, která poskytuje velký počet odpovídající možností (ordinální, ignoruje prázdné znaky, ignorování typu Kana atd.) prostřednictvím výčtu příznaků <xref:System.Globalization.CompareOptions>.

### <a name="stringcompareto"></a>String. CompareTo

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Tato metoda aktuálně nenabízí přetížení, které určuje <xref:System.StringComparison> typ. Tuto metodu je obvykle možné převést na doporučený formulář <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType>.

Typy, které implementují rozhraní <xref:System.IComparable> a <xref:System.IComparable%601> implementují tuto metodu. Protože nenabízí možnost <xref:System.StringComparison> parametru, implementace typů často umožňuje uživateli zadat <xref:System.StringComparer> ve svém konstruktoru. Následující příklad definuje třídu `FileName`, jejíž konstruktor třídy obsahuje parametr <xref:System.StringComparer>. Tento objekt <xref:System.StringComparer> se pak používá v metodě `FileName.CompareTo`.

[!code-csharp[Conceptual.Strings.BestPractices#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
[!code-vb[Conceptual.Strings.BestPractices#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]

### <a name="stringequals"></a>Řetězec. Equals

Výchozí interpretace: <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.

Třída <xref:System.String> umožňuje testovat rovnost voláním buď přetížení statického, nebo instance <xref:System.String.Equals%2A> metody, nebo pomocí statického operátoru rovnosti. Přetížení a operátor používají ve výchozím nastavení ordinální porovnávání. Přesto však doporučujeme, abyste volali přetížení, které explicitně určuje typ <xref:System.StringComparison>, i když chcete provést ordinální porovnávání; Díky tomu je snazší vyhledat kód pro konkrétní interpretaci řetězce.

### <a name="stringtoupper-and-stringtolower"></a>String. ToUpper a String. ToLower

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Při použití těchto metod byste měli být opatrní, protože vynucení řetězce na velká a malá písmena se často používá jako malá normalizace pro porovnávání řetězců bez ohledu na velikost písmen. V takovém případě zvažte použití porovnání bez rozlišení velkých a malých písmen.

K dispozici jsou také metody <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> a <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType>. <xref:System.String.ToUpperInvariant%2A> je standardním způsobem pro normalizaci velkých a malých písmen. Porovnávání pomocí <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> jsou chováním složení dvou volání: volání <xref:System.String.ToUpperInvariant%2A> na obou řetězcových argumentech a provádění porovnání pomocí <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.

Přetížení jsou také k dispozici pro převod na velká a malá písmena v konkrétní jazykové verzi předáním <xref:System.Globalization.CultureInfo> objekt, který představuje tuto jazykovou verzi metody.

### <a name="chartoupper-and-chartolower"></a>Char. ToUpper a Char. ToLower

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Tyto metody fungují podobně jako <xref:System.String.ToUpper%2A?displayProperty=nameWithType> a <xref:System.String.ToLower%2A?displayProperty=nameWithType> metody popsané v předchozí části.

### <a name="stringstartswith-and-stringendswith"></a>String. StartsWith a String. EndsWith

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Ve výchozím nastavení obě tyto metody provádějí porovnání zohledňující jazykovou verzi.

### <a name="stringindexof-and-stringlastindexof"></a>String. IndexOf a String. LastIndexOf

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Existuje nedostatek konzistence ve způsobu, jakým výchozí přetížení těchto metod provádí porovnání. Všechny metody <xref:System.String.IndexOf%2A?displayProperty=nameWithType> a <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>, které zahrnují parametr <xref:System.Char>, provádějí ordinální porovnávání, ale výchozí <xref:System.String.IndexOf%2A?displayProperty=nameWithType> a <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> metody, které zahrnují parametr <xref:System.String>, provádějí porovnání zohledňující jazykovou verzi.

Pokud zavoláte metodu <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> nebo <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> a předáte jí řetězec k vyhledání v aktuální instanci, doporučujeme, abyste volali přetížení, které explicitně určuje typ <xref:System.StringComparison>. Přetížení, která zahrnují argument <xref:System.Char>, neumožňují zadat typ <xref:System.StringComparison>.

## <a name="methods-that-perform-string-comparison-indirectly"></a>Metody, které provádějí porovnání řetězců nepřímo

Některé jiné neřetězcové metody, které mají porovnávání řetězců jako centrální operace, používají typ <xref:System.StringComparer>. Třída <xref:System.StringComparer> obsahuje šest statických vlastností, které vracejí <xref:System.StringComparer> instance, jejichž metody <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> provádějí následující typy porovnávání řetězců:

- Porovnávání řetězců závislé na jazykové verzi s použitím aktuální jazykové verze. Tento objekt <xref:System.StringComparer> je vrácen vlastností <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType>.
- Porovnávání bez rozlišování velkých a malých písmen pomocí aktuální jazykové verze. Tento objekt <xref:System.StringComparer> je vrácen vlastností <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType>.
- Porovnávání bez rozlišení jazykové verze pomocí pravidel porovnání slov pro invariantní jazykovou verzi. Tento objekt <xref:System.StringComparer> je vrácen vlastností <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType>.
- Porovnávání bez rozlišení velkých a malých písmen a nezávisle na jazykové verzi používá pravidla porovnávání slov invariantní jazykové verze. Tento objekt <xref:System.StringComparer> je vrácen vlastností <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType>.
- Ordinální porovnání Tento objekt <xref:System.StringComparer> je vrácen vlastností <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType>.
- Ordinální porovnávání bez rozlišování velkých a malých písmen. Tento objekt <xref:System.StringComparer> je vrácen vlastností <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType>.

### <a name="arraysort-and-arraybinarysearch"></a>Array. Sort a Array. BinarySearch

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Pokud ukládáte data do kolekce nebo je načtete do kolekce trvalá data ze souboru nebo databáze, přepnutí aktuální jazykové verze může zrušit platnost invariant v kolekci. Metoda <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> předpokládá, že prvky v poli, které mají být prohledány, jsou již řazeny. Pro seřazení libovolného elementu řetězce v poli <xref:System.Array.Sort%2A?displayProperty=nameWithType> metoda volá metodu <xref:System.String.Compare%2A?displayProperty=nameWithType> a seřadí jednotlivé prvky. Použití porovnávání závislého na jazykové verzi může být nebezpečné, pokud se změní jazyková verze mezi časem řazení pole a vyhledáním jeho obsahu. Například v následujícím kódu funguje ukládání a načítání na porovnávací funkci, která je implicitně poskytnuta vlastností `Thread.CurrentThread.CurrentCulture`. Pokud se jazyková verze může změnit mezi voláními `StoreNames` a `DoesNameExist`a zejména v případě, že je obsah pole trvale uložen mezi voláními dvou metod, binární vyhledávání může selhat.

[!code-csharp[Conceptual.Strings.BestPractices#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]

V následujícím příkladu se zobrazí doporučená variace, která používá stejné ordinální metody (nezávisle na jazykové verzi) pro řazení a hledání v poli. Kód změny se projeví v řádcích označených `Line A` a `Line B` v obou příkladech.

[!code-csharp[Conceptual.Strings.BestPractices#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
[!code-vb[Conceptual.Strings.BestPractices#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]

Pokud jsou tato data trvalá a přesunutá mezi kulturami a při řazení se používají k prezentaci těchto dat uživateli, můžete zvážit použití <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>, která funguje v jazykovém prostředí pro lepší výstup uživatele, ale neovlivňuje změny v jazykové verzi. Následující příklad upravuje dva předchozí příklady pro použití neutrální jazykové verze pro řazení a hledání pole.

[!code-csharp[Conceptual.Strings.BestPractices#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
[!code-vb[Conceptual.Strings.BestPractices#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]

### <a name="collections-example-hashtable-constructor"></a>Příklad kolekcí: konstruktor Hashtable

Řetězce hash představují druhý příklad operace, která je ovlivněna způsobem, ve kterém jsou porovnávány řetězce.

Následující příklad vytvoří instanci objektu <xref:System.Collections.Hashtable> předáním objektu <xref:System.StringComparer>, který je vrácen vlastností <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType>. Vzhledem k tomu, že třída <xref:System.StringComparer> odvozená od <xref:System.StringComparer> implementuje rozhraní <xref:System.Collections.IEqualityComparer>, použije se jeho metoda <xref:System.Collections.IEqualityComparer.GetHashCode%2A> k výpočtu hash kódu řetězců v zatřiďovací tabulce.

[!code-csharp[Conceptual.Strings.BestPractices#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
[!code-vb[Conceptual.Strings.BestPractices#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]

## <a name="displaying-and-persisting-formatted-data"></a>Zobrazení a zachování formátovaných dat

Když zobrazíte data, která nejsou řetězcová, například čísla a data a časy, naformátujete je pomocí kulturního nastavení uživatele. Ve výchozím nastavení následující všechny používají aktuální jazykovou verzi vlákna při formátování operací:

- Interpolované řetězce podporované kompilátory [C#](../../csharp/language-reference/tokens/interpolated.md) a [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) .
- Operace zřetězení řetězců, které používají [C#](../../csharp/language-reference/operators/addition-operator.md#string-concatenation) operátory zřetězení nebo [Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md ) nebo které volají metodu <xref:System.String.Concat%2A?displayProperty=nameWithType> přímo
- Metoda <xref:System.String.Format%2A?displayProperty=nameWithType>.
- Metody `ToString` číselné typy a typy data a času.

Chcete-li explicitně určit, že by měl být řetězec formátován pomocí konvencí určené jazykové verze nebo [invariantní jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture), můžete provést následující:

- Při použití metod <xref:System.String.Format%2A?displayProperty=nameWithType> a `ToString` zavolejte přetížení, které má parametr `provider`, například <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> nebo <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType>, a předejte mu vlastnost <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, <xref:System.Globalization.CultureInfo> instanci, která představuje požadovanou jazykovou verzi nebo vlastnost <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.

- Pro zřetězení řetězců nepovolujte, aby kompilátor prováděl žádné implicitní převody. Místo toho proveďte explicitní převod voláním `ToString` přetížení s parametrem `provider`. Například kompilátor implicitně používá aktuální jazykovou verzi při převodu <xref:System.Double> hodnoty na řetězec v následujícím C# kódu:

  [!code-csharp[Implicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#1)]

  Místo toho můžete explicitně zadat jazykovou verzi, jejíž konvence formátování jsou použity v převodu voláním metody <xref:System.Double.ToString(System.IFormatProvider)?displayProperty=nameWithType>, jak následující C# kód:

  [!code-csharp[Explicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#2)]

- Pro řetězcové interpolace namísto přiřazení interpolované řetězce k instanci <xref:System.String> přiřadit k <xref:System.FormattableString>. Pak můžete zavolat svou <xref:System.FormattableString.ToString?displayProperty=nameWithType> metodu, která vytvoří výsledný řetězec, který odráží konvenci aktuální jazykové verze, nebo můžete volat metodu <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> a vytvořit výsledný řetězec, který odráží konvence zadané jazykové verze. Můžete také předat formátovací řetězec do metody static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> pro vytvoření výsledného řetězce, který odráží konvenci neutrální jazykové verze. Tento postup znázorňuje následující příklad. (Výstup z příkladu odráží aktuální jazykovou verzi en-US.)

  [!code-csharp[String interpolation](~/samples/snippets/standard/base-types/string-practices/cs/formattable.cs)]
  [!code-vb[String interpolation](~/samples/snippets/standard/base-types/string-practices/vb/formattable.vb)]

Neřetězcová data můžete zachovat buď jako binární data, nebo jako formátovaná data. Pokud se rozhodnete ho uložit jako formátovaná data, měli byste zavolat přetížení metody formátování, které obsahuje parametr `provider` a předat mu vlastnost <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Invariantní jazyková verze poskytuje konzistentní formát pro formátovaná data, která jsou nezávislá na jazykové verzi a počítači. Naproti tomu trvalá data, která jsou formátována pomocí jiné kultury než invariantní jazyková verze, má několik omezení:

- Data budou pravděpodobně nepoužitelná, pokud jsou načtena v systému, který má jinou jazykovou verzi, nebo pokud uživatel aktuálního systému změní aktuální jazykovou verzi a pokusí se načíst data.
- Vlastnosti jazykové verze v určitém počítači se mohou lišit od hodnot Standard. Uživatel může kdykoli přizpůsobit nastavení zobrazení závislé na jazykové verzi. Z tohoto důvodu nemusí být formátovaná data uložená v systému čitelná, jakmile uživatel přizpůsobí kulturní nastavení. Přenositelnost formátovaných dat napříč počítači je pravděpodobně ještě více omezené.
- Mezinárodní, regionální nebo národní standardy, které řídí formátování čísel nebo dat a časů se mění v průběhu času, a tyto změny jsou začleněny do aktualizací operačního systému Windows. Když se změní konvence formátování, data naformátovaná pomocí předchozích konvencí můžou být nečitelná.

Následující příklad znázorňuje omezené přenositelnosti, která je výsledkem použití formátování zohledňující jazykovou verzi pro zachování dat. V příkladu se uloží pole hodnot data a času do souboru. Tyto jsou formátovány pomocí konvencí jazykové verze anglické (USA). Poté, co aplikace změní aktuální jazykovou verzi vlákna na francouzštinu (Švýcarsko), se pokusí přečíst uložené hodnoty pomocí formátovacích úmluv aktuální jazykové verze. Pokus o čtení dvou datových položek vyvolá výjimku <xref:System.FormatException> a pole dat nyní obsahuje dva nesprávné prvky, které se rovnají <xref:System.DateTime.MinValue>.

[!code-csharp[Conceptual.Strings.BestPractices#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
[!code-vb[Conceptual.Strings.BestPractices#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]

Pokud však nahradíte vlastnost <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> parametrem <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> v voláních <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> a <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, budou data trvalého data a času úspěšně obnovena, jak ukazuje následující výstup:

```console
06.05.1758 21:26
05.05.1818 07:19
22.04.1870 23:54
08.09.1890 06:47
18.02.1905 15:12
```

## <a name="see-also"></a>Viz také:

- [Práce s řetězci](manipulating-strings.md)
