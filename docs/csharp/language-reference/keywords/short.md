---
title: "short (Referenční dokumentace jazyka C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8ca3c5444c4fa7a49b7169be3e2a5b15d1a72207
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="short-c-reference"></a><span data-ttu-id="c6066-102">short (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c6066-102">short (C# Reference)</span></span>

<span data-ttu-id="c6066-103">`short`označuje celočíselný datový typ, který ukládá hodnoty podle velikosti a rozsah uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="c6066-103">`short` denotes an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="c6066-104">Typ</span><span class="sxs-lookup"><span data-stu-id="c6066-104">Type</span></span>|<span data-ttu-id="c6066-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c6066-105">Range</span></span>|<span data-ttu-id="c6066-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="c6066-106">Size</span></span>|<span data-ttu-id="c6066-107">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c6066-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`short`|<span data-ttu-id="c6066-108">-32 768 do 32 767</span><span class="sxs-lookup"><span data-stu-id="c6066-108">-32,768 to 32,767</span></span>|<span data-ttu-id="c6066-109">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="c6066-109">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="c6066-110">Literály</span><span class="sxs-lookup"><span data-stu-id="c6066-110">Literals</span></span>  

<span data-ttu-id="c6066-111">Můžete deklarace a inicializace `short` proměnné přiřazením decimal literál, hexadecimální literál, nebo (počínaje C# 7) binární literálu do ní.</span><span class="sxs-lookup"><span data-stu-id="c6066-111">You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="c6066-112">Pokud literálu celé číslo je mimo rozsah `short` (tj. Pokud je menší než <xref:System.Int16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int16.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="c6066-112">If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="c6066-113">V následujícím příkladu, celá čísla rovno 1,034, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou implicitně převést z [int](../../../csharp/language-reference/keywords/int.md) k `short` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c6066-113">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `short` values.</span></span>  
  
[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> <span data-ttu-id="c6066-114">Použijte předponu `0x` nebo `0X` k označení hexadecimální literál a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="c6066-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="c6066-115">Decimal literály mít žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="c6066-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="c6066-116">Od verze jazyka C# 7, byly přidány několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="c6066-116">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="c6066-117">C# 7.0 umožňuje použití znak podtržítka `_`, jako oddělovač číslice.</span><span class="sxs-lookup"><span data-stu-id="c6066-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="c6066-118">C# 7.2 umožňuje `_` má být použit jako číslice oddělovače pro binární nebo hexadecimální literál, po předponu.</span><span class="sxs-lookup"><span data-stu-id="c6066-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="c6066-119">Decimal literál není povolená tak, aby měl úvodní podtržítka.</span><span class="sxs-lookup"><span data-stu-id="c6066-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="c6066-120">Níže jsou uvedeny některé příklady.</span><span class="sxs-lookup"><span data-stu-id="c6066-120">Some examples are shown below.</span></span>

[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="c6066-121">Řešení přetížení kompilátoru</span><span class="sxs-lookup"><span data-stu-id="c6066-121">Compiler overload resolution</span></span>

 <span data-ttu-id="c6066-122">Při volání přetížené metody se musí použít přetypování.</span><span class="sxs-lookup"><span data-stu-id="c6066-122">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="c6066-123">Zvažte například následující přetížené metody, které používají `short` a [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="c6066-123">Consider, for example, the following overloaded methods that use `short` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 <span data-ttu-id="c6066-124">Pomocí `short` přetypování zaručuje, že správný typ je volána, například:</span><span class="sxs-lookup"><span data-stu-id="c6066-124">Using the `short` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="c6066-125">Převody</span><span class="sxs-lookup"><span data-stu-id="c6066-125">Conversions</span></span>  

 <span data-ttu-id="c6066-126">Je předdefinovaný implicitní převod z `short` k [int](../../../csharp/language-reference/keywords/int.md), [dlouho](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), nebo [ Decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="c6066-126">There is a predefined implicit conversion from `short` to [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="c6066-127">Nelze implicitně převést nonliteral číselnými typy větší velikost úložiště na `short` (viz [tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md) velikostí úložiště celočíselných typů).</span><span class="sxs-lookup"><span data-stu-id="c6066-127">You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="c6066-128">Zvažte například následující dva `short` proměnné `x` a `y`:</span><span class="sxs-lookup"><span data-stu-id="c6066-128">Consider, for example, the following two `short` variables `x` and `y`:</span></span>  
  
```csharp  
short x = 5, y = 12;  
```  
  
 <span data-ttu-id="c6066-129">Následující příkaz přiřazení vytvoří chybu kompilace, protože výsledkem aritmetické výrazu na pravé straně operátoru přiřazení [int](../../../csharp/language-reference/keywords/int.md) ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c6066-129">The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 <span data-ttu-id="c6066-130">Chcete-li tento problém vyřešit, použijte přetypování:</span><span class="sxs-lookup"><span data-stu-id="c6066-130">To fix this problem, use a cast:</span></span>  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 <span data-ttu-id="c6066-131">Je také možné použít následující příkazy, kde Cílová proměnná má stejnou velikost úložiště nebo větší velikost úložiště:</span><span class="sxs-lookup"><span data-stu-id="c6066-131">It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="c6066-132">Neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou na `short`.</span><span class="sxs-lookup"><span data-stu-id="c6066-132">There is no implicit conversion from floating-point types to `short`.</span></span> <span data-ttu-id="c6066-133">Například následující příkaz vygeneruje Chyba kompilátoru, pokud se používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="c6066-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 <span data-ttu-id="c6066-134">Informace v aritmetických výrazech s smíšený typy s plovoucí desetinnou čárkou a integrální typy najdete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [dvojité](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="c6066-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="c6066-135">Další informace o implicitní číselný převod pravidel najdete v tématu [implicitní číselné převody tabulky](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="c6066-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c6066-136">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c6066-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c6066-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6066-137">See Also</span></span>  
 <xref:System.Int16>  
 [<span data-ttu-id="c6066-138">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c6066-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c6066-139">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c6066-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c6066-140">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c6066-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c6066-141">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="c6066-141">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="c6066-142">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="c6066-142">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="c6066-143">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="c6066-143">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="c6066-144">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="c6066-144">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
