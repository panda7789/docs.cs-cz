---
title: "sbyte (Referenční dokumentace jazyka C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 010ac98f523eca5929100f7c51b8b6ef5d11de30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sbyte-c-reference"></a><span data-ttu-id="32e9a-102">sbyte (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="32e9a-102">sbyte (C# Reference)</span></span>

<span data-ttu-id="32e9a-103">`sbyte`označuje typ integrální, který ukládá hodnoty podle velikosti a rozsah uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="32e9a-103">`sbyte` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="32e9a-104">Typ</span><span class="sxs-lookup"><span data-stu-id="32e9a-104">Type</span></span>|<span data-ttu-id="32e9a-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="32e9a-105">Range</span></span>|<span data-ttu-id="32e9a-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="32e9a-106">Size</span></span>|<span data-ttu-id="32e9a-107">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32e9a-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|<span data-ttu-id="32e9a-108">-128 až 127</span><span class="sxs-lookup"><span data-stu-id="32e9a-108">-128 to 127</span></span>|<span data-ttu-id="32e9a-109">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="32e9a-109">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="32e9a-110">Literály</span><span class="sxs-lookup"><span data-stu-id="32e9a-110">Literals</span></span>  

<span data-ttu-id="32e9a-111">Můžete deklarace a inicializace `sbyte` proměnné přiřazením decimal literál, hexadecimální literál, nebo (počínaje C# 7) binární literálu do ní.</span><span class="sxs-lookup"><span data-stu-id="32e9a-111">You can declare and initialize an `sbyte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> 

<span data-ttu-id="32e9a-112">V následujícím příkladu, celá čísla rovno-102, která jsou reprezentovány jako decimal, šestnáctkové, a jsou binární literály převést z [int](../../../csharp/language-reference/keywords/int.md) k `sbyte` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="32e9a-112">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are converted from [int](../../../csharp/language-reference/keywords/int.md) to `sbyte` values.</span></span>    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> <span data-ttu-id="32e9a-113">Použijte předponu `0x` nebo `0X` k označení hexadecimální literál a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="32e9a-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="32e9a-114">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="32e9a-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="32e9a-115">Od verze jazyka C# 7, byly přidány několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="32e9a-115">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="32e9a-116">C# 7.0 umožňuje použití znak podtržítka `_`, jako oddělovač číslice.</span><span class="sxs-lookup"><span data-stu-id="32e9a-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="32e9a-117">C# 7.2 umožňuje `_` má být použit jako číslice oddělovače pro binární nebo hexadecimální literál, po předponu.</span><span class="sxs-lookup"><span data-stu-id="32e9a-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="32e9a-118">Decimal literál není povolená tak, aby měl úvodní podtržítka.</span><span class="sxs-lookup"><span data-stu-id="32e9a-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

 <span data-ttu-id="32e9a-119">Níže jsou uvedeny některé příklady.</span><span class="sxs-lookup"><span data-stu-id="32e9a-119">Some examples are shown below.</span></span>

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

<span data-ttu-id="32e9a-120">Pokud literálu celé číslo je mimo rozsah `sbyte` (tj. Pokud je menší než <xref:System.SByte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.SByte.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="32e9a-120">If the integer literal is outside the range of `sbyte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="32e9a-121">Pokud celé literál bez přípony, její typ je první z těchto typů, ve kterých může být reprezentován jeho hodnota: [int](int.md), [Celé_číslo](uint.md), [dlouho](long.md), [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="32e9a-121">When an integer literal has no suffix, its type is the first of these types in which its value can be represented: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span></span> <span data-ttu-id="32e9a-122">To znamená, že v tomto příkladu číselné literály `0x9A` a `0b10011010` se interpretují jako 32bitová podepsaná celá čísla s hodnotou 156, který přesahuje <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="32e9a-122">This means that, in this example, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="32e9a-123">Z toho důvodu je potřeba operátor přetypování a přiřazení se musí vyskytovat v [nezaškrtnuté](unchecked.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="32e9a-123">Because of this, the casting operator is needed, and the assignment must occur in an [unchecked](unchecked.md) context.</span></span> 

## <a name="compiler-overload-resolution"></a><span data-ttu-id="32e9a-124">Řešení přetížení kompilátoru</span><span class="sxs-lookup"><span data-stu-id="32e9a-124">Compiler overload resolution</span></span>

 <span data-ttu-id="32e9a-125">Při volání přetížené metody se musí použít přetypování.</span><span class="sxs-lookup"><span data-stu-id="32e9a-125">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="32e9a-126">Zvažte například následující přetížené metody, které používají `sbyte` a [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="32e9a-126">Consider, for example, the following overloaded methods that use `sbyte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 <span data-ttu-id="32e9a-127">Pomocí `sbyte` přetypování zaručuje, že správný typ je volána, například:</span><span class="sxs-lookup"><span data-stu-id="32e9a-127">Using the `sbyte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a><span data-ttu-id="32e9a-128">Převody</span><span class="sxs-lookup"><span data-stu-id="32e9a-128">Conversions</span></span>  
 <span data-ttu-id="32e9a-129">Je předdefinovaný implicitní převod z `sbyte` k [krátké](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [dlouho](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double ](../../../csharp/language-reference/keywords/double.md), nebo [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="32e9a-129">There is a predefined implicit conversion from `sbyte` to [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="32e9a-130">Nelze implicitně převést nonliteral číselnými typy větší velikost úložiště na `sbyte` (viz [tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md) velikostí úložiště celočíselných typů).</span><span class="sxs-lookup"><span data-stu-id="32e9a-130">You cannot implicitly convert nonliteral numeric types of larger storage size to `sbyte` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="32e9a-131">Zvažte například následující dva `sbyte` proměnné `x` a `y`:</span><span class="sxs-lookup"><span data-stu-id="32e9a-131">Consider, for example, the following two `sbyte` variables `x` and `y`:</span></span>  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 <span data-ttu-id="32e9a-132">Následující příkaz přiřazení bude k chybě kompilace vytvořit, protože výsledkem aritmetické výrazu na pravé straně operátoru přiřazení [int](../../../csharp/language-reference/keywords/int.md) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="32e9a-132">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 <span data-ttu-id="32e9a-133">Chcete-li tento problém vyřešit, přetypování výrazu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="32e9a-133">To fix this problem, cast the expression as in the following example:</span></span>  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 <span data-ttu-id="32e9a-134">Je ale možné použít následující příkazy, kde Cílová proměnná má stejnou velikost úložiště nebo větší velikost úložiště:</span><span class="sxs-lookup"><span data-stu-id="32e9a-134">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="32e9a-135">Všimněte si také, že neexistuje žádná implicitní převod z typů s plovoucí desetinnou čárkou na `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="32e9a-135">Notice also that there is no implicit conversion from floating-point types to `sbyte`.</span></span> <span data-ttu-id="32e9a-136">Například následující příkaz vygeneruje Chyba kompilátoru, pokud se používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="32e9a-136">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 <span data-ttu-id="32e9a-137">Informace o aritmetických výrazech s smíšený typy s plovoucí desetinnou čárkou a integrální typy najdete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [dvojité](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="32e9a-137">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="32e9a-138">Další informace o pravidlech implicitní převod číselného najdete v tématu [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="32e9a-138">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="32e9a-139">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="32e9a-139">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="32e9a-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="32e9a-140">See Also</span></span>  
 <xref:System.SByte>  
 [<span data-ttu-id="32e9a-141">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="32e9a-141">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="32e9a-142">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="32e9a-142">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="32e9a-143">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="32e9a-143">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="32e9a-144">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="32e9a-144">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="32e9a-145">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="32e9a-145">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="32e9a-146">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="32e9a-146">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="32e9a-147">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="32e9a-147">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
