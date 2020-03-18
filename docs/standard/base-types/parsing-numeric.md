---
title: Analýza číselných řetězců v rozhraní .NET
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
ms.openlocfilehash: ac44282a06b2b3710d3a9e5390c7a514c1632c3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127604"
---
# <a name="parsing-numeric-strings-in-net"></a>Analýza číselných řetězců v síti
Všechny číselné typy mají dvě `Parse` metody `TryParse`statické analýzy a , které můžete použít k převodu řetězcové reprezentace čísla na číselný typ. Tyto metody umožňují analyzovat řetězce, které byly vytvořeny pomocí formátovacích řetězců zdokumentovaných ve [standardních číselných formátovacích řetězcích](../../../docs/standard/base-types/standard-numeric-format-strings.md) a [vlastních číselných formátovacích řetězcích](../../../docs/standard/base-types/custom-numeric-format-strings.md). Ve výchozím `Parse` nastavení `TryParse` mohou metody a úspěšně převést řetězce, které obsahují integrální desetinné číslice pouze na celé hodnoty. Mohou úspěšně převést řetězce, které obsahují integrální a zlomkové desetinné číslice, oddělovače skupin a oddělovač desetinných míst na hodnoty s plovoucí desetinnou čárkou. Metoda `Parse` vyvolá výjimku, pokud se operace `TryParse` nezdaří, vzhledem k tomu, že metoda vrátí `false`.  
  
## <a name="parsing-and-format-providers"></a>Poskytovatelé analýzy a formátu  
 Řetězcové reprezentace číselných hodnot se obvykle liší podle jazykové verze. Prvky číselných řetězců, jako jsou symboly měny, oddělovače skupin (nebo tisíce) a oddělovače desetinných míst, se liší podle jazykové verze. Analýza metody implicitně nebo explicitně použít zprostředkovatele formátu, který rozpozná tyto varianty specifické pro jazykovou verzi. Pokud žádný zprostředkovatel formátu je zadán `Parse` `TryParse` v volání metody nebo, je použit <xref:System.Globalization.NumberFormatInfo> zprostředkovatel formátu <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> přidružené k aktuální jazykovou verzi podprocesu (objekt vrácený vlastností).  
  
 Zprostředkovatel formátu je reprezentován implementací. <xref:System.IFormatProvider> Toto rozhraní má jeden <xref:System.IFormatProvider.GetFormat%2A> člen, metodu, <xref:System.Type> jejíž jediný parametr je objekt, který představuje typ, který má být formátován. Tato metoda vrátí objekt, který poskytuje informace o formátování. Rozhraní .NET podporuje <xref:System.IFormatProvider> následující dvě implementace pro analýzu číselných řetězců:  
  
- Objekt, <xref:System.Globalization.CultureInfo> <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> jehož <xref:System.Globalization.NumberFormatInfo> metoda vrátí objekt, který poskytuje informace o formátování specifické pro jazykovou verzi.  
  
- Objekt, <xref:System.Globalization.NumberFormatInfo> <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> jehož metoda vrátí sám.  
  
 Následující příklad se pokusí převést každý <xref:System.Double> řetězec v poli na hodnotu. Nejprve se pokusí analyzovat řetězec pomocí zprostředkovatele formátu, který odráží konvence jazykové verze angličtiny (Spojené státy). Pokud tato operace <xref:System.FormatException>vyvolá , pokusí se analyzovat řetězec pomocí zprostředkovatele formátu, který odráží konvence francouzské (Francie) jazykové verze.  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Analýza a hodnoty NumberStyles  
 Prvky stylu (například prázdné místo, oddělovače skupin a oddělovač desetinných míst), které může operace analýzy zpracovat, jsou definovány hodnotou výčtu. <xref:System.Globalization.NumberStyles> Ve výchozím nastavení jsou řetězce, které představují celé hodnoty, analyzovány pomocí <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> hodnoty, která povoluje pouze číselné číslice, úvodní a koncové prázdné znaky a úvodní znaménko. Řetězce, které představují hodnoty s plovoucí desetinnou <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> desetinnou tágo, jsou analyzovány pomocí kombinace hodnot a; <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> tento složený styl umožňuje desetinné číslice spolu s úvodnía koncové prázdné místo, úvodní znaménko, oddělovač desetinných míst, oddělovač skupiny a exponent. Voláním přetížení `Parse` nebo `TryParse` metoda, která obsahuje <xref:System.Globalization.NumberStyles> parametr typu a <xref:System.Globalization.NumberStyles> nastavení jednoho nebo více příznaků, můžete řídit prvky stylu, které mohou být přítomny v řetězci pro operaci analýzy úspěšné.  
  
 Například řetězec, který obsahuje oddělovač skupiny <xref:System.Int32> nelze převést <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> na hodnotu pomocí metody. Převod je však úspěšný, <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> pokud použijete příznak, jak ukazuje následující příklad.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
