---
title: dynamic (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
ms.openlocfilehash: 840ecd6ab929b00e1be96c23eb06ccf362380f8e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140356"
---
# <a name="dynamic-c-reference"></a><span data-ttu-id="5b727-102">dynamic (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5b727-102">dynamic (C# Reference)</span></span>

<span data-ttu-id="5b727-103">`dynamic` Typ umožní operace, ve kterých se vyskytuje obejít kontrolu typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="5b727-103">The `dynamic` type enables the operations in which it occurs to bypass compile-time type checking.</span></span> <span data-ttu-id="5b727-104">Tyto operace jsou místo toho přeložit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="5b727-104">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="5b727-105">`dynamic` Typ zjednodušuje přístup k rozhraní API modelu COM, jako je například rozhraní API automatizace sady Office a taky dynamické rozhraní API, jako jsou knihovny Ironpythonu a do HTML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="5b727-105">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, and also to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="5b727-106">Typ `dynamic` se chová jako typ `object` ve většině případů.</span><span class="sxs-lookup"><span data-stu-id="5b727-106">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="5b727-107">Nicméně operace, které obsahují výrazy typu `dynamic` nevyřešených nebo typ zaškrtnutí kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="5b727-107">However, operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="5b727-108">Čas spuštění kompilátoru balíčky, které společně informace o operaci a tyto informace se později používá k vyhodnocení operaci.</span><span class="sxs-lookup"><span data-stu-id="5b727-108">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="5b727-109">Jako součást procesu proměnné typu `dynamic` jsou kompilovány do proměnné typu `object`.</span><span class="sxs-lookup"><span data-stu-id="5b727-109">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="5b727-110">Proto zadejte `dynamic` existuje pouze v době kompilace, ne za běhu.</span><span class="sxs-lookup"><span data-stu-id="5b727-110">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="5b727-111">V následujícím příkladu se liší od proměnné typu `dynamic` na proměnnou typu `object`.</span><span class="sxs-lookup"><span data-stu-id="5b727-111">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="5b727-112">Ověření typu každou proměnnou v době kompilace, umístěte ukazatel myši nad `dyn` nebo `obj` v `WriteLine` příkazy.</span><span class="sxs-lookup"><span data-stu-id="5b727-112">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="5b727-113">Technologie IntelliSense zobrazuje **dynamické** pro `dyn` a **objekt** pro `obj`.</span><span class="sxs-lookup"><span data-stu-id="5b727-113">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="5b727-114">`WriteLine` Příkazy zobrazuje typy za běhu `dyn` a `obj`.</span><span class="sxs-lookup"><span data-stu-id="5b727-114">The `WriteLine` statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="5b727-115">V tomto okamžiku mají stejný typ celé číslo.</span><span class="sxs-lookup"><span data-stu-id="5b727-115">At that point, both have the same type, integer.</span></span> <span data-ttu-id="5b727-116">Následující výstup je vytvořen:</span><span class="sxs-lookup"><span data-stu-id="5b727-116">The following output is produced:</span></span>

`System.Int32`

`System.Int32`

<span data-ttu-id="5b727-117">Pokud chcete zobrazit rozdíl mezi `dyn` a `obj` v době kompilace, přidejte následující dva řádky mezi prohlášení a `WriteLine` příkazů v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5b727-117">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="5b727-118">Chyba kompilátoru hlášené pro pokus o přidání celého čísla a objekt ve výrazu `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="5b727-118">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="5b727-119">Však žádná chybová zpráva pro `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="5b727-119">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="5b727-120">Výraz, který obsahuje `dyn` nepovolenou v době kompilace, protože typ `dyn` je `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="5b727-120">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

## <a name="context"></a><span data-ttu-id="5b727-121">Kontext</span><span class="sxs-lookup"><span data-stu-id="5b727-121">Context</span></span>

<span data-ttu-id="5b727-122">`dynamic` – Klíčové slovo se může objevit přímo, nebo jako součást sady konstruovaný typ v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="5b727-122">The `dynamic` keyword can appear directly or as a component of a constructed type in the following situations:</span></span>

- <span data-ttu-id="5b727-123">V deklaracích jako typ vlastnosti, pole, indexovací člen, parametr návratová hodnota místní proměnné nebo omezení typu.</span><span class="sxs-lookup"><span data-stu-id="5b727-123">In declarations, as the type of a property, field, indexer, parameter, return value, local variable, or type constraint.</span></span> <span data-ttu-id="5b727-124">Následující třídy definice používá `dynamic` v několika různých deklaracích.</span><span class="sxs-lookup"><span data-stu-id="5b727-124">The following class definition uses `dynamic` in several different declarations.</span></span>

    [!code-csharp[csrefKeywordsTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#22)]

- <span data-ttu-id="5b727-125">V explicitní převody typu, jako cílový typ převodu.</span><span class="sxs-lookup"><span data-stu-id="5b727-125">In explicit type conversions, as the target type of a conversion.</span></span>

    [!code-csharp[csrefKeywordsTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#23)]

- <span data-ttu-id="5b727-126">V libovolném kontextu, ve kterém se typy sloužit jako hodnoty, například na pravé straně `is` operátor nebo `as` operátor nebo jako argument `typeof` konstruovaný typ v rámci.</span><span class="sxs-lookup"><span data-stu-id="5b727-126">In any context where types serve as values, such as on the right side of an `is` operator or an `as` operator, or as the argument to `typeof` as part of a constructed type.</span></span> <span data-ttu-id="5b727-127">Například `dynamic` lze použít v těchto výrazů.</span><span class="sxs-lookup"><span data-stu-id="5b727-127">For example, `dynamic` can be used in the following expressions.</span></span>

    [!code-csharp[csrefKeywordsTypes#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#24)]

## <a name="example"></a><span data-ttu-id="5b727-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b727-128">Example</span></span>

<span data-ttu-id="5b727-129">Následující příklad používá `dynamic` v několika deklarace.</span><span class="sxs-lookup"><span data-stu-id="5b727-129">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="5b727-130">`Main` Metoda se také liší od typu v době kompilace kontroly s kontrolu typu za běhu.</span><span class="sxs-lookup"><span data-stu-id="5b727-130">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

<span data-ttu-id="5b727-131">Další informace a příklady najdete v tématu [použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="5b727-131">For more information and examples, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b727-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b727-132">See also</span></span>

- <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>  
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
- [<span data-ttu-id="5b727-133">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="5b727-133">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [<span data-ttu-id="5b727-134">object</span><span class="sxs-lookup"><span data-stu-id="5b727-134">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
- [<span data-ttu-id="5b727-135">is</span><span class="sxs-lookup"><span data-stu-id="5b727-135">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="5b727-136">as</span><span class="sxs-lookup"><span data-stu-id="5b727-136">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
- [<span data-ttu-id="5b727-137">typeof</span><span class="sxs-lookup"><span data-stu-id="5b727-137">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
- [<span data-ttu-id="5b727-138">Postupy: bezpečné přetypování pomocí porovnávání vzorů, jako například operátorů a is</span><span class="sxs-lookup"><span data-stu-id="5b727-138">How to: Safely cast Using pattern matching, as, and is Operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)  
- [<span data-ttu-id="5b727-139">Návod: Vytváření a používání dynamických objektů</span><span class="sxs-lookup"><span data-stu-id="5b727-139">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
