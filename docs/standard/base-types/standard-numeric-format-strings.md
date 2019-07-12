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
ms.openlocfilehash: 245492a8a903593dc1532b67ed96224e171aad7e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804725"
---
# <a name="standard-numeric-format-strings"></a>Standardní řetězce formátu čísla

Řetězce standardního číselného formátu se používají pro formátování běžných číselných typů. Řetězec standardního číselného formátu má podobu `Axx`, kde:

- `A` je jeden abecední znak nazvaný *specifikátor formátu*. Jakýkoli řetězec číselného formátu, který obsahuje více než jeden abecední znak, včetně prázdných znaků, je interpretován jako řetězec vlastního číselného formátu. Další informace najdete v tématu [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md).

- `xx` je volitelné celé číslo nazvané *specifikátor přesnosti*. Specifikátor přesnosti má rozsah od 0 do 99 a má vliv na počet číslic ve výsledku. Všimněte si, že specifikátor přesnosti určuje počet číslic v řetězcové reprezentaci čísla. Neprovádí zaokrouhlení samotného čísla. Chcete-li provést operaci zaokrouhlení, použijte <xref:System.Math.Ceiling%2A?displayProperty=nameWithType>, <xref:System.Math.Floor%2A?displayProperty=nameWithType>, nebo <xref:System.Math.Round%2A?displayProperty=nameWithType> metody.

  Když *specifikátor přesnosti* ovládacích prvků zobrazuje počet zlomkových číslic ve výsledném řetězci, výsledný řetězec číslo, které se zaokrouhlí na reprezentovatelné výsledek nejblíže neomezeně přesné výsledky. Pokud existují dva stejně téměř reprezentovatelné výsledky:
  - **Rozhraní .NET Framework a .NET Core až po .NET Core 2.0**, modul runtime vybere výsledek s větší nejméně významných číslic (to znamená, že použití <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>).
  - **V rozhraní .NET Core 2.1 nebo novější**, modul runtime vybere výsledků i nejméně významných číslic (to znamená, že použití <xref:System.MidpointRounding.ToEven?displayProperty=nameWithType>).

  > [!NOTE]
  > Specifikátor přesnosti určuje počet číslic ve výsledném řetězci. K vyplnění výsledný řetězec s úvodní a koncové mezery, použijte [složené formátování](../../../docs/standard/base-types/composite-formatting.md) funkcí a definování *součást zarovnání* v položce formátu.

Řetězce standardního číselného formátu jsou podporovány:

- Některá přetížení `ToString` metoda všechny číselné typy. Například můžete zadat číselný formátovací řetězec <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> a <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody.

- .NET [funkci složeného formátování](../../../docs/standard/base-types/composite-formatting.md), která je používána některými `Write` a `WriteLine` metody <xref:System.Console> a <xref:System.IO.StreamWriter> třídy, <xref:System.String.Format%2A?displayProperty=nameWithType> metoda a <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> metoda. Složený formátovací funkce umožňuje zahrnout řetězcové vyjádření více datových položek do jednoho řetězce, můžete určit šířku pole a zarovnání čísel v poli. Další informace najdete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md).

- [Interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md) v C# a Visual Basic, která poskytují zjednodušenou syntaxi ve srovnání s složených formátovacích řetězců.

> [!TIP]
> Můžete stáhnout [formátování nástroj](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), aplikaci, která umožňuje použití formátu řetězců pro číselné nebo datum a čas, hodnoty a zobrazí se výsledný řetězec.

