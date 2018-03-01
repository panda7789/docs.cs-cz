---
title: "Typy hodnot (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 281b811f2a8a1f2c364405b563f9f103899b492c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="value-types-c-reference"></a><span data-ttu-id="a97ca-102">Typy hodnot (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a97ca-102">Value Types (C# Reference)</span></span>
<span data-ttu-id="a97ca-103">Typy hodnot se skládá ze dvou hlavních kategorií:</span><span class="sxs-lookup"><span data-stu-id="a97ca-103">The value types consist of two main categories:</span></span>  
  
-   [<span data-ttu-id="a97ca-104">Struktury</span><span class="sxs-lookup"><span data-stu-id="a97ca-104">Structs</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="a97ca-105">Výčty</span><span class="sxs-lookup"><span data-stu-id="a97ca-105">Enumerations</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
 <span data-ttu-id="a97ca-106">Struktury spadá do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="a97ca-106">Structs fall into these categories:</span></span>  
  
-   <span data-ttu-id="a97ca-107">Číselné typy</span><span class="sxs-lookup"><span data-stu-id="a97ca-107">Numeric types</span></span>  
  
    -   [<span data-ttu-id="a97ca-108">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="a97ca-108">Integral types</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [<span data-ttu-id="a97ca-109">Typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="a97ca-109">Floating-point types</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [<span data-ttu-id="a97ca-110">Decimal</span><span class="sxs-lookup"><span data-stu-id="a97ca-110">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [<span data-ttu-id="a97ca-111">BOOL</span><span class="sxs-lookup"><span data-stu-id="a97ca-111">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)  
  
-   <span data-ttu-id="a97ca-112">Struktury definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="a97ca-112">User defined structs.</span></span>  
  
## <a name="main-features-of-value-types"></a><span data-ttu-id="a97ca-113">Hlavní funkce typů hodnot</span><span class="sxs-lookup"><span data-stu-id="a97ca-113">Main Features of Value Types</span></span>  
 <span data-ttu-id="a97ca-114">Proměnné, které jsou založeny na typy hodnot přímo obsahovat hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a97ca-114">Variables that are based on value types directly contain values.</span></span> <span data-ttu-id="a97ca-115">Přiřazení jednu proměnnou zadejte hodnotu do jiné kopie obsažené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a97ca-115">Assigning one value type variable to another copies the contained value.</span></span> <span data-ttu-id="a97ca-116">To se liší od přiřazení odkaz na typ proměnné, která zkopíruje odkaz na objekt, ale ne samotný objekt.</span><span class="sxs-lookup"><span data-stu-id="a97ca-116">This differs from the assignment of reference type variables, which copies a reference to the object but not the object itself.</span></span>  
  
 <span data-ttu-id="a97ca-117">Všechny typy hodnot implicitně odvozena z <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a97ca-117">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="a97ca-118">Na rozdíl od pro odkazové typy, nemůže být nový typ odvozený od typu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a97ca-118">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="a97ca-119">Odkazové typy, ale jako struktury můžete implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a97ca-119">However, like reference types, structs can implement interfaces.</span></span>  
  
 <span data-ttu-id="a97ca-120">Na rozdíl od odkazové typy nemohou obsahovat typ hodnoty `null` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a97ca-120">Unlike reference types, a value type cannot contain the `null` value.</span></span> <span data-ttu-id="a97ca-121">Ale [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md) funkce povolit u typů hodnot pro přiřazení ke `null`.</span><span class="sxs-lookup"><span data-stu-id="a97ca-121">However, the [nullable types](../../../csharp/programming-guide/nullable-types/index.md) feature does allow for value types to be assigned to `null`.</span></span>  
  
 <span data-ttu-id="a97ca-122">Každý typ hodnota má implicitní výchozí konstruktor, který inicializuje výchozí hodnota tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="a97ca-122">Each value type has an implicit default constructor that initializes the default value of that type.</span></span> <span data-ttu-id="a97ca-123">Informace o výchozí hodnoty typů hodnot najdete v tématu [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="a97ca-123">For information about default values of value types, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="main-features-of-simple-types"></a><span data-ttu-id="a97ca-124">Hlavní funkce jednoduché typy</span><span class="sxs-lookup"><span data-stu-id="a97ca-124">Main Features of Simple Types</span></span>  
 <span data-ttu-id="a97ca-125">Všechny jednoduché typy – tyto celé číslo na jazyka C# – jsou aliasy typy rozhraní .NET Framework systému.</span><span class="sxs-lookup"><span data-stu-id="a97ca-125">All of the simple types -- those integral to the C# language -- are aliases of the .NET Framework System types.</span></span> <span data-ttu-id="a97ca-126">Například [int](../../../csharp/language-reference/keywords/int.md) je zástupce <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a97ca-126">For example, [int](../../../csharp/language-reference/keywords/int.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a97ca-127">Úplný seznam aliasy, najdete v části [tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="a97ca-127">For a complete list of aliases, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span>  
  
 <span data-ttu-id="a97ca-128">Výrazy konstant, jejichž operandy jsou všechny jednoduchý typ konstanty, jsou vyhodnocovány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a97ca-128">Constant expressions, whose operands are all simple type constants, are evaluated at compilation time.</span></span>  
  
 <span data-ttu-id="a97ca-129">Jednoduché typy lze inicializovat pomocí literály.</span><span class="sxs-lookup"><span data-stu-id="a97ca-129">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="a97ca-130">Například "A" je literál typu `char` a 2001 je literál typu `int`.</span><span class="sxs-lookup"><span data-stu-id="a97ca-130">For example, 'A' is a literal of the type `char` and 2001 is a literal of the type `int`.</span></span>  
  
## <a name="initializing-value-types"></a><span data-ttu-id="a97ca-131">Inicializace typů hodnot</span><span class="sxs-lookup"><span data-stu-id="a97ca-131">Initializing Value Types</span></span>  
 <span data-ttu-id="a97ca-132">Před použitím je nutné inicializovat místní proměnné v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="a97ca-132">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="a97ca-133">Například může deklarovat místní proměnné bez inicializace jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a97ca-133">For example, you might declare a local variable without initialization as in the following example:</span></span>  
  
```  
int myInt;  
```  
  
 <span data-ttu-id="a97ca-134">Předtím, než je inicializovat nemůžete ji použít.</span><span class="sxs-lookup"><span data-stu-id="a97ca-134">You cannot use it before you initialize it.</span></span> <span data-ttu-id="a97ca-135">Můžete inicializovat pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="a97ca-135">You can initialize it using the following statement:</span></span>  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 <span data-ttu-id="a97ca-136">Tento příkaz je ekvivalentní následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="a97ca-136">This statement is equivalent to the following statement:</span></span>  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 <span data-ttu-id="a97ca-137">V příkazu stejné jako v následujících příkladech můžou mít samozřejmě deklaraci a inicializace:</span><span class="sxs-lookup"><span data-stu-id="a97ca-137">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>  
  
```  
int myInt = new int();  
```  
  
 <span data-ttu-id="a97ca-138">– nebo –</span><span class="sxs-lookup"><span data-stu-id="a97ca-138">–or–</span></span>  
  
```  
int myInt = 0;  
```  
  
 <span data-ttu-id="a97ca-139">Pomocí [nové](../../../csharp/language-reference/keywords/new.md) operátor volání výchozí konstruktor z konkrétního typu a přiřadí výchozí hodnota proměnné.</span><span class="sxs-lookup"><span data-stu-id="a97ca-139">Using the [new](../../../csharp/language-reference/keywords/new.md) operator calls the default constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="a97ca-140">V předchozím příkladu výchozí konstruktor přiřazenu hodnotu `0` k `myInt`.</span><span class="sxs-lookup"><span data-stu-id="a97ca-140">In the preceding example, the default constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="a97ca-141">Další informace o přiřazených voláním výchozí konstruktory hodnot najdete v tématu [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="a97ca-141">For more information about values assigned by calling default constructors, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="a97ca-142">Uživatelem definované typy využít [nové](../../../csharp/language-reference/keywords/new.md) volat výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="a97ca-142">With user-defined types, use [new](../../../csharp/language-reference/keywords/new.md) to invoke the default constructor.</span></span> <span data-ttu-id="a97ca-143">Například následující příkaz volá výchozí konstruktor z `Point` struktura:</span><span class="sxs-lookup"><span data-stu-id="a97ca-143">For example, the following statement invokes the default constructor of the `Point` struct:</span></span>  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 <span data-ttu-id="a97ca-144">Po toto volání se považuje struct výborný přiřadit; To znamená, že všichni její členové jsou inicializovány na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a97ca-144">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>  
  
 <span data-ttu-id="a97ca-145">Další informace o operátor new najdete v tématu [nové](../../../csharp/language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="a97ca-145">For more information about the new operator, see [new](../../../csharp/language-reference/keywords/new.md).</span></span>  
  
 <span data-ttu-id="a97ca-146">Informace o Formátovaní výstupu číselnými typy najdete v tématu [formátování číselných výsledků tabulky](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="a97ca-146">For information about formatting the output of numeric types, see [Formatting Numeric Results Table](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a97ca-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="a97ca-147">See Also</span></span>  
 [<span data-ttu-id="a97ca-148">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a97ca-148">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a97ca-149">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a97ca-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a97ca-150">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a97ca-150">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a97ca-151">Typy</span><span class="sxs-lookup"><span data-stu-id="a97ca-151">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="a97ca-152">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="a97ca-152">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [<span data-ttu-id="a97ca-153">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="a97ca-153">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)
