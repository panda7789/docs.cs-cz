---
title: Doporučené postupy pro použití řetězců v rozhraní .NET
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711477"
---
# <a name="best-practices-for-using-strings-in-net"></a>Doporučené postupy pro použití řetězců v rozhraní .NET

.NET poskytuje rozsáhlou podporu pro vývoj lokalizovaných a globalizovaných aplikací a usnadňuje použití konvencí aktuální jazykové verze nebo konkrétní jazykové verze při provádění běžných operací, jako je řazení a zobrazování řetězců. Ale řazení nebo porovnávání řetězců není vždy operace citlivá na jazykovou verzi. Například řetězce, které jsou používány interně aplikací obvykle by měly být zpracovány identicky ve všech kulturách. Když jsou interpretována kulturně nezávislá řetězcová data, jako jsou značky XML, značky HTML, uživatelská jména, cesty k souborům a názvy systémových objektů, jako by byla citlivá na jazykovou verzi, kód aplikace může podléhat jemným chybám, nízkému výkonu a v některých případech bezpečnostních otázek.

Toto téma zkoumá metody řazení, porovnávání a pouzdře řetězce v rozhraní .NET, představuje doporučení pro výběr vhodné metody zpracování řetězců a poskytuje další informace o metodách zpracování řetězců. Zkoumá také, jak jsou formátovaná data, jako jsou číselná data a data a čas, zpracována pro zobrazení a pro ukládání.

## <a name="recommendations-for-string-usage"></a>Doporučení pro použití řetězce

Při vývoji s rozhraním .NET postupujte podle těchto jednoduchých doporučení při použití řetězců:

- Použijte přetížení, která explicitně určují pravidla porovnání řetězců pro operace řetězce. Obvykle to zahrnuje volání přetížení metody, která <xref:System.StringComparison>má parametr typu .
- Použití <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> nebo pro porovnání jako bezpečné výchozí pro porovnávání řetězců bez jazykové verze.
- Použijte porovnání <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> s <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> nebo pro lepší výkon.
- Použijte operace řetězce, <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> které jsou založeny na při zobrazení výstupu pro uživatele.
- Použijte nejazykové <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> nebo <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> hodnoty namísto řetězcových operací založených na <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> tom, kdy je porovnání jazykově irelevantní (například symbolické).
- Použijte <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> metodu namísto metody při <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> normalizaci řetězců pro porovnání.
- Použijte přetížení <xref:System.String.Equals%2A?displayProperty=nameWithType> metody k testování, zda jsou dva řetězce stejné.
- Pomocí <xref:System.String.Compare%2A?displayProperty=nameWithType> metod <xref:System.String.CompareTo%2A?displayProperty=nameWithType> a můžete řadit řetězce, nikoli ke kontrole rovnosti.
- Pomocí formátování závislého na jazykové verzi můžete v uživatelském rozhraní zobrazit data, která nejsou pod řetězec, například čísla a kalendářní data. Pomocí formátování s [invariantní jazykovou verzí](xref:System.Globalization.CultureInfo.InvariantCulture) zachovat non-string data v řetězcové formě.

Při použití řetězců se vyhněte následujícím postupům:

- Nepoužívejte přetížení, které explicitně nebo implicitně neurčují pravidla porovnání řetězců pro operace řetězce.
- Ve většině případů nepoužívejte řetězcové operace založené na. <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> Jednou z mála výjimek je, když jsou trvalé jazykově smysluplné, ale kulturně agnostik data.
- Nepoužívejte přetížení <xref:System.String.Compare%2A?displayProperty=nameWithType> metody nebo <xref:System.String.CompareTo%2A> a otestujte vrácenou hodnotu nula k určení, zda jsou dva řetězce stejné.
- Nepoužívejte formátování citlivé na jazykovou verzi k uchování číselných dat nebo dat a dat a času v řetězcové podobě.

## <a name="specifying-string-comparisons-explicitly"></a>Explicitní určení porovnání řetězců

Většina metod manipulace s řetězci v rozhraní .NET je přetížena. Obvykle jedno nebo více přetížení přijmout výchozí nastavení, zatímco jiné přijmout žádné výchozí hodnoty a místo toho definovat přesný způsob, jakým řetězce mají být porovnány nebo manipulovat. Většina metod, které nejsou závislé na výchozí <xref:System.StringComparison>hodnoty patří parametr typu , což je výčet, který explicitně určuje pravidla pro porovnání řetězců podle jazykové verze a případ. Následující tabulka popisuje <xref:System.StringComparison> členy výčtu.