> Operace analýzy vždy používá konvencí formátování určité jazykové verze. Pokud nezadáte jazykovou verzi <xref:System.Globalization.CultureInfo> předáním nebo <xref:System.Globalization.NumberFormatInfo> objektu, bude použita jazyková verze přidružená k aktuálnímu vláknu.  
  
 V následující tabulce jsou <xref:System.Globalization.NumberStyles> uvedeny členy výčtu a popisuje vliv, který mají na operaci analýzy.  
  
|Hodnota NumberStyles|Vliv na řetězec, který má být analyzován|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Jsou povoleny pouze číselné číslice.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Oddělovač desetinných míst a zlomkové číslice jsou povoleny. Pro celé hodnoty je jako zlomková číslice povolena pouze nula. Platné oddělovače desetinných <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> míst <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> jsou určeny vlastností nebo.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|Znak "e" nebo "E" lze použít k označení exponenciálního zápisu. Viz <xref:System.Globalization.NumberStyles> další informace.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Úvodní prázdné místo je povoleno.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Koncové prázdné místo je povoleno.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Číslice mohou předcházet kladné nebo záporné znaménko.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Kladné nebo záporné znaménko může následovat číselné číslice.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Závorky lze použít k označení záporných hodnot.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Oddělovač skupiny je povolen. Znak oddělovače skupiny <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> je určen vlastností nebo.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Symbol měny je povolen. Symbol měny je definován <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> vlastností.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Řetězec, který má být analyzován, je interpretován jako šestnáctkové číslo. Může obsahovat šestnáctkové číslice 0-9, A-F a a-f. Tento příznak lze použít pouze k analýzě celých hodnot.|  
  
 <xref:System.Globalization.NumberStyles> Výčet navíc poskytuje následující složené styly, které <xref:System.Globalization.NumberStyles> obsahují více příznaků.  
  
|Hodnota Složených stylů čísel|Zahrnuje členy|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|Zahrnuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>styly <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> , a styly. Toto je výchozí styl používaný k analýzě celých hodnot.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|Zahrnuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>styly <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> , , a.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|Zahrnuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>styly <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> , , a.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Zahrnuje všechny <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> styly kromě a <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Zahrnuje všechny <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>styly kromě .|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|Zahrnuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>styly <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> , a styly.|  
  
## <a name="parsing-and-unicode-digits"></a>Analýza a číslice v kódování Unicode  
 Standard Unicode definuje body kódu pro číslice v různých systémech zápisu. Například body kódu od U + 0030 do U + 0039 představují základní latinka číslice 0 až 9, kódové body od U + 09E6 do U + 09EF představují bangla číslice 0 až 9 a body kódu od U + FF10 do U + FF19 představují číslice Fullwidth 0 až 9. Jediné číselné číslice rozpoznané metodami analýzy jsou však základní číslice latinky 0-9 s body kódu od U + 0030 do U + 0039. Pokud je numerická analýza metoda předána řetězec, který obsahuje všechny <xref:System.FormatException>ostatní číslice, metoda vyvolá .  
  
 Následující příklad používá <xref:System.Int32.Parse%2A?displayProperty=nameWithType> metodu k analýzě řetězců, které se skládají z číslic v různých systémech zápisu. Jak ukazuje výstup z příkladu, pokus o analýzu základních číslic latinky proběhne úspěšně, ale pokus o analýzu číslic Fullwidth, Arabic-Indic a Bangla se nezdaří.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Globalization.NumberStyles>
- [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
