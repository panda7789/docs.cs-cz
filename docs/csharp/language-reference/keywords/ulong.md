---
title: ulong (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
ms.openlocfilehash: 1f291d2dd2706231f018a04f0af86051cef6c28a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288304"
---
# <a name="ulong-c-reference"></a><span data-ttu-id="25236-102">ulong (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="25236-102">ulong (C# Reference)</span></span>

<span data-ttu-id="25236-103">`ulong` – Klíčové slovo označuje integrální typ, který ukládá hodnoty podle velikosti a rozsah uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="25236-103">The `ulong` keyword denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="25236-104">Typ</span><span class="sxs-lookup"><span data-stu-id="25236-104">Type</span></span>|<span data-ttu-id="25236-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="25236-105">Range</span></span>|<span data-ttu-id="25236-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="25236-106">Size</span></span>|<span data-ttu-id="25236-107">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="25236-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ulong`|<span data-ttu-id="25236-108">0 – 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="25236-108">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="25236-109">Celé číslo bez znaménka 64-bit</span><span class="sxs-lookup"><span data-stu-id="25236-109">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="25236-110">Literály</span><span class="sxs-lookup"><span data-stu-id="25236-110">Literals</span></span>  

<span data-ttu-id="25236-111">Můžete deklarace a inicializace `ulong` proměnné přiřazením decimal literál, hexadecimální literál, nebo (počínaje 7.0 C#) binární literálu do ní.</span><span class="sxs-lookup"><span data-stu-id="25236-111">You can declare and initialize a `ulong` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="25236-112">Pokud literálu celé číslo je mimo rozsah `ulong` (tj. Pokud je menší než <xref:System.UInt64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="25236-112">If the integer literal is outside the range of `ulong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="25236-113">V následujícím příkladu, celá čísla rovno 7,934,076,125, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `ulong` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="25236-113">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ulong` values.</span></span>  
  
[!code-csharp[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]  

> [!NOTE] 
> <span data-ttu-id="25236-114">Použijte předponu `0x` nebo `0X` k označení hexadecimální literál a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="25236-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="25236-115">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="25236-115">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="25236-116">Od verze jazyka C# 7.0, byly přidány několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="25236-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="25236-117">C# 7.0 umožňuje použití znak podtržítka `_`, jako oddělovač číslice.</span><span class="sxs-lookup"><span data-stu-id="25236-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="25236-118">C# 7.2 umožňuje `_` má být použit jako číslice oddělovače pro binární nebo hexadecimální literál, po předponu.</span><span class="sxs-lookup"><span data-stu-id="25236-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="25236-119">Decimal literál není povolená tak, aby měl úvodní podtržítka.</span><span class="sxs-lookup"><span data-stu-id="25236-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="25236-120">Níže jsou uvedeny některé příklady.</span><span class="sxs-lookup"><span data-stu-id="25236-120">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 <span data-ttu-id="25236-121">Literály celé číslo může obsahovat také příponu, která označuje typ.</span><span class="sxs-lookup"><span data-stu-id="25236-121">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="25236-122">Přípona `UL` nebo `ul` jednoznačně identifikuje jako číselný literál `ulong` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="25236-122">The suffix `UL` or `ul` unambiguously identifies a numeric literal as a `ulong` value.</span></span> <span data-ttu-id="25236-123">`L` Označuje příponu `ulong` literálovou hodnotou, překročí-li <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="25236-123">The `L` suffix denotes a `ulong` if the literal value exceeds <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="25236-124">A `U` nebo `u` označuje příponu `ulong` literálovou hodnotou, překročí-li <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="25236-124">And the `U` or `u` suffix denotes a `ulong` if the literal value exceeds <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="25236-125">Následující příklad používá `ul` příponu k označení dlouhých celých čísel:</span><span class="sxs-lookup"><span data-stu-id="25236-125">The following example uses the `ul` suffix to denote a long integer:</span></span>
 
[!code-csharp[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

<span data-ttu-id="25236-126">Pokud celé literál bez přípony, je její typ první z těchto typů, ve kterých může být reprezentován jeho hodnotu:</span><span class="sxs-lookup"><span data-stu-id="25236-126">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="25236-127">int</span><span class="sxs-lookup"><span data-stu-id="25236-127">int</span></span>](int.md)
2. [<span data-ttu-id="25236-128">uint</span><span class="sxs-lookup"><span data-stu-id="25236-128">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="25236-129">long</span><span class="sxs-lookup"><span data-stu-id="25236-129">long</span></span>](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a><span data-ttu-id="25236-130">Řešení přetížení kompilátoru</span><span class="sxs-lookup"><span data-stu-id="25236-130">Compiler overload resolution</span></span>
  
 <span data-ttu-id="25236-131">Běžně se používají přípona je s volání přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="25236-131">A common use of the suffix is with calling overloaded methods.</span></span> <span data-ttu-id="25236-132">Zvažte například následující přetížené metody, které používají `ulong` a [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="25236-132">Consider, for example, the following overloaded methods that use `ulong` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 <span data-ttu-id="25236-133">Pomocí přípony s `ulong` parametr zaručuje, že správný typ je volána, například:</span><span class="sxs-lookup"><span data-stu-id="25236-133">Using a suffix with the `ulong` parameter guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="25236-134">Převody</span><span class="sxs-lookup"><span data-stu-id="25236-134">Conversions</span></span>  
 <span data-ttu-id="25236-135">Je předdefinovaný implicitní převod z `ulong` k [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="25236-135">There is a predefined implicit conversion from `ulong` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="25236-136">Neexistuje žádný implicitní převod z `ulong` k libovolnému integrální typu.</span><span class="sxs-lookup"><span data-stu-id="25236-136">There is no implicit conversion from `ulong` to any integral type.</span></span> <span data-ttu-id="25236-137">Například následující příkaz vytvoří chybu kompilace bez explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="25236-137">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 <span data-ttu-id="25236-138">Je předdefinovaný implicitní převod z [bajtů](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), nebo [char](../../../csharp/language-reference/keywords/char.md) k `ulong`.</span><span class="sxs-lookup"><span data-stu-id="25236-138">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `ulong`.</span></span>  
  
 <span data-ttu-id="25236-139">Navíc není žádný implicitní převod z typů s plovoucí desetinnou čárkou na `ulong`.</span><span class="sxs-lookup"><span data-stu-id="25236-139">Also, there is no implicit conversion from floating-point types to `ulong`.</span></span> <span data-ttu-id="25236-140">Například následující příkaz vygeneruje Chyba kompilátoru, pokud se používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="25236-140">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 <span data-ttu-id="25236-141">Informace v aritmetických výrazech s smíšený typy s plovoucí desetinnou čárkou a integrální typy najdete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [dvojité](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="25236-141">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="25236-142">Další informace o implicitní číselný převod pravidel najdete v tématu [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="25236-142">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="25236-143">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="25236-143">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="25236-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="25236-144">See Also</span></span>  
 <xref:System.UInt64>  
 [<span data-ttu-id="25236-145">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="25236-145">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="25236-146">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="25236-146">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="25236-147">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="25236-147">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="25236-148">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="25236-148">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="25236-149">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="25236-149">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="25236-150">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="25236-150">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="25236-151">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="25236-151">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
