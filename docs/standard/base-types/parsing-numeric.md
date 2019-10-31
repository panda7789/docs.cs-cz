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
ms.openlocfilehash: ac44282a06b2b3710d3a9e5390c7a514c1632c3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127604"
---
# <a name="parsing-numeric-strings-in-net"></a>Analýza číselných řetězců v síti NET
Všechny číselné typy mají dvě statické metody analýzy, `Parse` a `TryParse`, které lze použít k převedení řetězcové reprezentace čísla na číselný typ. Tyto metody umožňují analyzovat řetězce, které byly vytvořeny pomocí řetězců formátu v hodnotách [standardního číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md) a řetězců [vlastního číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md). Ve výchozím nastavení metody `Parse` a `TryParse` mohou úspěšně převést řetězce, které obsahují celočíselné desítkové číslice pouze na celočíselné hodnoty. Můžou úspěšně převést řetězce, které obsahují celočíselné a zlomkové číslice, oddělovače skupin a oddělovač desetinných míst na hodnoty s plovoucí desetinnou čárkou. Metoda `Parse` vyvolá výjimku, pokud se operace nezdařila, zatímco metoda `TryParse` vrátí `false`.  
  
## <a name="parsing-and-format-providers"></a>Poskytovatelé analýzy a formátu  
 Obvykle se řetězcové reprezentace číselných hodnot liší podle jazykové verze. Prvky číselných řetězců, jako jsou symboly měn, oddělovače skupin (nebo tisíců) a oddělovač desetinných míst, se liší podle jazykové verze. Metody analýzy implicitně nebo explicitně používají poskytovatele formátu, který tyto variace specifické pro jazykovou verzi rozpoznává. Pokud není zadán žádný poskytovatel formátu ve volání metody `Parse` nebo `TryParse`, je použit poskytovatel formátu přidružený k aktuální jazykové verzi vlákna (objekt <xref:System.Globalization.NumberFormatInfo> vrácený vlastností <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType>).  
  
 Poskytovatel formátu je reprezentován implementací <xref:System.IFormatProvider>. Toto rozhraní má jednoho člena, metodu <xref:System.IFormatProvider.GetFormat%2A>, jejíž jeden parametr je <xref:System.Type> objekt, který představuje typ, který má být formátován. Tato metoda vrátí objekt, který poskytuje informace o formátování. Rozhraní .NET podporuje následující dvě implementace <xref:System.IFormatProvider> pro analýzu číselných řetězců:  
  
- Objekt <xref:System.Globalization.CultureInfo>, jehož metoda <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> vrací objekt <xref:System.Globalization.NumberFormatInfo>, který poskytuje informace o formátování specifické pro jazykovou verzi.  
  
- Objekt <xref:System.Globalization.NumberFormatInfo>, jehož metoda <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> vrací sebe sama.  
  
 Následující příklad se pokusí převést každý řetězec v poli na hodnotu <xref:System.Double>. Nejprve se pokusí analyzovat řetězec pomocí poskytovatele formátu, který odráží konvenci jazykové verze English (USA). Pokud tato operace vyvolá <xref:System.FormatException>, pokusí se analyzovat řetězec pomocí poskytovatele formátu, který odráží konvence francouzské jazykové verze (Francie).  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Analýza a hodnoty NumberStyles  
 Prvky stylu (například prázdné znaky, oddělovače skupin a oddělovač desetinných míst), které může operace analýzy zpracovat, jsou definovány hodnotou <xref:System.Globalization.NumberStyles> výčtu. Ve výchozím nastavení jsou řetězce, které představují celočíselné hodnoty, analyzovány pomocí <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> hodnoty, která povoluje pouze číslice, úvodní a koncové prázdné znaky a úvodní znaménko. Řetězce, které představují hodnoty s plovoucí desetinnou čárkou, jsou analyzovány pomocí kombinace <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> a <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>ch hodnot; Tento složený styl povoluje desítkové číslice spolu s úvodním a koncovým prázdným znakem, počáteční znaménko, oddělovač desetinných míst, oddělovač skupin a exponent. Voláním přetížení metody `Parse` nebo `TryParse`, která obsahuje parametr typu <xref:System.Globalization.NumberStyles> a nastavením jednoho nebo více příznaků <xref:System.Globalization.NumberStyles>, lze ovládat prvky stylu, které mohou být přítomny v řetězci pro úspěšné provedení operace analýzy.  
  
 Například řetězec, který obsahuje oddělovač skupiny, nelze převést na hodnotu <xref:System.Int32> pomocí metody <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType>. Převod je však úspěšný při použití příznaku <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>, jak ukazuje následující příklad.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
