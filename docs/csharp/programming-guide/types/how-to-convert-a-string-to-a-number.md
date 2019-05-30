---
title: 'Postupy: Převod řetězce na číslo - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 25f6fb5e8780611a6ca7396873d0a33684b65a48
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301373"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Postupy: Převod řetězce na číslo (C# Průvodce programováním v)

Můžete převést [řetězec](../../../csharp/language-reference/keywords/string.md) číslo při volání `Parse` nebo `TryParse` nalézt metodu pro různé číselné typy (`int`, `long`, `double`atd), nebo pomocí metody <xref:System.Convert?displayProperty=nameWithType>třídy.  
  
 Pokud máte řetězec, je o něco víc efektivní a jednoduchý volání `TryParse` – metoda (například [ `int.TryParse("11", out number)` ](xref:System.Int32.TryParse%2A)) nebo `Parse` – metoda (například [ `var number = int.Parse("11")` ](xref:System.Int32.Parse%2A)).  Použití <xref:System.Convert> metoda je užitečná více pro hlavní objekty, které implementují <xref:System.IConvertible>.  
  
 Můžete použít `Parse` nebo `TryParse` metody na číselný typ očekáváte, že řetězec obsahuje, jako <xref:System.Int32?displayProperty=nameWithType> typu.  <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> Používá metoda <xref:System.Int32.Parse%2A> interně.  `Parse` Metoda vrací převedený číslo; `TryParse` metoda vrátí hodnotu <xref:System.Boolean> hodnotu, která určuje, zda převod bylo úspěšné a vrátí převedený číslo v [ `out` parametr](../../../csharp/language-reference/keywords/out.md). Pokud řetězec není v platném formátu `Parse` vyvolá výjimku, zatímco `TryParse` vrátí [false](../../../csharp/language-reference/keywords/false-literal.md). Při volání metody `Parse` metoda, byste měli vždy používat zpracování výjimek pro zachycení <xref:System.FormatException> v případě, že operace analýzy nezdaří.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Volání metody analýzy a TryParse

`Parse` a `TryParse` metody ignorování prázdných znaků na začátku a na konci řetězce, ale všechny ostatní znaky musí být znaky, které tvoří příslušného číselného typu (`int`, `long`, `ulong`, `float`, `decimal`atd.).  Všechny prázdné znaky v řetězci, který tvoří číslo způsobí chybu.  Například můžete použít `decimal.TryParse` analyzovat "10", "10.3," nebo "10", ale tuto metodu nelze použít k analýze 10 z "10 X", "1 0" (Všimněte si vložené místo), "10. 3" (Všimněte si vložené místo), "10e1" (`float.TryParse` Tady můžete použít), a tak dále. Kromě toho, jehož hodnota je řetězec `null` nebo <xref:System.String.Empty?displayProperty=nameWithType> nejde úspěšně analyzovat. Můžete zkontrolovat hodnotu null nebo prázdný řetězec před pokusem o parsování voláním <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody. 

Následující příklad ukazuje úspěšné i neúspěšné volání `Parse` a `TryParse`.  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

Následující příklad ukazuje jeden přístup k analýze řetězec, který má obsahovat úvodní číselné znaky (včetně šestnáctkových znaků) a koncové znaky jiné než číselné. Přiřadí platné znaky ze začátku řetězce nový řetězec před voláním <xref:System.Int32.TryParse%2A> metody. Protože řetězce, který se má analyzovat obsahovat malý počet znaků, příklad volá <xref:System.String.Concat%2A?displayProperty=nameWithType> způsob přiřazení platné znaky pro nový řetězec. Pro větší řetězec <xref:System.Text.StringBuilder> třídu lze použít místo toho. 
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Volání metody převodu

Následující tabulka uvádí některé z metod z <xref:System.Convert> třídu, která slouží k převedení řetězce na číslo.  
  
|Číselný typ|Metoda|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 Následující příklad volá <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> způsobů, jak převést vstupní řetězec [int](../../../csharp/language-reference/keywords/int.md). V příkladu zachytí dvě nejčastější výjimky, které mohou být vyvolány touto metodou, <xref:System.FormatException> a <xref:System.OverflowException>. Pokud lze výsledné číslo zvýšit bez překročení <xref:System.Int32.MaxValue?displayProperty=nameWithType>, v příkladu se k výsledku přičte 1 a zobrazí výstup.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Viz také:

- [Typy](../../../csharp/programming-guide/types/index.md)
- [Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Nástroj pro formátování rozhraní .NET framework 4](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
