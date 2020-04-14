---
title: Vlastní řetězce číselného formátu
ms.date: 06/25/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- format strings
- custom numeric format strings
- numbers [.NET Framework], formatting
- format specifiers, numeric
- formatting numbers [.NET Framework]
- format specifiers, custom numeric format strings
ms.assetid: 6f74fd32-6c6b-48ed-8241-3c2b86dea5f4
ms.openlocfilehash: 5961cce4601a89b34708b7090207edfed63b5b08
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242982"
---
# <a name="custom-numeric-format-strings"></a>Vlastní řetězce číselného formátu

Lze vytvořit vlastní číselný formátovací řetězec, který se skládá z jednoho nebo několika vlastních číselných specifikátorů pro definování formátování číselných dat. Vlastní číselný formátovací řetězec je libovolný formátovací řetězec, který není [standardním číselným formátovacím řetězcem](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Vlastní číselné formátovací řetězce jsou podporovány některými přetíženími `ToString` metody všech číselných typů. Můžete například zadat číselný formátovací <xref:System.Int32.ToString%28System.String%29> <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29> řetězec a <xref:System.Int32> metody typu. Vlastní číselné formátovací řetězce jsou také podporovány [funkcí složeného](../../../docs/standard/base-types/composite-formatting.md)formátování `Write` `WriteLine` .NET <xref:System.Console> , <xref:System.IO.StreamWriter> která <xref:System.String.Format%2A?displayProperty=nameWithType> je používána <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> některými metodami a třídami a, metodou a metodou. Funkce [interpolace řetězců](../../csharp/language-reference/tokens/interpolated.md) také podporuje vlastní číselné formátovací řetězce.

> [!TIP]
> Můžete si stáhnout **nástroj Formátování**, aplikaci .NET Core Windows Forms, která umožňuje použít formátovací řetězce na číselné hodnoty nebo hodnoty data a času a zobrazí výsledný řetězec. Zdrojový kód je k dispozici pro [c#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) a [visual basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb).

<a name="table"></a>Následující tabulka popisuje vlastní specifikátory číselného formátu a zobrazuje ukázkový výstup vytvořený každým specifikátorem formátu. Další informace o použití vlastních číselných formátovacích řetězců a v části [Příklad](#example) naleznete v části [Poznámky,](#NotesCustomFormatting) kde naleznete komplexní ilustraci jejich použití.

|Specifikátor formátu|Name (Název)|Popis|Příklady|
|----------------------|----------|-----------------|--------------|
|"0"|Zástupný symbol nula|Nahradí nulu odpovídající číslicí, pokud je dostupná. V opačném případě se nula zobrazí ve výsledném řetězci.<br /><br /> Další informace: [Vlastní specifikátor "0"](#Specifier0).|1234.5678 ("00000") -> 01235<br /><br /> 0,45678 ("0,00", cs) -> 0,46<br /><br /> 0,45678 ("0,00", fr-FR) -> 0,46|
|"#"|Zástupný symbol číslice|Nahradí znak "#" odpovídající číslicí, pokud je k dispozici. V opačném případě se ve výsledném řetězci nezobrazí žádná číslice.<br /><br /> Všimněte si, že žádná číslice se zobrazí ve výsledném řetězci, pokud odpovídající číslice ve vstupním řetězci je nevýznamné 0. Například 0003 ("####") -> 3.<br /><br /> Další informace: [Vlastní specifikátor "#"](#SpecifierD).|1234.5678 ("####") -> 1235<br /><br /> 0,45678 ("#.##", cs.) -> .46<br /><br /> 0,45678 ("#.##", fr-FR) -> ,46|
|"."|Desetinná tečka|Určuje umístění oddělovače desetinných míst ve výsledném řetězci.<br /><br /> Více informací: ["." Vlastní specifikátor](#SpecifierPt).|0,45678 ("0,00", cs) -> 0,46<br /><br /> 0,45678 ("0,00", fr-FR) -> 0,46|
|","|Oddělovač skupin a číselné měřítko|Slouží jako oddělovač skupin a specifikátor číselného měřítka. Jako oddělovač skupin vloží znak oddělovače skupiny podle jazykové verze mezi jednotlivé skupiny. Jako specifikátor měřítka rozdělí číslo po 1000 pro každou zadanou čárku.<br /><br /> Další informace: ["," Vlastní specifikátor](#SpecifierTh).|Specifikátor oddělovače skupin:<br /><br /> 2147483647 ("##,#", cs.) -> 2 147 483 647<br /><br /> 2147483647 ("##,#", es-ES) -> 2.147.483.647<br /><br /> Specifikátor měřítka:<br /><br /> 2147483647 ("#,#,,", cs) -> 2 147<br /><br /> 2147483647 ("#,#,,", es-ES) -> 2,147|
|"%"|Zástupný znak procent|Vynásobí číslo 100 a vloží do výsledného řetězce symbol procenta podle jazykové verze.<br /><br /> Další informace: [Vlastní specifikátor %.](#SpecifierPct)|0,3697 (%#0,00", cs-US) -> %36,97<br /><br /> 0,3697 (%#0,00", el-GR) -> %36,97<br /><br /> 0,3697 ("##.0 %", cs)-> 37,0 %<br /><br /> 0,3697 ("##.0 %", el-GR) -> 37,0 %|
|"‰"|Zástupný symbol promile|Vynásobí číslo 1000 a vloží do výsledného řetězce symbol promile podle jazykové verze.<br /><br /> Další informace: [Vlastní specifikátor "‰"](#SpecifierPerMille).|0,03697 ("#0.00‰", cs) -> 36,97 ‰<br /><br /> 0,03697 ("#0.00‰", ru-RU) -> 36,97‰|
|"E0"<br /><br /> "E+0"<br /><br /> "E-0"<br /><br /> "e0"<br /><br /> "e+0"<br /><br /> "e-0"|Exponenciální zápis|Pokud následuje alespoň jedna 0 (nula), zformátuje výsledek pomocí exponenciálního zápisu. Velikost písmen "E" nebo "e" označuje velikost symbolu exponentu ve výsledném řetězci. Počet nul následujících znak "E" nebo "e" určuje minimální počet číslic v exponentu. Znaménko plus (+) označuje, že znak znaménka vždy předchází exponent. Znaménko mínus (-) označuje, že znak znaménka předchází pouze u záporných exponentů.<br /><br /> Další informace: [Vlastní specifikátory "E" a "e"](#SpecifierExponent).|987654 ("#0.0e0") -> 98,8e4<br /><br /> 1503.92311 ("0.0##e+00") -> 1.504e+03<br /><br /> 1.8901385E-16 ("0.0e+00") -> 1.9e-16|
|"\\"|Řídicí znak|Způsobí, že následující znak je interpretován jako literál, nikoli jako specifikátor vlastního formátu.<br /><br /> Další informace: ["\\" Escape Character](#SpecifierEscape).|987654 ("\\###00\\#") -> #987654 #|
|'*řetězec*'<br /><br /> "*řetězec*"|Oddělovač řetězcového literálu|Označuje, že uzavřené znaky by měly být zkopírovány do výsledného řetězce beze změny.<br/><br/>Další informace: [Literály znaků](#character-literals).|68 ("# 'stupňů'") -> 68 stupňů<br /><br /> 68 ("#' stupňů'") -> 68 stupňů|
|;|Oddělovač oddílů|Definuje oddíly se zvláštními formátovacími řetězci pro kladná, záporná a nulová čísla.<br /><br /> Více informací: [";" Oddělovač řezu](#SectionSeparator).|12.345 ("#0.0#;(#0.0#);-\0-") -> 12,35<br /><br /> 0 ("#0.0#;(#0.0.0#);-\0-") -> -0-<br /><br /> -12,345 ("#0.0#;(#0.0#);-\0-") -> (12,35)<br /><br /> 12.345 ("#0.0#;(#0.0#)") -> 12,35<br /><br /> 0 ("#0.0#;(#0.0#)") -> 0,0<br /><br /> -12,345 (#0.0#;(#0.0#))) -> (12,35).|
|Ostatní|Všechny ostatní znaky|Znak je zkopírován do výsledného řetězce beze změny.<br/><br/>Další informace: [Literály znaků](#character-literals).|68 ("# °") -> 68 °|

V následujících částech jsou uvedeny podrobné informace o jednotlivých vlastních specifikátorech číselného formátu.

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-partial-note.md)]

<a name="Specifier0"></a>

## <a name="the-0-custom-specifier"></a>Vlastní specifikátor "0"

Specifikátor vlastního formátu "0" slouží jako zástupný symbol nuly. Pokud právě formátovaná hodnota má číslici na pozici, kde se zobrazí nula ve formátovacím řetězci, je tato číslice zkopírována do výsledného řetězce. V opačném případě se ve výsledném řetězci zobrazí nula. Pozice nuly nejvíce vlevo od desetinné čárky a nuly nejvíce vpravo od desetinné čárky určuje rozsah číslic, které jsou vždy obsaženy ve výsledném řetězci.

Specifikátor "00" způsobí, že hodnota se zaokrouhlí na nejbližší číslici předcházející desítky, kde je vždy použito zaokrouhlení směrem od nuly. Například formátování 34,5 se specifikátorem "00" dává výslednou hodnotu 35.

Následující příklad zobrazí několik hodnot, které jsou formátovány pomocí vlastních formátovacích řetězců, které obsahují zástupné symboly nuly.

[!code-cpp[Formatting.Numeric.Custom#1](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#1)]
[!code-csharp[Formatting.Numeric.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#1)]
[!code-vb[Formatting.Numeric.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#1)]

[Zpět na stůl](#table)

<a name="SpecifierD"></a>

## <a name="the--custom-specifier"></a>Vlastní specifikátor "#"

Specifikátor vlastního formátu "#" slouží jako zástupný symbol číslice. Pokud právě formátovaná hodnota má číslici na pozici, kde se nachází ve formátovacím řetězci znak "#", zkopíruje se číslice do výsledného řetězce. V opačném případě není na této pozici v řetězci uloženo nic.

Tento specifikátor nikdy nezobrazí nulu, která není platnou číslici, a to ani v případě, že je nula jedinou číslicí v řetězci. Nulu zobrazí pouze v případě, že je podstatnou číslicí v zobrazeném řetězci.

Formátovací řetězec "## "způsobí, že hodnota se zaokrouhlí na nejbližší číslici předcházející desítky, kde je vždy použito zaokrouhlení směrem od nuly. Například formátování 34,5 se specifikátorem "##" dává výslednou hodnotu 35.

Následující příklad zobrazí několik hodnot, které jsou formátovány pomocí vlastních formátovacích řetězců, které obsahují zástupné symboly číslice.

[!code-cpp[Formatting.Numeric.Custom#2](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#2)]
[!code-csharp[Formatting.Numeric.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#2)]
[!code-vb[Formatting.Numeric.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#2)]

Chcete-li vrátit výsledný řetězec, ve kterém jsou chybějící číslice nebo počáteční nuly nahrazeny mezerami, použijte [prvek složeného formátování](../../../docs/standard/base-types/composite-formatting.md) a určete šířku pole, jak ukazuje následující příklad.

[!code-cpp[Formatting.Numeric.Custom#12](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/SpaceOrDigit1.cpp#12)]
[!code-csharp[Formatting.Numeric.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/SpaceOrDigit1.cs#12)]
[!code-vb[Formatting.Numeric.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/SpaceOrDigit1.vb#12)]

[Zpět na stůl](#table)

<a name="SpecifierPt"></a>

## <a name="the--custom-specifier"></a>Vlastní specifikátor "."

Specifikátor vlastního formátu "." vloží lokalizovaný oddělovač desetinných míst do výsledného řetězce. První tečka ve formátovacím řetězci určuje umístění oddělovače desetinných míst ve formátované hodnotě. Jakékoli další tečky jsou ignorovány.

Znak, který se používá jako oddělovač desetinného místa ve výsledném řetězci, není vždy tečkou; je určena <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> vlastností objektu, <xref:System.Globalization.NumberFormatInfo> který řídí formátování.

Následující příklad používá specifikátor formátu "." pro určení umístění desetinné tečky v několika výsledných řetězcích.

[!code-cpp[Formatting.Numeric.Custom#3](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#3)]
[!code-csharp[Formatting.Numeric.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#3)]
[!code-vb[Formatting.Numeric.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#3)]

[Zpět na stůl](#table)

<a name="SpecifierTh"></a>

## <a name="the--custom-specifier"></a>Vlastní specifikátor ","

Znak "," slouží jako oddělovač skupin a specifikátor číselného měřítka.

- Oddělovač skupin: Pokud je zadána jedna nebo více čárek mezi dva zástupné znaky pro číslice (0 nebo #), které formátují integrální číslice čísla, je znak oddělovače skupin vložen mezi každou číselnou skupinu do integrální části výstupu.

  <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A> Vlastnosti <xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A> a aktuálního <xref:System.Globalization.NumberFormatInfo> objektu určují znak použitý jako oddělovač číselných skupin a velikost každé číselné skupiny. Pokud je například pro formátování čísla 1000 použit řetězec "#,#" a invariantní jazyková verze, zobrazí se výstup "1,000".

- Specifikátor číselného měřítka: Pokud je zadána jedna nebo více čárek bezprostředně vlevo od explicitní nebo implicitní desetinné tečky, pak číslo, které má být formátováno, je vyděleno hodnotou 1000 pro každou tečku. Pokud je pro formátování čísla 100 milionů použit například řetězec "0,," , je výsledná hodnota "100".

Můžete použít oddělovač skupin a specifikátory číselného měřítka ve stejném formátovacím řetězci. Pokud je pro formátování čísla jedna miliarda použit například řetězec "#,0,," a invariantní jazyková verze, zobrazí se výstup "1,000".

Následující příklad ukazuje použití čárky jako oddělovače skupin.

[!code-cpp[Formatting.Numeric.Custom#4](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#4)]
[!code-csharp[Formatting.Numeric.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#4)]
[!code-vb[Formatting.Numeric.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#4)]

Následující příklad ukazuje použití čárky jako specifikátoru číselného měřítka.

[!code-cpp[Formatting.Numeric.Custom#5](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#5)]
[!code-csharp[Formatting.Numeric.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#5)]
[!code-vb[Formatting.Numeric.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#5)]

[Zpět na stůl](#table)

<a name="SpecifierPct"></a>

## <a name="the--custom-specifier"></a>Vlastní specifikátor %

Znak procent (%) ve formátovacím řetězci způsobí, že číslo bude vynásobené hodnotou 100 dříve, než je formátováno. Lokalizovaný symbol procenta je vložen do čísla na místo, kde se % vyskytuje ve formátovacím řetězci. Použitý znak procenta je <xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A> definován vlastností <xref:System.Globalization.NumberFormatInfo> aktuálního objektu.

Následující příklad definuje několik vlastních formátovacích řetězců, které obsahují vlastní specifikátor "%".

[!code-cpp[Formatting.Numeric.Custom#6](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#6)]
[!code-csharp[Formatting.Numeric.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#6)]
[!code-vb[Formatting.Numeric.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#6)]

[Zpět na stůl](#table)

<a name="SpecifierPerMille"></a>

## <a name="the--custom-specifier"></a>Vlastní specifikátor "‰"

Znak promile (‰ nebo \u2030) ve formátovacím řetězci způsobí, že číslo se vynásobí hodnotou 1000 dříve, než je formátováno. Příslušný symbol promile je vložen do vráceného řetězce na místě, kde se zobrazí symbol ‰ ve formátovacím řetězci. Použitý znak na promile je <xref:System.Globalization.NumberFormatInfo.PerMilleSymbol%2A?displayProperty=nameWithType> definován vlastností objektu, který poskytuje informace o formátování specifické pro jazykovou verzi.

Následující příklad definuje vlastní formátovací řetězec, který obsahuje vlastní specifikátor "‰".

[!code-cpp[Formatting.Numeric.Custom#9](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#9)]
[!code-csharp[Formatting.Numeric.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#9)]
[!code-vb[Formatting.Numeric.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#9)]

[Zpět na stůl](#table)

<a name="SpecifierExponent"></a>

## <a name="the-e-and-e-custom-specifiers"></a>Vlastní specifikátory "E" a "e"

Pokud je ve formátovacím řetězci přítomný některý z řetězců "E", "E+", "E-", "e", "e+" nebo "e-" a je okamžitě následován alespoň jednou nulou, je číslo formátováno pomocí vědeckého zápisu se znakem "E" nebo "e" vloženým mezi číslo a exponent. Počet nul následujících po indikátoru vědeckého zápisu určuje minimální počet číslic pro výstup exponentu. Formáty "E+" a "e+" označují, že znaménka plus nebo minus by měla vždy předcházet exponent. Formáty "E", "E-", "e" nebo "e-" označují, že znak znaménka by měl předcházet pouze záporné exponenty.

Následující příklad formátuje několik číselných hodnot pomocí specifikátorů pro vědecký zápis.

[!code-cpp[Formatting.Numeric.Custom#7](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#7)]
[!code-csharp[Formatting.Numeric.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#7)]
[!code-vb[Formatting.Numeric.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#7)]

[Zpět na stůl](#table)

<a name="SpecifierEscape"></a>

## <a name="the--escape-character"></a>"\\Escape charakter

Symboly "#", "0", ".", ",", "%" a "‰" jsou ve formátovacím řetězci interpretovány jako specifikátory formátu, nikoli jako literální znaky. V závislosti na jejich umístění ve vlastním formátovacím řetězci lze velké a malé písmeno "E" a také symboly + a - interpretovat jako specifikátory formátu.

Chcete-li zamezit interpretaci znaku jako specifikátoru formátu, lze před znak vložit zpětné lomítko (\), což je řídicí znak. Řídicí znak označuje, že následující znak je literální znak, který by měl být zařazen do výsledného řetězce beze změny.

Chcete-li zahrnout zpětné lomítko do výsledného řetězce,`\\`musíte jej uniknout s jiným zpětným lomítkem ( ).

> [!NOTE]
> Některé kompilátory, jako jsou například kompilátory jazyka C++ a jazyka C#, mohou také interpretovat jedno zpětné lomítko jako řídicí znak. Abyste se ujistili, zda je řetězec interpretován při formátování správně, můžete v jazyce C# použít literální řetězcový znak verbatim (znak @) před řetězcem, nebo v jazyce C# a C++ přidat další znak zpětného lomítka před každé zpětné lomítko. Následující příklad jazyka C# ukazuje oba přístupy.

Následující příklad používá řídicí znak, aby se zabránilo operaci formátování interpretovat znaky "#", "0" a "\\jako řídicí znaky nebo specifikátory formátu. Příklady jazyka C# používají další zpětné lomítko k tomu, aby zpětné lomítko bylo interpretováno jako literální znak.

[!code-cpp[Formatting.Numeric.Custom#11](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/escape1.cpp#11)]
[!code-csharp-interactive[Formatting.Numeric.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/escape1.cs#11)]
[!code-vb[Formatting.Numeric.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/escape1.vb#11)]

[Zpět na stůl](#table)

<a name="SectionSeparator"></a>

## <a name="the--section-separator"></a>Oddělovač oddílu ";"

Středník (;) je podmíněný specifikátor formátu, který aplikuje odlišné formátování pro číslo v závislosti na tom, zda je jeho hodnota kladná, záporná nebo nulová. Pro vytvoření takového typu formátování může vlastní formátovací řetězec obsahovat až tři oddíly oddělené středníky. Tyto oddíly jsou popsány v následující tabulce.

|Počet oddílů|Popis|
|------------------------|-----------------|
|Jeden oddíl|Formátovací řetězec se vztahuje na všechny hodnoty.|
|Dva oddíly|První oddíl je aplikován na kladné a nulové hodnoty a druhý oddíl je aplikován na záporné hodnoty.<br /><br /> Pokud číslo, které má být formátováno, je záporné, ale bude po zaokrouhlení podle formátu ve druhém oddílu rovno nule, bude výsledná nula formátována podle prvního oddílu.|
|Tři oddíly|První oddíl se používá pro kladná čísla, druhý oddíl pro záporné hodnoty a třetí oddíl pro nulové hodnoty.<br /><br /> Druhá část může být ponechána prázdná (tím, že mezi středníky nic nebude). V tomto případě se první část vztahuje na všechny nenulové hodnoty.<br /><br /> Pokud číslo, které má být formátováno, je nenulové, ale bude po zaokrouhlení podle formátu v prvním nebo druhém oddílu rovno nule, výsledná nula bude formátována podle třetího oddílu.|

Oddělovače oddílů ignorují všechna dříve existující formátování přidružená k číslu, pokud je na formátována konečná hodnota. Například záporné hodnoty se při použití oddělovače oddílu zobrazí vždy bez znaménka mínus. Pokud chcete, aby konečná formátovaná hodnota měla symbol mínus, měli byste explicitně zahrnout symbol mínus jako část specifikátoru vlastního formátu.

Následující příklad používá specifikátor formátu ";" pro formátování kladných, záporných a nulových čísel odlišným způsobem.

[!code-cpp[Formatting.Numeric.Custom#8](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#8)]
[!code-csharp-interactive[Formatting.Numeric.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#8)]
[!code-vb[Formatting.Numeric.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#8)]

[Zpět na stůl](#table)

## <a name="character-literals"></a>Literály znaků

Specifikátory formátu, které se zobrazují ve vlastním číselném formátovacím řetězci, jsou vždy interpretovány jako formátovací znaky a nikdy jako literálové znaky. To zahrnuje následující znaky:

- [0](#Specifier0)
- [\#](#SpecifierD)
- [%](#SpecifierPct)
- [‰](#SpecifierPerMille)
- '
- [\\](#SpecifierEscape)
- [.](#SpecifierPt)
- [,](#SpecifierTh)
- [E nebo e](#SpecifierExponent), v závislosti na jeho umístění ve formátovacím řetězci.

Všechny ostatní znaky jsou vždy interpretovány jako literály znaků a v operaci formátování jsou zahrnuty do výsledného řetězce beze změny.  V operaci analýzy musí přesně odpovídat znakům ve vstupním řetězci; porovnání se rozlišuje malá a velká písmena.

Následující příklad ilustruje jedno běžné použití jednotek literálu znaků (v tomto případě tisíce):

[!code-csharp-interactive[literal characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal2.cs#1)]
[!code-vb[literal characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal2.vb#1)]

Existují dva způsoby, jak označit, že znaky mají být interpretovány jako literálové znaky a nikoli jako formátovací znaky, aby mohly být zahrnuty do výsledného řetězce nebo úspěšně analyzovány ve vstupním řetězci:

- Únikem znak formátování. Další informace naleznete [v\\tématu " " escape character](#SpecifierEscape).

- Uzavřením celého literálu řetězce v uvozovkách apostrofů.

Následující příklad používá oba přístupy k zahrnutí vyhrazených znaků do vlastního číselného formátovacího řetězce.

[!code-csharp-interactive[including reserved characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal1.cs#1)]
[!code-vb[including reserved characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal1.vb#1)]

<a name="NotesCustomFormatting"></a>

## <a name="notes"></a>Poznámky

### <a name="floating-point-infinities-and-nan"></a>Nekonečna s plovoucí desetinnou tálicí a NaN

Bez ohledu na formátovací řetězec, <xref:System.Single> pokud <xref:System.Double> je hodnota typu nebo typu s plovoucí desetinnou desetinnou hodnotou kladné <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>nekonečno, záporné nekonečno nebo ne číslo (NaN), formátovaný řetězec je hodnota příslušného , <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>nebo <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> vlastnost i zadané aktuálně použitelným <xref:System.Globalization.NumberFormatInfo> objektem.

### <a name="control-panel-settings"></a>Nastavení Ovládacích panelů

Nastavení v ovládacím panelu **Místní a jazykové možnosti** ovlivňují výsledný řetězec vytvořený operací formátování. Tato nastavení se používají k <xref:System.Globalization.NumberFormatInfo> inicializaci objektu přidruženého k aktuální jazykové verzi vlákna a aktuální jazyková verze vlákna poskytuje hodnoty používané k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.

Kromě toho pokud <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> použijete konstruktor k vytvoření <xref:System.Globalization.CultureInfo> instance nového objektu, který představuje stejnou jazykovou verzi jako aktuální jazyková verze systému, <xref:System.Globalization.CultureInfo> budou na nový objekt použita všechna vlastní nastavení vytvořená položkou **Místní a jazykové možnosti** v Ovládacích panelech. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> Konstruktor můžete použít k <xref:System.Globalization.CultureInfo> vytvoření objektu, který neodráží vlastní nastavení systému.

### <a name="rounding-and-fixed-point-format-strings"></a>Zaokrouhlení a formátovací řetězce s pevnou hodem

Pro formátovací řetězce s pevnou desetinnou čárkou (což jsou formátovací řetězce, které neobsahují vědecké formátovací znaky) jsou čísla zaokrouhlena na tolik desetinných míst, kolik je zástupných symbolů číslic napravo od desetinné čárky. Pokud formátovací řetězec neobsahuje desetinnou čárku, bude číslo zaokrouhleno na nejbližší celé číslo. Pokud má dané číslo více číslic, než je počet zástupných symbolů číslic nalevo od desetinné čárky, jsou další číslice zkopírovány do výsledného řetězce bezprostředně před první zástupný symbol číslice.

[Zpět na stůl](#table)

<a name="example"></a>

## <a name="example"></a>Příklad

Následující příklad ukazuje dva vlastní číselné formátovací řetězce. V obou případech zástupný`#`symbol číslice ( ) zobrazí číselná data a všechny ostatní znaky se zkopírují do výsledného řetězce.

[!code-cpp[Formatting.Numeric.Custom#10](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/example1.cpp#10)]
[!code-csharp-interactive[Formatting.Numeric.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/example1.cs#10)]
[!code-vb[Formatting.Numeric.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/example1.vb#10)]

[Zpět na stůl](#table)

## <a name="see-also"></a>Viz také

- <xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Standardní číselné formátovací řetězce](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [Postupy: Vyplnění čísla úvodními nulami](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)
- [Ukázka: Nástroj pro formátování WinForms .NET (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Ukázka: Nástroj pro formátování WinForms .NET (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
