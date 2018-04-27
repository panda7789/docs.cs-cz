---
title: Standardní řetězce formátu čísla
ms.date: 09/10/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 34fe406dac4cbbc0c25e43f479154fd3e398ffc2
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="standard-numeric-format-strings"></a>Standardní řetězce formátu čísla
Řetězce standardního číselného formátu se používají pro formátování běžných číselných typů. Řetězec standardní číselného formátu má podobu `Axx`, kde:  
  
-   `A` je volána jeden znak abecedy *formátovací řetězec*. Jakýkoli řetězec číselného formátu, který obsahuje více než jeden abecední znak, včetně prázdných znaků, je interpretován jako řetězec vlastního číselného formátu. Další informace najdete v tématu [vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
-   `xx` je volána volitelné celé číslo *specifikátor přesnosti*. Specifikátor přesnosti má rozsah od 0 do 99 a má vliv na počet číslic ve výsledku. Všimněte si, že specifikátor přesnosti určuje počet číslic v řetězcovou reprezentaci číslo. Neprovádí zaokrouhlení samotného čísla. Chcete-li provést zaokrouhlení operaci, použijte <xref:System.Math.Ceiling%2A?displayProperty=nameWithType>, <xref:System.Math.Floor%2A?displayProperty=nameWithType>, nebo <xref:System.Math.Round%2A?displayProperty=nameWithType> metoda.  
  
     Když *specifikátor přesnosti* řídí počet zlomkové číslic ve výsledném řetězci výsledek řetězce podle čísla, která se zaokrouhlí směrem od nuly (tedy pomocí <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>).  
  
    > [!NOTE]
    >  Specifikátor přesnosti určuje počet číslic ve výsledném řetězci. K vyplnění výsledném řetězci s počáteční nebo koncové mezery, použijte [složené formátování](../../../docs/standard/base-types/composite-formatting.md) funkci a definovat *zarovnání součást* v položce formátu.  
  
Standardní řetězce formátu čísla podporuje:

- Některé přetížení `ToString` metoda všechny číselné typy. Můžete například zadat řetězec číselného formátu tak, aby <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> a <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody. 
 
- .NET [funkce složeného formátování](../../../docs/standard/base-types/composite-formatting.md), který je využíván jiným některé `Write` a `WriteLine` metody <xref:System.Console> a <xref:System.IO.StreamWriter> třídy, <xref:System.String.Format%2A?displayProperty=nameWithType> metody a <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> metoda. Funkce složeného formátu umožňuje zahrnout řetězcovou reprezentaci více položek dat do jednoho řetězce, zadejte šířku pole a budete moct sladit čísel v poli. Další informace najdete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md).  

- [Interpolované řetězce](../../csharp/language-reference/tokens/interpolated.md) v C# a Visual Basic, které poskytují zjednodušenou syntaxi ve srovnání s složených formátovacích řetězců.
 
> [!TIP]
>  Si můžete stáhnout [formátování nástroj](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d), aplikace, která umožňuje použití formátu řetězce na hodnotu numerické nebo datum a čas hodnoty a zobrazí výsledný řetězec.  
  
