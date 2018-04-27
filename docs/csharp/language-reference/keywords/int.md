---
title: int (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f3e82dd195252a8c55e4ba7b18b657b341553047
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="int-c-reference"></a><span data-ttu-id="af1b1-102">int (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="af1b1-102">int (C# Reference)</span></span>

<span data-ttu-id="af1b1-103">`int` označuje typ integrální, který ukládá hodnoty podle velikosti a rozsah uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="af1b1-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="af1b1-104">Typ</span><span class="sxs-lookup"><span data-stu-id="af1b1-104">Type</span></span>|<span data-ttu-id="af1b1-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="af1b1-105">Range</span></span>|<span data-ttu-id="af1b1-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="af1b1-106">Size</span></span>|<span data-ttu-id="af1b1-107">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="af1b1-107">.NET Framework type</span></span>|<span data-ttu-id="af1b1-108">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="af1b1-108">Default Value</span></span>|  
|----------|-----------|----------|-------------------------|-------------------|  
|`int`|<span data-ttu-id="af1b1-109">-2 147 483 648 na 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="af1b1-109">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="af1b1-110">32bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="af1b1-110">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="af1b1-111">0</span><span class="sxs-lookup"><span data-stu-id="af1b1-111">0</span></span>|  
  
## <a name="literals"></a><span data-ttu-id="af1b1-112">Literály</span><span class="sxs-lookup"><span data-stu-id="af1b1-112">Literals</span></span>  
 
<span data-ttu-id="af1b1-113">Můžete deklarace a inicializace `int` proměnné přiřazením decimal literál, hexadecimální literál, nebo (počínaje 7.0 C#) binární literálu do ní.</span><span class="sxs-lookup"><span data-stu-id="af1b1-113">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="af1b1-114">Pokud literálu celé číslo je mimo rozsah `int` (tj. Pokud je menší než <xref:System.Int32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="af1b1-114">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="af1b1-115">V následujícím příkladu, celá čísla rovno 90,946, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `int` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="af1b1-115">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> <span data-ttu-id="af1b1-116">Použijte předponu `0x` nebo `0X` k označení hexadecimální literál a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="af1b1-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="af1b1-117">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="af1b1-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="af1b1-118">Od verze jazyka C# 7.0, byly přidány několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="af1b1-118">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="af1b1-119">C# 7.0 umožňuje použití znak podtržítka `_`, jako oddělovač číslice.</span><span class="sxs-lookup"><span data-stu-id="af1b1-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="af1b1-120">C# 7.2 umožňuje `_` má být použit jako číslice oddělovače pro binární nebo hexadecimální literál, po předponu.</span><span class="sxs-lookup"><span data-stu-id="af1b1-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="af1b1-121">Decimal literál není povolená tak, aby měl úvodní podtržítka.</span><span class="sxs-lookup"><span data-stu-id="af1b1-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="af1b1-122">Níže jsou uvedeny některé příklady.</span><span class="sxs-lookup"><span data-stu-id="af1b1-122">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 <span data-ttu-id="af1b1-123">Literály celé číslo může obsahovat také příponu, která označuje typ, i když neexistuje žádné příponu, která označuje `int` typu.</span><span class="sxs-lookup"><span data-stu-id="af1b1-123">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="af1b1-124">Pokud celé literál bez přípony, je její typ první z těchto typů, ve kterých může být reprezentován jeho hodnotu:</span><span class="sxs-lookup"><span data-stu-id="af1b1-124">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="af1b1-125">uint</span><span class="sxs-lookup"><span data-stu-id="af1b1-125">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="af1b1-126">long</span><span class="sxs-lookup"><span data-stu-id="af1b1-126">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="af1b1-127">ulong</span><span class="sxs-lookup"><span data-stu-id="af1b1-127">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="af1b1-128">V těchto příkladech je literál 90946 typu `int`.</span><span class="sxs-lookup"><span data-stu-id="af1b1-128">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="af1b1-129">Převody</span><span class="sxs-lookup"><span data-stu-id="af1b1-129">Conversions</span></span>  
 <span data-ttu-id="af1b1-130">Je předdefinovaný implicitní převod z `int` k [dlouho](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="af1b1-130">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="af1b1-131">Příklad:</span><span class="sxs-lookup"><span data-stu-id="af1b1-131">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="af1b1-132">Je předdefinovaný implicitní převod z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtů](../../../csharp/language-reference/keywords/byte.md), [krátké](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), nebo [char](../../../csharp/language-reference/keywords/char.md) k `int`.</span><span class="sxs-lookup"><span data-stu-id="af1b1-132">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="af1b1-133">Například následující příkaz přiřazení způsobí chybu kompilace bez přetypování:</span><span class="sxs-lookup"><span data-stu-id="af1b1-133">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="af1b1-134">Všimněte si také, že neexistuje žádná implicitní převod z typů s plovoucí desetinnou čárkou na `int`.</span><span class="sxs-lookup"><span data-stu-id="af1b1-134">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="af1b1-135">Například následující příkaz vygeneruje Chyba kompilátoru, pokud se používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="af1b1-135">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="af1b1-136">Další informace o aritmetických výrazech s smíšený typy s plovoucí desetinnou čárkou a integrální typy najdete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [dvojité](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="af1b1-136">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="af1b1-137">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="af1b1-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="af1b1-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="af1b1-138">See Also</span></span>  
 <xref:System.Int32>  
 [<span data-ttu-id="af1b1-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="af1b1-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="af1b1-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="af1b1-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="af1b1-141">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="af1b1-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="af1b1-142">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="af1b1-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="af1b1-143">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="af1b1-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="af1b1-144">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="af1b1-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="af1b1-145">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="af1b1-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
