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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2f997cf398e59f8e30ac87c1e0360e43a448e85
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216706"
---
# <a name="standard-numeric-format-strings"></a>Standardní řetězce formátu čísla

Řetězce standardního číselného formátu se používají pro formátování běžných číselných typů. Standardní číselný formátovací řetězec má formu `Axx`, kde:

- `A`je jeden abecední znak nazvaný *specifikátor formátu*. Jakýkoli řetězec číselného formátu, který obsahuje více než jeden abecední znak, včetně prázdných znaků, je interpretován jako řetězec vlastního číselného formátu. Další informace najdete v tématu [vlastní číselné formátovací řetězce](../../../docs/standard/base-types/custom-numeric-format-strings.md).

- `xx`je volitelné celé číslo, které se nazývá *specifikátor přesnosti*. Specifikátor přesnosti má rozsah od 0 do 99 a má vliv na počet číslic ve výsledku. Všimněte si, že specifikátor přesnosti určuje počet číslic v řetězcové reprezentaci čísla. Neprovádí zaokrouhlení samotného čísla. K provedení operace zaokrouhlení použijte <xref:System.Math.Ceiling%2A?displayProperty=nameWithType>metodu, <xref:System.Math.Floor%2A?displayProperty=nameWithType>nebo <xref:System.Math.Round%2A?displayProperty=nameWithType> .

  Pokud *specifikátor přesnosti* řídí počet zlomkových číslic ve výsledném řetězci, výsledný řetězec odráží číslo, které je zaokrouhleno na reprezentovatelné výsledky nejbližší nekonečně přesnému výsledku. Pokud existují dva stejně blízkoně dostupné výsledky:
  - **V .NET Framework a .NET Core až do .NET core 2,0**vybírá modul runtime výsledek s větší nejméně významnou číslicí (tj. pomocí <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>).
  - **V .NET Core 2,1 a novější**modul runtime vybírá výsledek s nejméně významnou číslicí (tj. pomocí <xref:System.MidpointRounding.ToEven?displayProperty=nameWithType>).

  > [!NOTE]
  > Specifikátor přesnosti určuje počet číslic ve výsledném řetězci. Chcete-li doplnit výsledný řetězec pomocí počátečních nebo koncových mezer, použijte funkci [složeného formátování](../../../docs/standard/base-types/composite-formatting.md) a definujte *součást zarovnání* v položce formátu.

Standardní řetězce číselného formátu jsou podporovány v:

- Některá přetížení `ToString` metody pro všechny číselné typy. Například můžete do <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> metod a <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> zadávat řetězec číselného formátu.

- [Funkce složeného formátování](../../../docs/standard/base-types/composite-formatting.md)rozhraní .NET, která je používána některými `Write` <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console> `WriteLine` metodami a třídy a <xref:System.IO.StreamWriter> , metodou <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> a metodou. Funkce složeného formátu umožňuje zahrnout řetězcové vyjádření více datových položek do jednoho řetězce, zadat šířku pole a zarovnat čísla v poli. Další informace najdete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md).

- [Interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md) v C# a Visual Basic, které poskytují zjednodušenou syntaxi ve srovnání s řetězci složeného formátu.

