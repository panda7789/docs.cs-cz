---
title: int (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
ms.openlocfilehash: 95ac267bc70d2e7873593c08e0b10cb50fefd8c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524041"
---
# <a name="int-c-reference"></a><span data-ttu-id="41894-102">int (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="41894-102">int (C# Reference)</span></span>

<span data-ttu-id="41894-103">`int` označuje integrální typ, který uchovává hodnoty podle toho, velikost a rozsah je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="41894-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="41894-104">Typ</span><span class="sxs-lookup"><span data-stu-id="41894-104">Type</span></span>|<span data-ttu-id="41894-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="41894-105">Range</span></span>|<span data-ttu-id="41894-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="41894-106">Size</span></span>|<span data-ttu-id="41894-107">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="41894-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`int`|<span data-ttu-id="41894-108">-2 147 483 648 do 2 147 483 647</span><span class="sxs-lookup"><span data-stu-id="41894-108">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="41894-109">32bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="41894-109">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="41894-110">Literály</span><span class="sxs-lookup"><span data-stu-id="41894-110">Literals</span></span>  
 
<span data-ttu-id="41894-111">Můžete deklarovat a inicializovat `int` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.</span><span class="sxs-lookup"><span data-stu-id="41894-111">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="41894-112">Pokud celočíselný literál je mimo rozsah `int` (tj. Pokud je menší než <xref:System.Int32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="41894-112">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="41894-113">V následujícím příkladu celých čísel je rovno 90,946, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `int` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="41894-113">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> <span data-ttu-id="41894-114">Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="41894-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="41894-115">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="41894-115">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="41894-116">Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="41894-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="41894-117">C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="41894-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="41894-118">C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu.</span><span class="sxs-lookup"><span data-stu-id="41894-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="41894-119">Desítkový literál není povoleno mít vedoucího podtržítka.</span><span class="sxs-lookup"><span data-stu-id="41894-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="41894-120">Níže je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="41894-120">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 <span data-ttu-id="41894-121">Literály celých čísel může také obsahovat příponu, která označuje typ., ačkoli neexistuje žádné příponu, která označuje `int` typu.</span><span class="sxs-lookup"><span data-stu-id="41894-121">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="41894-122">Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnotu:</span><span class="sxs-lookup"><span data-stu-id="41894-122">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="41894-123">uint</span><span class="sxs-lookup"><span data-stu-id="41894-123">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="41894-124">long</span><span class="sxs-lookup"><span data-stu-id="41894-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="41894-125">ulong</span><span class="sxs-lookup"><span data-stu-id="41894-125">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="41894-126">V těchto příkladech je literál 90946 typu `int`.</span><span class="sxs-lookup"><span data-stu-id="41894-126">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="41894-127">Převody</span><span class="sxs-lookup"><span data-stu-id="41894-127">Conversions</span></span>  
 <span data-ttu-id="41894-128">Není předdefinovanou implicitní převod z `int` k [dlouhé](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), nebo [desítkové](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="41894-128">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="41894-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="41894-129">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="41894-130">Není předdefinovanou implicitní převod z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtů](../../../csharp/language-reference/keywords/byte.md), [krátký](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), nebo [char](../../../csharp/language-reference/keywords/char.md) k `int`.</span><span class="sxs-lookup"><span data-stu-id="41894-130">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="41894-131">Přiřazovací příkaz například způsobí chybu kompilace bez přetypování:</span><span class="sxs-lookup"><span data-stu-id="41894-131">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="41894-132">Všimněte si také, že neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `int`.</span><span class="sxs-lookup"><span data-stu-id="41894-132">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="41894-133">Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="41894-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="41894-134">Další informace o aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="41894-134">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="41894-135">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="41894-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="41894-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="41894-136">See Also</span></span>

- <xref:System.Int32>  
- [<span data-ttu-id="41894-137">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="41894-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="41894-138">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="41894-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="41894-139">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="41894-139">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="41894-140">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="41894-140">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="41894-141">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="41894-141">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="41894-142">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="41894-142">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="41894-143">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="41894-143">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
