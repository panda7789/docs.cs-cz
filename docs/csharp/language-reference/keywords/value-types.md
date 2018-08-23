---
title: Typy hodnot (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 17bbb0280c4db7d91e5d3cc3d3b6233b8db89cdc
ms.sourcegitcommit: bd4fa78f5a46133efdead1bc692a9aa2811d7868
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2018
ms.locfileid: "42754966"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="88e5a-102">Typy hodnot (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="88e5a-102">Value Types (C# Reference)</span></span>
<span data-ttu-id="88e5a-103">Typy hodnot se skládá ze dvou hlavních kategorií:</span><span class="sxs-lookup"><span data-stu-id="88e5a-103">The value types consist of two main categories:</span></span>  
  
-   [<span data-ttu-id="88e5a-104">Struktury</span><span class="sxs-lookup"><span data-stu-id="88e5a-104">Structs</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="88e5a-105">Výčty</span><span class="sxs-lookup"><span data-stu-id="88e5a-105">Enumerations</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
 <span data-ttu-id="88e5a-106">Struktury spadá do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="88e5a-106">Structs fall into these categories:</span></span>  
  
-   <span data-ttu-id="88e5a-107">Číselné typy</span><span class="sxs-lookup"><span data-stu-id="88e5a-107">Numeric types</span></span>  
  
    -   [<span data-ttu-id="88e5a-108">Celočíselné typy</span><span class="sxs-lookup"><span data-stu-id="88e5a-108">Integral types</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [<span data-ttu-id="88e5a-109">Typy s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="88e5a-109">Floating-point types</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
-   [<span data-ttu-id="88e5a-110">bool</span><span class="sxs-lookup"><span data-stu-id="88e5a-110">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)  
  
-   <span data-ttu-id="88e5a-111">Struktury definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="88e5a-111">User defined structs.</span></span>  
  
## <a name="main-features-of-value-types"></a><span data-ttu-id="88e5a-112">Hlavní funkce typů hodnot</span><span class="sxs-lookup"><span data-stu-id="88e5a-112">Main Features of Value Types</span></span>  
 <span data-ttu-id="88e5a-113">Proměnné, které jsou založené na hodnotách přímo obsahovat hodnoty.</span><span class="sxs-lookup"><span data-stu-id="88e5a-113">Variables that are based on value types directly contain values.</span></span> <span data-ttu-id="88e5a-114">Přiřazení jednu proměnnou typu hodnoty na jiné kopie omezením hodnoty.</span><span class="sxs-lookup"><span data-stu-id="88e5a-114">Assigning one value type variable to another copies the contained value.</span></span> <span data-ttu-id="88e5a-115">Tím se liší od přiřazení proměnné referenčního typu, který zkopíruje odkaz na objekt, ale nikoli samotného objektu.</span><span class="sxs-lookup"><span data-stu-id="88e5a-115">This differs from the assignment of reference type variables, which copies a reference to the object but not the object itself.</span></span>  
  
 <span data-ttu-id="88e5a-116">Všechny hodnotové typy jsou implicitně odvozena z <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="88e5a-116">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="88e5a-117">Na rozdíl od v případě typů odkazu nelze odvodit nový typ z typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="88e5a-117">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="88e5a-118">Nicméně, jako jsou typy odkazů, struktury mohou implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="88e5a-118">However, like reference types, structs can implement interfaces.</span></span>  
  
 <span data-ttu-id="88e5a-119">Na rozdíl od typy odkazů, nemůže obsahovat typ hodnoty `null` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="88e5a-119">Unlike reference types, a value type cannot contain the `null` value.</span></span> <span data-ttu-id="88e5a-120">Ale [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md) funkci povolit pro typy hodnot má být přiřazena k `null`.</span><span class="sxs-lookup"><span data-stu-id="88e5a-120">However, the [nullable types](../../../csharp/programming-guide/nullable-types/index.md) feature does allow for value types to be assigned to `null`.</span></span>  
  
 <span data-ttu-id="88e5a-121">Každý hodnotový typ má implicitní výchozí konstruktor, který inicializuje výchozí hodnota tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="88e5a-121">Each value type has an implicit default constructor that initializes the default value of that type.</span></span> <span data-ttu-id="88e5a-122">Informace o výchozí hodnoty typů hodnot najdete v tématu [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="88e5a-122">For information about default values of value types, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="main-features-of-simple-types"></a><span data-ttu-id="88e5a-123">Hlavní funkce jednoduché typy</span><span class="sxs-lookup"><span data-stu-id="88e5a-123">Main Features of Simple Types</span></span>  
 <span data-ttu-id="88e5a-124">Některé jednoduché typy – tyto celé číslo na jazyk C# – jsou aliasy typů rozhraní .NET Framework System.</span><span class="sxs-lookup"><span data-stu-id="88e5a-124">All of the simple types -- those integral to the C# language -- are aliases of the .NET Framework System types.</span></span> <span data-ttu-id="88e5a-125">Například [int](../../../csharp/language-reference/keywords/int.md) je alias pro <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="88e5a-125">For example, [int](../../../csharp/language-reference/keywords/int.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="88e5a-126">Úplný seznam aliasů naleznete v tématu [tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="88e5a-126">For a complete list of aliases, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span>  
  
 <span data-ttu-id="88e5a-127">Konstantní výrazy, jehož operandy jsou všechny jednoduchý typ konstanty, jsou vyhodnocovány v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="88e5a-127">Constant expressions, whose operands are all simple type constants, are evaluated at compilation time.</span></span>  
  
 <span data-ttu-id="88e5a-128">Jednoduché typy může být inicializována pomocí literálů.</span><span class="sxs-lookup"><span data-stu-id="88e5a-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="88e5a-129">Například "A" je literál typu `char` a 2001 je literál typu `int`.</span><span class="sxs-lookup"><span data-stu-id="88e5a-129">For example, 'A' is a literal of the type `char` and 2001 is a literal of the type `int`.</span></span>  
  
## <a name="initializing-value-types"></a><span data-ttu-id="88e5a-130">Inicializace typů hodnot</span><span class="sxs-lookup"><span data-stu-id="88e5a-130">Initializing Value Types</span></span>  
 <span data-ttu-id="88e5a-131">Lokální proměnné v jazyce C# musí být inicializován před jejich použití.</span><span class="sxs-lookup"><span data-stu-id="88e5a-131">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="88e5a-132">Například může prohlásit místní proměnné bez inicializace jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="88e5a-132">For example, you might declare a local variable without initialization as in the following example:</span></span>  
  
```csharp  
int myInt;  
```  
  
 <span data-ttu-id="88e5a-133">Nelze ji použít předtím, než ji inicializovat.</span><span class="sxs-lookup"><span data-stu-id="88e5a-133">You cannot use it before you initialize it.</span></span> <span data-ttu-id="88e5a-134">Můžete inicializovat pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="88e5a-134">You can initialize it using the following statement:</span></span>  
  
```csharp  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 <span data-ttu-id="88e5a-135">Tento příkaz je ekvivalentem následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="88e5a-135">This statement is equivalent to the following statement:</span></span>  
  
```csharp  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 <span data-ttu-id="88e5a-136">Můžete samozřejmě máte deklaraci a inicializaci ve stejném příkazu jako v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="88e5a-136">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>  
  
```csharp  
int myInt = new int();  
```  
  
 <span data-ttu-id="88e5a-137">– nebo –</span><span class="sxs-lookup"><span data-stu-id="88e5a-137">–or–</span></span>  
  
```csharp  
int myInt = 0;  
```  
  
 <span data-ttu-id="88e5a-138">Použití [nové](../../../csharp/language-reference/keywords/new.md) operátor volá výchozí konstruktor třídy určitého typu a přiřadí výchozí hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="88e5a-138">Using the [new](../../../csharp/language-reference/keywords/new.md) operator calls the default constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="88e5a-139">V předchozím příkladu, výchozí konstruktor přiřazena hodnota `0` k `myInt`.</span><span class="sxs-lookup"><span data-stu-id="88e5a-139">In the preceding example, the default constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="88e5a-140">Další informace o hodnoty přiřazené voláním výchozí konstruktory, naleznete v tématu [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="88e5a-140">For more information about values assigned by calling default constructors, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="88e5a-141">Pomocí uživatelem definované typy [nové](../../../csharp/language-reference/keywords/new.md) k vyvolání výchozího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="88e5a-141">With user-defined types, use [new](../../../csharp/language-reference/keywords/new.md) to invoke the default constructor.</span></span> <span data-ttu-id="88e5a-142">Například následující příkaz volá výchozí konstruktor třídy `Point` struktury:</span><span class="sxs-lookup"><span data-stu-id="88e5a-142">For example, the following statement invokes the default constructor of the `Point` struct:</span></span>  
  
```csharp  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 <span data-ttu-id="88e5a-143">Po tomto volání struktury považuje je jednoznačně přiřazovat; To znamená všech jejích členů jsou inicializovány na výchozích hodnotách.</span><span class="sxs-lookup"><span data-stu-id="88e5a-143">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>  
  
 <span data-ttu-id="88e5a-144">Další informace o operátoru new najdete v tématu [nové](../../../csharp/language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="88e5a-144">For more information about the new operator, see [new](../../../csharp/language-reference/keywords/new.md).</span></span>  
  
 <span data-ttu-id="88e5a-145">Informace o formátování výstupu číselné typy najdete v tématu [tabulka formátování číselných výsledků](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="88e5a-145">For information about formatting the output of numeric types, see [Formatting Numeric Results Table](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e5a-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="88e5a-146">See Also</span></span>  
 [<span data-ttu-id="88e5a-147">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88e5a-147">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="88e5a-148">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="88e5a-148">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="88e5a-149">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88e5a-149">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="88e5a-150">Typy</span><span class="sxs-lookup"><span data-stu-id="88e5a-150">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="88e5a-151">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="88e5a-151">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [<span data-ttu-id="88e5a-152">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="88e5a-152">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="88e5a-153">Typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="88e5a-153">Nullable types</span></span>](../../programming-guide/nullable-types/index.md)  
