---
title: "uint (Referenční dokumentace jazyka C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d32f7146d1f9e13d8cf0f275f4fd78b693b09d31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="uint-c-reference"></a><span data-ttu-id="2d308-102">uint (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2d308-102">uint (C# Reference)</span></span>

<span data-ttu-id="2d308-103">`uint` – Klíčové slovo označuje integrální typ, který ukládá hodnoty podle velikosti a rozsah uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="2d308-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="2d308-104">Typ</span><span class="sxs-lookup"><span data-stu-id="2d308-104">Type</span></span>|<span data-ttu-id="2d308-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2d308-105">Range</span></span>|<span data-ttu-id="2d308-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="2d308-106">Size</span></span>|<span data-ttu-id="2d308-107">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2d308-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`uint`|<span data-ttu-id="2d308-108">0 do 4 294 967 295</span><span class="sxs-lookup"><span data-stu-id="2d308-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="2d308-109">Celé číslo bez znaménka 32-bit</span><span class="sxs-lookup"><span data-stu-id="2d308-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
  
 <span data-ttu-id="2d308-110">**Poznámka:** `uint` typ není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="2d308-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="2d308-111">Použití `int` kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="2d308-111">Use `int` whenever possible.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="2d308-112">Literály</span><span class="sxs-lookup"><span data-stu-id="2d308-112">Literals</span></span>  

<span data-ttu-id="2d308-113">Můžete deklarace a inicializace `uint` proměnné přiřazením decimal literál, hexadecimální literál, nebo (počínaje C# 7) binární literálu do ní.</span><span class="sxs-lookup"><span data-stu-id="2d308-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="2d308-114">Pokud literálu celé číslo je mimo rozsah `uint` (tj. Pokud je menší než <xref:System.UInt32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="2d308-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="2d308-115">V následujícím příkladu, celá čísla rovno 3,000,000,000, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `uint` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2d308-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>  
  
[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]  

> [!NOTE] 
> <span data-ttu-id="2d308-116">Použijte předponu `0x` nebo `0X` k označení hexadecimální literál a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="2d308-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="2d308-117">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="2d308-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="2d308-118">Od verze jazyka C# 7, byly přidány několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="2d308-118">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="2d308-119">C# 7.0 umožňuje použití znak podtržítka `_`, jako oddělovač číslice.</span><span class="sxs-lookup"><span data-stu-id="2d308-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="2d308-120">C# 7.2 umožňuje `_` má být použit jako číslice oddělovače pro binární nebo hexadecimální literál, po předponu.</span><span class="sxs-lookup"><span data-stu-id="2d308-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="2d308-121">Decimal literál není povolená tak, aby měl úvodní podtržítka.</span><span class="sxs-lookup"><span data-stu-id="2d308-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="2d308-122">Níže jsou uvedeny některé příklady.</span><span class="sxs-lookup"><span data-stu-id="2d308-122">Some examples are shown below.</span></span>

[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]  
 
 <span data-ttu-id="2d308-123">Literály celé číslo může obsahovat také příponu, která označuje typ.</span><span class="sxs-lookup"><span data-stu-id="2d308-123">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="2d308-124">Přípona `U` nebo "u" označuje buď `uint` nebo `ulong`, v závislosti na hodnotě číselný literál.</span><span class="sxs-lookup"><span data-stu-id="2d308-124">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="2d308-125">Následující příklad používá `u` příponu k označení celé číslo bez znaménka obou typů.</span><span class="sxs-lookup"><span data-stu-id="2d308-125">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="2d308-126">Všimněte si, že je první literál `uint` protože její hodnota je menší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, zatímco druhý `ulong` vzhledem k tomu, že je jeho hodnota větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d308-126">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

[!code-csharp[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]  
 
<span data-ttu-id="2d308-127">Pokud celé literál bez přípony, je její typ první z těchto typů, ve kterých může být reprezentován jeho hodnotu:</span><span class="sxs-lookup"><span data-stu-id="2d308-127">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="2d308-128">celá čísla</span><span class="sxs-lookup"><span data-stu-id="2d308-128">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="2d308-129">dlouhá</span><span class="sxs-lookup"><span data-stu-id="2d308-129">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="2d308-130">ulong –</span><span class="sxs-lookup"><span data-stu-id="2d308-130">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a><span data-ttu-id="2d308-131">Převody</span><span class="sxs-lookup"><span data-stu-id="2d308-131">Conversions</span></span>  
 <span data-ttu-id="2d308-132">Je předdefinovaný implicitní převod z `uint` k [dlouho](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [ Decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="2d308-132">There is a predefined implicit conversion from `uint` to [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="2d308-133">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2d308-133">For example:</span></span>  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 <span data-ttu-id="2d308-134">Je předdefinovaný implicitní převod z [bajtů](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), nebo [char](../../../csharp/language-reference/keywords/char.md) k `uint`.</span><span class="sxs-lookup"><span data-stu-id="2d308-134">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `uint`.</span></span> <span data-ttu-id="2d308-135">V opačném případě je nutné použít přetypování.</span><span class="sxs-lookup"><span data-stu-id="2d308-135">Otherwise you must use a cast.</span></span> <span data-ttu-id="2d308-136">Například následující příkaz přiřazení způsobí chybu kompilace bez přetypování:</span><span class="sxs-lookup"><span data-stu-id="2d308-136">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 <span data-ttu-id="2d308-137">Všimněte si také, že neexistuje žádná implicitní převod z typů s plovoucí desetinnou čárkou na `uint`.</span><span class="sxs-lookup"><span data-stu-id="2d308-137">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="2d308-138">Například následující příkaz vygeneruje Chyba kompilátoru, pokud se používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="2d308-138">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 <span data-ttu-id="2d308-139">Informace o aritmetických výrazech s smíšený typy s plovoucí desetinnou čárkou a integrální typy najdete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [dvojité](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="2d308-139">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="2d308-140">Další informace o pravidlech implicitní převod číselného najdete v tématu [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="2d308-140">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2d308-141">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d308-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2d308-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d308-142">See Also</span></span>  
 <xref:System.UInt32>  
 [<span data-ttu-id="2d308-143">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d308-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2d308-144">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="2d308-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2d308-145">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d308-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2d308-146">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="2d308-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="2d308-147">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="2d308-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="2d308-148">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="2d308-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="2d308-149">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="2d308-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
