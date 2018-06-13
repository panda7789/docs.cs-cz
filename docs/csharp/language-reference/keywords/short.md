---
title: short (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: 657d5bb3866a3ad88226740ebf7ef12c3654e56b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288161"
---
# <a name="short-c-reference"></a>short (Referenční dokumentace jazyka C#)

`short` označuje celočíselný datový typ, který ukládá hodnoty podle velikosti a rozsah uvedené v následující tabulce.  
  
|Typ|Rozsah|Velikost|Typ rozhraní .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`short`|-32 768 do 32 767|16bitové celé číslo se znaménkem|<xref:System.Int16?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literály  

Můžete deklarace a inicializace `short` proměnné přiřazením decimal literál, hexadecimální literál, nebo (počínaje 7.0 C#) binární literálu do ní.  Pokud literálu celé číslo je mimo rozsah `short` (tj. Pokud je menší než <xref:System.Int16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int16.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace. 

V následujícím příkladu, celá čísla rovno 1,034, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou implicitně převést z [int](../../../csharp/language-reference/keywords/int.md) k `short` hodnoty.  
  
[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> Použijte předponu `0x` nebo `0X` k označení hexadecimální literál a předponu `0b` nebo `0B` k označení binární literál. Decimal literály mít žádná předpona.

Od verze jazyka C# 7.0, byly přidány několik funkcí za účelem zlepšení čitelnosti. 
 - C# 7.0 umožňuje použití znak podtržítka `_`, jako oddělovač číslice.
 - C# 7.2 umožňuje `_` má být použit jako číslice oddělovače pro binární nebo hexadecimální literál, po předponu. Decimal literál není povolená tak, aby měl úvodní podtržítka.

Níže jsou uvedeny některé příklady.

[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
## <a name="compiler-overload-resolution"></a>Řešení přetížení kompilátoru

 Při volání přetížené metody se musí použít přetypování. Zvažte například následující přetížené metody, které používají `short` a [int](../../../csharp/language-reference/keywords/int.md) parametry:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 Pomocí `short` přetypování zaručuje, že správný typ je volána, například:  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a>Převody  

 Je předdefinovaný implicitní převod z `short` k [int](../../../csharp/language-reference/keywords/int.md), [dlouho](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [ Decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Nelze implicitně převést nonliteral číselnými typy větší velikost úložiště na `short` (viz [tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md) velikostí úložiště celočíselných typů). Zvažte například následující dva `short` proměnné `x` a `y`:  
  
```csharp  
short x = 5, y = 12;  
```  
  
 Následující příkaz přiřazení vytvoří chybu kompilace, protože výsledkem aritmetické výrazu na pravé straně operátoru přiřazení [int](../../../csharp/language-reference/keywords/int.md) ve výchozím nastavení.  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 Chcete-li tento problém vyřešit, použijte přetypování:  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 Je také možné použít následující příkazy, kde Cílová proměnná má stejnou velikost úložiště nebo větší velikost úložiště:  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 Neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou na `short`. Například následující příkaz vygeneruje Chyba kompilátoru, pokud se používá explicitní přetypování:  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 Informace v aritmetických výrazech s smíšený typy s plovoucí desetinnou čárkou a integrální typy najdete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [dvojité](../../../csharp/language-reference/keywords/double.md).  
  
 Další informace o implicitní číselný převod pravidel najdete v tématu [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Int16>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
