---
title: short (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: f402b9d2d62bcc3ba265755d59a657b88c197482
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855787"
---
# <a name="short-c-reference"></a>short (Referenční dokumentace jazyka C#)

`short` označuje integrální datový typ, který uchovává hodnoty podle velikosti a oblasti, které jsou uvedeny v následující tabulce.  
  
|Typ|Rozsah|Velikost|Typ formátu .NET|  
|----------|-----------|----------|-------------------------|  
|`short`|-32 768 do 32 767|16bitové celé číslo se znaménkem|<xref:System.Int16?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literály  

Můžete deklarovat a inicializovat `short` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.  Pokud celočíselný literál je mimo rozsah `short` (tj. Pokud je menší než <xref:System.Int16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int16.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace. 

V následujícím příkladu celých čísel je rovno 1,034, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [int](../../../csharp/language-reference/keywords/int.md) k `short` hodnoty.  
  
[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál. Desítkové literály mají žádná předpona.

Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti. 
 - C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.
 - C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu. Desítkový literál není povoleno mít vedoucího podtržítka.

Níže je uvedeno několik příkladů.

[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
## <a name="compiler-overload-resolution"></a>Řešení přetížení kompilátoru

 Přetypování musí být použito při volání přetížené metody. Zvažte například následující přetížené metody, které používají `short` a [int](../../../csharp/language-reference/keywords/int.md) parametry:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 Použití `short` přetypování zaručuje, že správný typ název, například:  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a>Převody  

 Není předdefinovanou implicitní převod z `short` k [int](../../../csharp/language-reference/keywords/int.md), [dlouhé](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), nebo [ desetinné](../../../csharp/language-reference/keywords/decimal.md).  
  
 Nelze implicitně převést neliterální číselné typy větší velikosti úložiště `short` (naleznete v tématu [integrální typy tabulky](../../../csharp/language-reference/keywords/integral-types-table.md) pro velikosti úložiště celočíselných typů). Zvažte například následující dva `short` proměnné `x` a `y`:  
  
```csharp  
short x = 5, y = 12;  
```  
  
 Přiřazovací příkaz způsobí chybu kompilace, protože aritmetický výraz na pravé straně operátoru přiřazení vyhodnotí jako [int](../../../csharp/language-reference/keywords/int.md) ve výchozím nastavení.  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 Pokud chcete tento problém vyřešit, použijte přetypování:  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 Je také možné použít následující příkazy, kde Cílová proměnná se stejnou velikostí úložiště nebo větší velikost úložiště:  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 Neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `short`. Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 Informace v aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [double](../../../csharp/language-reference/keywords/double.md).  
  
 Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Int16>  
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
