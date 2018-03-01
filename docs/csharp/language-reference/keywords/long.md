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
# <a name="long-c-reference"></a><span data-ttu-id="ff547-102">long (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ff547-102">long (C# Reference)</span></span>

<span data-ttu-id="ff547-103">`long`označuje typ integrální, který ukládá hodnoty podle velikosti a rozsah uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ff547-103">`long` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="ff547-104">Typ</span><span class="sxs-lookup"><span data-stu-id="ff547-104">Type</span></span>|<span data-ttu-id="ff547-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ff547-105">Range</span></span>|<span data-ttu-id="ff547-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="ff547-106">Size</span></span>|<span data-ttu-id="ff547-107">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ff547-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`long`|<span data-ttu-id="ff547-108">-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="ff547-108">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="ff547-109">64bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="ff547-109">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="ff547-110">Literály</span><span class="sxs-lookup"><span data-stu-id="ff547-110">Literals</span></span> 

<span data-ttu-id="ff547-111">Můžete deklarace a inicializace `long` proměnné přiřazením decimal literál, hexadecimální literál, nebo (počínaje C# 7) binární literálu do ní.</span><span class="sxs-lookup"><span data-stu-id="ff547-111">You can declare and initialize a `long` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> 

<span data-ttu-id="ff547-112">V následujícím příkladu, celá čísla rovno 4 294 967 296 jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `long` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ff547-112">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `long` values.</span></span>  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> <span data-ttu-id="ff547-113">Použijte předponu `0x` nebo `0X` k označení hexadecimální literál a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="ff547-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="ff547-114">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="ff547-114">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="ff547-115">Od verze jazyka C# 7, byly přidány několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="ff547-115">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="ff547-116">C# 7.0 umožňuje použití znak podtržítka `_`, jako oddělovač číslice.</span><span class="sxs-lookup"><span data-stu-id="ff547-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="ff547-117">C# 7.2 umožňuje `_` má být použit jako číslice oddělovače pro binární nebo hexadecimální literál, po předponu.</span><span class="sxs-lookup"><span data-stu-id="ff547-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="ff547-118">Decimal literál není povolená tak, aby měl úvodní podtržítka.</span><span class="sxs-lookup"><span data-stu-id="ff547-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="ff547-119">Níže jsou uvedeny některé příklady.</span><span class="sxs-lookup"><span data-stu-id="ff547-119">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 <span data-ttu-id="ff547-120">Literály celé číslo může obsahovat také příponu, která označuje typ.</span><span class="sxs-lookup"><span data-stu-id="ff547-120">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="ff547-121">Přípona `L` označuje `long`.</span><span class="sxs-lookup"><span data-stu-id="ff547-121">The suffix `L` denotes a `long`.</span></span> <span data-ttu-id="ff547-122">Následující příklad používá `L` příponu k označení dlouhých celých čísel:</span><span class="sxs-lookup"><span data-stu-id="ff547-122">The following example uses the `L` suffix to denote a long integer:</span></span>
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  <span data-ttu-id="ff547-123">Můžete taky malé písmeno "l" jako příponu.</span><span class="sxs-lookup"><span data-stu-id="ff547-123">You can also use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="ff547-124">Ale tím se vygeneruje upozornění kompilátoru protože písmeno "l" je snadno zaměnit s číslice "1".</span><span class="sxs-lookup"><span data-stu-id="ff547-124">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="ff547-125">Pro přehlednost použijte "L".</span><span class="sxs-lookup"><span data-stu-id="ff547-125">Use "L" for clarity.</span></span>  
  
 <span data-ttu-id="ff547-126">Když použijete tuto příponu `L`, typ literálu celého čísla, je určen být buď `long` nebo [ulong](../../../csharp/language-reference/keywords/ulong.md), v závislosti na jeho velikost.</span><span class="sxs-lookup"><span data-stu-id="ff547-126">When you use the suffix `L`, the type of the literal integer is determined to be either `long` or [ulong](../../../csharp/language-reference/keywords/ulong.md), depending on its size.</span></span> <span data-ttu-id="ff547-127">V takovém případě je `long` protože je menší než rozsah [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="ff547-127">In this case, it is `long` because it less than the range of [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="ff547-128">Běžně se používají přípona je volání přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="ff547-128">A common use of the suffix is to call overloaded methods.</span></span> <span data-ttu-id="ff547-129">Například následující přetížené metody mít parametry typu `long` a [int](../../../csharp/language-reference/keywords/int.md):</span><span class="sxs-lookup"><span data-stu-id="ff547-129">For example, the following overloaded methods have parameters of type `long` and [int](../../../csharp/language-reference/keywords/int.md):</span></span>  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 <span data-ttu-id="ff547-130">`L` Příponu zaručuje, že správné přetížení nazývá:</span><span class="sxs-lookup"><span data-stu-id="ff547-130">The `L` suffix guarantees that the correct overload is called:</span></span>  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
<span data-ttu-id="ff547-131">Pokud celé literál bez přípony, je její typ první z těchto typů, ve kterých může být reprezentován jeho hodnotu:</span><span class="sxs-lookup"><span data-stu-id="ff547-131">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="ff547-132">celá čísla</span><span class="sxs-lookup"><span data-stu-id="ff547-132">int</span></span>](int.md)
2. [<span data-ttu-id="ff547-133">uint</span><span class="sxs-lookup"><span data-stu-id="ff547-133">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [<span data-ttu-id="ff547-134">ulong –</span><span class="sxs-lookup"><span data-stu-id="ff547-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 

<span data-ttu-id="ff547-135">Literál 4294967296 v předchozích příkladech je typu `long`, protože překračuje rozsah [Celé_číslo](../../../csharp/language-reference/keywords/uint.md) (viz [tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md) velikostí úložiště celočíselných typů).</span><span class="sxs-lookup"><span data-stu-id="ff547-135">The literal 4294967296 in the previous examples is of type `long`, because it exceeds the range of [uint](../../../csharp/language-reference/keywords/uint.md) (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span>  
  
 <span data-ttu-id="ff547-136">Pokud použijete `long` je typ s jinými integrální typy ve stejném výrazu výraz vyhodnocen jako `long` (nebo [bool](../../../csharp/language-reference/keywords/bool.md) v případě výrazy relační nebo logická hodnota).</span><span class="sxs-lookup"><span data-stu-id="ff547-136">If you use the `long` type with other integral types in the same expression, the expression is evaluated as `long` (or [bool](../../../csharp/language-reference/keywords/bool.md) in the case of relational or Boolean expressions).</span></span> <span data-ttu-id="ff547-137">Například následující výraz vyhodnotí jako `long`:</span><span class="sxs-lookup"><span data-stu-id="ff547-137">For example, the following expression evaluates as `long`:</span></span>  
  
```csharp  
898L + 88  
```  
  
 <span data-ttu-id="ff547-138">Informace v aritmetických výrazech s smíšený typy s plovoucí desetinnou čárkou a integrální typy najdete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [dvojité](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="ff547-138">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="ff547-139">Převody</span><span class="sxs-lookup"><span data-stu-id="ff547-139">Conversions</span></span>  
 <span data-ttu-id="ff547-140">Je předdefinovaný implicitní převod z `long` k [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="ff547-140">There is a predefined implicit conversion from `long` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="ff547-141">V opačném případě je nutné použít přetypování.</span><span class="sxs-lookup"><span data-stu-id="ff547-141">Otherwise a cast must be used.</span></span> <span data-ttu-id="ff547-142">Například následující příkaz vytvoří chybu kompilace bez explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="ff547-142">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 <span data-ttu-id="ff547-143">Je předdefinovaný implicitní převod z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtů](../../../csharp/language-reference/keywords/byte.md), [krátké](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), nebo [char](../../../csharp/language-reference/keywords/char.md) k `long`.</span><span class="sxs-lookup"><span data-stu-id="ff547-143">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `long`.</span></span>  
  
 <span data-ttu-id="ff547-144">Všimněte si také, že neexistuje žádná implicitní převod z typů s plovoucí desetinnou čárkou na `long`.</span><span class="sxs-lookup"><span data-stu-id="ff547-144">Notice also that there is no implicit conversion from floating-point types to `long`.</span></span> <span data-ttu-id="ff547-145">Například následující příkaz vygeneruje Chyba kompilátoru, pokud se používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="ff547-145">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="ff547-146">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ff547-146">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ff547-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff547-147">See Also</span></span>  
 <xref:System.Int64>  
 [<span data-ttu-id="ff547-148">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ff547-148">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ff547-149">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ff547-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ff547-150">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ff547-150">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ff547-151">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="ff547-151">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="ff547-152">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="ff547-152">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="ff547-153">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="ff547-153">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="ff547-154">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="ff547-154">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
