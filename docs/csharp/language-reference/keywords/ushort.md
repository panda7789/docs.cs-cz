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
ms.locfileid: "33288821"
---
# <a name="ushort-c-reference"></a><span data-ttu-id="4d886-102">ushort (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4d886-102">ushort (C# Reference)</span></span>

<span data-ttu-id="4d886-103">`ushort` – Klíčové slovo označuje celočíselný datový typ, který ukládá hodnoty podle velikosti a rozsah uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="4d886-103">The `ushort` keyword indicates an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="4d886-104">Typ</span><span class="sxs-lookup"><span data-stu-id="4d886-104">Type</span></span>|<span data-ttu-id="4d886-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4d886-105">Range</span></span>|<span data-ttu-id="4d886-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="4d886-106">Size</span></span>|<span data-ttu-id="4d886-107">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4d886-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ushort`|<span data-ttu-id="4d886-108">0 až 65 535</span><span class="sxs-lookup"><span data-stu-id="4d886-108">0 to 65,535</span></span>|<span data-ttu-id="4d886-109">Nepodepsané 16bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="4d886-109">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="4d886-110">Literály</span><span class="sxs-lookup"><span data-stu-id="4d886-110">Literals</span></span>  

<span data-ttu-id="4d886-111">Můžete deklarace a inicializace `ushort` proměnné přiřazením decimal literál, hexadecimální literál, nebo (počínaje 7.0 C#) binární literálu do ní.</span><span class="sxs-lookup"><span data-stu-id="4d886-111">You can declare and initialize a `ushort` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="4d886-112">Pokud literálu celé číslo je mimo rozsah `ushort` (tj. Pokud je menší než <xref:System.UInt16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="4d886-112">If the integer literal is outside the range of `ushort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="4d886-113">V následujícím příkladu, celá čísla rovno 65,034, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou implicitně převést z [int](../../../csharp/language-reference/keywords/int.md) k `ushort` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4d886-113">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `ushort` values.</span></span>    
  
[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> <span data-ttu-id="4d886-114">Použijte předponu `0x` nebo `0X` k označení hexadecimální literál a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="4d886-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="4d886-115">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="4d886-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="4d886-116">Od verze jazyka C# 7.0, byly přidány několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="4d886-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="4d886-117">C# 7.0 umožňuje použití znak podtržítka `_`, jako oddělovač číslice.</span><span class="sxs-lookup"><span data-stu-id="4d886-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="4d886-118">C# 7.2 umožňuje `_` má být použit jako číslice oddělovače pro binární nebo hexadecimální literál, po předponu.</span><span class="sxs-lookup"><span data-stu-id="4d886-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="4d886-119">Decimal literál není povolená tak, aby měl úvodní podtržítka.</span><span class="sxs-lookup"><span data-stu-id="4d886-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="4d886-120">Níže jsou uvedeny některé příklady.</span><span class="sxs-lookup"><span data-stu-id="4d886-120">Some examples are shown below.</span></span>

[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="4d886-121">Řešení přetížení kompilátoru</span><span class="sxs-lookup"><span data-stu-id="4d886-121">Compiler overload resolution</span></span>
  
 <span data-ttu-id="4d886-122">Při volání přetížené metody se musí použít přetypování.</span><span class="sxs-lookup"><span data-stu-id="4d886-122">A cast must be used when you call overloaded methods.</span></span> <span data-ttu-id="4d886-123">Zvažte například následující přetížené metody, které používají `ushort` a [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="4d886-123">Consider, for example, the following overloaded methods that use `ushort` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 <span data-ttu-id="4d886-124">Pomocí `ushort` přetypování zaručuje, že správný typ je volána, například:</span><span class="sxs-lookup"><span data-stu-id="4d886-124">Using the `ushort` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a><span data-ttu-id="4d886-125">Převody</span><span class="sxs-lookup"><span data-stu-id="4d886-125">Conversions</span></span>  
 <span data-ttu-id="4d886-126">Je předdefinovaný implicitní převod z `ushort` k [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [dlouho](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float ](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="4d886-126">There is a predefined implicit conversion from `ushort` to [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="4d886-127">Je předdefinovaný implicitní převod z [bajtů](../../../csharp/language-reference/keywords/byte.md) nebo [char](../../../csharp/language-reference/keywords/char.md) k `ushort`.</span><span class="sxs-lookup"><span data-stu-id="4d886-127">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md) or [char](../../../csharp/language-reference/keywords/char.md) to `ushort`.</span></span> <span data-ttu-id="4d886-128">V opačném případě musí být přetypování použít k provedení explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="4d886-128">Otherwise a cast must be used to perform an explicit conversion.</span></span> <span data-ttu-id="4d886-129">Zvažte například následující dva `ushort` proměnné `x` a `y`:</span><span class="sxs-lookup"><span data-stu-id="4d886-129">Consider, for example, the following two `ushort` variables `x` and `y`:</span></span>  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 <span data-ttu-id="4d886-130">Následující příkaz přiřazení bude k chybě kompilace vytvořit, protože výsledkem aritmetické výrazu na pravé straně operátoru přiřazení `int` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="4d886-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to `int` by default.</span></span>  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 <span data-ttu-id="4d886-131">Chcete-li tento problém vyřešit, použijte přetypování:</span><span class="sxs-lookup"><span data-stu-id="4d886-131">To fix this problem, use a cast:</span></span>  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 <span data-ttu-id="4d886-132">Je ale možné použít následující příkazy, kde Cílová proměnná má stejnou velikost úložiště nebo větší velikost úložiště:</span><span class="sxs-lookup"><span data-stu-id="4d886-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="4d886-133">Všimněte si také, že neexistuje žádná implicitní převod z typů s plovoucí desetinnou čárkou na `ushort`.</span><span class="sxs-lookup"><span data-stu-id="4d886-133">Notice also that there is no implicit conversion from floating-point types to `ushort`.</span></span> <span data-ttu-id="4d886-134">Například následující příkaz vygeneruje Chyba kompilátoru, pokud se používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="4d886-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 <span data-ttu-id="4d886-135">Informace o aritmetických výrazech s smíšený typy s plovoucí desetinnou čárkou a integrální typy najdete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [dvojité](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="4d886-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="4d886-136">Další informace o pravidlech implicitní převod číselného najdete v tématu [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="4d886-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4d886-137">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4d886-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4d886-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d886-138">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="4d886-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4d886-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4d886-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4d886-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4d886-141">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4d886-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4d886-142">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="4d886-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="4d886-143">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="4d886-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="4d886-144">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="4d886-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="4d886-145">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="4d886-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
