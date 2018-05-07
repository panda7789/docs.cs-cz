---
title: decimal (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: 590bd3c6347271f9c4e2c6fd6223db608e010b69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="decimal-c-reference"></a>decimal (Referenční dokumentace jazyka C#)
`decimal` – Klíčové slovo označuje typ dat 128-bit. Porovnání na jiné typy s plovoucí desetinnou čárkou `decimal` typ má více přesnost i s menším rozsahem, takže je vhodné pro finanční a peněžní výpočty. Přibližná rozsah a přesnost pro `decimal` typu jsou uvedené v následující tabulce.  
  
|Typ|Přibližný rozsah|Přesnost|Typ rozhraní .NET Framework|  
|----------|-----------------------|---------------|-------------------------|  
|`decimal`|(-7.9 × 10<sup>28</sup> 7.9 × 10<sup>28</sup>) / (10<sup>0</sup> na 10<sup>28</sup>)|28–29 významných číslic|<xref:System.Decimal?displayProperty=nameWithType>|  

Výchozí hodnota `decimal` je 0 m.
  
## <a name="literals"></a>Literály  
 Pokud chcete, aby číselný literál skutečné považován za `decimal`, použít příponu m nebo M, například:  
  
```csharp
decimal myMoney = 300.5m;  
```  
  
 Bez přípony m číslo považován za [dvojité](../../../csharp/language-reference/keywords/double.md) a vygeneruje chyby kompilátoru.  
  
## <a name="conversions"></a>Převody  
 Celočíselné typy jsou implicitně převést na `decimal` a vyhodnotí jako výsledek `decimal`. Z tohoto důvodu můžete inicializovat proměnnou desítkového čísla pomocí celočíselného literálu bez přípony, a to následovně:  
  
```csharp
decimal myMoney = 300;  
```  
  
 Neexistuje žádný implicitní převod mezi jiné typy s plovoucí desetinnou čárkou a `decimal` typ; proto přetypování použije pro převod mezi těmito dvěma typy. Příklad:  
  
```csharp
decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 Můžete také kombinovat `decimal` a číselnými integrální typy ve stejném výrazu. Kombinování však `decimal` a dalších typů s plovoucí desetinnou čárkou bez přetypování způsobí chybu kompilace.  
  
 Další informace o implicitních číselných převodů najdete v tématu [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Další informace o explicitních číselných převodů najdete v tématu [explicitní číselné převody tabulky](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## <a name="formatting-decimal-output"></a>Formátování desítkového výstupu  
 Výsledky můžete naformátovat pomocí `String.Format` metoda, nebo pomocí <xref:System.Console.Write%2A?displayProperty=nameWithType> metodu, která volá `String.Format()`. Formát měny je určen pomocí řetězce standardního formátu měny "C" nebo "c", jak je uvedeno v druhém příkladu dále v tomto článku. Další informace o `String.Format` metodu, najdete v části <xref:System.String.Format%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Příklad  
 Následující příklad způsobí chybu kompilátoru tak, že zkusíte přidat [dvojité](../../../csharp/language-reference/keywords/double.md) a `decimal` proměnné.  
  
```csharp  
decimal dec = 0m;
double dub = 9;  
// The following line causes an error that reads "Operator '+' cannot be applied to   
// operands of type 'double' and 'decimal'"  
Console.WriteLine(dec + dub);   
  
// You can fix the error by using explicit casting of either operand.  
Console.WriteLine(dec + (decimal)dub);  
Console.WriteLine((double)dec + dub);  
```  
  
 Výsledkem je následující chyba:  
  
 `Operator '+' cannot be applied to operands of type 'double' and 'decimal'`  
  
 V tomto příkladu `decimal` a [int](../../../csharp/language-reference/keywords/int.md) jsou kombinované ve stejném výrazu. Výsledek se vyhodnocuje `decimal` typu.  
  
 [!code-csharp[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je výstup naformátován pomocí řetězce formátu měny. Všimněte si, že `x` se zaokrouhlí, protože překročila $0,99 desetinných míst. Proměnná `y`, která představuje maximální číslice, se zobrazí přesně ve správném formátu.  
  
 [!code-csharp[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Decimal>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Standardní řetězce číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)
