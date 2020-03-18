---
title: Jak převést řetězec na číslo - C# Programovací průvodce
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 54a4562a5cc493fc287bdf2f6bcf9723557f2a05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157036"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Jak převést řetězec na číslo (C# Programovací průvodce)

[Řetězec](../../language-reference/builtin-types/reference-types.md) můžete převést na číslo `Parse` voláním `TryParse` metody nebo nalezené`int`na `long` `double`různých číselných typech ( <xref:System.Convert?displayProperty=nameWithType> , , , atd.) nebo pomocí metod ve třídě.  
  
 Pokud máte řetězec, je o něco efektivnější a `TryParse` jednodušší volat [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)metodu `Parse` (například) [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)nebo metodu (například).  Použití <xref:System.Convert> metody je užitečnější pro <xref:System.IConvertible>obecné objekty, které implementují .  
  
 Můžete použít `Parse` `TryParse` nebo metody na číselný typ, který <xref:System.Int32?displayProperty=nameWithType> očekáváte řetězec obsahuje, jako je například typ.  Metoda <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> používá <xref:System.Int32.Parse%2A> interně.  Metoda `Parse` vrátí převedené číslo; metoda `TryParse` vrátí <xref:System.Boolean> hodnotu, která označuje, zda byl převod úspěšný, a vrátí převedené číslo v [ `out` parametru](../../language-reference/keywords/out.md). Pokud řetězec není v platném `Parse` formátu, vyvolá výjimku, vzhledem k tomu, `TryParse` že vrátí `false`. Při volání `Parse` metody, měli byste vždy použít <xref:System.FormatException> zpracování výjimek zachytit v případě, že operace analýzy selže.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Volání Metody Parse a TryParse

Metody `Parse` `TryParse` a ignorují prázdné znaky na začátku a na konci řetězce, ale všechny ostatní`int` `long`znaky `ulong` `float`musí `decimal`být znaky, které tvoří příslušný číselný typ ( , , , , atd.).  Jakékoli prázdné místo v řetězci, který tvoří číslo způsobí chybu.  Můžete například použít `decimal.TryParse` k analýzě "10", "10.3" nebo " 10 ", ale tuto metodu nelze použít k analyzovat 10 z "10X", "1 0" (všimněte si vložené`float.TryParse` mezery), "10.3" (všimněte si vložené mezery), "10e1" (funguje zde) a tak dále. Kromě toho řetězec, jehož hodnota je `null` nebo <xref:System.String.Empty?displayProperty=nameWithType> se nezdaří analyzovat úspěšně. Můžete zkontrolovat nula nebo prázdný řetězec před pokusem o <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> jeho analýzu voláním metody.

Následující příklad ukazuje úspěšné i neúspěšné `Parse` `TryParse`volání a .  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

Následující příklad ilustruje jeden přístup k analýzě řetězec, který se očekává, že bude obsahovat úvodní číselné znaky (včetně šestnáctkových znaků) a koncové nečíselné znaky. Přiřadí platné znaky od začátku řetězce k novému <xref:System.Int32.TryParse%2A> řetězci před voláním metody. Vzhledem k tomu, že řetězce, které mají být analyzovány, obsahují malý počet znaků, příklad volá metodu <xref:System.String.Concat%2A?displayProperty=nameWithType> pro přiřazení platných znaků k novému řetězci. Pro větší řetězec <xref:System.Text.StringBuilder> třídy lze použít místo.
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Volání metod Convert

V následující tabulce jsou uvedeny <xref:System.Convert> některé metody z třídy, které můžete použít k převodu řetězce na číslo.  
  
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
  
 Následující příklad volá <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> metodu převést vstupní řetězec [na int](../../language-reference/builtin-types/integral-numeric-types.md). Příklad zachytí dvě nejběžnější výjimky, které mohou být <xref:System.FormatException> <xref:System.OverflowException>vyvolány touto metodou a . Pokud výsledné číslo může být zvýšení bez <xref:System.Int32.MaxValue?displayProperty=nameWithType>překročení , příklad přidá 1 k výsledku a zobrazí výstup.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Viz také

- [Typy](./index.md)
- [Jak určit, jestli řetězec představuje číselnou hodnotu](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Ukázka: Nástroj pro formátování WinForms .NET (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
