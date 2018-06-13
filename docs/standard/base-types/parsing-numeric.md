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
ms.openlocfilehash: 8e79c6cf8bfce4fa1ce37f7253e8583a67afe2f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576178"
---
# <a name="parsing-numeric-strings-in-net"></a>Analýza číselných řetězců v NET
Všechny číselné typy mají dvě statické metody analýzy `Parse` a `TryParse`, že můžete převést řetězcové vyjádření čísla do číselného typu. Tyto metody umožňují analyzovat řetězce, které byly vytvořeny pomocí řetězce formátu zdokumentována [standardní číselných řetězců formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md) a [vlastní řetězce číselného formátu](../../../docs/standard/base-types/custom-numeric-format-strings.md). Ve výchozím nastavení `Parse` a `TryParse` metody můžete převést úspěšně řetězce, které obsahují pouze na celé číslo hodnoty integrální desetinných míst. Úspěšně se můžete převést řetězce, které obsahují celých a desetinných desítková číslice, oddělovače skupin a oddělovač desetinných na hodnoty s plovoucí desetinnou čárkou. `Parse` Metoda vyvolá výjimku pokud operace selže, zatímco `TryParse` metoda vrátí `false`.  
  
## <a name="parsing-and-format-providers"></a>Poskytovatelé analýzy a formátu  
 Obvykle řetězec reprezentace číselné hodnoty se liší podle jazykové verze. Elementy oddělovačů číselných řetězců, jako je například Měna symboly, skupiny (nebo tisíců) a oddělovače desetinných míst všechny se liší podle jazykové verze. Analýza metody buď implicitně nebo explicitně pomocí zprostředkovatele formátu, který rozpoznává tyto odchylky specifické pro jazykovou verzi. Pokud je určen žádný zprostředkovatel formátu v volání `Parse` nebo `TryParse` metoda, formát zprostředkovatele spojeného s jazykové verze aktuálního vlákna ( <xref:System.Globalization.NumberFormatInfo> objekt vrácený <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> vlastnost) se používá.  
  
 Zprostředkovatel formátu je reprezentována <xref:System.IFormatProvider> implementace. Toto rozhraní má jednoho člena, <xref:System.IFormatProvider.GetFormat%2A> metoda, jejíž jeden parametr <xref:System.Type> objekt, který reprezentuje typ, který má být ve formátu. Tato metoda vrátí objekt, který poskytuje informace o formátování. Rozhraní .NET podporuje následující dva <xref:System.IFormatProvider> implementace pro Analýza číselných řetězců:  
  
-   A <xref:System.Globalization.CultureInfo> objekt, jehož <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrátí <xref:System.Globalization.NumberFormatInfo> objekt, který poskytuje informace o formátování specifické pro jazykovou verzi.  
  
-   A <xref:System.Globalization.NumberFormatInfo> objekt, jehož <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> metoda vrátí samu sebe.  
  
 V následujícím příkladu se snaží převést každý řetězec v poli <xref:System.Double> hodnotu. Nejprve se pokusí analyzovat řetězec pomocí zprostředkovatele formátu, který odráží konvencí jazykové verze Angličtina (Spojené státy). Pokud tato operace způsobí výjimku <xref:System.FormatException>, pokusí se analyzovat řetězec pomocí zprostředkovatele formátu, který odráží konvencí jazykové verze francouzština (Francie).  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Analýza a hodnoty NumberStyles  
 Jsou definované prvky stylu (například mezera, oddělovače skupin a oddělovač desetinných míst), které může zpracovat operaci analýzy <xref:System.Globalization.NumberStyles> hodnota výčtu. Ve výchozím nastavení jsou řetězců, které představují celočíselné hodnoty analyzovat pomocí <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> hodnotu, která umožňuje pouze číslice, úvodní a koncové mezery a počáteční přihlášení. Řetězců, které představují hodnoty s plovoucí desetinnou čárkou jsou analyzovat pomocí kombinace <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> a <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> hodnoty; tento složený styl povolí desetinných míst spolu s počátečních a koncových mezer na začátku přihlašovací, oddělovač desetinných míst, skupinu oddělovač a exponentem. Při volání přetížení `Parse` nebo `TryParse` metoda, která obsahuje parametr typu <xref:System.Globalization.NumberStyles> a nastavení jeden nebo více <xref:System.Globalization.NumberStyles> příznaky, můžete řídit prvky stylu, které můžou být v řetězci pro operace analýzy úspěšné.  
  
 Například řetězec, který obsahuje oddělovač skupiny nelze převést na <xref:System.Int32> hodnotu pomocí <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> metoda. Ale je převod úspěšný, pokud použijete <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> příznak, jak ukazuje následující příklad.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  Operace analýzy vždy používá formátování konvencí konkrétní jazykové verze. Pokud nezadáte jazykovou verzi předáním <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.NumberFormatInfo> objektu, se používá jazykovou verzi spojenou s aktuálním vláknem.  
  
 Následující tabulka uvádí členy <xref:System.Globalization.NumberStyles> výčtu a popisuje, o tom, že jsou na operaci analýzy.  
  