|Člen StringComparison|Popis|
|-----------------------------|-----------------|
|<xref:System.StringComparison.CurrentCulture>|Provede porovnání rozlišování velkých a malých písmen pomocí aktuální jazykové verze.|
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|Provede porovnání bez rozlišování velkých a malých písmen pomocí aktuální jazykové verze.|
|<xref:System.StringComparison.InvariantCulture>|Provede porovnání rozlišování velkých a malých písmen pomocí invariantní jazykové verze.|
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|Provede porovnání bez rozlišování velkých a malých písmen pomocí invariantní jazykové verze.|
|<xref:System.StringComparison.Ordinal>|Provede pořazovační porovnání.|
|<xref:System.StringComparison.OrdinalIgnoreCase>|Provede řadové porovnání bez rozlišování velkých a malých písmen.|

Například <xref:System.String.IndexOf%2A> metoda, která vrací index podřetězce v <xref:System.String> objektu, který odpovídá znaku nebo řetězci, má devět přetížení:

- <xref:System.String.IndexOf%28System.Char%29>, <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29>a <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>, které ve výchozím nastavení provádějí řadové (rozlišování velkých a nerozlišující malá a velká písmena) vyhledávají znak v řetězci.
- <xref:System.String.IndexOf%28System.String%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>a , které ve výchozím nastavení provádějí hledání dílčího řetězce v řetězci rozlišující malá a velká písmena a jazykovou verzi.
- <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>a <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29>, které obsahují <xref:System.StringComparison> parametr typu, který umožňuje zadat formu porovnání.

Doporučujeme vybrat přetížení, které nepoužívá výchozí hodnoty, z následujících důvodů:

