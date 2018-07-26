---
title: override (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 8f692dfdf8bd34ddb62623d86ec3dadd2b8dead3
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199261"
---
# <a name="override-c-reference"></a><span data-ttu-id="cd6aa-102">override (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="cd6aa-102">override (C# Reference)</span></span>
<span data-ttu-id="cd6aa-103">`override` Modifikátor je potřeba rozšířit nebo upravit abstraktní nebo virtuální provádění zděděné metody, vlastnosti, indexeru nebo události.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd6aa-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd6aa-104">Example</span></span>  
 <span data-ttu-id="cd6aa-105">V tomto příkladu `Square` třída musí poskytovat implementaci přepsané `Area` protože `Area` se dědí z abstraktní `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="cd6aa-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 <span data-ttu-id="cd6aa-106">`override` Metody poskytuje novou implementaci člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="cd6aa-107">Metoda, která je přepsána `override` prohlášení je označován jako přepsané základní metodě.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="cd6aa-108">Přepsané základní metoda musí mít stejný podpis jako `override` metody.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="cd6aa-109">Informace o dědičnosti, naleznete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="cd6aa-109">For information about inheritance, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="cd6aa-110">Nevirtuální nebo statické metody nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="cd6aa-111">Přepsané základní metoda musí být `virtual`, `abstract`, nebo `override`.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="cd6aa-112">`override` Deklarace nemůže změnit přístupnost `virtual` metody.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="cd6aa-113">Obě `override` metoda a `virtual` metoda musí mít stejný [úrovně modifikátor přístupu](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="cd6aa-113">Both the `override` method and the `virtual` method must have the same [access level modifier](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="cd6aa-114">Nelze použít `new`, `static`, nebo `virtual` modifikátory upravit `override` metody.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>  
  
 <span data-ttu-id="cd6aa-115">Přepsání deklarace vlastnost musíte zadat přesně stejné modifikátor přístupu, typ a název jako zděděné vlastnosti a musí být přepsané vlastnosti `virtual`, `abstract`, nebo `override`.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="cd6aa-116">Další informace o tom, jak používat `override` – klíčové slovo, naleznete v tématu [Správa verzí pomocí nových klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít nová klíčová slova Override a](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="cd6aa-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd6aa-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd6aa-117">Example</span></span>  
 <span data-ttu-id="cd6aa-118">Tento příklad definuje základní třídu s názvem `Employee`a odvozená třída s názvem `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="cd6aa-119">`SalesEmployee` Třída zahrnuje další vlastnost `salesbonus`a přepíše metodu `CalculatePay` aby vzít v úvahu.</span><span class="sxs-lookup"><span data-stu-id="cd6aa-119">The `SalesEmployee` class includes an extra property, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="cd6aa-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cd6aa-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cd6aa-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd6aa-121">See Also</span></span>  
 [<span data-ttu-id="cd6aa-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cd6aa-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cd6aa-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="cd6aa-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cd6aa-124">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="cd6aa-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [<span data-ttu-id="cd6aa-125">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cd6aa-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="cd6aa-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="cd6aa-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="cd6aa-127">abstract</span><span class="sxs-lookup"><span data-stu-id="cd6aa-127">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
 [<span data-ttu-id="cd6aa-128">virtual</span><span class="sxs-lookup"><span data-stu-id="cd6aa-128">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="cd6aa-129">new</span><span class="sxs-lookup"><span data-stu-id="cd6aa-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="cd6aa-130">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="cd6aa-130">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)