<a name="table"></a> Následující tabulka popisuje specifikátory standardní číselného formátu a zobrazí ukázkový výstup produkovaný každým specifikátorem formátu. Najdete v článku [poznámky](#NotesStandardFormatting) části Další informace o používání standardní řetězce formátu čísla a [příklad](#example) části pro komplexní ukázky použití.  
  
|Specifikátor formátu|Název|Popis|Příklady|  
|----------------------|----------|-----------------|--------------|  
|"C" nebo "c"|Měna|Výsledek: hodnota měny.<br /><br /> Podporováno: všemi číselnými typy.<br /><br /> Specifikátor přesnosti: počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: určené <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Další informace: [The měny ("C") formát specifikátor](#CFormatString).|123.456 ("C", en US) -> $123,46<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥ 123<br /><br /> -123.456 ("C3", en US) -> ($123.456)<br /><br /> -123.456 ("C3", fr-FR) ->-123,456 €<br /><br /> -123.456 ("C3", ja-JP) ->-¥ 123.456|  
|"D" nebo "d"|Desetinné číslo|Výsledek: celá čísla s volitelným záporným znaménkem.<br /><br /> Podporováno: pouze integrálovými typy.<br /><br /> Specifikátor přesnosti: minimální počet číslic.<br /><br /> Výchozí specifikátor přesnosti: minimální požadovaný počet číslic.<br /><br /> Další informace: [The specifikátor formátu desítkového čísla d](#DFormatString).|1234-1234 ("D") &GT;<br /><br /> -1234 ("D6") -&GT;-001234|  
|"E" nebo "e"|Exponenciální (vědecký) zápis|Výsledek: exponenciální zápis.<br /><br /> Podporováno: všemi číselnými typy.<br /><br /> Specifikátor přesnosti: počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: 6.<br /><br /> Další informace: [exponenciálním ("E") specifikátor formátu](#EFormatString).|1052.0329112756 ("E" en US) -> 1.052033E + 003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1, 052033e + 003<br /><br /> -1052.0329112756 ("e2", en US) -> - 1.05e + 003<br /><br /> -1052.0329112756 ("E2", fr_FR) -> -1, 05E + 003|  
|"F" nebo "f"|Pevná desetinná čárka|Výsledek: integrální a desítkové číslo s volitelným záporným znaménkem.<br /><br /> Podporováno: všemi číselnými typy.<br /><br /> Specifikátor přesnosti: počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: určené <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Další informace: [s pevnou desetinnou čárkou specifikátor formátu ("F")](#FFormatString).|1234.567 ("F" en US) -> 1234,57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1" en US) -> 1234.0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234.56 ("F4", en US) ->-1234.5600<br /><br /> -1234.56 ("F4", de-DE) -> - 1234,5600|  
|"G" nebo "g"|Obecné|Výsledek: Další compact s pevnou desetinnou čárkou nebo vědecký zápis.<br /><br /> Podporováno: všemi číselnými typy.<br /><br /> Specifikátor přesnosti: počet nejvýznamnějších číslic.<br /><br /> Výchozí specifikátor přesnosti: závisí na číselném typu.<br /><br /> Další informace: [obecné ("G") specifikátor formátu](#GFormatString).|-123.456 ("G", en US) ->-123.456<br /><br /> -123.456 ("G", sv-SE) ->-123,456<br /><br /> 123.4546 ("G4" en US) -> 123.5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e-25 ("G", en US) -> - 1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1, 23456789E 25|  
|"N" nebo "n"|Číslo|Výsledek: integrální a desítkové číslice, oddělovače skupin a oddělovač desetinných míst s volitelným záporným znaménkem.<br /><br /> Podporováno: všemi číselnými typy.<br /><br /> Specifikátor přesnosti: požadovaný počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: určené <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Další informace: [The číselné ("N") specifikátor formátu](#NFormatString).|1234.567 ("N" en US) -> 1,234.57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1" en US) -> 1,234.0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234.56 ("N3", en US) ->-1,234.560<br /><br /> -1234.56 ("N3", ru-RU) -> 234,560-1|  
|"P" nebo "p"|Procento|Výsledek: číslo vynásobené číslem 100 a zobrazené se symbolem procenta.<br /><br /> Podporováno: všemi číselnými typy.<br /><br /> Specifikátor přesnosti: požadovaný počet desetinných míst.<br /><br /> Výchozí specifikátor přesnosti: určené <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType>.<br /><br /> Další informace: [specifikátor formátu Percent ("P")](#PFormatString).|1 ("P" en US) -> % 100,00<br /><br /> 1 ("P", fr-FR) -> 100,00 %<br /><br /> -0.39678 ("P1", en US) ->-39.7 %<br /><br /> -0.39678 ("P1", fr-FR) -> - 39,7 %|  
|"R" nebo "r"|Zpáteční převod|Výsledek: řetězec, který může použít operaci zpátečního převodu na stejné číslo.<br /><br /> Podporuje: <xref:System.Single>, <xref:System.Double>, a <xref:System.Numerics.BigInteger>.<br /><br /> Poznámka: Doporučujeme pro <xref:System.Numerics.BigInteger> pouze typu. Pro <xref:System.Double> typy, použijte "G17"; pro <xref:System.Single> typy, použijte "G9". </br> Specifikátor přesnosti: ignorováno.<br /><br /> Další informace: [specifikátor formátu Round-trip ("R")](#RFormatString).|123456789.12345678 ("R") -&GT; 123456789.12345678<br /><br /> -1234567890.12345678 ("R") -&GT;-1234567890.1234567|  
|"X" nebo "x"|Šestnáctková hodnota|Výsledek: šestnáctkový řetězec.<br /><br /> Podporováno: pouze integrálovými typy.<br /><br /> Specifikátor přesnosti: počet číslic ve výsledném řetězci.<br /><br /> Další informace: [šestnáctkové ("X") specifikátor formátu](#XFormatString).|255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|  
|Jakýkoli jiný samostatný znak|Neznámý specifikátor|Výsledek: Vrátí <xref:System.FormatException> za běhu.||  
  
<a name="Using"></a>   
## <a name="using-standard-numeric-format-strings"></a>Používání řetězců standardního číselného formátu  
 Řetězec standardního číselného formátu lze použít pro definování formátování číselné hodnoty jedním ze dvou způsobů:  
  
-   Může být předán přetížení `ToString` metodu, která má `format` parametr. Následující příklad formátuje číselnou hodnotu jako řetězec měny v aktuální jazykovou verzi (v tomto případě jazyková verze en US).  
  
     [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
     [!code-csharp[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
     [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]  
  
-   Můžete zadat jako `formatString` argument v položce formátu použít s tyto metody jako <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, a <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>. Další informace najdete v tématu [složené formátování](../../../docs/standard/base-types/composite-formatting.md). Následující příklad používá položku formátu pro vložení hodnoty měny do řetězce.  
  
     [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
     [!code-csharp[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
     [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]  
  
     Volitelně můžete zadat `alignment` argument a nastavte šířku číselná pole a zda je jeho hodnota vpravo nebo vlevo zarovnaný. Následující příklad doleva zarovná hodnotu měny v poli 28 znaků, a ho vpravo-hodnotu měny v poli 14 znaků.  
  
     [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
     [!code-csharp[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
     [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]  
  
-   Můžete zadat jako `formatString` argument položku interpolované výraz interpolované řetězce. Další informace najdete v tématu [řetězec interpolace](../../csharp/language-reference/tokens/interpolated.md) téma v referenční dokumentace jazyka C# nebo [interpolované řetězce](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) téma v referenční dokumentace jazyka Visual Basic.  
  
 Následující oddíly obsahují podrobné informace o jednotlivých řetězcích standardního číselného formátu.  
  
<a name="CFormatString"></a>   
## <a name="the-currency-c-format-specifier"></a>Specifikátor formátu měny ("C")  
 Specifikátor formátu "C" (neboli měny) převede číslo na řetězec, který představuje peněžní částku. Specifikátor přesnosti označuje požadovaný počet desetinných míst ve výsledném řetězci. Pokud je vynechán specifikátor přesnosti, výchozí přesnost je definovaná <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> vlastnost.  
  
 Pokud má formátovaná hodnota větší než zadaný nebo výchozí počet desetinných míst, je desetinná hodnota ve výsledném řetězci zaokrouhlena. Pokud je vpravo od zadaného počtu desetinných míst hodnota 5 nebo vyšší, bude poslední číslice ve výsledném řetězci zaokrouhlena směrem nahoru.  
  
 Výsledný řetězec má vliv informace formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. Následující tabulka uvádí <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování vrácený řetězec.  
  
|Vlastnost NumberFormatInfo|Popis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Definuje umístění symbolu měny pro kladné hodnoty.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Určuje umístění symbolu měny pro záporné hodnoty a určuje, zda záporné znaménko je reprezentována závorkách nebo <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> vlastnost.|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje záporné znaménko použít, pokud <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> označuje, že nejsou použity závorky.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Definuje symbol měny.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Definuje výchozí počet desítkových číslic v hodnotě měny. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální a desítkové číslice.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Definuje řetězec, který odděluje skupiny integrálních čísel.|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Definuje počet celých číslic, které se zobrazují ve skupině.|  
  
 Následující příklad formátuje <xref:System.Double> hodnotu s specifikátor formátu měny.  
  
 [!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
 [!code-csharp[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
 [!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]  
  
 [Zpět k tabulce](#table)  
  
<a name="DFormatString"></a>   
## <a name="the-decimal-d-format-specifier"></a>Specifikátor formátu desítkového čísla ("D")  
 Specifikátor formátu "D" (desítkové číslo) převede číslo na řetězec desítkových číslic (0-9), kterému předchází symbol mínus, je-li číslo záporné. Tento formát je podporován pouze pro integrální typy.  
  
 Specifikátor přesnosti označuje minimální počet číslic požadovaných ve výsledném řetězci. V případě potřeby je číslo doplněno nulami po levé straně za účelem vytvoření počtu číslic, který je dán specifikátorem přesnosti. Pokud není zadán žádný specifikátor přesnosti, je výchozí hodnotou minimální hodnota požadovaná k vytvoření celého čísla bez počátečních nul.  
  
 Výsledný řetězec má vliv informace formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. Jak znázorňuje následující tabulka, jediná vlastnost ovlivňuje formátování výsledného řetězce.  
  
|Vlastnost NumberFormatInfo|Popis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|  
  
 Následující příklad formátuje <xref:System.Int32> hodnotu s specifikátor formátu desetinného čísla.  
  
 [!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
 [!code-csharp[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
 [!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]  
  
 [Zpět k tabulce](#table)  
  
<a name="EFormatString"></a>   
## <a name="the-exponential-e-format-specifier"></a>Exponenciální specifikátor formátu ("E")  
 Exponenciální specifikátor formátu ("E") převede číslo na řetězec ve formě "-d.ddd…E+ddd" nebo "-d.ddd…e+ddd", kde každé "d" označuje číslici (0-9). Pokud je číslo záporné, řetězec začíná symbolem mínus. Desetinné čárce předchází vždy přesně jedna číslice.  
  
 Specifikátor přesnosti označuje požadovaný počet číslic za desetinnou čárkou. Pokud specifikátor přesnosti vynecháte, je za desetinnou čárkou použit výchozí počet šesti číslic.  
  
 Velikost specifikátoru formátu označuje, zda má být před exponentem použita předpona "E" nebo "e". Exponent se skládá vždy ze znaménka plus nebo mínus a minimálně tří číslic. Aby byl tento minimální požadavek splněn, je exponent v případě potřeby doplněn nulami.  
  
 Výsledný řetězec má vliv informace formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. Následující tabulka uvádí <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování vrácený řetězec.  
  
|Vlastnost NumberFormatInfo|Popis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné pro koeficient i pro exponent.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic v koeficientu.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Definuje řetězec, který označuje, že exponent je kladný.|  
  
 Následující příklad formátuje <xref:System.Double> hodnotu s specifikátor exponenciálním formátu.  
  
 [!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
 [!code-csharp[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
 [!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]  
  
 [Zpět k tabulce](#table)  
  
<a name="FFormatString"></a>   
## <a name="the-fixed-point-f-format-specifier"></a>Specifikátor formátu s pevnou desetinnou čárkou ("F")  
 S pevnou desetinnou čárkou specifikátor formátu ("F") převádí číslo na řetězec ve formátu "-ddd, ddd …" kde každý "d" označuje číslici (0-9). Pokud je číslo záporné, řetězec začíná symbolem mínus.  
  
 Specifikátor přesnosti označuje požadovaný počet desetinných míst. Pokud je vynechán specifikátor přesnosti, aktuální <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> vlastnost dodává číselnou přesnost.  
  
 Výsledný řetězec má vliv informace formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. Následující tabulka uvádí vlastnosti <xref:System.Globalization.NumberFormatInfo> objekt, který řídí formátování výsledný řetězec.  
  
|Vlastnost NumberFormatInfo|Popis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definuje výchozí počet desítkových číslic. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|  
  
 Následující příklad formátuje <xref:System.Double> a <xref:System.Int32> hodnotu s specifikátor formátu s pevnou desetinnou čárkou.  
  
 [!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
 [!code-csharp[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
 [!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]  
  
 [Zpět k tabulce](#table)  
  
<a name="GFormatString"></a>   
## <a name="the-general-g-format-specifier"></a>Specifikátor obecného formátu ("G")  
 Obecné ("") specifikátor formátu převádí číslo další compact s pevnou desetinnou čárkou nebo vědecký zápis, v závislosti na typu číslo a zda je přítomen specifikátorem přesnosti. Specifikátor přesnosti definuje maximální počet platných číslic, které mohou být zobrazeny ve výsledném řetězci. Pokud specifikátor přesnosti vynecháte nebo je specifikátor nulový, pak typ čísla určuje výchozí přesnost, jak je uvedeno v následující tabulce.  
  
|Číselný typ|Výchozí přesnost|  
|------------------|-----------------------|  
|<xref:System.Byte> Nebo <xref:System.SByte>|3 číslice|  
|<xref:System.Int16> Nebo <xref:System.UInt16>|5 číslic|  
|<xref:System.Int32> Nebo <xref:System.UInt32>|10 číslic|  
|<xref:System.Int64>|19 číslic|  
|<xref:System.UInt64>|20 číslic|  
|<xref:System.Numerics.BigInteger>|Neomezená (stejné jako ["R"](#RFormatString))|  
|<xref:System.Single>|7 míst|  
|<xref:System.Double>|15 číslic.|  
|<xref:System.Decimal>|29 míst|  
  
 Zápis s pevnou desetinnou čárkou se používá v případě, že exponent, který by byl výsledkem vyjádření čísla ve vědeckém zápisu, je větší než -5 a menší než specifikátor přesnosti. Jinak se použije vědecký zápis. V případě potřeby obsahuje výsledek desetinnou čárku a koncové nuly po vynechání desetinné čárky. Pokud je k dispozici specifikátor přesnosti a počet platných číslic ve výsledku překračuje zadanou přesnost, pak jsou přebytečné koncové nuly odstraněny zaokrouhlením.  
  
 Ale pokud je číslo <xref:System.Decimal> a specifikátor přesnosti je tento parametr vynechán, s pevnou desetinnou čárkou zápis se vždy používá a koncové nuly se zachovají.  
  
 Pokud použijete vědecký zápis, pak je před exponentem ve výsledku předpona "E", je-li specifikátor formát "G"; nebo předpona "e", je-li specifikátor formátu "g". Exponent obsahuje minimálně dvě číslice. Tím se liší od formátu pro vědecký zápis, který je vytvořen exponenciálním specifikátorem formátu, což zahrnuje minimálně tři číslice v exponentu.  
 
Všimněte si, že při použití s <xref:System.Double> hodnotu specifikátor formátu "G17" zajišťuje, že původní <xref:System.Double> hodnota úspěšně odezvy. Důvodem je, že <xref:System.Double> je IEEE 754 2008-kompatibilní s dvojitou přesností (`binary64`) plovoucí číslo bodu, která poskytuje až 17 platných číslic. Doporučujeme místo jeho použití ["R" formátovací řetězec](#RFormatString), protože v některých případech "R" nepodaří úspěšně odezvy Dvojitá přesnost hodnot s plovoucí desetinnou. Následující příklad ilustruje jeden takový případ.

[!code-csharp[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs)]   
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]   

Při použití s <xref:System.Single> hodnotu specifikátor formátu "G9" zajišťuje, že původní <xref:System.Single> hodnota úspěšně odezvy. Důvodem je, že <xref:System.Single> je IEEE 754 2008-kompatibilní s jednoduchou přesností (`binary32`) plovoucí číslo bodu, která poskytuje až devět platných číslic. Doporučujeme místo jeho použití ["R" formátovací řetězec](#RFormatString), protože v některých případech "R" nepodaří úspěšně odezvy jednoduchou přesností hodnot s plovoucí desetinnou.

 Výsledný řetězec má vliv informace formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. Následující tabulka uvádí <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování řetězce výsledek.  
  
|Vlastnost NumberFormatInfo|Popis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Definuje řetězec, který označuje, že exponent je kladný.|  
  
 Následující příklad formátuje různé hodnoty s plovoucí desetinnou čárkou se specifikátorem obecného formátu.  
  
 [!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
 [!code-csharp[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
 [!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]  
  
 [Zpět k tabulce](#table)  
  
<a name="NFormatString"></a>   
## <a name="the-numeric-n-format-specifier"></a>Specifikátor číselného formátu ("N")  
 Specifikátor číselného formátu ("N") převede číslo na řetězec ve formě "-d,ddd,ddd.ddd…", kde "-" označuje symbol záporného čísla, je-li vyžadován, "d" označuje číslice (0-9), "," označuje oddělovač skupin a "." označuje symbol desetinné čárky. Specifikátor přesnosti označuje požadovaný počet číslic za desetinnou čárkou. Pokud je vynechán specifikátor přesnosti, počet desetinných míst je definována aktuálním <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> vlastnost.  
  
 Výsledný řetězec má vliv informace formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. Následující tabulka uvádí <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování řetězce výsledek.  
  
|Vlastnost NumberFormatInfo|Popis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|  
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Definuje formát záporné hodnoty a určuje, zda záporné znaménko je reprezentována závorkách nebo <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> vlastnost.|  
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Definuje počet integrálních číslic zobrazených mezi oddělovači skupin.|  
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Definuje řetězec, který odděluje skupiny integrálních čísel.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální a desítkové číslice.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Definuje výchozí počet desítkových číslic. Tuto hodnotu lze přepsat pomocí specifikátoru přesnosti.|  
  
 Následující příklad formátuje různé hodnoty s plovoucí desetinnou čárkou se specifikátorem číselného formátu.  
  
 [!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
 [!code-csharp[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
 [!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]  
  
 [Zpět k tabulce](#table)  
  
<a name="PFormatString"></a>   
## <a name="the-percent-p-format-specifier"></a>Specifikátor procentuálního formátu ("P")  
 Specifikátor procentuálního formátu ("P") vynásobí číslo 100 a převede ho na řetězec, který představuje procenta. Specifikátor přesnosti označuje požadovaný počet desetinných míst. Pokud je vynechán specifikátor přesnosti, výchozí číselná přesnost poskytnutá aktuální <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> vlastnost se používá.  
  
 Následující tabulka uvádí <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování vrácený řetězec.  
  
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
 [!code-csharp[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
 [!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]  
  
 [Zpět k tabulce](#table)  
  
<a name="RFormatString"></a>   
## <a name="the-round-trip-r-format-specifier"></a>Specifikátor formátu zpátečního převodu ("R")  
 Operace round-trip specifikátor formátu ("R") se pokusí zajistit, že je zpět do stejné číselnou hodnotu analyzovat číselnou hodnotu, která je převedeno na řetězec. Tento formát je podporován pouze <xref:System.Single>, <xref:System.Double>, a <xref:System.Numerics.BigInteger> typy.  

Pro <xref:System.Double> a <xref:System.Single> hodnoty, specifikace formátu "R" v některých případech se nepodaří úspěšně odezvy původní hodnotu a také nabízí relativně nízký výkon. Místo toho doporučujeme používat ["G17"](#GFormatString) formátovací řetězec pro <xref:System.Double> hodnoty a ["G9"](#GFormatString) specifikátor formátu pro úspěšně odezvy <xref:System.Single> hodnoty.

 Když <xref:System.Numerics.BigInteger> hodnota je formátován pomocí tohoto specifikátor, jeho řetězcovou reprezentaci obsahuje všechny platných číslic ve <xref:System.Numerics.BigInteger> hodnotu.  
  
 Ačkoli můžete použít také specifikátor přesnosti, bude ignorován. Pokud použijete tento specifikátor, má zpáteční převod přednost nad přesností.    
 Výsledný řetězec má vliv informace formátování aktuálního <xref:System.Globalization.NumberFormatInfo> objektu. Následující tabulka uvádí <xref:System.Globalization.NumberFormatInfo> vlastnosti, které řídí formátování řetězce výsledek.  
  
|Vlastnost NumberFormatInfo|Popis|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Definuje řetězec, který označuje, že číslo je záporné.|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Definuje řetězec, který odděluje integrální číslice od desítkových číslic.|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Definuje řetězec, který označuje, že exponent je kladný.|  
  
 Následující příklad formátuje <xref:System.Numerics.BigInteger> hodnotu s specifikátor odezvy formátu.  
  
 [!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
 [!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
 [!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]  
  
> [!IMPORTANT]
>  V některých případech <xref:System.Double> hodnoty formátu číselného formátu standardní řetězec "R" úspěšně odezvy nezadávejte Pokud zkompilovat pomocí `/platform:x64` nebo `/platform:anycpu` přepínače a spustit v 64bitových systémech. Viz odstavec Další informace.  
  
 Chcete-li vyřešit problém <xref:System.Double> hodnoty naformátovaný standardní číselného formátu "R" není úspěšně řetězci odezvy, pokud zkompilovat pomocí `/platform:x64` nebo `/platform:anycpu` přepínače a spustit v 64bitových systémech. můžete ho naformátovat <xref:System.Double> hodnoty pomocí řetězce "G17" standardní číselného formátu. Následující příklad používá řetězec formátu "R" s <xref:System.Double> tento není operace round-trip nemá hodnotu úspěšně, a také používá "G17" formátu řetězce na úspěšně odezvy původní hodnotu.  
  
 [!code-csharp[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#5)]
 [!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]  
  
 [Zpět k tabulce](#table)  
  
<a name="XFormatString"></a>   
## <a name="the-hexadecimal-x-format-specifier"></a>Specifikátor šestnáctkového formátu ("X")  
 Specifikátor šestnáctkového formátu ("X") převede číslo na řetězec šestnáctkových číslic. Velikost specifikátoru formátu označuje, zda pro šestnáctkové číslice, které jsou větší než 9, je nutné používat velká nebo malá písmena. Například pro vytvoření řetězce "ABCDEF" použijte formát "X", pro vytvoření řetězce "abcdef" použijte formát "x". Tento formát je podporován pouze pro integrální typy.  
  
 Specifikátor přesnosti označuje minimální počet číslic požadovaných ve výsledném řetězci. V případě potřeby je číslo doplněno nulami po levé straně za účelem vytvoření počtu číslic, který je dán specifikátorem přesnosti.  
  
 Výsledný řetězec není ovlivněn informace o aktuální formátování <xref:System.Globalization.NumberFormatInfo> objektu.  
  
 Následující příklad formátuje <xref:System.Int32> hodnoty s šestnáctkovým formátovací řetězec.  
  
 [!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
 [!code-csharp[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
 [!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]  
  
 [Zpět k tabulce](#table)  
  
<a name="NotesStandardFormatting"></a>   
## <a name="notes"></a>Poznámky  
  
### <a name="control-panel-settings"></a>Nastavení části Ovládací panely  
 Nastavení v **místní a jazykové nastavení** položky v Ovládacích panelech vliv výsledný řetězec vytvořený při operaci formátování. Tato nastavení slouží k chybě při inicializaci <xref:System.Globalization.NumberFormatInfo> objekt přidružený k aktuální jazykovou verzi vlákna, které poskytuje hodnoty použité k řízení formátování. Počítače, které používají různá nastavení, generují různé výsledné řetězce.  
  
 Kromě toho pokud <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> konstruktor se používá k vytvoření instance nového <xref:System.Globalization.CultureInfo> objekt, který reprezentuje stejnou jazykovou verzi jako aktuální systémovou kulturu jakékoli vlastní nastavení **místní a jazykové nastavení** na ovládacím panelu se použijí k novému <xref:System.Globalization.CultureInfo> objektu. Můžete použít <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktor k vytvoření <xref:System.Globalization.CultureInfo> objekt, který vlastní nastavení systému.  
  
### <a name="numberformatinfo-properties"></a>Vlastnosti objektu NumberFormatInfo  
 Formátování je ovlivněno vlastnosti aktuální <xref:System.Globalization.NumberFormatInfo> objekt, který je poskytnut implicitně aktuální jazykovou verzi vlákna nebo explicitně pomocí <xref:System.IFormatProvider> parametru metody, která vyvolá formátování. Zadejte <xref:System.Globalization.NumberFormatInfo> nebo <xref:System.Globalization.CultureInfo> objekt pro tento parametr.  
  
> [!NOTE]
>  Informace o přizpůsobení vzory nebo řetězce použité při formátování číselných hodnot najdete v tématu <xref:System.Globalization.NumberFormatInfo> třída tématu.  
  
### <a name="integral-and-floating-point-numeric-types"></a>Integrální typy čísel a typy s plovoucí desetinnou čárkou  
 Některé popisy specifikátorů standardního číselného formátu odkazují na integrální číselné typy nebo typy s plovoucí desetinnou čárkou. Integrální číselné typy jsou <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, a <xref:System.Numerics.BigInteger>. Číselné typy s plovoucí desetinnou čárkou jsou <xref:System.Decimal>, <xref:System.Single>, a <xref:System.Double>.  
  
### <a name="floating-point-infinities-and-nan"></a>Nekonečno s plovoucí desetinnou čárkou a NaN  
 Bez ohledu na řetězec formátu Pokud hodnota <xref:System.Single> nebo <xref:System.Double> s plovoucí desetinnou čárkou typ je kladné nekonečno, záporné nekonečno nebo nečíselné (NaN), formátovaný řetězec je hodnotou příslušné <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>, <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>, nebo <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> vlastnost, která je zadána aktuálně používán <xref:System.Globalization.NumberFormatInfo> objektu.  
  
<a name="example"></a>   
## <a name="example"></a>Příklad  
 Následující příklad formátuje číselnou integrální hodnotu a hodnotu s plovoucí desetinnou čárkou pomocí jazykové verze en-US a všech specifikátorů standardního číselného formátu. Tento příklad používá dva konkrétní číselnými typy (<xref:System.Double> a <xref:System.Int32>), ale by poskytují podobné výsledky pro některý z dalších číselných základních typů (<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Numerics.BigInteger>, <xref:System.Decimal>, a <xref:System.Single>).  
  
 [!code-csharp[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#1)]
 [!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Globalization.NumberFormatInfo>  
 [Vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)  
 [Postupy: Zarovnání čísla úvodními nulami](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)  
 [Ukázka: Rozhraní .NET Framework 4 formátování nástroj](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)  
 [Složené formátování](../../../docs/standard/base-types/composite-formatting.md)
