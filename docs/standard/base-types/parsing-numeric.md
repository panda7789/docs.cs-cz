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
ms.openlocfilehash: 8903d0443594885b3b0e8cca716eda8177c60cca
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988800"
---
# <a name="parsing-numeric-strings-in-net"></a>Analýza číselných řetězců v síti NET
Všechny číselné typy mají dvě statické metody `Parse` analýzy a `TryParse`, které lze použít k převedení řetězcové reprezentace čísla na číselný typ. Tyto metody umožňují analyzovat řetězce, které byly vytvořeny pomocí řetězců formátu v hodnotách [standardního číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md) a řetězců [vlastního číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md). Ve výchozím nastavení `Parse` metody a `TryParse` mohou úspěšně převést řetězce, které obsahují celočíselné desítkové číslice pouze na celočíselné hodnoty. Můžou úspěšně převést řetězce, které obsahují celočíselné a zlomkové číslice, oddělovače skupin a oddělovač desetinných míst na hodnoty s plovoucí desetinnou čárkou. Metoda vyvolá výjimku, pokud se operace nezdařila, `TryParse` zatímco metoda vrátí `false`. `Parse`  
  
## <a name="parsing-and-format-providers"></a>Poskytovatelé analýzy a formátu  
 Obvykle se řetězcové reprezentace číselných hodnot liší podle jazykové verze. Prvky číselných řetězců, jako jsou symboly měn, oddělovače skupin (nebo tisíců) a oddělovač desetinných míst, se liší podle jazykové verze. Metody analýzy implicitně nebo explicitně používají poskytovatele formátu, který tyto variace specifické pro jazykovou verzi rozpoznává. Pokud není zadán žádný poskytovatel `Parse` formátu ve volání metody nebo `TryParse` , je použit poskytovatel formátu přidružený k <xref:System.Globalization.NumberFormatInfo> aktuální jazykové verzi vlákna (objekt vrácený <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> vlastností).  
  
 Zprostředkovatel formátu je reprezentován <xref:System.IFormatProvider> implementací. Toto rozhraní má jednoho člena, <xref:System.IFormatProvider.GetFormat%2A> metodu, jejíž jeden parametr <xref:System.Type> je objekt, který představuje typ, který má být formátován. Tato metoda vrátí objekt, který poskytuje informace o formátování. Rozhraní .NET podporuje následující dvě <xref:System.IFormatProvider> implementace pro analýzu číselných řetězců:  
  
- Objekt, jehož <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrací <xref:System.Globalization.NumberFormatInfo> objekt, který poskytuje informace o formátování specifické pro jazykovou verzi. <xref:System.Globalization.CultureInfo>  
  
- Objekt, jehož <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrací sám sebe. <xref:System.Globalization.NumberFormatInfo>  
  
 Následující příklad se pokusí převést každý řetězec v poli na <xref:System.Double> hodnotu. Nejprve se pokusí analyzovat řetězec pomocí poskytovatele formátu, který odráží konvenci jazykové verze English (USA). Pokud tato operace vyvolá výjimku <xref:System.FormatException>, pokusí se analyzovat řetězec pomocí poskytovatele formátu, který odráží konvence francouzské jazykové verze (Francie).  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Analýza a hodnoty NumberStyles  
 Prvky stylu (například prázdné znaky, oddělovače skupin a oddělovač desetinných míst), které může operace analýzy zpracovat, jsou definovány <xref:System.Globalization.NumberStyles> hodnotou výčtu. Ve výchozím nastavení jsou řetězce, které představují celočíselné hodnoty, analyzovány <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> pomocí hodnoty, která povoluje pouze číselné číslice, úvodní a koncové prázdné znaky a úvodní znaménko. Řetězce, které představují hodnoty s plovoucí desetinnou čárkou, jsou analyzovány <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> pomocí <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> kombinace hodnot a. Tento složený styl povoluje desítkové číslice spolu s úvodním a koncovým prázdným znakem, úvodní znaménko, oddělovač desetinných míst, skupina oddělovač a exponent. Voláním přetížení `Parse` metody nebo `TryParse` , která obsahuje parametr typu <xref:System.Globalization.NumberStyles> a nastavením jednoho nebo více <xref:System.Globalization.NumberStyles> příznaků, lze řídit prvky stylu, které mohou být přítomny v řetězci pro operaci analýzy na provedena.  
  
 Například řetězec, který obsahuje oddělovač skupiny, nelze převést na <xref:System.Int32> hodnotu <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> pomocí metody. Převod je však úspěšný při použití <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> příznaku, jak ukazuje následující příklad.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