> Operace analýzy vždy používá konvence formátování konkrétní jazykové verze. Pokud nezadáte jazykovou verzi předáním <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.NumberFormatInfo> objektu, je použita jazyková verze přidružená k aktuálnímu vláknu.  
  
 Následující tabulka uvádí členy výčtu <xref:System.Globalization.NumberStyles> a popisuje účinek, který mají na operaci analýzy.  
  
|Hodnota NumberStyles|Vliv na řetězec, který se má analyzovat|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Jsou povoleny pouze číslice.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Oddělovač desetinných míst a číslice zlomků jsou povoleny. U celočíselných hodnot je jako zlomková číslice povolena pouze nula. Platné oddělovače desetinných míst jsou určeny vlastností <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|Znak "e" nebo "E" lze použít k označení exponenciálního zápisu. Další informace najdete v tématu <xref:System.Globalization.NumberStyles>.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Je povoleno počáteční prázdné místo.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Koncová mezera je povolena.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Kladné nebo záporné znaménko může předcházet číslicemi.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Kladné nebo záporné znaménko může následovat po číslicích.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Závorky lze použít k označení záporných hodnot.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Oddělovač skupin je povolený. Znak oddělovače skupiny je určený vlastností <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Symbol měny je povolený. Symbol měny je definován vlastností <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Řetězec, který má být analyzován, je interpretován jako šestnáctkové číslo. Může zahrnovat hexadecimální číslice 0-9, A-F a a-F. Tento příznak lze použít pouze k analýze celočíselných hodnot.|  
  
 Kromě toho výčet <xref:System.Globalization.NumberStyles> poskytuje následující složené styly, které obsahují více příznaků <xref:System.Globalization.NumberStyles>.  
  
|Složená hodnota NumberStyles|Obsahuje členy|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|Obsahuje styly <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>a <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>. Toto je výchozí styl použitý k analýze celočíselných hodnot.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|Zahrnuje styly <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>a <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|Zahrnuje styly <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>a <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Zahrnuje všechny styly kromě <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> a <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Zahrnuje všechny styly kromě <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|Obsahuje styly <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>a <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
  
## <a name="parsing-and-unicode-digits"></a>Analýza a číslice v kódování Unicode  
 Standard Unicode definuje body kódu pro číslice v různých systémech pro psaní. Například body kódu z U + 0030 na U + 0039 reprezentují základní číslice od 0 do 9, body kódu z + 09E6 do U + 09EF reprezentují hodnoty bengálština 0 až 9 a body kódu z U + FF10 do U + FF19 reprezentují tučná čísla 0 až 9. Jedinými číselnými číslicemi, které byly rozpoznány metodou analýzy, jsou však základní číslice latinky 0-9 a body kódu z U + 0030 až U + 0039. Pokud je metoda číselné analýzy předána řetězcem, který obsahuje jakékoli jiné číslice, vyvolá metoda <xref:System.FormatException>.  
  
 Následující příklad používá metodu <xref:System.Int32.Parse%2A?displayProperty=nameWithType> k analýze řetězců, které se skládají z číslic v různých systémech pro zápis. Jak ukazuje výstup z příkladu, pokus o analýzu základních číslic latinky je úspěšný, ale pokus o analýzu tučné, arabského a desítkové číslice selže.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.NumberStyles>
- [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
