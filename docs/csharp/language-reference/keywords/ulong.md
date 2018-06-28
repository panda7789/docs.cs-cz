---
title: ulong (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
ms.openlocfilehash: 96975bcfc270694a59a19e7c40183083dbc5bd98
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027990"
---
# <a name="ulong-c-reference"></a>ulong (Referenční dokumentace jazyka C#)

`ulong` – Klíčové slovo označuje integrální typ, který ukládá hodnoty podle velikosti a rozsah uvedené v následující tabulce.  
  
|Typ|Rozsah|Velikost|Typ formátu .NET|  
|----------|-----------|----------|-------------------------|  
|`ulong`|0 – 18,446,744,073,709,551,615|Celé číslo bez znaménka 64-bit|<xref:System.UInt64?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literály  

Můžete deklarace a inicializace `ulong` proměnné přiřazením decimal literál, hexadecimální literál, nebo (počínaje 7.0 C#) binární literálu do ní.  Pokud literálu celé číslo je mimo rozsah `ulong` (tj. Pokud je menší než <xref:System.UInt64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace. 

V následujícím příkladu, celá čísla rovno 7,934,076,125, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `ulong` hodnoty.  
  
[!code-csharp[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]  

> [!NOTE] 
> Použijte předponu `0x` nebo `0X` k označení hexadecimální literál a předponu `0b` nebo `0B` k označení binární literál. Decimal literály mít žádná předpona. 

Od verze jazyka C# 7.0, byly přidány několik funkcí za účelem zlepšení čitelnosti. 
 - C# 7.0 umožňuje použití znak podtržítka `_`, jako oddělovač číslice.
 - C# 7.2 umožňuje `_` má být použit jako číslice oddělovače pro binární nebo hexadecimální literál, po předponu. Decimal literál není povolená tak, aby měl úvodní podtržítka.

Níže jsou uvedeny některé příklady.

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 Literály celé číslo může obsahovat také příponu, která označuje typ. Přípona `UL` nebo `ul` jednoznačně identifikuje jako číselný literál `ulong` hodnotu. `L` Označuje příponu `ulong` literálovou hodnotou, překročí-li <xref:System.Int64.MaxValue?displayProperty=nameWithType>. A `U` nebo `u` označuje příponu `ulong` literálovou hodnotou, překročí-li <xref:System.UInt32.MaxValue?displayProperty=nameWithType>. Následující příklad používá `ul` příponu k označení dlouhých celých čísel:
 
[!code-csharp[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

Pokud celé literál bez přípony, je její typ první z těchto typů, ve kterých může být reprezentován jeho hodnotu: 

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. [long](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a>Řešení přetížení kompilátoru
  
 Běžně se používají přípona je s volání přetížené metody. Zvažte například následující přetížené metody, které používají `ulong` a [int](../../../csharp/language-reference/keywords/int.md) parametry:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 Pomocí přípony s `ulong` parametr zaručuje, že správný typ je volána, například:  
  
```csharp  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a>Převody  
 Je předdefinovaný implicitní převod z `ulong` k [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Neexistuje žádný implicitní převod z `ulong` k libovolnému integrální typu. Například následující příkaz vytvoří chybu kompilace bez explicitní přetypování:  
  
```csharp  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 Je předdefinovaný implicitní převod z [bajtů](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), nebo [char](../../../csharp/language-reference/keywords/char.md) k `ulong`.  
  
 Navíc není žádný implicitní převod z typů s plovoucí desetinnou čárkou na `ulong`. Například následující příkaz vygeneruje Chyba kompilátoru, pokud se používá explicitní přetypování:  
  
```csharp  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 Informace v aritmetických výrazech s smíšený typy s plovoucí desetinnou čárkou a integrální typy najdete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [dvojité](../../../csharp/language-reference/keywords/double.md).  
  
 Další informace o implicitní číselný převod pravidel najdete v tématu [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.UInt64>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
