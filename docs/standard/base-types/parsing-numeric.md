---
title: Analýza číselných řetězců v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parsing strings, numeric strings
- numeric strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
ms.assetid: e39324ee-72e5-42d4-a80d-bf3ee7fc6c59
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ba1ded1757d71a2b7839ae8b45489da53763b8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603609"
---
# <a name="parsing-numeric-strings-in-net"></a>Analýza číselných řetězců v síti
Všechny číselné typy mají dvě metody statické analýzy `Parse` a `TryParse`, že vám pomůže převést řetězcové vyjádření čísla na číselného typu. Tyto metody umožňují Analýza řetězců, které byly vytvořeny pomocí formátovacích řetězců dokumentovány v článku [Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md) a [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md). Ve výchozím nastavení `Parse` a `TryParse` metody můžete převést úspěšně řetězce, které obsahují integrální desítkových číslic pouze pro celočíselné hodnoty. Můžete úspěšně převodu řetězce, které obsahují celých a desetinných desítkové číslice, oddělovače skupin a oddělovač desetinných míst pro hodnoty s plovoucí desetinnou čárkou. `Parse` Metoda vyvolá výjimku, pokud se operace nezdaří, zatímco `TryParse` vrátí metoda `false`.  
  
## <a name="parsing-and-format-providers"></a>Poskytovatelé analýzy a formátu  
 Řetězcové reprezentace číselných hodnot se obvykle liší podle jazykové verze. Prvky oddělovače číselných řetězců jako měnu symboly, skupiny (nebo tisíc) a oddělovače desetinných míst všechny se liší podle jazykové verze. Analýza kódu metody implicitně nebo explicitně použijte poskytovatele formátu, který rozpoznává tyto odchylky specifické pro jazykovou verzi. Pokud je zadán žádný zprostředkovatel formátu ve volání `Parse` nebo `TryParse` metody, poskytovatele formátu přidruženého k aktuální jazykové verzi vlákna ( <xref:System.Globalization.NumberFormatInfo> objekt vrácený <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> vlastnost) se používá.  
  
 Poskytovatele formátu počítaném od <xref:System.IFormatProvider> implementace. Toto rozhraní má jediný člen <xref:System.IFormatProvider.GetFormat%2A> metoda, jejíž jediný parametr je <xref:System.Type> objekt, který představuje typ, který má být formátován. Tato metoda vrátí objekt, který poskytuje informace o formátování. .NET podporuje následující dva <xref:System.IFormatProvider> implementace pro Analýza číselných řetězců:  
  
-   A <xref:System.Globalization.CultureInfo> jehož <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrátí hodnotu <xref:System.Globalization.NumberFormatInfo> objekt, který poskytuje informace o formátování specifické pro jazykovou verzi.  
  
-   A <xref:System.Globalization.NumberFormatInfo> jehož <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrací samu sebe.  
  
 Následující příklad se snaží převést každý řetězec v matici <xref:System.Double> hodnotu. Nejprve se pokusí analyzovat řetězec pomocí poskytovatele formátu, který odráží úmluv jazykové verze Angličtina (Spojené státy). Pokud tato operace vyvolá <xref:System.FormatException>, pokusí se analyzovat řetězec pomocí poskytovatele formátu, který odráží konvence jazykovou verzi francouzština (Francie).  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Analýza a hodnoty NumberStyles  
 Prvky stylu (například mezeru, oddělovače skupin a oddělovač desetinných míst), které dokáže zpracovat operace analýzy jsou definovány <xref:System.Globalization.NumberStyles> hodnota výčtu. Ve výchozím nastavení, jsou analyzovány řetězců, které představují celočíselných hodnot s použitím <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> hodnotu, která povoluje jen číselné znaky, úvodní a koncové prázdné znaky a počátečním znaménkem. Řetězce, které představují hodnoty s plovoucí desetinnou čárkou jsou analyzovány pomocí kombinace <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> a <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> hodnoty; tento složený styl povolení desítkových číslic spolu s úvodní a koncové prázdné znaky, úvodní znaménko, oddělovač desetinných míst, skupinu oddělovač a exponent. Voláním přetížení `Parse` nebo `TryParse` metoda, která zahrnuje parametr typu <xref:System.Globalization.NumberStyles> a nastavení jeden nebo více <xref:System.Globalization.NumberStyles> příznaky, můžete řídit prvky stylu, které může být k dispozici v řetězci pro operace analýzy úspěšné.  
  
 Například řetězec obsahující oddělovač skupin nelze převést na <xref:System.Int32> hodnotu s použitím <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> metody. Ale, že převod je úspěšný používáte <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> příznak, jak ukazuje následující příklad.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  Operace analýzy vždy používá konvence formátování konkrétní jazykové verze. Pokud nezadáte předáním jazykovou verzi <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.NumberFormatInfo> objektu se používá jazykové verze přidružené k aktuální vlákno.  
  
 V následující tabulce jsou uvedeny jako objekty její členové <xref:System.Globalization.NumberStyles> výčet a popisuje vliv na operace analýzy.  
  