|Hodnota NumberStyles|Vliv na řetězec, který má být analyzován|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|Jsou povoleny pouze číslice.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|Oddělovač desetinných míst a míst za desetinnou čárkou jsou povoleny. Celé číslo hodnoty je povoleno pouze nula jako zlomkové číslice. Jsou určena platná oddělovače desetinných míst <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> vlastnost.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|"E" nebo "E" znak slouží k označení exponenciálním zápisu. V tématu <xref:System.Globalization.NumberStyles> Další informace.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|Je povolená počátečních prázdných znaků.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|Je povolené koncové prázdné znaky.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Kladné a záporné přihlašovací lze předcházet číslice.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Kladné a záporné přihlašovací můžete postupovat podle číslice.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Závorky lze použít k určení záporné hodnoty.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|Oddělovač skupin je povolená. Je dáno oddělovací znak. skupiny <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> vlastnost.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|Je povolená symbolu měny. Symbolu měny je definována <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> vlastnost.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|Řetězec, který má být analyzován interpretována jako o hexadecimální číslo. Může obsahovat šestnáctkové číslice 0 – 9, A-F a a-f. Tento příznak slouží pouze k analyzovat celočíselné hodnoty.|  
  
 Kromě toho <xref:System.Globalization.NumberStyles> výčet obsahuje následující složené stylů, mezi které patří několika <xref:System.Globalization.NumberStyles> příznaky.  
  
|Hodnota kompozitního NumberStyles|Obsahuje členy|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|Zahrnuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, a <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> styly. Toto je výchozí styl použitá k analýze celočíselné hodnoty.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|Zahrnuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, a <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> styly.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|Zahrnuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, a <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> styly.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Zahrnuje všechny styly s výjimkou <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> a <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Zahrnuje všechny styly s výjimkou <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|Zahrnuje <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, a <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> styly.|  
  
## <a name="parsing-and-unicode-digits"></a>Analýza a číslice v kódování Unicode  
 Standardu Unicode definuje body kódu pro číslic v různých systémech zápis. Například body kódu z U + 0030 pro U + 0039 představují základní Latinské číslice 0 až 9, body kódu z U + 09E6 k U + 09EF představují bengálském číslice 0 až 9 a body kódu z U + FF10 k U + FF19 představují tučné číslice 0 až 9. Základní Latinské číslice 0 – 9 s body kódu z U + 0030 při U + 0039 jsou však pouze číselné číslic rozpoznána analýzou metody. Pokud jednu číslici analýza metoda je předán řetězec, který obsahuje jiné číslic, vyvolá metoda <xref:System.FormatException>.  
  
 Následující příklad používá <xref:System.Int32.Parse%2A?displayProperty=nameWithType> metoda analyzovat řetězce, které se skládají z číslic v různých systémů zápisu. Jak ukazuje výstup z příkladu pokusu o analýzu základní Latinské číslic úspěšné, ale pokus o analyzovat plnou šířkou, Arabská a bengálském číslic selže.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Globalization.NumberStyles>  
 [Analýza řetězců](../../../docs/standard/base-types/parsing-strings.md)  
 [Typy formátování](../../../docs/standard/base-types/formatting-types.md)
