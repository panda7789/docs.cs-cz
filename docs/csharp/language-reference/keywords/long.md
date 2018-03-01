---
title: "long (Referenční dokumentace jazyka C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f18bed80550b293195961fd9d42491dd571cbaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="long-c-reference"></a>long (Referenční dokumentace jazyka C#)

`long`označuje typ integrální, který ukládá hodnoty podle velikosti a rozsah uvedené v následující tabulce.  
  
|Typ|Rozsah|Velikost|Typ rozhraní .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`long`|-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807|64bitové celé číslo se znaménkem|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literály 

Můžete deklarace a inicializace `long` proměnné přiřazením decimal literál, hexadecimální literál, nebo (počínaje C# 7) binární literálu do ní. 

V následujícím příkladu, celá čísla rovno 4 294 967 296 jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `long` hodnoty.  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> Použijte předponu `0x` nebo `0X` k označení hexadecimální literál a předponu `0b` nebo `0B` k označení binární literál. Decimal literály mít žádná předpona. 

Od verze jazyka C# 7, byly přidány několik funkcí za účelem zlepšení čitelnosti. 
 - C# 7.0 umožňuje použití znak podtržítka `_`, jako oddělovač číslice.
 - C# 7.2 umožňuje `_` má být použit jako číslice oddělovače pro binární nebo hexadecimální literál, po předponu. Decimal literál není povolená tak, aby měl úvodní podtržítka.

Níže jsou uvedeny některé příklady.

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 Literály celé číslo může obsahovat také příponu, která označuje typ. Přípona `L` označuje `long`. Následující příklad používá `L` příponu k označení dlouhých celých čísel:
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  Můžete taky malé písmeno "l" jako příponu. Ale tím se vygeneruje upozornění kompilátoru protože písmeno "l" je snadno zaměnit s číslice "1". Pro přehlednost použijte "L".  
  
 Když použijete tuto příponu `L`, typ literálu celého čísla, je určen být buď `long` nebo [ulong](../../../csharp/language-reference/keywords/ulong.md), v závislosti na jeho velikost. V takovém případě je `long` protože je menší než rozsah [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Běžně se používají přípona je volání přetížené metody. Například následující přetížené metody mít parametry typu `long` a [int](../../../csharp/language-reference/keywords/int.md):  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 `L` Příponu zaručuje, že správné přetížení nazývá:  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
Pokud celé literál bez přípony, je její typ první z těchto typů, ve kterých může být reprezentován jeho hodnotu: 

1. [celá čísla](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [ulong –](../../../csharp/language-reference/keywords/ulong.md) 

Literál 4294967296 v předchozích příkladech je typu `long`, protože překračuje rozsah [Celé_číslo](../../../csharp/language-reference/keywords/uint.md) (viz [tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md) velikostí úložiště celočíselných typů).  
  
 Pokud použijete `long` je typ s jinými integrální typy ve stejném výrazu výraz vyhodnocen jako `long` (nebo [bool](../../../csharp/language-reference/keywords/bool.md) v případě výrazy relační nebo logická hodnota). Například následující výraz vyhodnotí jako `long`:  
  
```csharp  
898L + 88  
```  
  
 Informace v aritmetických výrazech s smíšený typy s plovoucí desetinnou čárkou a integrální typy najdete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [dvojité](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="conversions"></a>Převody  
 Je předdefinovaný implicitní převod z `long` k [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [decimal](../../../csharp/language-reference/keywords/decimal.md). V opačném případě je nutné použít přetypování. Například následující příkaz vytvoří chybu kompilace bez explicitní přetypování:  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 Je předdefinovaný implicitní převod z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtů](../../../csharp/language-reference/keywords/byte.md), [krátké](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), nebo [char](../../../csharp/language-reference/keywords/char.md) k `long`.  
  
 Všimněte si také, že neexistuje žádná implicitní převod z typů s plovoucí desetinnou čárkou na `long`. Například následující příkaz vygeneruje Chyba kompilátoru, pokud se používá explicitní přetypování:  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Int64>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
