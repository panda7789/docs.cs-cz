---
title: ushort (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: 03638893978779fcfd34544363d935fa5e609481
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ushort-c-reference"></a>ushort (Referenční dokumentace jazyka C#)

`ushort` – Klíčové slovo označuje celočíselný datový typ, který ukládá hodnoty podle velikosti a rozsah uvedené v následující tabulce.  
  
|Typ|Rozsah|Velikost|Typ rozhraní .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`ushort`|0 až 65 535|Nepodepsané 16bitové celé číslo|<xref:System.UInt16?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literály  

Můžete deklarace a inicializace `ushort` proměnné přiřazením decimal literál, hexadecimální literál, nebo (počínaje 7.0 C#) binární literálu do ní. Pokud literálu celé číslo je mimo rozsah `ushort` (tj. Pokud je menší než <xref:System.UInt16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.

V následujícím příkladu, celá čísla rovno 65,034, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou implicitně převést z [int](../../../csharp/language-reference/keywords/int.md) k `ushort` hodnoty.    
  
[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> Použijte předponu `0x` nebo `0X` k označení hexadecimální literál a předponu `0b` nebo `0B` k označení binární literál. Decimal literály mít žádná předpona.

Od verze jazyka C# 7.0, byly přidány několik funkcí za účelem zlepšení čitelnosti. 
 - C# 7.0 umožňuje použití znak podtržítka `_`, jako oddělovač číslice.
 - C# 7.2 umožňuje `_` má být použit jako číslice oddělovače pro binární nebo hexadecimální literál, po předponu. Decimal literál není povolená tak, aby měl úvodní podtržítka.

Níže jsou uvedeny některé příklady.

[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a>Řešení přetížení kompilátoru
  
 Při volání přetížené metody se musí použít přetypování. Zvažte například následující přetížené metody, které používají `ushort` a [int](../../../csharp/language-reference/keywords/int.md) parametry:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 Pomocí `ushort` přetypování zaručuje, že správný typ je volána, například:  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a>Převody  
 Je předdefinovaný implicitní převod z `ushort` k [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [dlouho](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float ](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Je předdefinovaný implicitní převod z [bajtů](../../../csharp/language-reference/keywords/byte.md) nebo [char](../../../csharp/language-reference/keywords/char.md) k `ushort`. V opačném případě musí být přetypování použít k provedení explicitní převod. Zvažte například následující dva `ushort` proměnné `x` a `y`:  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 Následující příkaz přiřazení bude k chybě kompilace vytvořit, protože výsledkem aritmetické výrazu na pravé straně operátoru přiřazení `int` ve výchozím nastavení.  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 Chcete-li tento problém vyřešit, použijte přetypování:  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 Je ale možné použít následující příkazy, kde Cílová proměnná má stejnou velikost úložiště nebo větší velikost úložiště:  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 Všimněte si také, že neexistuje žádná implicitní převod z typů s plovoucí desetinnou čárkou na `ushort`. Například následující příkaz vygeneruje Chyba kompilátoru, pokud se používá explicitní přetypování:  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 Informace o aritmetických výrazech s smíšený typy s plovoucí desetinnou čárkou a integrální typy najdete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [dvojité](../../../csharp/language-reference/keywords/double.md).  
  
 Další informace o pravidlech implicitní převod číselného najdete v tématu [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.UInt16>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