> [!TIP]
> Můžete si stáhnout **formátovací nástroj**, aplikaci .net Core model Windows Forms, která umožňuje použití řetězců formátu na číselné hodnoty nebo hodnoty data a času a zobrazuje výsledný řetězec. Zdrojový kód je k dispozici pro [C#](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) a [Visual Basic](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb).

<a name="table"></a>Následující tabulka popisuje standardní specifikátory číselného formátu a zobrazuje vzorový výstup vyprodukovaný každým specifikátorem formátu. Další informace o použití standardních číselných formátovacích řetězců naleznete v části [poznámky](#NotesStandardFormatting) a v části [příklad](#example) pro komplexní ilustraci jejich použití.

|Specifikátor formátu|Name|Popis|Příklady|
|----------------------|----------|-----------------|--------------|
|"C" nebo "c"|Měna|Vyústit Hodnota měny.<br /><br /> Podporováno: Všechny číselné typy.<br /><br /> Specifikátor přesnosti: Počet desetinných číslic.<br /><br /> Výchozí specifikátor přesnosti: <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType>Definováno.<br /><br /> Další informace: [Specifikátor formátu měny ("C")](#CFormatString).|123,456 ("C", en-us)-> \\$123,46<br /><br /> 123,456 ("C", fr-FR)-> 123, 46 €<br /><br /> 123,456 ("C", ja-JP)-> ¥123<br /><br /> -123,456 ("C3", en-us)-> (\\$123,456)<br /><br /> -123,456 ("C3", fr-FR)->-€123 456<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|
|"D" nebo "d"|Desetinné číslo|Vyústit Celočíselné číslice s volitelným záporným znaménkem<br /><br /> Podporováno: Pouze integrální typy.<br /><br /> Specifikátor přesnosti: Minimální počet číslic<br /><br /> Výchozí specifikátor přesnosti: Vyžaduje se minimální počet číslic.<br /><br /> Další informace: [Specifikátor formátu desítkového čísla ("D")](#DFormatString).|1234 ("D")-> 1234<br /><br /> -1234 ("D6")->-001234|
|"E" nebo "e"|Exponenciální (vědecký) zápis|Vyústit Exponenciální notace<br /><br /> Podporováno: Všechny číselné typy.<br /><br /> Specifikátor přesnosti: Počet desetinných číslic.<br /><br /> Výchozí specifikátor přesnosti: 6.<br /><br /> Další informace: [Exponenciální specifikátor formátu ("E")](#EFormatString).|1052,0329112756 ("E", en-US)-> 1.052033 E + 003<br /><br /> 1052,0329112756 ("e", fr-FR)-> 1, 052033e + 003<br /><br /> -1052,0329112756 ("E2", en-US)->-1,05 e + 003<br /><br /> -1052,0329112756 ("E2", fr-FR)->-1, 05E + 003|
|"F" nebo "f"|Pevná desetinná čárka|Vyústit Celočíselná a desítková čísla s volitelným záporným znaménkem.<br /><br /> Podporováno: Všechny číselné typy.<br /><br /> Specifikátor přesnosti: Počet desetinných číslic.<br /><br /> Výchozí specifikátor přesnosti: <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>Definováno.<br /><br /> Další informace: [Specifikátor formátu s pevnou desetinnou čárkou ("F")](#FFormatString).|1234,567 ("F", en-US)-> 1234,57<br /><br /> 1234,567 ("F", de-DE)-> 1234, 57<br /><br /> 1234 ("F1", en-US)-> 1234,0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234,56 ("F4", en-US)->-1234,5600<br /><br /> -1234,56 ("F4", de-DE)->-1234, 1234,5600|
|"G" nebo "g"|Obecné|Vyústit Kompaktnější z pevného bodu nebo vědeckého zápisu.<br /><br /> Podporováno: Všechny číselné typy.<br /><br /> Specifikátor přesnosti: Počet platných číslic<br /><br /> Výchozí specifikátor přesnosti: Závisí na číselném typu.<br /><br /> Další informace: [Obecný specifikátor formátu ("G")](#GFormatString).|-123,456 ("G", en-US)->-123,456<br /><br /> -123,456 ("G", sv-SE)->-123 456<br /><br /> 123,4546 ("G4", en-US)-> 123,5<br /><br /> 123,4546 ("G4", sv-SE)-> 123, 5<br /><br /> -1.234567890 e-25 ("G", en-US)->-1.23456789 E-25<br /><br /> -1.234567890 e-25 ("G", sv-SE)->-1, 23456789E-25|
|"N" nebo "n"|Číslo|Vyústit Celočíselné a desítkové číslice, oddělovače skupin a oddělovač desetinných míst s volitelným záporným znaménkem.<br /><br /> Podporováno: Všechny číselné typy.<br /><br /> Specifikátor přesnosti: Požadovaný počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>Definováno.<br /><br /> Další informace: [Číselný specifikátor formátu ("N")](#NFormatString).|1234,567 ("N", en-US)-> 1 234,57<br /><br /> 1234,567 ("N", ru-RU)-> 1 234, 57<br /><br /> 1234 ("N1", en-US)-> 1 234,0<br /><br /> 1234 ("N1", ru-RU)-> 1 234, 0<br /><br /> -1234,56 ("N3", en-US)->-1 234,560<br /><br /> -1234,56 ("N3", ru-RU)->-1 234 560|
|"P" nebo "p"|Procento|Vyústit Číslo vynásobené 100em a zobrazeným symbolem procenta<br /><br /> Podporováno: Všechny číselné typy.<br /><br /> Specifikátor přesnosti: Požadovaný počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType>Definováno.<br /><br /> Další informace: [Procentuální specifikátor formátu ("P")](#PFormatString).|1 ("P", en-US) – > 100,00%<br /><br /> 1 ("P", fr-FR) -> 100,00 %<br /><br /> -0,39678 ("P1", en-US)->-39,7%<br /><br /> -0,39678 ("P1", fr-FR)->-39, 7%|
|"R" nebo "r"|Zpáteční převod|Vyústit Řetězec, který může být zpáteční cestou k stejnému číslu.<br /><br /> Podporováno v: <xref:System.Single>, <xref:System.Double>a <xref:System.Numerics.BigInteger>.<br /><br /> Poznámka: Doporučuje se <xref:System.Numerics.BigInteger> jenom pro typ. Pro <xref:System.Double> typy použijte "G17"; pro <xref:System.Single> typy použijte "G9". <br> Specifikátor přesnosti: Přeskočen.<br /><br /> Další informace: [Specifikátor formátu Round-Trip ("R")](#RFormatString).|123456789,12345678 ("R")-> 123456789,12345678<br /><br /> -1234567890,12345678 ("R")->-1234567890,1234567|
|"X" nebo "x"|Šestnáctková hodnota|Vyústit Šestnáctkový řetězec.<br /><br /> Podporováno: Pouze integrální typy.<br /><br /> Specifikátor přesnosti: Počet číslic ve výsledném řetězci.<br /><br /> Další informace: [Šestnáctkový specifikátor formátu ("X")](#XFormatString).|255 ("X") -> FF<br /><br /> -1 ("x")-> FF<br /><br /> 255 ("X4") – > 00ff<br /><br /> -1 ("X4") -> 00FF|
|Jakýkoli jiný samostatný znak|Neznámý specifikátor|Vyústit Vyvolá za běhu v době běhu. <xref:System.FormatException>||

<a name="Using"></a>

## <a name="using-standard-numeric-format-strings"></a>Používání řetězců standardního číselného formátu

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Řetězec standardního číselného formátu lze použít pro definování formátování číselné hodnoty jedním ze dvou způsobů:

- Může být předán přetížení `ToString` metody, která `format` má parametr. Následující příklad formátuje číselnou hodnotu jako řetězec měny v aktuální jazykové verzi (v tomto případě jazykovou verzi en-US).

  [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
  [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]

- `formatString` Dá se zadat jako argument v položce formátu používané s těmito metodami jako <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>a <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>. Další informace najdete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md). Následující příklad používá položku formátu pro vložení hodnoty měny do řetězce.

  [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
  [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]

  Volitelně můžete `alignment` zadat argument pro určení šířky číselného pole a zda je jeho hodnota zarovnána vpravo nebo vlevo. Následující příklad Zarovná hodnotu měny v poli se 28 znaky a v poli se 14 znaky Zarovná hodnotu měny.

  [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
  [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]

- Dá se zadat jako `formatString` argument v položce interpolované výrazu interpolované řetězcové položky. Další informace naleznete v tématu o [interpolaci řetězce](../../csharp/language-reference/tokens/interpolated.md) v C# odkazu nebo v tématu [interpolované řetězce](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) v odkazu Visual Basic.

Následující oddíly obsahují podrobné informace o jednotlivých řetězcích standardního číselného formátu.

<a name="CFormatString"></a>

## <a name="the-currency-c-format-specifier"></a>Specifikátor formátu měny ("C")

Specifikátor formátu "C" (neboli měny) převede číslo na řetězec, který představuje peněžní částku. Specifikátor přesnosti označuje požadovaný počet desetinných míst ve výsledném řetězci. Pokud je specifikátor přesnosti vynechán, je výchozí přesnost definována <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> vlastností.

Pokud má formátovaná hodnota větší než zadaný nebo výchozí počet desetinných míst, je desetinná hodnota ve výsledném řetězci zaokrouhlena. Pokud je vpravo od zadaného počtu desetinných míst hodnota 5 nebo vyšší, bude poslední číslice ve výsledném řetězci zaokrouhlena směrem nahoru.

Na výsledný řetězec má vliv informace o formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. V následující tabulce jsou uvedeny <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování vráceného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Definuje umístění symbolu měny pro kladné hodnoty.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Definuje umístění symbolu měny pro záporné hodnoty a určuje, zda je záporné znaménko představováno závorkami nebo <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> vlastností.|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje záporné znaménko, které <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> se používá, pokud označuje, že se nepoužívají kulaté závorky.|
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Definuje symbol měny.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Definuje výchozí počet desítkových číslic v hodnotě měny. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální a desítkové číslice.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Definuje řetězec, který odděluje skupiny integrálních čísel.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Definuje počet celých číslic, které se zobrazují ve skupině.|

Následující příklad formátuje <xref:System.Double> hodnotu pomocí specifikátoru formátu měny:

[!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
[!code-csharp[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
[!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]

[Zpět na tabulku](#table)

<a name="DFormatString"></a>

## <a name="the-decimal-d-format-specifier"></a>Specifikátor formátu desítkového čísla ("D")

Specifikátor formátu "D" (desítkové číslo) převede číslo na řetězec desítkových číslic (0-9), kterému předchází symbol mínus, je-li číslo záporné. Tento formát je podporován pouze pro integrální typy.

Specifikátor přesnosti označuje minimální počet číslic požadovaných ve výsledném řetězci. V případě potřeby je číslo doplněno nulami po levé straně za účelem vytvoření počtu číslic, který je dán specifikátorem přesnosti. Pokud není zadán žádný specifikátor přesnosti, je výchozí hodnotou minimální hodnota požadovaná k vytvoření celého čísla bez počátečních nul.

Na výsledný řetězec má vliv informace o formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. Jak znázorňuje následující tabulka, jediná vlastnost ovlivňuje formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|

Následující příklad formátuje <xref:System.Int32> hodnotu se specifikátorem desítkového formátu.

[!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
[!code-csharp-interactive[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
[!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]

[Zpět na tabulku](#table)

<a name="EFormatString"></a>

## <a name="the-exponential-e-format-specifier"></a>Exponenciální specifikátor formátu ("E")

Exponenciální specifikátor formátu ("E") převede číslo na řetězec ve formě "-d.ddd…E+ddd" nebo "-d.ddd…e+ddd", kde každé "d" označuje číslici (0-9). Pokud je číslo záporné, řetězec začíná symbolem mínus. Desetinné čárce předchází vždy přesně jedna číslice.

Specifikátor přesnosti označuje požadovaný počet číslic za desetinnou čárkou. Pokud specifikátor přesnosti vynecháte, je za desetinnou čárkou použit výchozí počet šesti číslic.

Velikost specifikátoru formátu označuje, zda má být před exponentem použita předpona "E" nebo "e". Exponent se skládá vždy ze znaménka plus nebo mínus a minimálně tří číslic. Aby byl tento minimální požadavek splněn, je exponent v případě potřeby doplněn nulami.

Na výsledný řetězec má vliv informace o formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. V následující tabulce jsou uvedeny <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování vráceného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné pro koeficient i pro exponent.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic v koeficientu.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Definuje řetězec, který označuje, že exponent je kladný.|

Následující příklad formátuje <xref:System.Double> hodnotu pomocí exponenciálního specifikátoru formátu:

[!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
[!code-csharp[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
[!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]

[Zpět na tabulku](#table)

<a name="FFormatString"></a>

## <a name="the-fixed-point-f-format-specifier"></a>Specifikátor formátu s pevnou desetinnou čárkou ("F")

Specifikátor formátu s pevnou desetinnou čárkou ("F") převede číslo na řetězec ve formátu "-ddd. ddd...". kde každé "d" označuje číslici (0-9). Pokud je číslo záporné, řetězec začíná symbolem mínus.

Specifikátor přesnosti označuje požadovaný počet desetinných míst. Pokud je specifikátor přesnosti vynechán, aktuální <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> vlastnost poskytuje číselnou přesnost.

Na výsledný řetězec má vliv informace o formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. V následující tabulce jsou uvedeny vlastnosti <xref:System.Globalization.NumberFormatInfo> objektu, které řídí formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definuje výchozí počet desítkových číslic. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|

Následující příklad formátuje <xref:System.Double> <xref:System.Int32> a a hodnotu pomocí specifikátoru formátu s pevnou desetinnou čárkou:

[!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
[!code-csharp[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
[!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]

[Zpět na tabulku](#table)

<a name="GFormatString"></a>

## <a name="the-general-g-format-specifier"></a>Specifikátor obecného formátu ("G")

Obecný specifikátor formátu ("G") převede číslo na více kompaktních hodnot s pevnou desetinnou čárkou nebo vědeckým zápisem v závislosti na typu čísla a na tom, zda je k dispozici specifikátor přesnosti. Specifikátor přesnosti definuje maximální počet platných číslic, které mohou být zobrazeny ve výsledném řetězci. Pokud specifikátor přesnosti vynecháte nebo je specifikátor nulový, pak typ čísla určuje výchozí přesnost, jak je uvedeno v následující tabulce.

|Číselný typ|Výchozí přesnost|
|------------------|-----------------------|
|<xref:System.Byte> Nebo <xref:System.SByte>|3 číslice|
|<xref:System.Int16> Nebo <xref:System.UInt16>|5 číslic|
|<xref:System.Int32> Nebo <xref:System.UInt32>|10 číslic|
|<xref:System.Int64>|19 číslic|
|<xref:System.UInt64>|20 číslic|
|<xref:System.Numerics.BigInteger>|Neomezeno (stejné jako ["R"](#RFormatString))|
|<xref:System.Single>|7 číslic|
|<xref:System.Double>|15 číslic|
|<xref:System.Decimal>|29 číslic|

Zápis s pevnou desetinnou čárkou se používá v případě, že exponent, který by byl výsledkem vyjádření čísla ve vědeckém zápisu, je větší než -5 a menší než specifikátor přesnosti. Jinak se použije vědecký zápis. V případě potřeby obsahuje výsledek desetinnou čárku a koncové nuly po vynechání desetinné čárky. Pokud je k dispozici specifikátor přesnosti a počet platných číslic ve výsledku překračuje zadanou přesnost, pak jsou přebytečné koncové nuly odstraněny zaokrouhlením.

Pokud je <xref:System.Decimal> však číslo a specifikátor přesnosti vynecháno, je vždy použit zápis s pevnou desetinnou čárkou a koncové nuly jsou zachovány.

Pokud použijete vědecký zápis, pak je před exponentem ve výsledku předpona "E", je-li specifikátor formát "G"; nebo předpona "e", je-li specifikátor formátu "g". Exponent obsahuje minimálně dvě číslice. Tím se liší od formátu pro vědecký zápis, který je vytvořen exponenciálním specifikátorem formátu, což zahrnuje minimálně tři číslice v exponentu.

Všimněte si, že při použití s <xref:System.Double> hodnotou specifikátor formátu "G17" zajišťuje úspěšné odezvy původní <xref:System.Double> hodnoty. Důvodem je <xref:System.Double> to, že je číslo s plovoucí desetinnou čárkou`binary64`() s dvojitou přesností kompatibilní s IEEE 754-2008, které poskytuje až 17 platných číslic přesnosti. Doporučujeme použít místo [specifikátoru formátu "r"](#RFormatString), protože v některých případech "r" nemůže úspěšně přesměrovat hodnoty s plovoucí desetinnou čárkou s dvojitou přesností na cestu. Následující příklad ukazuje jeden takový případ.

[!code-csharp-interactive[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs#GeneralFormatSpecifier)]
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]

Při použití s <xref:System.Single> hodnotou specifikátor formátu "G9" zajišťuje, aby původní <xref:System.Single> hodnota úspěšně převedla odezvy. Důvodem je <xref:System.Single> to, že se jedná o číslo s plovoucí desetinnou`binary32`čárkou () s přesností na IEEE 754-2008, které poskytuje až devět platných číslic přesnosti. Z důvodů výkonu doporučujeme použít místo [specifikátoru formátu "R"](#RFormatString).

Na výsledný řetězec má vliv informace o formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. V následující tabulce jsou uvedeny <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Definuje řetězec, který označuje, že exponent je kladný.|

Následující příklad formátuje různé hodnoty s plovoucí desetinnou čárkou pomocí obecného specifikátoru formátu:

[!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
[!code-csharp[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
[!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]

[Zpět na tabulku](#table)

<a name="NFormatString"></a>

## <a name="the-numeric-n-format-specifier"></a>Specifikátor číselného formátu ("N")

Specifikátor číselného formátu ("N") převede číslo na řetězec ve formě "-d,ddd,ddd.ddd…", kde "-" označuje symbol záporného čísla, je-li vyžadován, "d" označuje číslice (0-9), "," označuje oddělovač skupin a "." označuje symbol desetinné čárky. Specifikátor přesnosti označuje požadovaný počet číslic za desetinnou čárkou. Pokud je specifikátor přesnosti vynechán, je počet desetinných míst definován aktuální <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> vlastností.

Na výsledný řetězec má vliv informace o formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. V následující tabulce jsou uvedeny <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Definuje formát záporných hodnot a určuje, zda je záporné znaménko představováno závorkami nebo <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> vlastností.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Definuje počet integrálních číslic zobrazených mezi oddělovači skupin.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Definuje řetězec, který odděluje skupiny integrálních čísel.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální a desítkové číslice.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definuje výchozí počet desítkových číslic. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|

Následující příklad formátuje různé hodnoty s plovoucí desetinnou čárkou pomocí specifikátoru číselného formátu:

[!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
[!code-csharp[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
[!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]

[Zpět na tabulku](#table)

<a name="PFormatString"></a>

## <a name="the-percent-p-format-specifier"></a>Specifikátor procentuálního formátu ("P")

Specifikátor procentuálního formátu ("P") vynásobí číslo 100 a převede ho na řetězec, který představuje procenta. Specifikátor přesnosti označuje požadovaný počet desetinných míst. Pokud je specifikátor přesnosti vynechán, je použita výchozí číselná přesnost dodaná aktuální <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> vlastností.

V následující tabulce jsou uvedeny <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování vráceného řetězce.

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

Následující příklad formátuje hodnoty s plovoucí desetinnou čárkou pomocí specifikátoru formátu procenta:

[!code-cpp[Formatting.Numeric.Standard#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#7)]
[!code-csharp[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
[!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]

[Zpět na tabulku](#table)

<a name="RFormatString"></a>

## <a name="the-round-trip-r-format-specifier"></a>Specifikátor formátu zpátečního převodu ("R")

Specifikátor formátu Round-Trip ("R") se pokusí zajistit, že číselná hodnota, která je převedena na řetězec, bude analyzována zpět do stejné číselné hodnoty. Tento formát je podporován pouze pro <xref:System.Single>typy, <xref:System.Double>a. <xref:System.Numerics.BigInteger>

Pro <xref:System.Double> hodnoty specifikátor formátu "R" v některých případech se nepodaří úspěšně odeslat původní hodnotu z cesty. U obou <xref:System.Double> <xref:System.Single> hodnot i nabízí také poměrně špatný výkon. Místo toho doporučujeme použít specifikátor formátu ["G17"](#GFormatString) pro <xref:System.Double> hodnoty a <xref:System.Single> specifikátor formátu ["G9"](#GFormatString) k úspěšnému zacyklení hodnot.

Pokud je <xref:System.Numerics.BigInteger> hodnota formátována pomocí tohoto specifikátoru, Řetězcová reprezentace obsahuje všechny významné číslice v hodnotě. <xref:System.Numerics.BigInteger>

Ačkoli můžete použít také specifikátor přesnosti, bude ignorován. Pokud použijete tento specifikátor, má zpáteční převod přednost nad přesností.
Na výsledný řetězec má vliv informace o formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. V následující tabulce jsou uvedeny <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Definuje řetězec, který označuje, že exponent je kladný.|

Následující příklad formátuje <xref:System.Numerics.BigInteger> hodnotu pomocí specifikátoru formátu Round-Trip.

[!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
[!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
[!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]

> [!IMPORTANT]
> V některých případech <xref:System.Double> hodnoty formátované pomocí standardního číselného formátovacího řetězce "R" nemusejí úspěšně odcyklovat cestu, pokud jsou `/platform:x64` kompilovány pomocí přepínačů nebo `/platform:anycpu` a spouštěny v 64 systémech. Další informace najdete v následujícím článku.

Chcete-li se vyhnout problému <xref:System.Double> hodnot formátovaných pomocí standardního číselného formátovacího řetězce "R", neúspěšně se zaokrouhlí na `/platform:x64` Trip `/platform:anycpu` , pokud jsou kompilovány pomocí přepínačů nebo a spouštěny v <xref:System.Double> systémech 64. můžete formátovat hodnoty pomocí standardního číselného formátovacího řetězce "G17". Následující příklad používá formátovací řetězec "R" s <xref:System.Double> hodnotou, která neprovádí operaci round-trip, a také používá řetězec formátu "G17" k úspěšnému přenosu původní hodnoty:

[!code-csharp[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#RoundTrip)]
[!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]

[Zpět na tabulku](#table)

<a name="XFormatString"></a>

## <a name="the-hexadecimal-x-format-specifier"></a>Specifikátor šestnáctkového formátu ("X")

Specifikátor šestnáctkového formátu ("X") převede číslo na řetězec šestnáctkových číslic. Velikost specifikátoru formátu označuje, zda pro šestnáctkové číslice, které jsou větší než 9, je nutné používat velká nebo malá písmena. Například pro vytvoření řetězce "ABCDEF" použijte formát "X", pro vytvoření řetězce "abcdef" použijte formát "x". Tento formát je podporován pouze pro integrální typy.

Specifikátor přesnosti označuje minimální počet číslic požadovaných ve výsledném řetězci. V případě potřeby je číslo doplněno nulami po levé straně za účelem vytvoření počtu číslic, který je dán specifikátorem přesnosti.

Na výsledný řetězec nemá vliv informace o formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu.

Následující příklad formátuje <xref:System.Int32> hodnoty pomocí hexadecimálního specifikátoru formátu.

[!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
[!code-csharp-interactive[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
[!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]

[Zpět na tabulku](#table)

<a name="NotesStandardFormatting"></a>

## <a name="notes"></a>Poznámky

### <a name="control-panel-settings"></a>Nastavení části Ovládací panely

Nastavení v položce **místní a jazykové** nastavení v Ovládacích panelech ovlivní výsledný řetězec vytvořený při operaci formátování. Tato nastavení slouží k inicializaci <xref:System.Globalization.NumberFormatInfo> objektu přidruženého k aktuální jazykové verzi vlákna, které poskytuje hodnoty použité k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.

Kromě toho, pokud <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> je konstruktor použit k vytvoření instance nového <xref:System.Globalization.CultureInfo> objektu, který představuje stejnou jazykovou verzi jako aktuální jazyková verze systému, jakákoli vlastní nastavení, která byla vytvořena položkou **místní a jazykové nastavení** v Ovládacích panelech bude použito pro nový <xref:System.Globalization.CultureInfo> objekt. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Konstruktor můžete použít k <xref:System.Globalization.CultureInfo> vytvoření objektu, který nereflektuje vlastní nastavení systému.

### <a name="numberformatinfo-properties"></a>Vlastnosti objektu NumberFormatInfo

Formátování je ovlivněno vlastnostmi aktuálního <xref:System.Globalization.NumberFormatInfo> objektu, který je poskytnut implicitně aktuální jazykovou verzí vlákna nebo explicitně <xref:System.IFormatProvider> parametrem metody, která vyvolá formátování. Zadejte objekt <xref:System.Globalization.CultureInfo> nebo pro tento parametr. <xref:System.Globalization.NumberFormatInfo>

> [!NOTE]
> Informace o přizpůsobení vzorů nebo řetězců použitých ve formátování číselných hodnot naleznete <xref:System.Globalization.NumberFormatInfo> v tématu třídy.

### <a name="integral-and-floating-point-numeric-types"></a>Integrální typy čísel a typy s plovoucí desetinnou čárkou

Některé popisy specifikátorů standardního číselného formátu odkazují na integrální číselné typy nebo typy s plovoucí desetinnou čárkou. Integrální <xref:System.Byte>číselné typy jsou, <xref:System.Int64> ,<xref:System.UInt16>,,, ,<xref:System.UInt64>, a<xref:System.Numerics.BigInteger>. <xref:System.Int16> <xref:System.SByte> <xref:System.Int32> <xref:System.UInt32> Číselné typy s plovoucí desetinnou čárkou <xref:System.Single>jsou <xref:System.Decimal>, <xref:System.Double>a.

### <a name="floating-point-infinities-and-nan"></a>Nekonečno s plovoucí desetinnou čárkou a NaN

Bez ohledu na řetězec formátu, <xref:System.Single> Pokud je hodnota nebo <xref:System.Double> typu s plovoucí desetinnou čárkou kladné nekonečno, záporné nekonečno nebo není číslo (NaN), formátovaný řetězec je hodnota příslušné <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>hodnoty, <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>nebo <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> vlastnost, která je určena aktuálně použitelným <xref:System.Globalization.NumberFormatInfo> objektem.

## <a name="example"></a>Příklad

[!INCLUDE[interactive-note](~/includes/csharp-interactive-partial-note.md)]

Následující příklad formátuje číselnou integrální hodnotu a hodnotu s plovoucí desetinnou čárkou pomocí jazykové verze en-US a všech specifikátorů standardního číselného formátu. V tomto příkladu se používají dva konkrétní číselné<xref:System.Double> typy <xref:System.Int32>(a), ale by výsledkem byly podobné výsledky pro libovolný z dalších číselných<xref:System.Byte>základních <xref:System.SByte> <xref:System.Int32>typů <xref:System.Int16>(, <xref:System.Int64>,,,, <xref:System.UInt16>, ,<xref:System.UInt64>, ,<xref:System.Single>a )<xref:System.Decimal>. <xref:System.UInt32> <xref:System.Numerics.BigInteger>

[!code-csharp[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#FinalExample)]
[!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]

## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.NumberFormatInfo>
- [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Postupy: Doplnit číslo počátečními nulami](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)
- [Složené formátování](../../../docs/standard/base-types/composite-formatting.md)
- [Ukázka: nástroj formátování WinForms pro .NET CoreC#()](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
- [Ukázka: nástroj formátování WinForms pro .NET Core (Visual Basic)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-vb)