- Některá přetížení s výchozími parametry <xref:System.Char> (ty, které hledají instanci řetězce) provádějí řadové porovnání, zatímco jiné (ty, které hledají řetězec v instanci řetězce) jsou citlivé na jazykovou verzi. Je obtížné si vzpomenout, která metoda používá výchozí hodnotu a snadno zmást přetížení.
- Záměr kódu, který závisí na výchozí hodnoty pro volání metody není jasné. V následujícím příkladu, který se opírá o výchozí hodnoty, je obtížné zjistit, zda vývojář skutečně zamýšlel řadové nebo jazykové porovnání dvou řetězců, nebo zda rozdíl v případu mezi `protocol` a "http" může způsobit návrat testu rovnosti `false`.

     [!code-csharp[Conceptual.Strings.BestPractices#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]

Obecně doporučujeme volat metodu, která není závislá na výchozí hodnoty, protože umožňuje záměr kódu jednoznačné. To zase dělá kód čitelnější a snadněji ladit a udržovat. Následující příklad řeší otázky vznesené v předchozím příkladu. Je jasné, že se používá ordinální porovnání a že rozdíly v případě jsou ignorovány.

[!code-csharp[Conceptual.Strings.BestPractices#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
[!code-vb[Conceptual.Strings.BestPractices#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]

## <a name="the-details-of-string-comparison"></a>Podrobnosti porovnání řetězců

Porovnání řetězců je srdcem mnoha operací souvisejících s řetězci, zejména řazení a testování rovnosti. Řetězce seřadí v určeném pořadí: Pokud se "my" zobrazí před "řetězce" v seřazeném seznamu řetězců, musí "my" porovnat méně než nebo rovno "řetězec". Navíc porovnání implicitně definuje rovnost. Operace porovnání vrátí nulu pro řetězce, které považuje za rovné. Dobrý výklad je, že ani řetězec je menší než ostatní. Většina smysluplné operace zahrnující řetězce zahrnují jeden nebo oba tyto postupy: porovnání s jiným řetězcem a provádění dobře definované operace řazení.

> [!NOTE]
> Můžete si stáhnout [tabulku tloušťky řazení](https://www.microsoft.com/download/details.aspx?id=10921), sadu textových souborů, které obsahují informace o hmotnosti znaků používané při řazení a porovnávání operací pro operační systémy Windows, a [výchozí tabulku prvků řazení unicode](https://www.unicode.org/Public/UCA/latest/allkeys.txt), nejnovější verzi tabulky hmotnosti řazení pro Linux a macOS. Konkrétní verze tabulky řazení hmotnosti na Linux a macOS závisí na verzi [mezinárodních komponent pro](http://site.icu-project.org/) knihovny Unicode nainstalované v systému. Informace o verzích ICU a verzích Unicode, které implementují, naleznete [v tématu Stažení JIP](http://site.icu-project.org/download).

Vyhodnocení dvou řetězců pro rovnost nebo pořadí řazení však nepřináší jeden, správný výsledek; výsledek závisí na kritériích použitých k porovnání řetězců. Zejména porovnání řetězců, které jsou řadové nebo které jsou založeny na konvencích písmen a řazení aktuální jazykové verze nebo [invariantní jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture) (jazyková verze agnostik národního prostředí založená na anglickém jazyce) mohou vést k různým výsledkům.

Porovnání řetězců pomocí různých verzí rozhraní .NET nebo použití rozhraní .NET v různých operačních systémech nebo verzích operačního systému může navíc vracet různé výsledky. Další informace naleznete [v tématu Řetězce a Unicode Standard](xref:System.String#Unicode).

### <a name="string-comparisons-that-use-the-current-culture"></a>Porovnání řetězců, které používají aktuální jazykovou verzi

Jedním z kritérií zahrnuje použití konvencí aktuální jazykové verze při porovnávání řetězců. Porovnání, které jsou založeny na aktuální jazykové verzi použít aktuální jazykovou verzi vlákna nebo národní prostředí. Pokud jazyková verze není nastavena uživatelem, je výchozí nastavení v okně **Místní možnosti** v Ovládacích panelech. Vždy byste měli použít porovnání, které jsou založeny na aktuální jazykové verzi, když data jsou jazykově relevantní a když odráží interakci uživatele citlivou na jazykovou verzi.

Však porovnání a caseing chování v rozhraní .NET změní při změně jazykové verze. K tomu dochází, když se aplikace spustí v počítači, který má jinou jazykovou verzi než počítač, ve kterém byla aplikace vyvinuta, nebo když vykonávající vlákno změní svou jazykovou verzi. Toto chování je úmyslné, ale zůstává nezřejmé pro mnoho vývojářů. Následující příklad ilustruje rozdíly v pořadí řazení mezi jazykovou verzí americké angličtiny ("en-US") a švédštiny ("sv-SE"). Všimněte si, že slova "ångström", "Windows" a "Visual Studio" se zobrazí v různých pozicích v seřazených polí řetězců.

[!code-csharp[Conceptual.Strings.BestPractices#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
[!code-vb[Conceptual.Strings.BestPractices#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]

Porovnání bez rozlišování velkých a malých písmen, které používají aktuální jazykovou verzi jsou stejné jako porovnání zjištovaní jazykovou verzi, s tím rozdílem, že ignorují případ, jak je diktováno aktuální jazykovou verzí vlákna. Toto chování se může projevit také v pořadí řazení.

Porovnání, které používají aktuální sémantiku kultury jsou výchozí pro následující metody:

- <xref:System.String.Compare%2A?displayProperty=nameWithType>přetížení, které neobsahují <xref:System.StringComparison> parametr.
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>Přetížení.
- Výchozí <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> metoda a <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda s `null` <xref:System.Globalization.CultureInfo> parametrem.
- Výchozí <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> metoda a <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType> metoda s `null` <xref:System.Globalization.CultureInfo> parametrem.
- <xref:System.String.IndexOf%2A?displayProperty=nameWithType>přetížení, které <xref:System.String> přijímají jako vyhledávací parametr a <xref:System.StringComparison> které nemají parametr.
- <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>přetížení, které <xref:System.String> přijímají jako vyhledávací parametr a <xref:System.StringComparison> které nemají parametr.

V každém případě doporučujeme volat přetížení, <xref:System.StringComparison> které má parametr, aby záměr volání metody jasné.

Subtilní a ne tak jemné chyby se mohou objevit, když jsou jazykově interpretována nejazykná řetězcová data nebo když jsou řetězcová data z určité jazykové verze interpretována pomocí konvencí jiné jazykové verze. Kanonickým příkladem je problém Turecka a I.

Pro téměř všechny latinské abecedy, včetně americké angličtiny, znak "i" (\u0069) je malá verze znaku "I" (\u0049). Toto pravidlo krytu se rychle stane výchozím nastavením pro uživatele programování v takové jazykové verzi. Turecká abeceda ("tr-TR") však obsahuje znak "I s tečkou" "İ" (\u0130), což je hlavní verze "i". Turečtina také obsahuje malý znak "i bez tečky", "ı" (\u0131), který má velká písmena "I". K tomuto chování dochází také v ázerbájdžánské jazykové verzi ("az").

Proto předpoklady o svitek "i" nebo lowercasing "I" nejsou platné mezi všechny jazykové verze. Pokud použijete výchozí přetížení pro rutiny porovnání řetězců, budou podléhat odchylkám mezi jazyky. Pokud data, která mají být porovnána, nejsou jazyková, může použití výchozího přetížení vést k nežádoucím výsledkům, jak dokládá následující pokus o porovnání řetězců "file" a "FILE" bez rozlišování velkých a malých písmen.

[!code-csharp[Conceptual.Strings.BestPractices#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
[!code-vb[Conceptual.Strings.BestPractices#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]

Toto porovnání může způsobit významné problémy, pokud je jazyková verze neúmyslně použita v nastavení citlivém na zabezpečení, jako v následujícím příkladu. Volání metody, `IsFileURI("file:")` například vrátí, `true` pokud aktuální jazyková `false` verze je angličtina USA, ale pokud aktuální jazyková verze je turečtina. Tak, na turecké systémy, někdo mohl obejít bezpečnostní opatření, která blokují přístup k malá a velká písmena URI, které začínají "FILE:".

[!code-csharp[Conceptual.Strings.BestPractices#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
[!code-vb[Conceptual.Strings.BestPractices#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]

V tomto případě protože "file:" je určen k interpretovat jako nejazykové, jazyková jazyková verze necitlivý identifikátor, kód by měl být místo toho zapsán, jak je znázorněno v následujícím příkladu:

[!code-csharp[Conceptual.Strings.BestPractices#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
[!code-vb[Conceptual.Strings.BestPractices#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]

### <a name="ordinal-string-operations"></a>Operace řadových řetězců

Zadání hodnoty <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> nebo v volání metody znamená nejazykové porovnání, ve kterém jsou ignorovány vlastnosti přirozených jazyků. Metody, které jsou <xref:System.StringComparison> vyvolány s těmito hodnotami rozhodnutí o operaci základního řetězce na jednoduché porovnání bajtů namísto velikosti písmen nebo tabulky ekvivalence, které jsou parametrizovány jazykovou verzí. Ve většině případů tento přístup nejlépe vyhovuje zamýšlené interpretaci řetězců při vytváření kódu rychlejší a spolehlivější.

Ordinální porovnání jsou porovnání řetězců, ve kterých je každý bajt každého řetězce porovnán bez jazykové interpretace; například "windows" neodpovídá "Windows". Toto je v podstatě `strcmp` volání funkce runtime C. Toto porovnání použijte, pokud kontext určuje, že řetězce by měly být přesně spárovány nebo vyžaduje konzervativní zásady párování. Kromě toho řadové porovnání je nejrychlejší porovnání operace, protože platí žádná jazyková pravidla při určování výsledku.

Řetězce v rozhraní .NET mohou obsahovat vložené prázdné znaky. Jeden z nejjasnějších rozdílů mezi řadovým a jazykovou verzí citlivé porovnání (včetně porovnání, které používají invariantní jazykovou verzi) se týká zpracování vložené prázdné znaky v řetězci. Tyto znaky jsou ignorovány <xref:System.String.Compare%2A?displayProperty=nameWithType> při <xref:System.String.Equals%2A?displayProperty=nameWithType> použití a metody k provádění porovnání zjitřující jazykovou verzi (včetně porovnání, které používají invariantní jazykovou verzi). V důsledku toho v porovnání zjitřující jazykovou verzi řetězce, které obsahují vložené prázdné znaky lze považovat za rovna řetězce, které nejsou.

> [!IMPORTANT]
> Přestože metody porovnávání řetězců ignorují vložené <xref:System.String.EndsWith%2A?displayProperty=nameWithType> <xref:System.String.IndexOf%2A?displayProperty=nameWithType>prázdné <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>znaky, metody vyhledávání řetězců, například <xref:System.String.StartsWith%2A?displayProperty=nameWithType> <xref:System.String.Contains%2A?displayProperty=nameWithType>, , , a ne.

Následující příklad provádí porovnání řetězce "Aa" citlivé na jazykovou verzi s podobným řetězcem, který obsahuje několik vložených prázdných znaků mezi "A" a "a" a ukazuje, jak jsou oba řetězce považovány za rovné:

[!code-csharp[Conceptual.Strings.BestPractices#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]

Řetězce se však nepovažují za rovné při použití řadového porovnání, jak ukazuje následující příklad:
  
[!code-csharp[Conceptual.Strings.BestPractices#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
[!code-vb[Conceptual.Strings.BestPractices#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]

Další nejkonzervativnější přístup jsou posvěcená případová písmena. Tato porovnání ignorují většinu krytů; například "windows" odpovídá "Windows". Při práci s znaky ASCII je <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>tato zásada ekvivalentní , s tím rozdílem, že ignoruje obvyklé ascii caseing. Proto libovolný znak v [A, Z] (\u0041-\u005A) odpovídá odpovídajícímu znaku v [a,z] (\u0061-\007A). Caseing mimo rozsah ASCII používá tabulky invariantní jazykové verze. Proto následující porovnání:

[!code-csharp[Conceptual.Strings.BestPractices#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
[!code-vb[Conceptual.Strings.BestPractices#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]

je ekvivalentní (ale rychlejší než) toto srovnání:

[!code-csharp[Conceptual.Strings.BestPractices#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
[!code-vb[Conceptual.Strings.BestPractices#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]

Tato srovnání jsou stále velmi rychlá.

> [!NOTE]
> Chování řetězce systému souborů, klíčů a hodnot registru a proměnných prostředí je nejlépe reprezentováno <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>.

Oba <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> a používat binární hodnoty přímo a jsou nejvhodnější pro porovnávání. Pokud si nejste jisti nastavením porovnání, použijte jednu z těchto dvou hodnot. Protože však provádějí porovnání bajtů po bajtu, neseřazují se podle jazykového pořadí řazení (například podle anglického slovníku), ale podle binárního pořadí řazení. Výsledky mohou vypadat liché ve většině kontextů, pokud jsou zobrazeny uživatelům.

Ordinální sémantiku jsou <xref:System.String.Equals%2A?displayProperty=nameWithType> výchozí pro přetížení, <xref:System.StringComparison> které neobsahují argument (včetně operátoru rovnosti). V každém případě doporučujeme volat přetížení, <xref:System.StringComparison> které má parametr.

### <a name="string-operations-that-use-the-invariant-culture"></a>řetězcové operace, které používají invariantní jazykovou verzi

Porovnání s invariantní jazykovou <xref:System.Globalization.CultureInfo.CompareInfo%2A> verzi použít <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost vrácenou statickou vlastnost. Toto chování je stejné ve všech systémech; překládá všechny znaky mimo jeho rozsah do co se domnívá, že jsou ekvivalentní invariantní znaky. Tato zásada může být užitečná pro udržování jedné sady chování řetězce napříč jazyky, ale často poskytuje neočekávané výsledky.

Porovnání bez rozlišování velkých a malých písmen s invariantní jazykovou verzí používá statickou <xref:System.Globalization.CultureInfo.CompareInfo%2A> vlastnost vrácenou statickou <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastností také pro porovnání informací. Všechny rozdíly mezi písmeny mezi těmito přeložené znaky jsou ignorovány.

Porovnání, které <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> používají a pracují stejně na řetězce ASCII. Však <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> dělá jazyková rozhodnutí, která nemusí být vhodné pro řetězce, které musí být interpretovány jako sada bajtů. Objekt `CultureInfo.InvariantCulture.CompareInfo` umožňuje <xref:System.String.Compare%2A> metoda interpretovat určité sady znaků jako ekvivalentní. Například následující ekvivalence je platná pod invariantní jazykovou verzi:

InvariantCulture: a + ° = å

Malé písmeno latinky A znak "a" (\u0061), který je vedle znaku DIASTRÁL NAD ZNAKEM "+ " " " (\u030a), je interpretován jako malé písmeno latinky A s kroužkem nad znakem "å" (\u00e5). Jak ukazuje následující příklad, toto chování se liší od ordinálního porovnání.

[!code-csharp[Conceptual.Strings.BestPractices#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
[!code-vb[Conceptual.Strings.BestPractices#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]

Při interpretaci názvů souborů, souborů cookie nebo čehokoli jiného, kde se může zobrazit kombinace, jako je "å", nebodinální porovnání stále nabízejí nejtransparentnější a nejpříhodnější chování.

Po zralé úvaze má invariantní jazyková verze velmi málo vlastností, které jsou užitečné pro porovnání. Provádí porovnání jazykově relevantním způsobem, který mu brání zaručit úplnou symbolickou ekvivalenci, ale není to volba pro zobrazení v jakékoli jazykové verzi. Jedním z mála důvodů, proč použít <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> pro porovnání je zachovat objednaná data pro mezikulturní identické zobrazení. Například pokud velký datový soubor, který obsahuje seznam seřazených identifikátorů pro zobrazení doprovází aplikace, přidání do tohoto seznamu by vyžadovalo vložení s invariantním stylem řazení.

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Výběr člena StringComparison pro volání metody

Následující tabulka popisuje mapování z kontextu sémantického řetězce na člen výčtu: <xref:System.StringComparison>

|Data|Chování|Odpovídající System.StringComparison<br /><br /> hodnota|
|----------|--------------|-----------------------------------------------------|
|Vnitřní identifikátory rozlišující malá a velká písmena.<br /><br /> Identifikátory rozlišující malá a velká písmena ve standardech, jako je XML a HTTP.<br /><br /> Nastavení související se zabezpečením rozlišují malá a velká písmena.|Nejazykový identifikátor, kde se přesně shodují bajty.|<xref:System.StringComparison.Ordinal>|
|Vnitřní identifikátory bez rozlišování velkých a malých písmen.<br /><br /> Identifikátory bez rozlišování velkých a malých písmen ve standardech, jako je XML a HTTP.<br /><br /> Cesty k souborům.<br /><br /> Klíče a hodnoty registru.<br /><br /> Proměnné prostředí.<br /><br /> Identifikátory prostředků (například názvy popisovačů).<br /><br /> Nastavení související se zabezpečením bez rozlišování velkých a malých písmen.|Nejazykový identifikátor, pokud je případ irelevantní; zejména data uložená ve většině systémových služeb systému Windows.|<xref:System.StringComparison.OrdinalIgnoreCase>|
|Některé trvalá, jazykově relevantní data.<br /><br /> Zobrazení jazykových dat, která vyžadují pevné pořadí řazení.|Kulturně agnostik data, která je stále jazykově relevantní.|<xref:System.StringComparison.InvariantCulture><br /><br /> -nebo-<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|
|Data zobrazená uživateli.<br /><br /> Většina uživatelských vstupů.|Data, která vyžadují místní jazykové zvyky.|<xref:System.StringComparison.CurrentCulture><br /><br /> -nebo-<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|

## <a name="common-string-comparison-methods-in-net"></a>Běžné metody porovnání řetězců v rozhraní .NET

Následující části popisují metody, které se nejčastěji používají pro porovnání řetězců.

### <a name="stringcompare"></a>String.compare

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Jako operace nejvíce centrální interpretace řetězce, všechny instance těchto volání metody by měly být zkoumány k určení, zda řetězce by měly být interpretovány podle aktuální jazykové verze nebo disociované od jazykové verze (symbolicky). Obvykle je to druhé a <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> místo toho by mělo být použito porovnání.

Třída, <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> která je vrácena <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> vlastností, <xref:System.Globalization.CompareInfo.Compare%2A> také obsahuje metodu, která poskytuje velký počet možností párování (řadové, ignorování prázdného místa, <xref:System.Globalization.CompareOptions> ignorování typu kana a tak dále) pomocí výčtu příznaku.

### <a name="stringcompareto"></a>String.CompareTo

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Tato metoda aktuálně nenabízí přetížení, které <xref:System.StringComparison> určuje typ. Obvykle je možné převést tuto <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metodu na doporučenou formu.

Typy, které <xref:System.IComparable> <xref:System.IComparable%601> implementují a rozhraní implementovat tuto metodu. Vzhledem k tomu, že <xref:System.StringComparison> nenabízí možnost parametru, implementace <xref:System.StringComparer> typů často umožňují uživateli zadat v jejich konstruktoru. Následující příklad definuje `FileName` třídu, jejíž <xref:System.StringComparer> konstruktor třídy obsahuje parametr. Tento <xref:System.StringComparer> objekt se pak `FileName.CompareTo` používá v metodě.

[!code-csharp[Conceptual.Strings.BestPractices#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
[!code-vb[Conceptual.Strings.BestPractices#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]

### <a name="stringequals"></a>String.Equals

Výchozí interpretace: <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.

Třída <xref:System.String> umožňuje testovat rovnost voláním přetížení statické metody <xref:System.String.Equals%2A> nebo instance nebo pomocí operátoru statické rovnosti. Přetížení a operátor použití ordinální porovnání ve výchozím nastavení. Však stále doporučujeme volat přetížení, které <xref:System.StringComparison> explicitně určuje typ i v případě, že chcete provést ordinální porovnání; To usnadňuje hledání kódu pro určitý řetězec interpretace.

### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper a String.ToLower

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Při použití těchto metod byste měli být opatrní, protože vynucení řetězce na velká nebo malá písmena se často používá jako malá normalizace pro porovnání řetězců bez ohledu na velká písmena. Pokud ano, zvažte použití porovnání bez rozlišování velkých a malých písmen.

A <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> metody jsou také k dispozici. <xref:System.String.ToUpperInvariant%2A>je standardní způsob normalizace případu. Porovnání provedené <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pomocí jsou behaviorálně složení dvou <xref:System.String.ToUpperInvariant%2A> volání: volání na oba argumenty řetězce a provedení porovnání pomocí <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.

Přetížení jsou také k dispozici pro převod na velká a malá <xref:System.Globalization.CultureInfo> písmena v určité jazykové verzi předáním objektu, který představuje tuto jazykovou verzi metodě.

### <a name="chartoupper-and-chartolower"></a>Char.ToUpper a Char.ToLower

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Tyto metody fungují podobně <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType> jako metody a popsané v předchozí části.

### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith a String.EndsWith

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Ve výchozím nastavení obě tyto metody provést porovnání zjitřující jazykovou verzi.

### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf a String.LastIndexOf

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Je nedostatek konzistence v jak výchozí přetížení těchto metod provádět porovnání. Všechny <xref:System.String.IndexOf%2A?displayProperty=nameWithType> <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> a metody, <xref:System.Char> které obsahují parametr provést řadové <xref:System.String.IndexOf%2A?displayProperty=nameWithType> porovnání, ale výchozí a <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> metody, které obsahují <xref:System.String> parametr provést porovnání zdůvodu jazykové verze.

Pokud zavoláte <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> metodu or a předáte ji řetězec, který se vykreslo v aktuální instanci, doporučujeme volat přetížení, které explicitně určuje <xref:System.StringComparison> typ. Přetížení, které obsahují <xref:System.Char> argument neumožňují zadat <xref:System.StringComparison> typ.

## <a name="methods-that-perform-string-comparison-indirectly"></a>Metody, které provádějí porovnání řetězců nepřímo

Některé metody bez řetězce, které mají porovnání <xref:System.StringComparer> řetězců jako centrální operace použít typ. Třída <xref:System.StringComparer> obsahuje šest statických <xref:System.StringComparer> vlastností, které vracejí instance, jejichž <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> metody provádějí následující typy porovnání řetězců:

- Porovnání řetězců citlivých na jazykovou verzi pomocí aktuální jazykové verze. Tento <xref:System.StringComparer> objekt je <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType> vrácenvlastností.
- Porovnání bez rozlišování velkých a malých písmen pomocí aktuální jazykové verze. Tento <xref:System.StringComparer> objekt je <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType> vrácenvlastností.
- Porovnání necitlivé na jazykovou verzi pomocí pravidla porovnání slov invariantní jazykové verze. Tento <xref:System.StringComparer> objekt je <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType> vrácenvlastností.
- Případ nerozlišující a necitlivé jazyky porovnání pomocí pravidla porovnání slov invariantní jazykové verze. Tento <xref:System.StringComparer> objekt je <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType> vrácenvlastností.
- Ordinální srovnání. Tento <xref:System.StringComparer> objekt je <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType> vrácenvlastností.
- Porovnání ordinálního porovnání bez rozlišování velkých a malých písmen. Tento <xref:System.StringComparer> objekt je <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> vrácenvlastností.

### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort a Array.BinarySearch

Výchozí interpretace: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Při ukládání dat v kolekci nebo čtení trvalých dat ze souboru nebo databáze do kolekce, přepínání aktuální jazykové verze může zneplatnit invariants v kolekci. Metoda <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> předpokládá, že prvky v poli, které mají být prohledány jsou již seřazeny. Chcete-li seřadit libovolný <xref:System.Array.Sort%2A?displayProperty=nameWithType> prvek řetězce <xref:System.String.Compare%2A?displayProperty=nameWithType> v poli, metoda volá metodu k objednání jednotlivých prvků. Použití porovnání citlivé na jazykovou verzi může být nebezpečné, pokud se změní jazyková verze mezi časem řazení pole a jeho obsahem. Například v následujícím kódu úložiště a načítání pracovat na porovnávání, který `Thread.CurrentThread.CurrentCulture` je poskytován implicitně vlastnost. Pokud jazyková verze může `StoreNames` změnit `DoesNameExist`mezi volání a , a zejména pokud obsah pole jsou trvalé někde mezi dvěma volání metody, binární hledání může selhat.

[!code-csharp[Conceptual.Strings.BestPractices#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]

Doporučená varianta se zobrazí v následujícím příkladu, který používá stejnou řadovou (necitlivou) metodu porovnání k řazení a vyhledávání pole. Kód změny se projeví v `Line A` řádcích označených a `Line B` ve dvou příkladech.

[!code-csharp[Conceptual.Strings.BestPractices#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
[!code-vb[Conceptual.Strings.BestPractices#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]

Pokud tato data jsou trvalé a přesunuty napříč jazykovými verzemi a řazení se <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>používá k prezentaci těchto dat uživateli, můžete zvážit použití , který pracuje jazykově pro lepší výstup uživatele, ale není ovlivněn a změny v jazykové verzi. Následující příklad upravuje dva předchozí příklady pro použití invariantní jazykové verze pro řazení a vyhledávání pole.

[!code-csharp[Conceptual.Strings.BestPractices#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
[!code-vb[Conceptual.Strings.BestPractices#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]

### <a name="collections-example-hashtable-constructor"></a>Příklad kolekcí: Hashtable konstruktor

Řetězce hash poskytuje druhý příklad operace, která je ovlivněna způsobem, ve kterém jsou porovnány řetězce.

Následující příklad inkoniuje <xref:System.Collections.Hashtable> objekt <xref:System.StringComparer> předáním objektu, <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> který je vrácen vlastností. Vzhledem <xref:System.StringComparer> k tomu, <xref:System.StringComparer> že třída, která je odvozena z implementuje <xref:System.Collections.IEqualityComparer> rozhraní, jeho <xref:System.Collections.IEqualityComparer.GetHashCode%2A> metoda se používá k výpočtu hash kód řetězců v tabulce hash.

[!code-csharp[Conceptual.Strings.BestPractices#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
[!code-vb[Conceptual.Strings.BestPractices#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]

## <a name="displaying-and-persisting-formatted-data"></a>Zobrazení a zachování formátovaných dat

Pokud uživatelům zobrazíte neřetězcová data, jako jsou čísla a data a časy, naformátujte je pomocí kulturního nastavení uživatele. Ve výchozím nastavení používají všichni následující jazyková verze aktuálního vlákna při operacích formátování:

- Interpolované řetězce podporované kompilátory [jazyka C#](../../csharp/language-reference/tokens/interpolated.md) a [Visual Basic.](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)
- Operace zřetězení řetězců, které používají operátory zřetězení <xref:System.String.Concat%2A?displayProperty=nameWithType> jazyka [C#](../../csharp/language-reference/operators/addition-operator.md#string-concatenation) nebo Visual [Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md ) nebo které přímo volají metodu.
- Metoda. <xref:System.String.Format%2A?displayProperty=nameWithType>
- Metody `ToString` číselných typů a typy data a času.

Chcete-li explicitně určit, že řetězec by měl být formátován pomocí konvencí určené jazykové verze nebo [invariantní jazykové verze](xref:System.Globalization.CultureInfo.InvariantCulture), můžete provést následující kroky:

- Při použití <xref:System.String.Format%2A?displayProperty=nameWithType> `ToString` metody a, volání přetížení, který `provider` má parametr, jako <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> je <xref:System.Globalization.CultureInfo> například <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> nebo <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType>, a <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType> předat vlastnost, instance, která představuje požadovanou jazykovou verzi nebo vlastnost.

- Pro zřetězení řetězce nepovolte kompilátoru provádět žádné implicitní převody. Místo toho proveďte explicitní `ToString` převod voláním `provider` přetížení, které má parametr. Například kompilátor implicitně používá aktuální jazykovou <xref:System.Double> verzi při převodu hodnoty na řetězec v následujícím kódu jazyka C#:

  [!code-csharp[Implicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#1)]

  Místo toho můžete explicitně určit jazykovou verzi, jejíž formátování <xref:System.Double.ToString(System.IFormatProvider)?displayProperty=nameWithType> konvence se používají v převodu voláním metody, jako následující kód Jazyka C#:

  [!code-csharp[Explicit String Conversion](~/samples/snippets/standard/base-types/string-practices/cs/tostring.cs#2)]

- Pro interpolaci řetězců, nikoli přiřazení interpolovaného <xref:System.String> řetězce k instanci, přiřaďte ji k . <xref:System.FormattableString> Potom můžete volat <xref:System.FormattableString.ToString?displayProperty=nameWithType> jeho metoda vytvořit výsledný řetězec, který odráží konvence aktuální jazykové <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> verze, nebo můžete volat metodu k vytvoření výsledný řetězec, který odráží konvence zadané jazykové verze. Formátovatelný řetězec můžete také předat <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> statické metodě a vytvořit výsledný řetězec, který odráží konvence invariantní jazykové verze. Tento postup znázorňuje následující příklad. (Výstup z příkladu odráží aktuální jazykovou verzi en US.)

  [!code-csharp[String interpolation](~/samples/snippets/standard/base-types/string-practices/cs/formattable.cs)]
  [!code-vb[String interpolation](~/samples/snippets/standard/base-types/string-practices/vb/formattable.vb)]

Můžete zachovat non-string data buď jako binární data nebo jako formátovaná data. Pokud se rozhodnete uložit jako formátovaná data, měli byste zavolat `provider` přetížení metody formátování, které obsahuje parametr, a předat mu <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost. Invariantní jazyková verze poskytuje konzistentní formát pro formátovaná data, která je nezávislá na jazykové verzi a počítači. Naproti tomu trvalá data, která je formátována pomocí jazykové verze než invariantní jazykové verze má řadu omezení:

- Data je pravděpodobně nepoužitelná, pokud je načtena v systému, který má jinou jazykovou verzi, nebo pokud uživatel aktuálního systému změní aktuální jazykovou verzi a pokusí se načíst data.
- Vlastnosti jazykové verze v určitém počítači se mohou lišit od standardních hodnot. Uživatel může kdykoli přizpůsobit nastavení zobrazení zkoumaná jazykovou verzi. Z tohoto důvodu formátovaná data uložená v systému nemusí být čitelná poté, co uživatel přizpůsobí nastavení kultury. Přenositelnost formátovaných dat mezi počítači bude pravděpodobně ještě omezenější.
- Mezinárodní, regionální nebo národní standardy, které řídí formátování čísel nebo dat a časů, se v průběhu času mění a tyto změny jsou začleněny do aktualizací operačního systému Windows. Při změně formátování konvence, data, která byla formátována pomocí předchozích konvencí může stát nečitelný.

Následující příklad ilustruje omezenou přenositelnost, která je výsledkem použití formátování citlivé ho jazykové verze k uchování dat. Příklad ukládá do souboru pole hodnot data a času. Ty jsou formátovány pomocí konvencí jazykové verze Angličtina (Spojené státy). Poté, co aplikace změní aktuální jazykovou verzi vlákna na francouzštinu (Švýcarsko), pokusí se číst uložené hodnoty pomocí konvencí formátování aktuální jazykové verze. Pokus o čtení dvou datových položek <xref:System.FormatException> vyvolá výjimku a pole dat nyní obsahuje <xref:System.DateTime.MinValue>dva nesprávné prvky, které se rovnají .

[!code-csharp[Conceptual.Strings.BestPractices#21](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/persistence.cs#21)]
[!code-vb[Conceptual.Strings.BestPractices#21](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/persistence.vb#21)]

Pokud však nahradíte <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost ve <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> volání <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>do a , budou trvalá data data a času úspěšně obnovena, jak ukazuje následující výstup:

```console
06.05.1758 21:26
05.05.1818 07:19
22.04.1870 23:54
08.09.1890 06:47
18.02.1905 15:12
```

## <a name="see-also"></a>Viz také

- [Práce s řetězci](manipulating-strings.md)
