---
title: byte (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: 4ac913bd0d1bd178211ad26a720a80e22877c961
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="byte-c-reference"></a>byte (Referenční dokumentace jazyka C#)

`byte` označuje typ integrální, který ukládá hodnoty, které je uvedené v následující tabulce.  
  
|Typ|Rozsah|Velikost|Typ rozhraní .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`byte`|0 až 255|Nepodepsané 8bitové celé číslo|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literály  

 Můžete deklarace a inicializace `byte` proměnné přiřazením decimal literál, hexadecimální literál, nebo (počínaje 7.0 C#) binární literálu do ní. Pokud literálu celé číslo je mimo rozsah `byte` (tj. Pokud je menší než <xref:System.Byte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Byte.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.

V následujícím příkladu, celá čísla rovno 201, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou implicitně převést z [int](../../../csharp/language-reference/keywords/int.md) k `byte` hodnoty.    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> Použijte předponu `0x` nebo `0X` k označení hexadecimální literál a předponu `0b` nebo `0B` k označení binární literál. Decimal literály mít žádná předpona.

Od verze jazyka C# 7.0, byly přidány několik funkcí za účelem zlepšení čitelnosti. 
 - C# 7.0 umožňuje použití znak podtržítka `_`, jako oddělovač číslice.
 - C# 7.2 umožňuje `_` má být použit jako číslice oddělovače pro binární nebo hexadecimální literál, po předponu. Decimal literál není povolená tak, aby měl úvodní podtržítka.

Níže jsou uvedeny některé příklady.

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a>Převody  
 Je předdefinovaný implicitní převod z `byte` k [krátké](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [dlouho ](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Nelze implicitně převést bez literál číselné typy větší velikost úložiště na `byte`. Další informace o velikosti úložiště celočíselných typů najdete v tématu [tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md). Zvažte například následující dva `byte` proměnné `x` a `y`:  
  
```csharp  
byte x = 10, y = 20;  
```  
  
 Následující příkaz přiřazení bude k chybě kompilace vytvořit, protože výsledkem aritmetické výrazu na pravé straně operátoru přiřazení `int` ve výchozím nastavení.  
  
```csharp  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 Chcete-li tento problém vyřešit, použijte přetypování:  
  
```csharp  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 Je ale možné použít následující příkazy, kde Cílová proměnná má stejnou velikost úložiště nebo větší velikost úložiště:  
  
```csharp  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Navíc není žádný implicitní převod z typů s plovoucí desetinnou čárkou na `byte`. Například následující příkaz vygeneruje Chyba kompilátoru, pokud se používá explicitní přetypování:  
  
```csharp  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 Při volání přetížené metody, se musí použít přetypování. Zvažte například následující přetížené metody, které používají `byte` a [int](../../../csharp/language-reference/keywords/int.md) parametry:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 Pomocí `byte` přetypování zaručuje, že správný typ je volána, například:  
  
```csharp  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 Informace v aritmetických výrazech s smíšený typy s plovoucí desetinnou čárkou a integrální typy najdete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [dvojité](../../../csharp/language-reference/keywords/double.md).  
  
 Další informace o implicitní číselný převod pravidel najdete v tématu [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Byte>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
