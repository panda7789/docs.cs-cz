---
title: Standardní řetězce formátu čísla
ms.date: 06/10/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- standard format strings, numeric
- format strings
- numbers [.NET Framework], formatting
- format specifiers, numeric
- standard numeric format strings
- formatting numbers [.NET Framework]
- format specifiers, standard numeric format strings
ms.openlocfilehash: 9b0c784a1c7b6b428636a1a4c99ec8e2bb76a9e0
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242709"
---
# <a name="standard-numeric-format-strings"></a>Standardní řetězce formátu čísla

Řetězce standardního číselného formátu se používají pro formátování běžných číselných typů. Standardní číselný formátovací `Axx`řetězec má podobu , kde:

- `A`je jeden abecední znak nazývaný *specifikátor formátu*. Jakýkoli řetězec číselného formátu, který obsahuje více než jeden abecední znak, včetně prázdných znaků, je interpretován jako řetězec vlastního číselného formátu. Další informace naleznete [v tématu Vlastní číselné formátovací řetězce](../../../docs/standard/base-types/custom-numeric-format-strings.md).

- `xx`je volitelné celé číslo nazývané *specifikátor přesnosti*. Specifikátor přesnosti má rozsah od 0 do 99 a má vliv na počet číslic ve výsledku. Všimněte si, že specifikátor přesnosti řídí počet číslic v řetězcové reprezentaci čísla. Neprovádí zaokrouhlení samotného čísla. Chcete-li provést operaci zaokrouhlení, použijte metodu <xref:System.Math.Ceiling%2A?displayProperty=nameWithType>, <xref:System.Math.Floor%2A?displayProperty=nameWithType>nebo <xref:System.Math.Round%2A?displayProperty=nameWithType> metodu.

  Když *specifikátor přesnosti* řídí počet desetinných číslic ve výsledném řetězci, výsledný řetězec odráží číslo, které je zaokrouhleno na reprezentativní výsledek, který je nejblíže nekonečně přesnému výsledku. Pokud existují dva stejně blízké reprezentativní výsledky:
  - **V rozhraní .NET Framework a .NET Core až do .NET Core 2.0**vybere runtime výsledek <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>s větší nejméně významnou číslicí (tj. pomocí ).
  - **Na .NET Core 2.1 a novější**, runtime vybere výsledek s ještě <xref:System.MidpointRounding.ToEven?displayProperty=nameWithType>nejméně významné číslice (to znamená pomocí ).

  > [!NOTE]
  > Specifikátor přesnosti určuje počet číslic ve výsledném řetězci. Chcete-li vytvořit výsledný řetězec s úvodními nebo koncovými mezerami, použijte prvek [složeného formátování](../../../docs/standard/base-types/composite-formatting.md) a definujte *komponentu zarovnání* v položce formátu.

Standardní číselné formátovací řetězce jsou podporovány:

- Některé přetížení `ToString` metody všech číselných typů. Metodám <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> a <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> můžete například zadat číselný formátovací řetězec.

- [Funkce složeného formátování](../../../docs/standard/base-types/composite-formatting.md).NET , která `Write` je `WriteLine` používána <xref:System.Console> <xref:System.IO.StreamWriter> některými <xref:System.String.Format%2A?displayProperty=nameWithType> metodami a <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> třídy, metoda a metoda. Funkce složeného formátu umožňuje zahrnout řetězcovou reprezentaci více datových položek do jednoho řetězce, určit šířku pole a zarovnat čísla v poli. Další informace naleznete [v tématu Kompozitní formátování](../../../docs/standard/base-types/composite-formatting.md).

- [Interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md) v jazyce C# a visual basicu, které poskytují zjednodušenou syntaxi ve srovnání s složenými formátovacími řetězci.

