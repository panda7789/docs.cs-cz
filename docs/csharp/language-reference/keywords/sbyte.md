---
title: sbyte (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
ms.openlocfilehash: 1dca23c4a4216f1edc79b7701a002a28652aed26
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577392"
---
# <a name="sbyte-c-reference"></a>sbyte (Referenční dokumentace jazyka C#)

`sbyte` označuje integrální typ, který uchovává hodnoty podle toho, velikost a rozsah je znázorněno v následující tabulce.  
  
|Typ|Rozsah|Velikost|Typ formátu .NET|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|-128 až 127|8bitové celé číslo se znaménkem|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literály  

Můžete deklarovat a inicializovat `sbyte` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu. 

V následujícím příkladu celých čísel je rovno-102, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou převedeny z [int](../../../csharp/language-reference/keywords/int.md) k `sbyte` hodnoty.    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál. Desítkové literály mají žádná předpona.

Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti. 
 - C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.
 - C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu. Desítkový literál není povoleno mít vedoucího podtržítka.

 Níže je uvedeno několik příkladů.

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

Pokud celočíselný literál je mimo rozsah `sbyte` (tj. Pokud je menší než <xref:System.SByte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.SByte.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace. Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnota: [int](int.md), [uint](uint.md), [dlouhé](long.md), [ulong](ulong.md). To znamená, že v tomto příkladu číselné literály `0x9A` a `0b10011010` jsou interpretovány jako 32bitová celá čísla se znaménkem s hodnotou 156, což překračuje <xref:System.SByte.MaxValue?displayProperty=nameWithType>. Z toho důvodu je potřeba operátor přetypování a přiřazení se musí vyskytovat v [Nekontrolovaná](unchecked.md) kontextu. 

## <a name="compiler-overload-resolution"></a>Řešení přetížení kompilátoru

 Přetypování musí být použito při volání přetížené metody. Zvažte například následující přetížené metody, které používají `sbyte` a [int](../../../csharp/language-reference/keywords/int.md) parametry:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 Použití `sbyte` přetypování zaručuje, že správný typ název, například:  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a>Převody  
 Není předdefinovanou implicitní převod z `sbyte` k [krátký](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [dlouhé](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double ](../../../csharp/language-reference/keywords/double.md), nebo [desítkové](../../../csharp/language-reference/keywords/decimal.md).  
  
 Nelze implicitně převést neliterální číselné typy větší velikosti úložiště `sbyte` (naleznete v tématu [integrální typy tabulky](../../../csharp/language-reference/keywords/integral-types-table.md) pro velikosti úložiště celočíselných typů). Zvažte například následující dva `sbyte` proměnné `x` a `y`:  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 Přiřazovací příkaz způsobí chybu kompilace, protože aritmetický výraz na pravé straně operátoru přiřazení vyhodnotí jako [int](../../../csharp/language-reference/keywords/int.md) ve výchozím nastavení.  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 Chcete-li vyřešit tento problém, přetypování výrazu jako v následujícím příkladu:  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 Je ale možné použít následující příkazy, kde Cílová proměnná se stejnou velikostí úložiště nebo větší velikost úložiště:  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Všimněte si také, že neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `sbyte`. Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 Informace o aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [double](../../../csharp/language-reference/keywords/double.md).  
  
 Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.SByte>  
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
