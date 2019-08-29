---
title: 'Postupy: Převod řetězce na číslo – C# programový průvodce'
ms.custom: seodec18
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 377074bf09cf1e24ec022cee506588a9dcb8cb80
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133706"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Postupy: Převod řetězce na číslo (C# Průvodce programováním)

Můžete převést [řetězec](../../language-reference/keywords/string.md) na `Parse` číslo voláním metody nebo `TryParse` , která se nachází na různých číselných typech (`int`, `long`, `double`atd.), nebo pomocí metod ve <xref:System.Convert?displayProperty=nameWithType> třídě.  
  
 Pokud máte řetězec, je poněkud efektivnější `TryParse` a jednoduše zavolejte metodu ( [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)například) nebo `Parse` metodu (například [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)).  Použití metody je užitečnější pro obecné objekty, které implementují <xref:System.IConvertible>. <xref:System.Convert>  
  
 Můžete použít `Parse` metody nebo `TryParse` u číselného typu, který řetězec obsahuje, jako je <xref:System.Int32?displayProperty=nameWithType> například typ.  <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> Metoda používá<xref:System.Int32.Parse%2A> interně.  Metoda vrátí převedený `TryParse` počet; metoda vrátí <xref:System.Boolean> hodnotu, která označuje, zda byl převod úspěšný [ `out` ](../../language-reference/keywords/out.md), a vrátí převedený počet v parametru. `Parse` Pokud řetězec není v platném formátu, `Parse` vyvolá výjimku, zatímco `TryParse` vrátí [false](../../language-reference/keywords/false-literal.md). Při volání `Parse` metody byste měli vždy použít zpracování výjimek k zachycení a <xref:System.FormatException> v případě, že operace analýzy není úspěšná.  
  
## <a name="calling-the-parse-and-tryparse-methods"></a>Volání metod Parse a TryParse

`ulong``int` `long`Metody a ignorujíprázdnéznakynazačátkuanakonciřetězce,alevšechnyostatníznakymusíbýtznaky,kterétvořípříslušnýčíselnýtyp(,,,`TryParse` `Parse` `float` ,`decimal`atd.).  Jakékoli prázdné místo v řetězci, které tvoří číslo, způsobí chybu.  Můžete například použít `decimal.TryParse` k analýze "10", "10,3" nebo "10", ale tuto metodu nelze použít k analýze 10 z "10x", "1 0" (Všimněte si vloženého prostoru), "10 .3" (poznámení s vloženým prostorem), "10E1" (`float.TryParse` funguje zde) atd. Kromě toho je řetězec, jehož hodnota je `null` nebo <xref:System.String.Empty?displayProperty=nameWithType> se nedaří analyzovat úspěšně. Před pokusem o jeho analýzu můžete zadat hodnotu null nebo prázdný řetězec voláním <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metody. 

Následující příklad ukazuje úspěšné i neúspěšné volání `Parse` metody a. `TryParse`  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

Následující příklad ilustruje jeden z přístupů k analýze řetězce, který by měl obsahovat úvodní číselné znaky (včetně hexadecimálních znaků) a koncových znaků, které nejsou číselné. Před voláním <xref:System.Int32.TryParse%2A> metody přiřadí platné znaky od začátku řetězce k novému řetězci. Vzhledem k tomu, že řetězce, které mají být analyzovány obsahují malý počet znaků, příklad <xref:System.String.Concat%2A?displayProperty=nameWithType> volá metodu pro přiřazení platných znaků novému řetězci. Pro větší řetězec <xref:System.Text.StringBuilder> lze místo toho použít třídu. 
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a>Volání metod Convert

V následující tabulce jsou uvedeny některé z metod <xref:System.Convert> třídy, které lze použít k převodu řetězce na číslo.  
  
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
  
 Následující příklad volá <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> metodu pro převod vstupního řetězce na typ [int](../../language-reference/builtin-types/integral-numeric-types.md). Příklad zachytí dvě nejběžnější výjimky, které mohou být vyvolány touto metodou, <xref:System.FormatException> a <xref:System.OverflowException>. Pokud se výsledný počet dá zvýšit bez překročení <xref:System.Int32.MaxValue?displayProperty=nameWithType>, příklad přidá 1 k výsledku a zobrazí výstup.  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a>Viz také:

- [Typy](./index.md)
- [Postupy: Určení, zda řetězec představuje číselnou hodnotu](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Ukázka: nástroj formátování WinForms pro .NET CoreC#()](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)
