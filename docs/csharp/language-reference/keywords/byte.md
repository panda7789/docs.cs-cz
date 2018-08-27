---
title: byte (Referenční dokumentace jazyka C#)
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: 28acbe67b85637550fdb1f5e290a9abb60bf5c65
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42908238"
---
# <a name="byte-c-reference"></a><span data-ttu-id="3b643-102">byte (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3b643-102">byte (C# Reference)</span></span>

<span data-ttu-id="3b643-103">`byte` označuje integrální typ, který ukládá hodnoty, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="3b643-103">`byte` denotes an integral type that stores values as indicated in the following table.</span></span>  
  
|<span data-ttu-id="3b643-104">Typ</span><span class="sxs-lookup"><span data-stu-id="3b643-104">Type</span></span>|<span data-ttu-id="3b643-105">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3b643-105">Range</span></span>|<span data-ttu-id="3b643-106">Velikost</span><span class="sxs-lookup"><span data-stu-id="3b643-106">Size</span></span>|<span data-ttu-id="3b643-107">Typ formátu .NET</span><span class="sxs-lookup"><span data-stu-id="3b643-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`byte`|<span data-ttu-id="3b643-108">0 až 255</span><span class="sxs-lookup"><span data-stu-id="3b643-108">0 to 255</span></span>|<span data-ttu-id="3b643-109">Celé číslo bez znaménka 8 bitů</span><span class="sxs-lookup"><span data-stu-id="3b643-109">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="3b643-110">Literály</span><span class="sxs-lookup"><span data-stu-id="3b643-110">Literals</span></span>  

 <span data-ttu-id="3b643-111">Můžete deklarovat a inicializovat `byte` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.</span><span class="sxs-lookup"><span data-stu-id="3b643-111">You can declare and initialize a `byte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="3b643-112">Pokud celočíselný literál je mimo rozsah `byte` (tj. Pokud je menší než <xref:System.Byte.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Byte.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="3b643-112">If the integer literal is outside the range of `byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="3b643-113">V následujícím příkladu celých čísel je rovno 201, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [int](../../../csharp/language-reference/keywords/int.md) k `byte` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3b643-113">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `byte` values.</span></span>    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> <span data-ttu-id="3b643-114">Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál.</span><span class="sxs-lookup"><span data-stu-id="3b643-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="3b643-115">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="3b643-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="3b643-116">Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti.</span><span class="sxs-lookup"><span data-stu-id="3b643-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="3b643-117">C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.</span><span class="sxs-lookup"><span data-stu-id="3b643-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="3b643-118">C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu.</span><span class="sxs-lookup"><span data-stu-id="3b643-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="3b643-119">Desítkový literál není povoleno mít vedoucího podtržítka.</span><span class="sxs-lookup"><span data-stu-id="3b643-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="3b643-120">Níže je uvedeno několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="3b643-120">Some examples are shown below.</span></span>

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a><span data-ttu-id="3b643-121">Převody</span><span class="sxs-lookup"><span data-stu-id="3b643-121">Conversions</span></span>  
 <span data-ttu-id="3b643-122">Není předdefinovanou implicitní převod z `byte` k [krátký](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [dlouhý ](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), nebo [desítkové](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="3b643-122">There is a predefined implicit conversion from `byte` to [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="3b643-123">Nelze implicitně převést číselné typy literálu větší velikosti úložiště `byte`.</span><span class="sxs-lookup"><span data-stu-id="3b643-123">You cannot implicitly convert non-literal numeric types of larger storage size to `byte`.</span></span> <span data-ttu-id="3b643-124">Další informace o velikosti úložiště celočíselných typů naleznete v tématu [integrální typy tabulky](../../../csharp/language-reference/keywords/integral-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="3b643-124">For more information on the storage sizes of integral types, see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md).</span></span> <span data-ttu-id="3b643-125">Zvažte například následující dva `byte` proměnné `x` a `y`:</span><span class="sxs-lookup"><span data-stu-id="3b643-125">Consider, for example, the following two `byte` variables `x` and `y`:</span></span>  
  
```csharp  
byte x = 10, y = 20;  
```  
  
 <span data-ttu-id="3b643-126">Přiřazovací příkaz způsobí chybu kompilace, protože aritmetický výraz na pravé straně operátoru přiřazení vyhodnotí jako `int` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="3b643-126">The following assignment statement will produce a compilation error, because the arithmetic expression on the right-hand side of the assignment operator evaluates to `int` by default.</span></span>  
  
```csharp  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 <span data-ttu-id="3b643-127">Pokud chcete tento problém vyřešit, použijte přetypování:</span><span class="sxs-lookup"><span data-stu-id="3b643-127">To fix this problem, use a cast:</span></span>  
  
```csharp  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 <span data-ttu-id="3b643-128">Je ale možné použít následující příkazy, kde Cílová proměnná se stejnou velikostí úložiště nebo větší velikost úložiště:</span><span class="sxs-lookup"><span data-stu-id="3b643-128">It is possible though, to use the following statements where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="3b643-129">Také, neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `byte`.</span><span class="sxs-lookup"><span data-stu-id="3b643-129">Also, there is no implicit conversion from floating-point types to `byte`.</span></span> <span data-ttu-id="3b643-130">Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:</span><span class="sxs-lookup"><span data-stu-id="3b643-130">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 <span data-ttu-id="3b643-131">Při volání přetížené metody, musíte použít přetypování.</span><span class="sxs-lookup"><span data-stu-id="3b643-131">When calling overloaded methods, a cast must be used.</span></span> <span data-ttu-id="3b643-132">Zvažte například následující přetížené metody, které používají `byte` a [int](../../../csharp/language-reference/keywords/int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="3b643-132">Consider, for example, the following overloaded methods that use `byte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 <span data-ttu-id="3b643-133">Použití `byte` přetypování zaručuje, že správný typ název, například:</span><span class="sxs-lookup"><span data-stu-id="3b643-133">Using the `byte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 <span data-ttu-id="3b643-134">Informace v aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="3b643-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="3b643-135">Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="3b643-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3b643-136">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3b643-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3b643-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b643-137">See Also</span></span>  
 <xref:System.Byte>  
 [<span data-ttu-id="3b643-138">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3b643-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3b643-139">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3b643-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3b643-140">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3b643-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3b643-141">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="3b643-141">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="3b643-142">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="3b643-142">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="3b643-143">Tabulka implicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="3b643-143">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="3b643-144">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="3b643-144">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