> Operace analýzy vždy používá konvence formátování konkrétní jazykové verze. Pokud nezadáte jazykovou verzi předáním <xref:System.Globalization.CultureInfo> objektu nebo <xref:System.Globalization.NumberFormatInfo> , je použita jazyková verze přidružená k aktuálnímu vláknu.  
  
 Následující tabulka uvádí členy <xref:System.Globalization.NumberStyles> výčtu a popisuje účinek, který mají na operaci analýzy.  
  
|Hodnota NumberStyles|Vliv na řetězec, který se má analyzovat|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Jsou povoleny pouze číslice.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Oddělovač desetinných míst a číslice zlomků jsou povoleny. U celočíselných hodnot je jako zlomková číslice povolena pouze nula. Platné oddělovače desetinných míst jsou určeny <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> vlastností <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> or.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|Znak "e" nebo "E" lze použít k označení exponenciálního zápisu. Další <xref:System.Globalization.NumberStyles> informace najdete v tématu.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Je povoleno počáteční prázdné místo.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Koncová mezera je povolena.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Kladné nebo záporné znaménko může předcházet číslicemi.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Kladné nebo záporné znaménko může následovat po číslicích.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Závorky lze použít k označení záporných hodnot.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Oddělovač skupin je povolený. Znak oddělovače skupiny je určen <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> vlastností or. <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType>|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Symbol měny je povolený. Symbol měny je definován <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> vlastností.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Řetězec, který má být analyzován, je interpretován jako šestnáctkové číslo. Může zahrnovat hexadecimální číslice 0-9, A-F a a-F. Tento příznak lze použít pouze k analýze celočíselných hodnot.|  
  
 Kromě toho <xref:System.Globalization.NumberStyles> výčet poskytuje následující složené styly, které obsahují více <xref:System.Globalization.NumberStyles> příznaků.  
  
|Složená hodnota NumberStyles|Obsahuje členy|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|Obsahuje styly <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>a <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> . Toto je výchozí styl použitý k analýze celočíselných hodnot.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> Obsahujestyly<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, ,,<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> , a. <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType> Obsahujestyly<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, ,,<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> a. <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType> <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Zahrnuje všechny styly kromě <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> a <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Zahrnuje všechny styly s <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>výjimkou.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|Obsahuje styly <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>a <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> .|  
  
## <a name="parsing-and-unicode-digits"></a>Analýza a číslice v kódování Unicode  
 Standard Unicode definuje body kódu pro číslice v různých systémech pro psaní. Například body kódu z U + 0030 na U + 0039 reprezentují základní číslice od 0 do 9, body kódu z + 09E6 do U + 09EF reprezentují hodnoty bengálština 0 až 9 a body kódu z U + FF10 do U + FF19 reprezentují tučná čísla 0 až 9. Jedinými číselnými číslicemi, které byly rozpoznány metodou analýzy, jsou však základní číslice latinky 0-9 a body kódu z U + 0030 až U + 0039. Pokud je metoda číselné analýzy předána řetězcem, který obsahuje jakékoli jiné číslice, vyvolá <xref:System.FormatException>metoda.  
  
 Následující příklad používá <xref:System.Int32.Parse%2A?displayProperty=nameWithType> metodu k analýze řetězců, které se skládají z číslic v různých systémech pro zápis. Jak ukazuje výstup z příkladu, pokus o analýzu základních číslic latinky je úspěšný, ale pokus o analýzu tučné, arabského a desítkové číslice selže.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.NumberStyles>
- [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)
- [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