> [!TIP]
> Můžete si stáhnout **nástroj Formátování**, aplikaci .NET Core Windows Forms, která umožňuje použít formátovací řetězce na číselné hodnoty nebo hodnoty data a času a zobrazí výsledný řetězec. Zdrojový kód je k dispozici pro [c#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) a [visual basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb).

<a name="table"></a>Následující tabulka popisuje specifikátory standardního číselného formátu a zobrazuje ukázkový výstup vytvořený každým specifikátorem formátu. Další informace o používání standardních číselných formátovacích řetězců a v části [Příklad](#example) naleznete v části [Poznámky,](#NotesStandardFormatting) kde naleznete komplexní ilustraci jejich použití.

|Specifikátor formátu|Name (Název)|Popis|Příklady|
|----------------------|----------|-----------------|--------------|
|"C" nebo "c"|Měna|Výsledek: hodnota měny.<br /><br /> Podporováno: všemi číselnými typy.<br /><br /> Specifikátor přesnosti: počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: Definováno . <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType><br /><br /> Další informace: [Specifikátor formátu Měna ("C").](#CFormatString)|123.456 ("C", cs-US) \\-> $123.46<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> 123 jenů<br /><br /> -123.456 ("C3", cs-> (\\123.456 dolarů)<br /><br /> -123.456 ("C3", fr-FR) -> -123 456 €<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|
|"D" nebo "d"|Desetinné číslo|Výsledek: celá čísla s volitelným záporným znaménkem.<br /><br /> Podporováno: pouze integrálovými typy.<br /><br /> Specifikátor přesnosti: minimální počet číslic.<br /><br /> Výchozí specifikátor přesnosti: minimální požadovaný počet číslic.<br /><br /> Další informace: [Specifikátor formátu Decimal("D")](#DFormatString).|1234 ("D") -> 1234<br /><br /> -1234 ("D6") -> -001234|
|"E" nebo "e"|Exponenciální (vědecký) zápis|Výsledek: exponenciální zápis.<br /><br /> Podporováno: všemi číselnými typy.<br /><br /> Specifikátor přesnosti: počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: 6.<br /><br /> Další informace: [Exponenciální ("E") Specifikátor formátu](#EFormatString).|1052.0329112756 ("E", cs) -> 1,052033E+003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1,052033e+003<br /><br /> -1052.0329112756 ("e2", en-US) -> -1,05e+003<br /><br /> -1052.0329112756 ("E2", fr-FR) -> -1,05E+003|
|"F" nebo "f"|Pevná desetinná čárka|Výsledek: integrální a desítkové číslo s volitelným záporným znaménkem.<br /><br /> Podporováno: všemi číselnými typy.<br /><br /> Specifikátor přesnosti: počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: Definováno . <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType><br /><br /> Další informace: [Specifikátor formátu s pevným bodem ("F")](#FFormatString).|1234.567 ("F", cs-US) -> 1234,57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1", cs) -> 1234,0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234,56 ("F4", cs) -> -1234,5600<br /><br /> -1234,56 ("F4", de-DE) -> -1234 5600|
|"G" nebo "g"|Obecné|Výsledek: Čím kompaktnější je buď zápis s pevným bodem, nebo vědecký zápis.<br /><br /> Podporováno: všemi číselnými typy.<br /><br /> Specifikátor přesnosti: počet nejvýznamnějších číslic.<br /><br /> Výchozí specifikátor přesnosti: závisí na číselném typu.<br /><br /> Další informace: [Obecný ("G") Specifikátor formátu](#GFormatString).|-123.456 ("G", cs.) -> -123,456<br /><br /> -123.456 ("G", sv-SE) -> -123 456 .<br /><br /> 123.4546 ("G4", cs.) -> 123,5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1,234567890e-25 ("G", en-US) -> -1,23456789E-25<br /><br /> -1,234567890e-25 ("G", sv-SE) -> -1,23456789E-25|
|"N" nebo "n"|Číslo|Výsledek: integrální a desítkové číslice, oddělovače skupin a oddělovač desetinných míst s volitelným záporným znaménkem.<br /><br /> Podporováno: všemi číselnými typy.<br /><br /> Specifikátor přesnosti: požadovaný počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: Definováno . <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType><br /><br /> Další informace: [Numerický (N") Specifikátor formátu](#NFormatString).|1234.567 ("N", cs) -> 1 234,57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1", cs) -> 1 234,0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234,56 ("N3", cs)-> -1 234,560 ....<br /><br /> -1234,56 ("N3", ru-RU) -> -1 234 560|
|"P" nebo "p"|Procento|Výsledek: číslo vynásobené číslem 100 a zobrazené se symbolem procenta.<br /><br /> Podporováno: všemi číselnými typy.<br /><br /> Specifikátor přesnosti: požadovaný počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: Definováno . <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType><br /><br /> Další informace: [Specifikátor formátu Procentuální (P).](#PFormatString)|1 ("P", cs) -> 100,00 %<br /><br /> 1 ("P", fr-FR) -> 100,00 %<br /><br /> -0,39678 ("P1", cs) -> -39,7 %<br /><br /> -0,39678 ("P1", fr-FR) -> -39,7 %|
|"R" nebo "r"|Zpáteční převod|Výsledek: řetězec, který může použít operaci zpátečního převodu na stejné číslo.<br /><br /> Podporováno: <xref:System.Single> <xref:System.Double>, <xref:System.Numerics.BigInteger>, a .<br /><br /> Poznámka: Doporučeno <xref:System.Numerics.BigInteger> pouze pro daný typ. Pro <xref:System.Double> typy použijte "G17"; pro <xref:System.Single> typy použijte "G9". <br> Specifikátor přesnosti: ignorováno.<br /><br /> Další informace: [Specifikátor formátu Round-trip ("R")](#RFormatString).|123456789.12345678 ("R") -> 123456789.12345678<br /><br /> -1234567890.12345678 ("R") -> -1234567890.1234567|
|"X" nebo "x"|Šestnáctková hodnota|Výsledek: šestnáctkový řetězec.<br /><br /> Podporováno: pouze integrálovými typy.<br /><br /> Specifikátor přesnosti: počet číslic ve výsledném řetězci.<br /><br /> Další informace: [HexaDecimal ("X") Specifikátor formátu](#XFormatString).|255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|
|Jakýkoli jiný samostatný znak|Neznámý specifikátor|Výsledek: Vyvolá <xref:System.FormatException> za běhu.||

<a name="Using"></a>

## <a name="using-standard-numeric-format-strings"></a>Používání řetězců standardního číselného formátu

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Řetězec standardního číselného formátu lze použít pro definování formátování číselné hodnoty jedním ze dvou způsobů:

- Může být předán přetížení `ToString` metody, která `format` má parametr. Následující příklad formátuje číselnou hodnotu jako řetězec měny v aktuální jazykové verzi (v tomto případě jazykové verzi en US).

  [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
  [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]

- Může být zadán `formatString` jako argument ve formátu položky <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>používané <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>s takovými metodami jako , a . Další informace naleznete [v tématu Kompozitní formátování](../../../docs/standard/base-types/composite-formatting.md). Následující příklad používá položku formátu pro vložení hodnoty měny do řetězce.

  [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
  [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]

  Volitelně můžete zadat `alignment` argument k určení šířky číselného pole a zda je jeho hodnota zarovnána doprava nebo doleva. Následující příklad vlevo zarovná hodnotu měny v poli o 28 znacích a v poli se 14 znaky zarovná hodnotu měny doprava.

  [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
  [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]

- Může být zadán `formatString` jako argument v interpolované výrazové položce interpolovaného řetězce. Další informace naleznete v tématu [Interpolace řetězce](../../csharp/language-reference/tokens/interpolated.md) v odkazu Jazyka C# nebo v tématu [interpolovaných řetězců](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) v odkazu jazyka Visual Basic.

Následující oddíly obsahují podrobné informace o jednotlivých řetězcích standardního číselného formátu.

<a name="CFormatString"></a>

## <a name="the-currency-c-format-specifier"></a>Specifikátor formátu měny ("C")

Specifikátor formátu "C" (neboli měny) převede číslo na řetězec, který představuje peněžní částku. Specifikátor přesnosti označuje požadovaný počet desetinných míst ve výsledném řetězci. Pokud je specifikátor přesnosti vynechán, výchozí přesnost <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> je definována vlastností.

Pokud má formátovaná hodnota větší než zadaný nebo výchozí počet desetinných míst, je desetinná hodnota ve výsledném řetězci zaokrouhlena. Pokud je vpravo od zadaného počtu desetinných míst hodnota 5 nebo vyšší, bude poslední číslice ve výsledném řetězci zaokrouhlena směrem nahoru.

Výsledný řetězec je ovlivněn informacemi o formátování <xref:System.Globalization.NumberFormatInfo> aktuálního objektu. V následující tabulce <xref:System.Globalization.NumberFormatInfo> jsou uvedeny vlastnosti, které řídí formátování vráceného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Definuje umístění symbolu měny pro kladné hodnoty.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Definuje umístění symbolu měny pro záporné hodnoty a určuje, zda je záporné znaménko reprezentováno závorky nebo vlastností. <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje záporné znaménko použité, pokud <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> označuje, že se nepoužívají závorky.|
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Definuje symbol měny.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Definuje výchozí počet desítkových číslic v hodnotě měny. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální a desítkové číslice.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Definuje řetězec, který odděluje skupiny integrálních čísel.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Definuje počet celých číslic, které se zobrazují ve skupině.|

Následující příklad formátuje <xref:System.Double> hodnotu pomocí specifikátoru formátu měny:

[!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
[!code-csharp[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
[!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]

[Zpět na stůl](#table)

<a name="DFormatString"></a>

## <a name="the-decimal-d-format-specifier"></a>Specifikátor formátu desítkového čísla ("D")

Specifikátor formátu "D" (desítkové číslo) převede číslo na řetězec desítkových číslic (0-9), kterému předchází symbol mínus, je-li číslo záporné. Tento formát je podporován pouze pro integrální typy.

Specifikátor přesnosti označuje minimální počet číslic požadovaných ve výsledném řetězci. V případě potřeby je číslo doplněno nulami po levé straně za účelem vytvoření počtu číslic, který je dán specifikátorem přesnosti. Pokud není zadán žádný specifikátor přesnosti, je výchozí hodnotou minimální hodnota požadovaná k vytvoření celého čísla bez počátečních nul.

Výsledný řetězec je ovlivněn informacemi o formátování <xref:System.Globalization.NumberFormatInfo> aktuálního objektu. Jak znázorňuje následující tabulka, jediná vlastnost ovlivňuje formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|

Následující příklad formátuje <xref:System.Int32> hodnotu pomocí specifikátoru desítkového formátu.

[!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
[!code-csharp-interactive[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
[!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]

[Zpět na stůl](#table)

<a name="EFormatString"></a>

## <a name="the-exponential-e-format-specifier"></a>Exponenciální specifikátor formátu ("E")

Exponenciální specifikátor formátu ("E") převede číslo na řetězec ve formě "-d.ddd…E+ddd" nebo "-d.ddd…e+ddd", kde každé "d" označuje číslici (0-9). Pokud je číslo záporné, řetězec začíná symbolem mínus. Desetinné čárce předchází vždy přesně jedna číslice.

Specifikátor přesnosti označuje požadovaný počet číslic za desetinnou čárkou. Pokud specifikátor přesnosti vynecháte, je za desetinnou čárkou použit výchozí počet šesti číslic.

Velikost specifikátoru formátu označuje, zda má být před exponentem použita předpona "E" nebo "e". Exponent se skládá vždy ze znaménka plus nebo mínus a minimálně tří číslic. Aby byl tento minimální požadavek splněn, je exponent v případě potřeby doplněn nulami.

Výsledný řetězec je ovlivněn informacemi o formátování <xref:System.Globalization.NumberFormatInfo> aktuálního objektu. V následující tabulce <xref:System.Globalization.NumberFormatInfo> jsou uvedeny vlastnosti, které řídí formátování vráceného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné pro koeficient i pro exponent.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic v koeficientu.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Definuje řetězec, který označuje, že exponent je kladný.|

Následující příklad formátuje <xref:System.Double> hodnotu pomocí specifikátoru exponenciálního formátu:

[!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
[!code-csharp[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
[!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]

[Zpět na stůl](#table)

<a name="FFormatString"></a>

## <a name="the-fixed-point-f-format-specifier"></a>Specifikátor formátu s pevnou desetinnou čárkou ("F")

Specifikátor formátu s pevným bodem ("F") převede číslo na řetězec formuláře "-ddd.ddd..." kde každé "d" označuje číslici (0-9). Pokud je číslo záporné, řetězec začíná symbolem mínus.

Specifikátor přesnosti označuje požadovaný počet desetinných míst. Pokud je specifikátor přesnosti vynechán, aktuální <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> vlastnost poskytuje číselnou přesnost.

Výsledný řetězec je ovlivněn informacemi o formátování <xref:System.Globalization.NumberFormatInfo> aktuálního objektu. V následující tabulce jsou <xref:System.Globalization.NumberFormatInfo> uvedeny vlastnosti objektu, které řídí formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definuje výchozí počet desítkových číslic. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|

Následující příklad formátuje <xref:System.Double> hodnotu a a hodnotu <xref:System.Int32> s specifikátorem formátu s pevným bodem:

[!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
[!code-csharp[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
[!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]

[Zpět na stůl](#table)

<a name="GFormatString"></a>

## <a name="the-general-g-format-specifier"></a>Specifikátor obecného formátu ("G")

Obecný specifikátor formátu ("G") převede číslo na kompaktnější buď pevný bod, nebo vědecký zápis, v závislosti na typu čísla a na tom, zda je k dispozici specifikátor přesnosti. Specifikátor přesnosti definuje maximální počet platných číslic, které mohou být zobrazeny ve výsledném řetězci. Pokud specifikátor přesnosti vynecháte nebo je specifikátor nulový, pak typ čísla určuje výchozí přesnost, jak je uvedeno v následující tabulce.

|Číselný typ|Výchozí přesnost|
|------------------|-----------------------|
|<xref:System.Byte> nebo <xref:System.SByte>|3 číslice|
|<xref:System.Int16> nebo <xref:System.UInt16>|5 číslic|
|<xref:System.Int32> nebo <xref:System.UInt32>|10 číslic|
|<xref:System.Int64>|19 číslic|
|<xref:System.UInt64>|20 číslic|
|<xref:System.Numerics.BigInteger>|Neomezené (stejné jako ["R"](#RFormatString))|
|<xref:System.Single>|7 číslic|
|<xref:System.Double>|15 číslic|
|<xref:System.Decimal>|29 číslic|

Zápis s pevnou desetinnou čárkou se používá v případě, že exponent, který by byl výsledkem vyjádření čísla ve vědeckém zápisu, je větší než -5 a menší než specifikátor přesnosti. Jinak se použije vědecký zápis. V případě potřeby obsahuje výsledek desetinnou čárku a koncové nuly po vynechání desetinné čárky. Pokud je k dispozici specifikátor přesnosti a počet platných číslic ve výsledku překračuje zadanou přesnost, pak jsou přebytečné koncové nuly odstraněny zaokrouhlením.

Pokud je však <xref:System.Decimal> číslo a specifikátor přesnosti je vynechán, vždy se používá zápis s pevným bodem a koncové nuly jsou zachovány.

Pokud použijete vědecký zápis, pak je před exponentem ve výsledku předpona "E", je-li specifikátor formát "G"; nebo předpona "e", je-li specifikátor formátu "g". Exponent obsahuje minimálně dvě číslice. Tím se liší od formátu pro vědecký zápis, který je vytvořen exponenciálním specifikátorem formátu, což zahrnuje minimálně tři číslice v exponentu.

Všimněte si, že <xref:System.Double> při použití s hodnotou specifikátor formátu "G17" zajišťuje, že původní <xref:System.Double> hodnota úspěšně round-trips. Důvodem <xref:System.Double> je, že je IEEE 754-2008`binary64`kompatibilní dvojité přesnosti ( ) číslo s plovoucí desetinnou desetinnou tálicí, která poskytuje až 17 platných číslic přesnosti. Doporučujeme jeho použití namísto [specifikátoru formátu "R"](#RFormatString), protože v některých případech "R" se nezdaří úspěšně round-trip dvojité přesnosti hodnoty s plovoucí desetinnou desetinnou desetinnou desetinnou hodnotou. Následující příklad ilustruje jeden takový případ.

[!code-csharp-interactive[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs#GeneralFormatSpecifier)]
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]

Při použití <xref:System.Single> s hodnotou specifikátor formátu "G9" <xref:System.Single> zajišťuje, že původní hodnota úspěšně round-trips. Důvodem <xref:System.Single> je, že je IEEE 754-2008`binary32`kompatibilní s jednou přesností ( ) číslo s plovoucí desetinnou desetinnou desetinnou tálicí, která poskytuje až devět platných číslic přesnosti. Z důvodů výkonu doporučujeme jeho použití namísto [specifikátoru formátu "R"](#RFormatString).

Výsledný řetězec je ovlivněn informacemi o formátování <xref:System.Globalization.NumberFormatInfo> aktuálního objektu. V následující tabulce <xref:System.Globalization.NumberFormatInfo> jsou uvedeny vlastnosti, které řídí formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Definuje řetězec, který označuje, že exponent je kladný.|

Následující příklad formátuje různé hodnoty s plovoucí desetinnou desetinnou desetinnou hodnotou pomocí specifikátoru obecného formátu:

[!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
[!code-csharp[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
[!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]

[Zpět na stůl](#table)

<a name="NFormatString"></a>

## <a name="the-numeric-n-format-specifier"></a>Specifikátor číselného formátu ("N")

Specifikátor číselného formátu ("N") převede číslo na řetězec ve formě "-d,ddd,ddd.ddd…", kde "-" označuje symbol záporného čísla, je-li vyžadován, "d" označuje číslice (0-9), "," označuje oddělovač skupin a "." označuje symbol desetinné čárky. Specifikátor přesnosti označuje požadovaný počet číslic za desetinnou čárkou. Pokud je specifikátor přesnosti vynechán, počet desetinných míst <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> je definován aktuální vlastností.

Výsledný řetězec je ovlivněn informacemi o formátování <xref:System.Globalization.NumberFormatInfo> aktuálního objektu. V následující tabulce <xref:System.Globalization.NumberFormatInfo> jsou uvedeny vlastnosti, které řídí formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Definuje formát záporných hodnot a určuje, zda je záporné znaménko reprezentováno závorky nebo vlastností. <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Definuje počet integrálních číslic zobrazených mezi oddělovači skupin.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Definuje řetězec, který odděluje skupiny integrálních čísel.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální a desítkové číslice.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definuje výchozí počet desítkových číslic. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|

Následující příklad formátuje různé hodnoty s plovoucí desetinnou desetinnou desetinnou hodnotou s specifikátorem formátu čísla:

[!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
[!code-csharp[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
[!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]

[Zpět na stůl](#table)

<a name="PFormatString"></a>

## <a name="the-percent-p-format-specifier"></a>Specifikátor procentuálního formátu ("P")

Specifikátor procentuálního formátu ("P") vynásobí číslo 100 a převede ho na řetězec, který představuje procenta. Specifikátor přesnosti označuje požadovaný počet desetinných míst. Pokud je specifikátor přesnosti vynechán, použije se <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> výchozí číselná přesnost dodaná aktuální vlastností.

V následující tabulce <xref:System.Globalization.NumberFormatInfo> jsou uvedeny vlastnosti, které řídí formátování vráceného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.PercentPositivePattern%2A>|Definuje umístění symbolu procenta pro kladné hodnoty.|
|<xref:System.Globalization.NumberFormatInfo.PercentNegativePattern%2A>|Definuje umístění symbolu procenta a záporného symbolu pro záporné hodnoty.|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A>|Definuje symbol procenta.|
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A>|Definuje výchozí počet desetinných míst v procentuální hodnotě. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální a desítkové číslice.|
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSeparator%2A>|Definuje řetězec, který odděluje skupiny integrálních čísel.|
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSizes%2A>|Definuje počet celých číslic, které se zobrazují ve skupině.|

Následující příklad formátuje hodnoty s plovoucí desetinnou desetinnou hodnotou pomocí specifikátoru formátu procent:

[!code-cpp[Formatting.Numeric.Standard#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#7)]
[!code-csharp[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
[!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]

[Zpět na stůl](#table)

<a name="RFormatString"></a>

## <a name="the-round-trip-r-format-specifier"></a>Specifikátor formátu zpátečního převodu ("R")

Specifikátor formátu Round-trip ("R") se pokusí zajistit, že číselná hodnota, která je převedena na řetězec, je analyzována zpět na stejnou číselnou hodnotu. Tento formát je podporován <xref:System.Single> <xref:System.Double>pouze <xref:System.Numerics.BigInteger> pro , a typy.

U <xref:System.Double> hodnot specifikátor formátu "R" v některých případech se nezdaří úspěšně round-trip původní hodnotu. Pro <xref:System.Double> oba <xref:System.Single> a hodnoty nabízí také relativně nízký výkon. Místo toho doporučujeme použít specifikátor formátu ["G17"](#GFormatString) pro <xref:System.Double> hodnoty a specifikátor formátu ["G9"](#GFormatString) k úspěšnému odezvy. <xref:System.Single>

Pokud <xref:System.Numerics.BigInteger> je hodnota formátována pomocí tohoto specifikátoru, její řetězcová reprezentace obsahuje všechny významné číslice v hodnotě. <xref:System.Numerics.BigInteger>

Ačkoli můžete použít také specifikátor přesnosti, bude ignorován. Pokud použijete tento specifikátor, má zpáteční převod přednost nad přesností.
Výsledný řetězec je ovlivněn informacemi o formátování <xref:System.Globalization.NumberFormatInfo> aktuálního objektu. V následující tabulce <xref:System.Globalization.NumberFormatInfo> jsou uvedeny vlastnosti, které řídí formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Definuje řetězec, který označuje, že exponent je kladný.|

Následující příklad formátuje <xref:System.Numerics.BigInteger> hodnotu pomocí specifikátoru formátu round-trip.

[!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
[!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
[!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]

> [!IMPORTANT]
> V některých <xref:System.Double> případech hodnoty formátované standardním číselným formátovacím řetězcem "R" `/platform:x64` `/platform:anycpu` nejsou úspěšně round-trip, pokud jsou kompilovány pomocí přepínačů nebo a běží v 64bitových systémech. Další informace naleznete v následujícím odstavci.

Chcete-li vyřešit <xref:System.Double> problém s hodnotami formátovanými standardním číselným formátovacím řetězcem `/platform:x64` `/platform:anycpu` "R", který není úspěšně round-tripping, pokud je kompilován pomocí přepínačů nebo a spuštěn v 64bitových systémech., můžete formátovat <xref:System.Double> hodnoty pomocí standardního číselného formátovacího řetězce "G17". Následující příklad používá formátovací řetězec "R" s hodnotou, <xref:System.Double> která není úspěšně round-trip a také používá řetězec formátu "G17" úspěšně round-trip původní hodnotu:

[!code-csharp[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#RoundTrip)]
[!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]

[Zpět na stůl](#table)

<a name="XFormatString"></a>

## <a name="the-hexadecimal-x-format-specifier"></a>Specifikátor šestnáctkového formátu ("X")

Specifikátor šestnáctkového formátu ("X") převede číslo na řetězec šestnáctkových číslic. Velikost specifikátoru formátu označuje, zda pro šestnáctkové číslice, které jsou větší než 9, je nutné používat velká nebo malá písmena. Například pro vytvoření řetězce "ABCDEF" použijte formát "X", pro vytvoření řetězce "abcdef" použijte formát "x". Tento formát je podporován pouze pro integrální typy.

Specifikátor přesnosti označuje minimální počet číslic požadovaných ve výsledném řetězci. V případě potřeby je číslo doplněno nulami po levé straně za účelem vytvoření počtu číslic, který je dán specifikátorem přesnosti.

Výsledný řetězec není ovlivněn informacemi o formátování <xref:System.Globalization.NumberFormatInfo> aktuálního objektu.

Následující příklad formátuje <xref:System.Int32> hodnoty pomocí specifikátoru šestnáctkového formátu.

[!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
[!code-csharp-interactive[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
[!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]

[Zpět na stůl](#table)

<a name="NotesStandardFormatting"></a>

## <a name="notes"></a>Poznámky

### <a name="control-panel-settings"></a>Nastavení části Ovládací panely

Nastavení v ovládacím panelu **Místní a jazykové možnosti** ovlivňují výsledný řetězec vytvořený operací formátování. Tato nastavení se používají k <xref:System.Globalization.NumberFormatInfo> inicializaci objektu přidruženého k aktuální jazykové verzi vlákna, který poskytuje hodnoty používané k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.

Kromě toho pokud <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> konstruktor slouží k vytvoření instance <xref:System.Globalization.CultureInfo> nový objekt, který představuje stejnou jazykovou verzi jako aktuální jazykovou verzi systému, všechny <xref:System.Globalization.CultureInfo> vlastní nastavení stanovené **položky regionální a jazykové možnosti** v ovládacím panelu budou použity na nový objekt. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29> Konstruktor můžete použít k <xref:System.Globalization.CultureInfo> vytvoření objektu, který neodráží vlastní nastavení systému.

### <a name="numberformatinfo-properties"></a>Vlastnosti objektu NumberFormatInfo

Formátování je ovlivněno vlastnostmi aktuálního <xref:System.Globalization.NumberFormatInfo> objektu, který je implicitně poskytován aktuální jazykovou verzí vlákna nebo explicitně <xref:System.IFormatProvider> parametrem metody, která vyvolá formátování. Zadejte <xref:System.Globalization.NumberFormatInfo> <xref:System.Globalization.CultureInfo> objekt nebo objekt pro tento parametr.

> [!NOTE]
> Informace o přizpůsobení vzorků nebo řetězců používaných při formátování číselných <xref:System.Globalization.NumberFormatInfo> hodnot naleznete v tématu třídy.

### <a name="integral-and-floating-point-numeric-types"></a>Integrální typy čísel a typy s plovoucí desetinnou čárkou

Některé popisy specifikátorů standardního číselného formátu odkazují na integrální číselné typy nebo typy s plovoucí desetinnou čárkou. Integrální <xref:System.Byte>číselné <xref:System.Int32>typy <xref:System.Int64> <xref:System.UInt16>jsou <xref:System.UInt32> <xref:System.UInt64>, <xref:System.SByte> <xref:System.Numerics.BigInteger>, <xref:System.Int16>, , , , , a . Číselné typy s <xref:System.Decimal>plovoucí <xref:System.Single>desetinnou desetinnou desetinnou hodnotou jsou , a <xref:System.Double>.

### <a name="floating-point-infinities-and-nan"></a>Nekonečno s plovoucí desetinnou čárkou a NaN

Bez ohledu na formátovací řetězec, <xref:System.Single> pokud <xref:System.Double> je hodnota typu nebo typu s plovoucí desetinnou desetinnou hodnotou kladné <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>nekonečno, záporné nekonečno nebo ne číslo (NaN), formátovaný řetězec je hodnota příslušného , <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>nebo <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> vlastnost, která je určena aktuálně použitelným <xref:System.Globalization.NumberFormatInfo> objektem.

## <a name="example"></a>Příklad

[!INCLUDE[interactive-note](~/includes/csharp-interactive-partial-note.md)]

Následující příklad formátuje číselnou integrální hodnotu a hodnotu s plovoucí desetinnou čárkou pomocí jazykové verze en-US a všech specifikátorů standardního číselného formátu. Tento příklad používá dva<xref:System.Double> konkrétní <xref:System.Int32>číselné typy ( a ), ale přinesl<xref:System.Byte> <xref:System.SByte>by <xref:System.Int16> <xref:System.Int32>podobné výsledky pro některý z ostatních číselných základních typů ( , , , <xref:System.Int64> <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Numerics.BigInteger>, <xref:System.Decimal>, a <xref:System.Single>).

[!code-csharp[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#FinalExample)]
[!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]

## <a name="see-also"></a>Viz také

- <xref:System.Globalization.NumberFormatInfo>
- [Vlastní číselné formátovací řetězce](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Postupy: Vyplnění čísla úvodními nulami](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)
- [Složené formátování](../../../docs/standard/base-types/composite-formatting.md)
- [Ukázka: Nástroj pro formátování WinForms .NET (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Ukázka: Nástroj pro formátování WinForms .NET (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
