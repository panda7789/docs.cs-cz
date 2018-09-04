---
title: byte (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: ee70b7c804423a35e2db3fe20ac4b66d8d1b98e2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505092"
---
# <a name="byte-c-reference"></a>byte (Referenční dokumentace jazyka C#)

`byte` označuje integrální typ, který ukládá hodnoty, jak je uvedeno v následující tabulce.  
  
|Typ|Rozsah|Velikost|Typ formátu .NET|  
|----------|-----------|----------|-------------------------|  
|`byte`|0 až 255|Celé číslo bez znaménka 8 bitů|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literály  

 Můžete deklarovat a inicializovat `byte` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu. Pokud celočíselný literál je mimo rozsah `byte` (tj. Pokud je menší než <xref:System.Byte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Byte.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.

V následujícím příkladu celých čísel je rovno 201, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [int](../../../csharp/language-reference/keywords/int.md) k `byte` hodnoty.    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál. Desítkové literály mají žádná předpona.

Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti. 
 - C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.
 - C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu. Desítkový literál není povoleno mít vedoucího podtržítka.

Níže je uvedeno několik příkladů.

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a>Převody  
 Není předdefinovanou implicitní převod z `byte` k [krátký](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [dlouhý ](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), nebo [desítkové](../../../csharp/language-reference/keywords/decimal.md).  
  
 Nelze implicitně převést číselné typy literálu větší velikosti úložiště `byte`. Další informace o velikosti úložiště celočíselných typů naleznete v tématu [integrální typy tabulky](../../../csharp/language-reference/keywords/integral-types-table.md). Zvažte například následující dva `byte` proměnné `x` a `y`:  
  
```csharp  
byte x = 10, y = 20;  
```  
  
 Přiřazovací příkaz způsobí chybu kompilace, protože aritmetický výraz na pravé straně operátoru přiřazení vyhodnotí jako `int` ve výchozím nastavení.  
  
```csharp  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 Pokud chcete tento problém vyřešit, použijte přetypování:  
  
```csharp  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 Je ale možné použít následující příkazy, kde Cílová proměnná se stejnou velikostí úložiště nebo větší velikost úložiště:  
  
```csharp  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Také, neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `byte`. Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:  
  
```csharp  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 Při volání přetížené metody, musíte použít přetypování. Zvažte například následující přetížené metody, které používají `byte` a [int](../../../csharp/language-reference/keywords/int.md) parametry:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 Použití `byte` přetypování zaručuje, že správný typ název, například:  
  
```csharp  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 Informace v aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [double](../../../csharp/language-reference/keywords/double.md).  
  
 Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  

- <xref:System.Byte>  
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
