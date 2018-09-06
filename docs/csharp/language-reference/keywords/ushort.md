---
title: ushort (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: 2f038378e1af85520cea13d914da69dfcb054ac0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857294"
---
# <a name="ushort-c-reference"></a><span data-ttu-id="474a2-102">ushort (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="474a2-102">ushort (C# Reference)</span></span>

<span data-ttu-id="474a2-103">`ushort` – Klíčové slovo určuje celočíselný datový typ, který uchovává hodnoty podle velikosti a oblasti, které jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="474a2-103">The `ushort` keyword indicates an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="474a2-104">Typ</span><span class="sxs-lookup"><span data-stu-id="474a2-104">Type</span></span>|<span data-ttu-id="474a2-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="474a2-105">Range</span></span>|<span data-ttu-id="474a2-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="474a2-106">Size</span></span>|<span data-ttu-id="474a2-107">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="474a2-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ushort`|<span data-ttu-id="474a2-108">0 až 65 535</span><span class="sxs-lookup"><span data-stu-id="474a2-108">0 to 65,535</span></span>|<span data-ttu-id="474a2-109">Celé číslo bez znaménka 16 bitů</span><span class="sxs-lookup"><span data-stu-id="474a2-109">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="474a2-110">Literály</span><span class="sxs-lookup"><span data-stu-id="474a2-110">Literals</span></span>  

<span data-ttu-id="474a2-111">Můžete deklarovat a inicializovat `ushort` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.</span><span class="sxs-lookup"><span data-stu-id="474a2-111">You can declare and initialize a `ushort` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="474a2-112">Pokud celočíselný literál je mimo rozsah `ushort` (tj. Pokud je menší než <xref:System.UInt16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="474a2-112">If the integer literal is outside the range of `ushort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="474a2-113">V následujícím příkladu celých čísel je rovno 65,034, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [int](../../../csharp/language-reference/keywords/int.md) k `ushort` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="474a2-113">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `ushort` values.</span></span>    
  
[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> <span data-ttu-id="474a2-114">Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="474a2-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="474a2-115">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="474a2-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="474a2-116">Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="474a2-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="474a2-117">C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="474a2-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="474a2-118">C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu.</span><span class="sxs-lookup"><span data-stu-id="474a2-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="474a2-119">Desítkový literál není povoleno mít vedoucího podtržítka.</span><span class="sxs-lookup"><span data-stu-id="474a2-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="474a2-120">Níže je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="474a2-120">Some examples are shown below.</span></span>

[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="474a2-121">Řešení přetížení kompilátoru</span><span class="sxs-lookup"><span data-stu-id="474a2-121">Compiler overload resolution</span></span>
  
 <span data-ttu-id="474a2-122">Přetypování musí být použito při volání přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="474a2-122">A cast must be used when you call overloaded methods.</span></span> <span data-ttu-id="474a2-123">Zvažte například následující přetížené metody, které používají `ushort` a [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="474a2-123">Consider, for example, the following overloaded methods that use `ushort` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 <span data-ttu-id="474a2-124">Použití `ushort` přetypování zaručuje, že správný typ název, například:</span><span class="sxs-lookup"><span data-stu-id="474a2-124">Using the `ushort` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a><span data-ttu-id="474a2-125">Převody</span><span class="sxs-lookup"><span data-stu-id="474a2-125">Conversions</span></span>  
 <span data-ttu-id="474a2-126">Není předdefinovanou implicitní převod z `ushort` k [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [dlouhé](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [plovoucí desetinnou čárkou ](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), nebo [desítkové](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="474a2-126">There is a predefined implicit conversion from `ushort` to [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="474a2-127">Není předdefinovanou implicitní převod z [bajtů](../../../csharp/language-reference/keywords/byte.md) nebo [char](../../../csharp/language-reference/keywords/char.md) k `ushort`.</span><span class="sxs-lookup"><span data-stu-id="474a2-127">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md) or [char](../../../csharp/language-reference/keywords/char.md) to `ushort`.</span></span> <span data-ttu-id="474a2-128">V opačném případě musí být použito k provedení explicitního převodu přetypování.</span><span class="sxs-lookup"><span data-stu-id="474a2-128">Otherwise a cast must be used to perform an explicit conversion.</span></span> <span data-ttu-id="474a2-129">Zvažte například následující dva `ushort` proměnné `x` a `y`:</span><span class="sxs-lookup"><span data-stu-id="474a2-129">Consider, for example, the following two `ushort` variables `x` and `y`:</span></span>  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 <span data-ttu-id="474a2-130">Přiřazovací příkaz způsobí chybu kompilace, protože aritmetický výraz na pravé straně operátoru přiřazení vyhodnotí jako `int` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="474a2-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to `int` by default.</span></span>  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 <span data-ttu-id="474a2-131">Pokud chcete tento problém vyřešit, použijte přetypování:</span><span class="sxs-lookup"><span data-stu-id="474a2-131">To fix this problem, use a cast:</span></span>  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 <span data-ttu-id="474a2-132">Je ale možné použít následující příkazy, kde Cílová proměnná se stejnou velikostí úložiště nebo větší velikost úložiště:</span><span class="sxs-lookup"><span data-stu-id="474a2-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="474a2-133">Všimněte si také, že neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `ushort`.</span><span class="sxs-lookup"><span data-stu-id="474a2-133">Notice also that there is no implicit conversion from floating-point types to `ushort`.</span></span> <span data-ttu-id="474a2-134">Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="474a2-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 <span data-ttu-id="474a2-135">Informace o aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="474a2-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="474a2-136">Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="474a2-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="474a2-137">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="474a2-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="474a2-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="474a2-138">See Also</span></span>

- <xref:System.UInt16>  
- [<span data-ttu-id="474a2-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="474a2-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="474a2-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="474a2-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="474a2-141">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="474a2-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="474a2-142">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="474a2-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="474a2-143">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="474a2-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="474a2-144">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="474a2-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="474a2-145">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="474a2-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