|Hodnota NumberStyles|Vliv na řetězec, který má být analyzován|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Jsou povoleny pouze číslice.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Oddělovač desetinných míst a zlomkových číslic, které jsou povoleny. Pro celočíselné hodnoty smí obsahovat pouze nula jako zlomková číslice. Jsou určeny platné oddělovače desetinných míst <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> vlastnost.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|"E" nebo znak "E" lze použít k označení exponenciální notaci. Zobrazit <xref:System.Globalization.NumberStyles> pro další informace.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Smí obsahovat úvodní mezery.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Smí obsahovat koncové prázdné znaky.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Kladného či záporného znaménka lze před číslicemi.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Kladného či záporného znaménka můžete postupovat podle číselné znaky.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Závorky lze použít k označení záporné hodnoty.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Oddělovač skupin je povolený. Znak oddělovače skupin závisí <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> vlastnost.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Smí obsahovat symbol měny. Je definován symbol měny <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> vlastnost.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Řetězec, který má být analyzován, je interpretován jako šestnáctkové číslo. Může obsahovat šestnáctkové číslice 0-9, A-F a a-f. Tento příznak slouží pouze k parsování hodnot typu integer.|  
  
 Kromě toho <xref:System.Globalization.NumberStyles> výčet obsahuje následující složené styly, mezi které patří několika <xref:System.Globalization.NumberStyles> příznaky.  
  
|Složené hodnoty NumberStyles|Obsahuje členy|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|Zahrnuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, a <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> styly. Toto je výchozí styl použitá k analýze celočíselné hodnoty.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|Zahrnuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, a <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> styly.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|Zahrnuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, a <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> styly.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Zahrnuje všechny styly, s výjimkou <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> a <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Zahrnuje všechny styly, s výjimkou <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|Zahrnuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, a <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> styly.|  
  
## <a name="parsing-and-unicode-digits"></a>Analýza a číslice v kódování Unicode  
 Unicode standard definuje kódových bodů číslice v různých písmové systémy. Například body kódu z U + 0030 U + 0039 představují základní latinky číslice 0 – 9, body kódu z U + 09E6 U + 09EF představují Bengálština číslice 0 – 9 a body kódu z U + FF10 U + FF19 představují tučné číslice 0 až 9. Základní latinky číslice 0 – 9 s body kódu z U + 0030 U + 0039 jsou však pouze číselné znaky, které jsou rozpoznány analýzou metody. Pokud číselnou při analýze metody je předán řetězec, který obsahuje všechny číslice, vyvolá metoda výjimku <xref:System.FormatException>.  
  
 V následujícím příkladu <xref:System.Int32.Parse%2A?displayProperty=nameWithType> metody k analýze řetězce, které se skládají z číslic v různých písmové systémy. Jak výstup z příkladu ukazuje, pokus o analýzu základní latinky číslic úspěšné, ale pokus analyzovat tučné, Arabská a Bengálština číslic selže.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.NumberStyles>
- [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
