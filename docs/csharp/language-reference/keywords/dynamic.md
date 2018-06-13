---
title: dynamic (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
ms.openlocfilehash: 59957ce6b2a26c1d24dc1178630eef8551db3340
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217136"
---
# <a name="dynamic-c-reference"></a><span data-ttu-id="6b598-102">dynamic (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6b598-102">dynamic (C# Reference)</span></span>
<span data-ttu-id="6b598-103">`dynamic` Typ umožňuje operace, ve kterých se vyskytuje obejít kontrolu typu v čase kompilace.</span><span class="sxs-lookup"><span data-stu-id="6b598-103">The `dynamic` type enables the operations in which it occurs to bypass compile-time type checking.</span></span> <span data-ttu-id="6b598-104">Tyto operace jsou místo toho vyřešeny za běhu.</span><span class="sxs-lookup"><span data-stu-id="6b598-104">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="6b598-105">`dynamic` Typ zjednodušuje přístup k rozhraní API modelu COM, jako je například rozhraní API Office automatizace a také pro dynamické rozhraní API, jako je například IronPython knihovny a k HTML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="6b598-105">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, and also to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="6b598-106">Typ `dynamic` chová jako typ `object` ve většině případů.</span><span class="sxs-lookup"><span data-stu-id="6b598-106">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="6b598-107">Ale operace, které obsahují výrazy typu `dynamic` se nevyřeší nebo typ zaškrtnutí kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="6b598-107">However, operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="6b598-108">Doba běhu kompilátoru balíčky, které společně informace o operaci a tyto informace se později používá k vyhodnocení operaci.</span><span class="sxs-lookup"><span data-stu-id="6b598-108">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="6b598-109">Jako součást procesu, proměnné typu `dynamic` kompilovány do proměnné typu `object`.</span><span class="sxs-lookup"><span data-stu-id="6b598-109">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="6b598-110">Proto zadejte `dynamic` existuje pouze při kompilaci, není v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6b598-110">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>  
  
 <span data-ttu-id="6b598-111">V následujícím příkladu se liší od proměnné typu `dynamic` proměnné typu `object`.</span><span class="sxs-lookup"><span data-stu-id="6b598-111">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="6b598-112">Ověření typu pro každou proměnnou v době kompilace, umístěte ukazatel myši nad `dyn` nebo `obj` v `WriteLine` příkazy.</span><span class="sxs-lookup"><span data-stu-id="6b598-112">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="6b598-113">IntelliSense zobrazí **dynamické** pro `dyn` a **objekt** pro `obj`.</span><span class="sxs-lookup"><span data-stu-id="6b598-113">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]  
  
 <span data-ttu-id="6b598-114">`WriteLine` Příkazy zobrazuje typy spuštění `dyn` a `obj`.</span><span class="sxs-lookup"><span data-stu-id="6b598-114">The `WriteLine` statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="6b598-115">V tomto bodě mají stejného typu, celé číslo.</span><span class="sxs-lookup"><span data-stu-id="6b598-115">At that point, both have the same type, integer.</span></span> <span data-ttu-id="6b598-116">Vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6b598-116">The following output is produced:</span></span>  
  
 `System.Int32`  
  
 `System.Int32`  
  
 <span data-ttu-id="6b598-117">Rozdíl mezi `dyn` a `obj` při kompilaci, přidejte následující dva řádky mezi deklarací a `WriteLine` příkazy v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b598-117">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>  
  
```csharp  
dyn = dyn + 3;  
obj = obj + 3;  
```  
  
 <span data-ttu-id="6b598-118">Chyba kompilátoru hlášené pro pokus o přidání celé číslo a objekt ve výrazu `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="6b598-118">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="6b598-119">Ale žádná chybová zpráva pro `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="6b598-119">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="6b598-120">Výraz, který obsahuje `dyn` kontrolována v době kompilace, protože typ `dyn` je `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="6b598-120">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>  
  
## <a name="context"></a><span data-ttu-id="6b598-121">Kontext</span><span class="sxs-lookup"><span data-stu-id="6b598-121">Context</span></span>  
 <span data-ttu-id="6b598-122">`dynamic` – Klíčové slovo může vyskytovat přímo, nebo jako součást sady typu vytvořený v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="6b598-122">The `dynamic` keyword can appear directly or as a component of a constructed type in the following situations:</span></span>  
  
-   <span data-ttu-id="6b598-123">V deklaracích jako typ vlastnost, pole, indexer, parametr vrátí hodnotu, místní proměnné, nebo zadejte omezení.</span><span class="sxs-lookup"><span data-stu-id="6b598-123">In declarations, as the type of a property, field, indexer, parameter, return value, local variable, or type constraint.</span></span> <span data-ttu-id="6b598-124">Následující třídy definice používá `dynamic` v několika různých deklarace.</span><span class="sxs-lookup"><span data-stu-id="6b598-124">The following class definition uses `dynamic` in several different declarations.</span></span>  
  
     [!code-csharp[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]  
  
-   <span data-ttu-id="6b598-125">Při převodu explicitního typu jako cílový typ převodu z.</span><span class="sxs-lookup"><span data-stu-id="6b598-125">In explicit type conversions, as the target type of a conversion.</span></span>  
  
     [!code-csharp[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]  
  
-   <span data-ttu-id="6b598-126">V libovolném kontextu, kde se typy sloužit jako hodnoty, například na pravé straně `is` operátor nebo `as` operátor, nebo jako argument `typeof` jako součást sestavené typu.</span><span class="sxs-lookup"><span data-stu-id="6b598-126">In any context where types serve as values, such as on the right side of an `is` operator or an `as` operator, or as the argument to `typeof` as part of a constructed type.</span></span> <span data-ttu-id="6b598-127">Například `dynamic` lze použít v těchto výrazů.</span><span class="sxs-lookup"><span data-stu-id="6b598-127">For example, `dynamic` can be used in the following expressions.</span></span>  
  
     [!code-csharp[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="6b598-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b598-128">Example</span></span>  
 <span data-ttu-id="6b598-129">Následující příklad používá `dynamic` v několika deklarace.</span><span class="sxs-lookup"><span data-stu-id="6b598-129">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="6b598-130">`Main` Metoda se také liší od kontroly s povolenou kontrolou běhového typu typu kompilaci.</span><span class="sxs-lookup"><span data-stu-id="6b598-130">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]  
  
 <span data-ttu-id="6b598-131">Další informace a příklady naleznete v tématu [použití typu dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="6b598-131">For more information and examples, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b598-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b598-132">See Also</span></span>  
 <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>  
 <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
 [<span data-ttu-id="6b598-133">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="6b598-133">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="6b598-134">object</span><span class="sxs-lookup"><span data-stu-id="6b598-134">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
 [<span data-ttu-id="6b598-135">is</span><span class="sxs-lookup"><span data-stu-id="6b598-135">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="6b598-136">as</span><span class="sxs-lookup"><span data-stu-id="6b598-136">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
 [<span data-ttu-id="6b598-137">typeof</span><span class="sxs-lookup"><span data-stu-id="6b598-137">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 [<span data-ttu-id="6b598-138">Postupy: Bezpečné přetypování pomocí operátorů as a is</span><span class="sxs-lookup"><span data-stu-id="6b598-138">How to: Safely Cast by Using as and is Operators</span></span>](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)  
 [<span data-ttu-id="6b598-139">Návod: Vytváření a používání dynamických objektů</span><span class="sxs-lookup"><span data-stu-id="6b598-139">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
