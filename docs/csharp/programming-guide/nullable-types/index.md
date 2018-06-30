---
title: Typy s povolenou hodnotou Null (Průvodce programováním v C#)
ms.date: 05/15/2017
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: 64b326b82cd022ed6590a232546690e2ec2a5c78
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105485"
---
# <a name="nullable-types-c-programming-guide"></a><span data-ttu-id="afb79-102">Typy s povolenou hodnotou Null (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="afb79-102">Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="afb79-103">Typy s možnou hodnotou Null jsou instancemi třídy <xref:System.Nullable%601?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="afb79-103">Nullable types are instances of the <xref:System.Nullable%601?displayProperty=nameWithType> struct.</span></span> <span data-ttu-id="afb79-104">Typ s možnou hodnotou Null může představovat správné rozsahu hodnot pro její základní typ hodnoty, plus další `null` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="afb79-104">A nullable type can represent the correct range of values for its underlying value type, plus an additional `null` value.</span></span> <span data-ttu-id="afb79-105">Například `Nullable<Int32>`, výrazný "S možnou hodnotou Null Int32," může být přiřazena libovolná hodnota od -2147483648 2147483647 nebo jej lze přiřadit `null` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="afb79-105">For example, a `Nullable<Int32>`, pronounced "Nullable of Int32," can be assigned any value from -2147483648 to 2147483647, or it can be assigned the `null` value.</span></span> <span data-ttu-id="afb79-106">A `Nullable<bool>` je možné přiřadit hodnoty [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), nebo [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="afb79-106">A `Nullable<bool>` can be assigned the values [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), or [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="afb79-107">Schopnost přidělit `null` na typy číselné a logická hodnota je obzvláště užitečná při pracujete s databází a jiné datové typy, které obsahují prvky, které nemusí být přiřazena hodnota.</span><span class="sxs-lookup"><span data-stu-id="afb79-107">The ability to assign `null` to numeric and Boolean types is especially useful when you are dealing with databases and other data types that contain elements that may not be assigned a value.</span></span> <span data-ttu-id="afb79-108">Například logické pole v databázi můžete ukládat hodnoty `true` nebo `false`, nebo to může být definovaný.</span><span class="sxs-lookup"><span data-stu-id="afb79-108">For example, a Boolean field in a database can store the values `true` or `false`, or it may be undefined.</span></span> 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
<span data-ttu-id="afb79-109">Další příklady najdete v tématu [pomocí typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span><span class="sxs-lookup"><span data-stu-id="afb79-109">For more examples, see [Using Nullable Types](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)</span></span>  
  
## <a name="nullable-types-overview"></a><span data-ttu-id="afb79-110">Přehled typů s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="afb79-110">Nullable Types Overview</span></span>  
 <span data-ttu-id="afb79-111">Typy s možnou hodnotou Null mít následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="afb79-111">Nullable types have the following characteristics:</span></span>  
  
-   <span data-ttu-id="afb79-112">Typy s možnou hodnotou Null představují typ hodnoty proměnné, které lze přiřadit hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="afb79-112">Nullable types represent value-type variables that can be assigned the value of `null`.</span></span> <span data-ttu-id="afb79-113">Nelze vytvořit typ s možnou hodnotou Null založený na typu odkaz.</span><span class="sxs-lookup"><span data-stu-id="afb79-113">You cannot create a nullable type based on a reference type.</span></span> <span data-ttu-id="afb79-114">(Referenční dokumentace typy již podporují `null` hodnotu.)</span><span class="sxs-lookup"><span data-stu-id="afb79-114">(Reference types already support the `null` value.)</span></span>  
  
-   <span data-ttu-id="afb79-115">Syntaxe `T?` je sdružená vlastnost <xref:System.Nullable%601>, kde `T` je typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="afb79-115">The syntax `T?` is shorthand for <xref:System.Nullable%601>, where `T` is a value type.</span></span> <span data-ttu-id="afb79-116">Jsou dva formuláře zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="afb79-116">The two forms are interchangeable.</span></span>  
  
-   <span data-ttu-id="afb79-117">Stejně jako obyčejnou hodnota typu, například přiřadit hodnotu Null typu `int? x = 10;` nebo `double? d = 4.108;`.</span><span class="sxs-lookup"><span data-stu-id="afb79-117">Assign a value to a nullable type just as you would for an ordinary value type, for example `int? x = 10;` or `double? d = 4.108;`.</span></span> <span data-ttu-id="afb79-118">Typ s možnou hodnotou Null lze také přiřadit hodnotu `null`: `int? x = null;`.</span><span class="sxs-lookup"><span data-stu-id="afb79-118">A nullable type can also be assigned the value `null`: `int? x = null;`.</span></span>  
  
-   <span data-ttu-id="afb79-119">Použití <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> metoda vrátí přiřazenou hodnotu nebo výchozí hodnota pro základní typ, pokud je hodnota `null`, například `int j = x.GetValueOrDefault();`</span><span class="sxs-lookup"><span data-stu-id="afb79-119">Use the <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> method to return either the assigned value, or the default value for the underlying type if the value is `null`, for example `int j = x.GetValueOrDefault();`</span></span>  
  
-   <span data-ttu-id="afb79-120">Použití <xref:System.Nullable%601.HasValue%2A> a <xref:System.Nullable%601.Value%2A> vlastnosti jen pro čtení k testování pro hodnotu null a načíst hodnotu, jak je znázorněno v následujícím příkladu: `if(x.HasValue) j = x.Value;`</span><span class="sxs-lookup"><span data-stu-id="afb79-120">Use the <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> read-only properties to test for null and retrieve the value, as shown in the following example: `if(x.HasValue) j = x.Value;`</span></span>  
  
    -   <span data-ttu-id="afb79-121">`HasValue` Vlastnost vrátí `true` Pokud proměnná obsahuje hodnotu, nebo `false` Pokud je `null`.</span><span class="sxs-lookup"><span data-stu-id="afb79-121">The `HasValue` property returns `true` if the variable contains a value, or `false` if it is `null`.</span></span>  
  
    -   <span data-ttu-id="afb79-122">`Value` Vlastnost vrací hodnotu, pokud jeden je přiřazen.</span><span class="sxs-lookup"><span data-stu-id="afb79-122">The `Value` property returns a value if one is assigned.</span></span> <span data-ttu-id="afb79-123">V opačném <xref:System.InvalidOperationException?displayProperty=nameWithType> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="afb79-123">Otherwise, a <xref:System.InvalidOperationException?displayProperty=nameWithType> is thrown.</span></span>  
  
    -   <span data-ttu-id="afb79-124">Výchozí hodnota pro `HasValue` je `false`.</span><span class="sxs-lookup"><span data-stu-id="afb79-124">The default value for `HasValue` is `false`.</span></span> <span data-ttu-id="afb79-125">`Value` Vlastnost nemá žádnou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="afb79-125">The `Value` property has no default value.</span></span>  
  
    -   <span data-ttu-id="afb79-126">Můžete také `==` a `!=` operátory s Null typu, jak je znázorněno v následujícím příkladu: `if (x != null) y = x;`</span><span class="sxs-lookup"><span data-stu-id="afb79-126">You can also use the `==` and `!=` operators with a nullable type, as shown in the following example: `if (x != null) y = x;`</span></span>  
  
-   <span data-ttu-id="afb79-127">Použití `??` operátor přiřadit výchozí hodnotu, která bude použita, pokud typu s povolenou hodnotou Null, jejíž aktuální hodnota je `null` se přiřadí k použití hodnot Null typu, například `int? x = null; int y = x ?? -1;`</span><span class="sxs-lookup"><span data-stu-id="afb79-127">Use the `??` operator to assign a default value that will be applied when a nullable type whose current value is `null` is assigned to a non-nullable type, for example `int? x = null; int y = x ?? -1;`</span></span>  
  
-   <span data-ttu-id="afb79-128">Vnořené typy s možnou hodnotou Null nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="afb79-128">Nested nullable types are not allowed.</span></span> <span data-ttu-id="afb79-129">Následující řádek nebude kompilace: `Nullable<Nullable<int>> n;`</span><span class="sxs-lookup"><span data-stu-id="afb79-129">The following line will not compile: `Nullable<Nullable<int>> n;`</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="afb79-130">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="afb79-130">Related Sections</span></span>  
 <span data-ttu-id="afb79-131">Další informace:</span><span class="sxs-lookup"><span data-stu-id="afb79-131">For more information:</span></span>  
  
-   [<span data-ttu-id="afb79-132">Použití typů s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="afb79-132">Using Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [<span data-ttu-id="afb79-133">Zabalení typů s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="afb79-133">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [<span data-ttu-id="afb79-134">?? – operátor</span><span class="sxs-lookup"><span data-stu-id="afb79-134">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="afb79-135">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="afb79-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="afb79-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="afb79-136">See Also</span></span>  
 <xref:System.Nullable>  
 [<span data-ttu-id="afb79-137">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="afb79-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="afb79-138">C#</span><span class="sxs-lookup"><span data-stu-id="afb79-138">C#</span></span>](../../../csharp/index.md)  
 [<span data-ttu-id="afb79-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="afb79-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="afb79-140">Co přesně 'zrušit' znamená?</span><span class="sxs-lookup"><span data-stu-id="afb79-140">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
