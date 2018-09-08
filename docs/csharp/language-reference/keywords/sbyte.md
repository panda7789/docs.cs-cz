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
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213790"
---
# <a name="sbyte-c-reference"></a><span data-ttu-id="a9d78-102">sbyte (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a9d78-102">sbyte (C# Reference)</span></span>

<span data-ttu-id="a9d78-103">`sbyte` označuje integrální typ, který uchovává hodnoty podle toho, velikost a rozsah je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a9d78-103">`sbyte` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="a9d78-104">Typ</span><span class="sxs-lookup"><span data-stu-id="a9d78-104">Type</span></span>|<span data-ttu-id="a9d78-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="a9d78-105">Range</span></span>|<span data-ttu-id="a9d78-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="a9d78-106">Size</span></span>|<span data-ttu-id="a9d78-107">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="a9d78-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|<span data-ttu-id="a9d78-108">-128 až 127</span><span class="sxs-lookup"><span data-stu-id="a9d78-108">-128 to 127</span></span>|<span data-ttu-id="a9d78-109">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="a9d78-109">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="a9d78-110">Literály</span><span class="sxs-lookup"><span data-stu-id="a9d78-110">Literals</span></span>  

<span data-ttu-id="a9d78-111">Můžete deklarovat a inicializovat `sbyte` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.</span><span class="sxs-lookup"><span data-stu-id="a9d78-111">You can declare and initialize an `sbyte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> 

<span data-ttu-id="a9d78-112">V následujícím příkladu celých čísel je rovno-102, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou převedeny z [int](../../../csharp/language-reference/keywords/int.md) k `sbyte` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a9d78-112">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are converted from [int](../../../csharp/language-reference/keywords/int.md) to `sbyte` values.</span></span>    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> <span data-ttu-id="a9d78-113">Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="a9d78-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="a9d78-114">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="a9d78-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="a9d78-115">Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="a9d78-115">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="a9d78-116">C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="a9d78-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="a9d78-117">C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu.</span><span class="sxs-lookup"><span data-stu-id="a9d78-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="a9d78-118">Desítkový literál není povoleno mít vedoucího podtržítka.</span><span class="sxs-lookup"><span data-stu-id="a9d78-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

 <span data-ttu-id="a9d78-119">Níže je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="a9d78-119">Some examples are shown below.</span></span>

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

<span data-ttu-id="a9d78-120">Pokud celočíselný literál je mimo rozsah `sbyte` (tj. Pokud je menší než <xref:System.SByte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.SByte.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="a9d78-120">If the integer literal is outside the range of `sbyte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="a9d78-121">Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnota: [int](int.md), [uint](uint.md), [dlouhé](long.md), [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="a9d78-121">When an integer literal has no suffix, its type is the first of these types in which its value can be represented: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span></span> <span data-ttu-id="a9d78-122">To znamená, že v tomto příkladu číselné literály `0x9A` a `0b10011010` jsou interpretovány jako 32bitová celá čísla se znaménkem s hodnotou 156, což překračuje <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a9d78-122">This means that, in this example, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a9d78-123">Z toho důvodu je potřeba operátor přetypování a přiřazení se musí vyskytovat v [Nekontrolovaná](unchecked.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="a9d78-123">Because of this, the casting operator is needed, and the assignment must occur in an [unchecked](unchecked.md) context.</span></span> 

## <a name="compiler-overload-resolution"></a><span data-ttu-id="a9d78-124">Řešení přetížení kompilátoru</span><span class="sxs-lookup"><span data-stu-id="a9d78-124">Compiler overload resolution</span></span>

 <span data-ttu-id="a9d78-125">Přetypování musí být použito při volání přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="a9d78-125">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="a9d78-126">Zvažte například následující přetížené metody, které používají `sbyte` a [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="a9d78-126">Consider, for example, the following overloaded methods that use `sbyte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 <span data-ttu-id="a9d78-127">Použití `sbyte` přetypování zaručuje, že správný typ název, například:</span><span class="sxs-lookup"><span data-stu-id="a9d78-127">Using the `sbyte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a><span data-ttu-id="a9d78-128">Převody</span><span class="sxs-lookup"><span data-stu-id="a9d78-128">Conversions</span></span>  
 <span data-ttu-id="a9d78-129">Není předdefinovanou implicitní převod z `sbyte` k [krátký](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [dlouhé](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double ](../../../csharp/language-reference/keywords/double.md), nebo [desítkové](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="a9d78-129">There is a predefined implicit conversion from `sbyte` to [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="a9d78-130">Nelze implicitně převést neliterální číselné typy větší velikosti úložiště `sbyte` (naleznete v tématu [integrální typy tabulky](../../../csharp/language-reference/keywords/integral-types-table.md) pro velikosti úložiště celočíselných typů).</span><span class="sxs-lookup"><span data-stu-id="a9d78-130">You cannot implicitly convert nonliteral numeric types of larger storage size to `sbyte` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="a9d78-131">Zvažte například následující dva `sbyte` proměnné `x` a `y`:</span><span class="sxs-lookup"><span data-stu-id="a9d78-131">Consider, for example, the following two `sbyte` variables `x` and `y`:</span></span>  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 <span data-ttu-id="a9d78-132">Přiřazovací příkaz způsobí chybu kompilace, protože aritmetický výraz na pravé straně operátoru přiřazení vyhodnotí jako [int](../../../csharp/language-reference/keywords/int.md) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="a9d78-132">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 <span data-ttu-id="a9d78-133">Chcete-li vyřešit tento problém, přetypování výrazu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a9d78-133">To fix this problem, cast the expression as in the following example:</span></span>  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 <span data-ttu-id="a9d78-134">Je ale možné použít následující příkazy, kde Cílová proměnná se stejnou velikostí úložiště nebo větší velikost úložiště:</span><span class="sxs-lookup"><span data-stu-id="a9d78-134">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="a9d78-135">Všimněte si také, že neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="a9d78-135">Notice also that there is no implicit conversion from floating-point types to `sbyte`.</span></span> <span data-ttu-id="a9d78-136">Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="a9d78-136">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 <span data-ttu-id="a9d78-137">Informace o aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="a9d78-137">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="a9d78-138">Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="a9d78-138">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a9d78-139">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a9d78-139">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a9d78-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9d78-140">See Also</span></span>

- <xref:System.SByte>  
- [<span data-ttu-id="a9d78-141">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a9d78-141">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a9d78-142">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a9d78-142">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a9d78-143">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a9d78-143">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="a9d78-144">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="a9d78-144">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="a9d78-145">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="a9d78-145">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="a9d78-146">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="a9d78-146">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="a9d78-147">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="a9d78-147">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