<a name="table"></a> Následující tabulka popisuje specifikátory standardního číselného formátu a zobrazuje ukázkový výstup vyprodukovaný každým specifikátorem formátu. Najdete v článku [poznámky](#NotesStandardFormatting) části Další informace o používání řetězců standardního číselného formátu a [příklad](#example) části komplexní ukázky použití.

|Specifikátor formátu|Name|Popis|Příklady|
|----------------------|----------|-----------------|--------------|
|"C" nebo "c"|Měna|Výsledek: Hodnotu měny.<br /><br /> Podporuje: Všechny číselné typy.<br /><br /> Specifikátor přesnosti: Počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: Určené <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Další informace: [Specifikátor formátu Currency ("C")](#CFormatString).|123.456 ("C" en US) -> `$123.46`<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥ 123<br /><br /> ->-123.456 ("C3", en US) `($123.456)`<br /><br /> -123.456 ("C3", fr-FR) -> €-123,456<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|
|"D" nebo "d"|Desetinné číslo|Výsledek: Celá čísla s volitelným záporným znaménkem.<br /><br /> Podporuje: Pouze celočíselné typy.<br /><br /> Specifikátor přesnosti: Minimální počet číslic.<br /><br /> Výchozí specifikátor přesnosti: Minimální požadovaný počet číslic.<br /><br /> Další informace: [Specifikátor formátu desítkového](#DFormatString).|1234-1234 ("D") ><br /><br /> -1234 ("D6") -> -001234|
|"E" nebo "e"|Exponenciální (vědecký) zápis|Výsledek: Exponenciální notaci.<br /><br /> Podporuje: Všechny číselné typy.<br /><br /> Specifikátor přesnosti: Počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: 6.<br /><br /> Další informace: [Specifikátor exponenciálního ("E") formátu](#EFormatString).|1052.0329112756 ("E" en US) -> 1.052033E + 003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1 052033e + 003<br /><br /> -1052.0329112756 ("e2", en US) -> - 1.05e + 003<br /><br /> -1052.0329112756 ("E2", fr-FR) -> -1,05E+003|
|"F" nebo "f"|Pevná desetinná čárka|Výsledek: Integrální a desítkové číslo s volitelným záporným znaménkem.<br /><br /> Podporuje: Všechny číselné typy.<br /><br /> Specifikátor přesnosti: Počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: Určené <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Další informace: [Specifikátor formátu s pevnou desetinnou čárkou ("F")](#FFormatString).|1234.567 ("F" en US) -> 1234.57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1" en US) -> 1234.0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234.56 ("F4", en US) ->-1234.5600<br /><br /> -1234.56 ("F4", de-DE) -> - 1234,5600|
|"G" nebo "g"|Obecné|Výsledek: Další compact s pevnou desetinnou čárkou nebo vědecký zápis.<br /><br /> Podporuje: Všechny číselné typy.<br /><br /> Specifikátor přesnosti: Počet platných číslic.<br /><br /> Výchozí specifikátor přesnosti: Závisí na číselném typu.<br /><br /> Další informace: [Specifikátor obecného ("G") formátu](#GFormatString).|-123.456 ("G", en US) ->-123.456<br /><br /> -123.456 ("G", sv-SE) ->-123,456<br /><br /> 123.4546 ("G4" en US) -> 123.5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e – 25 ("G", en US) -> - 1.23456789E – 25<br /><br /> -1.234567890e – 25 ("G", sv-SE) -> -1, 23456789E 25|
|"N" nebo "n"|Číslo|Výsledek: Integrální a desítkové číslice, oddělovače skupin a oddělovač desetinných míst s volitelným záporným znaménkem.<br /><br /> Podporuje: Všechny číselné typy.<br /><br /> Specifikátor přesnosti: Požadovaný počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: Určené <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Další informace: [Specifikátor formátu ("N") číselné](#NFormatString).|1234.567 ("N" en US) -> 1,234.57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1" en US) -> 1,234.0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234.56 ("N3" en US) ->-1,234.560<br /><br /> -1234.56 ("N3", ru-RU) -> 234,560-1|
|"P" nebo "p"|Procento|Výsledek: Číslo vynásobené číslem 100 a zobrazují se symbolem procenta.<br /><br /> Podporuje: Všechny číselné typy.<br /><br /> Specifikátor přesnosti: Požadovaný počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: Určené <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Další informace: [Specifikátor formátu procent ("P")](#PFormatString).|1 ("P" en US) -> % 100,00<br /><br /> 1 ("P", fr-FR) -> 100,00 %<br /><br /> -0.39678 ("P1", en US) ->-39.7 %<br /><br /> -0.39678 ("P1", fr-FR) -> - 39,7 %|
|"R" nebo "r"|Zpáteční převod|Výsledek: Řetězec, který můžete zpátečního převodu na stejné číslo.<br /><br /> Podporuje: <xref:System.Single>, <xref:System.Double>, a <xref:System.Numerics.BigInteger>.<br /><br /> Poznámka: Doporučuje <xref:System.Numerics.BigInteger> pouze typu. Pro <xref:System.Double> typy, použijte "G17"; pro <xref:System.Single> typy, použijte "G9". <br> Specifikátor přesnosti: Ignorovat.<br /><br /> Další informace: [Specifikátor formátu Round-trip ("R")](#RFormatString).|123456789.12345678 ("R") -> 123456789.12345678<br /><br /> -1234567890.12345678 ("R") ->-1234567890.1234567|
|"X" nebo "x"|Šestnáctková hodnota|Výsledek: Je možné šestnáctkový řetězec.<br /><br /> Podporuje: Pouze celočíselné typy.<br /><br /> Specifikátor přesnosti: Počet číslic ve výsledném řetězci.<br /><br /> Další informace: [Šestnáctková ("X") specifikátor formátu](#XFormatString).|255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|
|Jakýkoli jiný samostatný znak|Neznámý specifikátor|Výsledek: Vyvolá výjimku <xref:System.FormatException> v době běhu.||

<a name="Using"></a>

## <a name="using-standard-numeric-format-strings"></a>Používání řetězců standardního číselného formátu

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Řetězec standardního číselného formátu lze použít pro definování formátování číselné hodnoty jedním ze dvou způsobů:

- Může být předán přetížení `ToString` metodu, která má `format` parametru. Následující příklad formátuje číselnou hodnotu jako řetězec měny v aktuální jazykové verzi (v tomto případě jazykové verze en US).

  [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
  [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]

- Lze je zadat jako `formatString` argument v položce formátu pomocí metod jako <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, a <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>. Další informace najdete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md). Následující příklad používá položku formátu pro vložení hodnoty měny do řetězce.

  [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
  [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]

  Volitelně můžete zadat `alignment` argument určující šířku číselného pole a jeho hodnota určuje, zda je zarovnaný doprava nebo doleva. Následující příklad vlevo – zarovná hodnotu měny v poli 28 znaků a je vpravo – zarovná hodnotu měny v poli 14 znak.

  [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
  [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]

- Lze je zadat jako `formatString` argument v interpolovaném řetězci položka interpolovaný výraz. Další informace najdete v tématu [interpolace](../../csharp/language-reference/tokens/interpolated.md) tématu v referenční dokumentace jazyka C# nebo [interpolovaných řetězců](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) tématu v referenční dokumentace jazyka Visual Basic.

Následující oddíly obsahují podrobné informace o jednotlivých řetězcích standardního číselného formátu.

<a name="CFormatString"></a>

## <a name="the-currency-c-format-specifier"></a>Specifikátor formátu měny ("C")

Specifikátor formátu "C" (neboli měny) převede číslo na řetězec, který představuje peněžní částku. Specifikátor přesnosti označuje požadovaný počet desetinných míst ve výsledném řetězci. Pokud specifikátor přesnosti je vynechán, je výchozí přesnost definována <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> vlastnost.

Pokud má formátovaná hodnota větší než zadaný nebo výchozí počet desetinných míst, je desetinná hodnota ve výsledném řetězci zaokrouhlena. Pokud je vpravo od zadaného počtu desetinných míst hodnota 5 nebo vyšší, bude poslední číslice ve výsledném řetězci zaokrouhlena směrem nahoru.

Výsledný řetězec je ovlivněn informace o formátování aktuálního objektu <xref:System.Globalization.NumberFormatInfo> objektu. Následující tabulce jsou uvedeny <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování vráceného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Definuje umístění symbolu měny pro kladné hodnoty.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Definuje umístění symbolu měny pro záporné hodnoty a určuje, zda je záporné znaménko představováno závorkami nebo <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> vlastnost.|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje záporné znaménko použité Pokud <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> označuje, že nejsou použity závorky.|
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Definuje symbol měny.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Definuje výchozí počet desítkových číslic v hodnotě měny. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální a desítkové číslice.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Definuje řetězec, který odděluje skupiny integrálních čísel.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Definuje počet celých číslic, které se zobrazují ve skupině.|

Následující příklad formátuje <xref:System.Double> specifikátorem formátu měny.

[!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
[!code-csharp-interactive[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
[!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]

[Zpět k tabulce](#table)

<a name="DFormatString"></a>

## <a name="the-decimal-d-format-specifier"></a>Specifikátor formátu desítkového čísla ("D")

Specifikátor formátu "D" (desítkové číslo) převede číslo na řetězec desítkových číslic (0-9), kterému předchází symbol mínus, je-li číslo záporné. Tento formát je podporován pouze pro integrální typy.

Specifikátor přesnosti označuje minimální počet číslic požadovaných ve výsledném řetězci. V případě potřeby je číslo doplněno nulami po levé straně za účelem vytvoření počtu číslic, který je dán specifikátorem přesnosti. Pokud není zadán žádný specifikátor přesnosti, je výchozí hodnotou minimální hodnota požadovaná k vytvoření celého čísla bez počátečních nul.

Výsledný řetězec je ovlivněn informace o formátování aktuálního objektu <xref:System.Globalization.NumberFormatInfo> objektu. Jak znázorňuje následující tabulka, jediná vlastnost ovlivňuje formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|

Následující příklad formátuje <xref:System.Int32> specifikátorem desítkového formátu.

[!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
[!code-csharp-interactive[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
[!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]

[Zpět k tabulce](#table)

<a name="EFormatString"></a>

## <a name="the-exponential-e-format-specifier"></a>Exponenciální specifikátor formátu ("E")

Exponenciální specifikátor formátu ("E") převede číslo na řetězec ve formě "-d.ddd…E+ddd" nebo "-d.ddd…e+ddd", kde každé "d" označuje číslici (0-9). Pokud je číslo záporné, řetězec začíná symbolem mínus. Desetinné čárce předchází vždy přesně jedna číslice.

Specifikátor přesnosti označuje požadovaný počet číslic za desetinnou čárkou. Pokud specifikátor přesnosti vynecháte, je za desetinnou čárkou použit výchozí počet šesti číslic.

Velikost specifikátoru formátu označuje, zda má být před exponentem použita předpona "E" nebo "e". Exponent se skládá vždy ze znaménka plus nebo mínus a minimálně tří číslic. Aby byl tento minimální požadavek splněn, je exponent v případě potřeby doplněn nulami.

Výsledný řetězec je ovlivněn informace o formátování aktuálního objektu <xref:System.Globalization.NumberFormatInfo> objektu. Následující tabulce jsou uvedeny <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování vráceného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné pro koeficient i pro exponent.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic v koeficientu.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Definuje řetězec, který označuje, že exponent je kladný.|

Následující příklad formátuje <xref:System.Double> specifikátorem exponenciálního formátu.

[!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
[!code-csharp-interactive[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
[!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]

[Zpět k tabulce](#table)

<a name="FFormatString"></a>

## <a name="the-fixed-point-f-format-specifier"></a>Specifikátor formátu s pevnou desetinnou čárkou ("F")

Specifikátor formátu s pevnou desetinnou čárkou ("F") převede číslo na řetězec ve tvaru "-ddd.ddd…" kde každé "d" označuje číslici (0-9). Pokud je číslo záporné, řetězec začíná symbolem mínus.

Specifikátor přesnosti označuje požadovaný počet desetinných míst. Pokud specifikátor přesnosti je vynechán, aktuální <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> vlastnost dodává číselnou přesnost.

Výsledný řetězec je ovlivněn informace o formátování aktuálního objektu <xref:System.Globalization.NumberFormatInfo> objektu. V následující tabulce jsou uvedeny vlastnosti <xref:System.Globalization.NumberFormatInfo> , které řídí formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definuje výchozí počet desítkových číslic. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|

Následující příklad formátuje <xref:System.Double> a <xref:System.Int32> specifikátorem formátu s pevnou desetinnou čárkou.

[!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
[!code-csharp-interactive[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
[!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]

[Zpět k tabulce](#table)

<a name="GFormatString"></a>

## <a name="the-general-g-format-specifier"></a>Specifikátor obecného formátu ("G")

Specifikátor obecného formátu ("G") převede číslo na další compact s pevnou desetinnou čárkou nebo vědecký zápis, v závislosti na typu čísla a určuje, zda je k dispozici specifikátor přesnosti. Specifikátor přesnosti definuje maximální počet platných číslic, které mohou být zobrazeny ve výsledném řetězci. Pokud specifikátor přesnosti vynecháte nebo je specifikátor nulový, pak typ čísla určuje výchozí přesnost, jak je uvedeno v následující tabulce.

|Číselný typ|Výchozí přesnost|
|------------------|-----------------------|
|<xref:System.Byte> Nebo <xref:System.SByte>|3 číslice|
|<xref:System.Int16> Nebo <xref:System.UInt16>|5 číslic|
|<xref:System.Int32> Nebo <xref:System.UInt32>|10 číslic|
|<xref:System.Int64>|19 číslic|
|<xref:System.UInt64>|20 číslic|
|<xref:System.Numerics.BigInteger>|Neomezený počet (stejné jako ["R"](#RFormatString))|
|<xref:System.Single>|7 číslic|
|<xref:System.Double>|15 číslic|
|<xref:System.Decimal>|29 platnými číslicemi|

Zápis s pevnou desetinnou čárkou se používá v případě, že exponent, který by byl výsledkem vyjádření čísla ve vědeckém zápisu, je větší než -5 a menší než specifikátor přesnosti. Jinak se použije vědecký zápis. V případě potřeby obsahuje výsledek desetinnou čárku a koncové nuly po vynechání desetinné čárky. Pokud je k dispozici specifikátor přesnosti a počet platných číslic ve výsledku překračuje zadanou přesnost, pak jsou přebytečné koncové nuly odstraněny zaokrouhlením.

Nicméně pokud je číslo <xref:System.Decimal> a specifikátor přesnosti je vynechán, je vždy použit zápis s pevnou desetinnou čárkou a přebytečné nuly jsou zachovány.

Pokud použijete vědecký zápis, pak je před exponentem ve výsledku předpona "E", je-li specifikátor formát "G"; nebo předpona "e", je-li specifikátor formátu "g". Exponent obsahuje minimálně dvě číslice. Tím se liší od formátu pro vědecký zápis, který je vytvořen exponenciálním specifikátorem formátu, což zahrnuje minimálně tři číslice v exponentu.

Všimněte si, že při použití s <xref:System.Double> hodnotu, specifikátor formátu "G17" zajistí, že původní <xref:System.Double> úspěšně hodnota doby odezvy. Důvodem je, že <xref:System.Double> je IEEE 754-2008-kompatibilní s dvojitou přesností (`binary64`) číslo s desetinnou čárkou, která poskytuje až 17 nejvýznamnějších číslic přesnosti s plovoucí desetinnou čárkou. Doporučujeme místo jeho použití [specifikátor formátu "R"](#RFormatString), protože v některých případech "R" nepodaří úspěšně round-trip hodnot s plovoucí čárkou dvojitou přesností. Následující příklad ukazuje jeden takový případ.

[!code-csharp-interactive[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs#GeneralFormatSpecifier)]
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]

Při použití s <xref:System.Single> hodnotu, specifikátor formátu "G9" zajistí, že původní <xref:System.Single> úspěšně hodnota doby odezvy. Důvodem je, že <xref:System.Single> je IEEE 754-2008-kompatibilní s jednoduchou přesností (`binary32`) číslo s desetinnou čárkou, která poskytuje až devět nejvýznamnějších číslic přesnosti s plovoucí desetinnou čárkou. Kvůli výkonu doporučujeme místo jeho použití [specifikátor formátu "R"](#RFormatString).

Výsledný řetězec je ovlivněn informace o formátování aktuálního objektu <xref:System.Globalization.NumberFormatInfo> objektu. Následující tabulce jsou uvedeny <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Definuje řetězec, který označuje, že exponent je kladný.|

Následující příklad formátuje různé hodnoty s plovoucí desetinnou čárkou se specifikátorem obecného formátu.

[!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
[!code-csharp-interactive[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
[!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]

[Zpět k tabulce](#table)

<a name="NFormatString"></a>

## <a name="the-numeric-n-format-specifier"></a>Specifikátor číselného formátu ("N")

Specifikátor číselného formátu ("N") převede číslo na řetězec ve formě "-d,ddd,ddd.ddd…", kde "-" označuje symbol záporného čísla, je-li vyžadován, "d" označuje číslice (0-9), "," označuje oddělovač skupin a "." označuje symbol desetinné čárky. Specifikátor přesnosti označuje požadovaný počet číslic za desetinnou čárkou. Pokud specifikátor přesnosti je vynechán, počet desetinných míst je definován aktuální <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> vlastnost.

Výsledný řetězec je ovlivněn informace o formátování aktuálního objektu <xref:System.Globalization.NumberFormatInfo> objektu. Následující tabulce jsou uvedeny <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Definuje formát záporných hodnot a určuje, zda je záporné znaménko představováno závorkami nebo <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> vlastnost.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Definuje počet integrálních číslic zobrazených mezi oddělovači skupin.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Definuje řetězec, který odděluje skupiny integrálních čísel.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální a desítkové číslice.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definuje výchozí počet desítkových číslic. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|

Následující příklad formátuje různé hodnoty s plovoucí desetinnou čárkou se specifikátorem číselného formátu.

[!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
[!code-csharp-interactive[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
[!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]

[Zpět k tabulce](#table)

<a name="PFormatString"></a>

## <a name="the-percent-p-format-specifier"></a>Specifikátor procentuálního formátu ("P")

Specifikátor procentuálního formátu ("P") vynásobí číslo 100 a převede ho na řetězec, který představuje procenta. Specifikátor přesnosti označuje požadovaný počet desetinných míst. Pokud specifikátor přesnosti je vynechán, je výchozí číselná přesnost poskytovaná aktuální <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> vlastnost se používá.

Následující tabulce jsou uvedeny <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování vráceného řetězce.

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

Následující příklad formátuje různé hodnoty s plovoucí desetinnou čárkou se specifikátorem procentuálního formátu.

[!code-cpp[Formatting.Numeric.Standard#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#7)]
[!code-csharp-interactive[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
[!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]

[Zpět k tabulce](#table)

<a name="RFormatString"></a>

## <a name="the-round-trip-r-format-specifier"></a>Specifikátor formátu zpátečního převodu ("R")

Operace round-trip specifikátor formátu ("R") se pokusí zajistit, že číselná hodnota, která je převedena na řetězec je analyzována zpět na stejnou číselnou hodnotu. Tento formát je podporován pouze pro <xref:System.Single>, <xref:System.Double>, a <xref:System.Numerics.BigInteger> typy.

Pro <xref:System.Double> hodnoty, specifikátor formátu "R" v některých případech se nepodaří úspěšně odezvy na původní hodnotu. U obou <xref:System.Double> a <xref:System.Single> hodnoty, nabízí také relativně nízký výkon. Namísto toho doporučujeme použít ["G17"](#GFormatString) formátovací řetězec pro <xref:System.Double> hodnoty a ["G9"](#GFormatString) specifikátor formátu pro úspěšně round-trip <xref:System.Single> hodnoty.

Když <xref:System.Numerics.BigInteger> hodnota formátována pomocí tohoto specifikátoru, obsahuje všechny významné číslice v řetězcové vyjádření <xref:System.Numerics.BigInteger> hodnotu.

Ačkoli můžete použít také specifikátor přesnosti, bude ignorován. Pokud použijete tento specifikátor, má zpáteční převod přednost nad přesností.
Výsledný řetězec je ovlivněn informace o formátování aktuálního objektu <xref:System.Globalization.NumberFormatInfo> objektu. Následující tabulce jsou uvedeny <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování výsledného řetězce.

|Vlastnost NumberFormatInfo|Popis|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Definuje řetězec, který označuje, že exponent je kladný.|

Následující příklad formátuje <xref:System.Numerics.BigInteger> specifikátorem formátu round-trip.

[!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
[!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
[!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]

> [!IMPORTANT]
> V některých případech <xref:System.Double> hodnoty ve formátu s řetězce standardního číselného formátu "R" úspěšně round-trip Pokud zkompilován pomocí `/platform:x64` nebo `/platform:anycpu` přepínače a spustit v 64bitových systémech. Viz odstavec pro další informace.

Chcete-li vyřešit problém <xref:System.Double> hodnoty naformátovaná pomocí standardního číselného formátu "R" řetězec není úspěšně verzemi, pokud kompilováno s použitím `/platform:x64` nebo `/platform:anycpu` přepínače a spustit v 64bitové systémy. můžete naformátovat <xref:System.Double> hodnoty pomocí řetězce standardního číselného formátu "G17". Následující příklad používá řetězec formátu "R" s <xref:System.Double> fakturuje se u tohoto není operace round-trip hodnotu úspěšně, a také používá "G17" Formát řetězec, který se úspěšně odezvy na původní hodnotu.

[!code-csharp-interactive[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#RoundTrip)]
[!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]

[Zpět k tabulce](#table)

<a name="XFormatString"></a>

## <a name="the-hexadecimal-x-format-specifier"></a>Specifikátor šestnáctkového formátu ("X")

Specifikátor šestnáctkového formátu ("X") převede číslo na řetězec šestnáctkových číslic. Velikost specifikátoru formátu označuje, zda pro šestnáctkové číslice, které jsou větší než 9, je nutné používat velká nebo malá písmena. Například pro vytvoření řetězce "ABCDEF" použijte formát "X", pro vytvoření řetězce "abcdef" použijte formát "x". Tento formát je podporován pouze pro integrální typy.

Specifikátor přesnosti označuje minimální počet číslic požadovaných ve výsledném řetězci. V případě potřeby je číslo doplněno nulami po levé straně za účelem vytvoření počtu číslic, který je dán specifikátorem přesnosti.

Výsledný řetězec nemá vliv informace o formátování aktuálního objektu <xref:System.Globalization.NumberFormatInfo> objektu.

Následující příklad formátuje <xref:System.Int32> hodnoty s šestnáctkovým specifikátorem formátu.

[!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
[!code-csharp-interactive[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
[!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]

[Zpět k tabulce](#table)

<a name="NotesStandardFormatting"></a>

## <a name="notes"></a>Poznámky

### <a name="control-panel-settings"></a>Nastavení části Ovládací panely

Nastavení **místní a jazykové nastavení** položky v Ovládacích panelech ovlivní výsledný řetězec vytvořený při operaci formátování. Tato nastavení slouží k inicializaci <xref:System.Globalization.NumberFormatInfo> objekt přidružený k aktuální jazykové verzi vlákna, které poskytuje hodnoty použité k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.

Kromě toho pokud <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> konstruktor se používá k vytvoření instance nového <xref:System.Globalization.CultureInfo> objekt, který představuje stejnou jazykovou verzi jako aktuální jazyková verze systému, jakákoli vlastní nastavení podle **místní a jazykové nastavení** v Ovládacích panelech budou použita pro nový <xref:System.Globalization.CultureInfo> objektu. Můžete použít <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktor k vytvoření <xref:System.Globalization.CultureInfo> objekt, který nepředstavuje vlastní nastavení systému.

### <a name="numberformatinfo-properties"></a>Vlastnosti objektu NumberFormatInfo

Formátování je ovlivněno vlastnostmi aktuálního <xref:System.Globalization.NumberFormatInfo> objekt, který je poskytnut implicitně aktuální jazykovou verzí vlákna nebo explicitně parametrem <xref:System.IFormatProvider> parametru metody, která vyvolá formátování. Zadejte <xref:System.Globalization.NumberFormatInfo> nebo <xref:System.Globalization.CultureInfo> objekt pro tento parametr.

> [!NOTE]
> Informace o přizpůsobení vzorů nebo řetězců použitých ve formátování číselných hodnot naleznete v tématu <xref:System.Globalization.NumberFormatInfo> třídě.

### <a name="integral-and-floating-point-numeric-types"></a>Integrální typy čísel a typy s plovoucí desetinnou čárkou

Některé popisy specifikátorů standardního číselného formátu odkazují na integrální číselné typy nebo typy s plovoucí desetinnou čárkou. Integrální číselné typy jsou <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, a <xref:System.Numerics.BigInteger>. Číselné typy s plovoucí desetinnou čárkou jsou <xref:System.Decimal>, <xref:System.Single>, a <xref:System.Double>.

### <a name="floating-point-infinities-and-nan"></a>Nekonečno s plovoucí desetinnou čárkou a NaN

Bez ohledu na formátovací řetězec Pokud hodnota <xref:System.Single> nebo <xref:System.Double> je typ s plovoucí desetinnou čárkou kladné nekonečno, záporné nekonečno nebo nečíselné (NaN), je formátovaný řetězec hodnotou příslušné <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>, <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>, nebo <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> vlastnost, která je určena pomocí aktuálního použitého <xref:System.Globalization.NumberFormatInfo> objektu.

## <a name="example"></a>Příklad

[!INCLUDE[interactive-note](~/includes/csharp-interactive-partial-note.md)]

Následující příklad formátuje číselnou integrální hodnotu a hodnotu s plovoucí desetinnou čárkou pomocí jazykové verze en-US a všech specifikátorů standardního číselného formátu. Tento příklad používá dva konkrétní číselné typy (<xref:System.Double> a <xref:System.Int32>), ale produkoval by podobné výsledky pro každý z dalších číselných základních typů (<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Numerics.BigInteger>, <xref:System.Decimal>, a <xref:System.Single>).

[!code-csharp-interactive[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#FinalExample)]
[!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]

## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.NumberFormatInfo>
- [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
- [Postupy: Zarovnání čísla úvodními nulami](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)
- [Ukázka: Formátovací nástroj rozhraní .NET Framework 4](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
- [Složené formátování](../../../docs/standard/base-types/composite-formatting.md)
