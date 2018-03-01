---
title: "override (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 807fae02ca4e6f616c77877cc8815405baaf8428
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="override-c-reference"></a><span data-ttu-id="ae304-102">override (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ae304-102">override (C# Reference)</span></span>
<span data-ttu-id="ae304-103">`override` Modifikátor je potřeba rozšířit nebo změnit abstraktní nebo virtuální implementace zděděné metoda, vlastnost, indexer nebo událostí.</span><span class="sxs-lookup"><span data-stu-id="ae304-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae304-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae304-104">Example</span></span>  
 <span data-ttu-id="ae304-105">V tomto příkladu `Square` třída musí obsahovat přepsaného implementace `Area` protože `Area` dědí z abstraktní `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="ae304-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 <span data-ttu-id="ae304-106">`override` Metoda poskytuje nové implementaci člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ae304-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="ae304-107">Metoda, která je přepsat `override` deklarace se označuje jako přepsaného základní metody.</span><span class="sxs-lookup"><span data-stu-id="ae304-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="ae304-108">Přepsané základní metody musí mít stejný podpis jako `override` metoda.</span><span class="sxs-lookup"><span data-stu-id="ae304-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="ae304-109">Informace o dědičnosti najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="ae304-109">For information about inheritance, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="ae304-110">Nejde přepsat bez virtuální nebo statické metody.</span><span class="sxs-lookup"><span data-stu-id="ae304-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="ae304-111">Přepsané základní metody musí být `virtual`, `abstract`, nebo `override`.</span><span class="sxs-lookup"><span data-stu-id="ae304-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="ae304-112">`override` Deklarace nelze změnit usnadnění přístupu `virtual` metoda.</span><span class="sxs-lookup"><span data-stu-id="ae304-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="ae304-113">Obě `override` metoda a `virtual` metoda musí mít stejnou [úrovně – modifikátor přístupu](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="ae304-113">Both the `override` method and the `virtual` method must have the same [access level modifier](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="ae304-114">Nelze použít `new`, `static`, nebo `virtual` modifikátory upravit `override` metoda.</span><span class="sxs-lookup"><span data-stu-id="ae304-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>  
  
 <span data-ttu-id="ae304-115">Přepsání deklarace vlastnosti musíte zadat přesně stejný – modifikátor přístupu, typ a název jako zděděnou vlastnost a musí být vlastnost přepsaného `virtual`, `abstract`, nebo `override`.</span><span class="sxs-lookup"><span data-stu-id="ae304-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="ae304-116">Další informace o tom, jak používat `override` – klíčové slovo, najdete v části [Správa verzí pomocí nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="ae304-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae304-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae304-117">Example</span></span>  
 <span data-ttu-id="ae304-118">Tento příklad definuje základní třídu s názvem `Employee`a odvozené třídy s názvem `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="ae304-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="ae304-119">`SalesEmployee` Třída obsahuje doplňující vlastnosti, `salesbonus`a přepíše metodu `CalculatePay` Chcete-li vzít v úvahu.</span><span class="sxs-lookup"><span data-stu-id="ae304-119">The `SalesEmployee` class includes an extra property, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ae304-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae304-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ae304-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae304-121">See Also</span></span>  
 [<span data-ttu-id="ae304-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae304-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ae304-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ae304-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ae304-124">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="ae304-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [<span data-ttu-id="ae304-125">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae304-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ae304-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="ae304-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="ae304-127">abstraktní</span><span class="sxs-lookup"><span data-stu-id="ae304-127">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
 [<span data-ttu-id="ae304-128">virtuální</span><span class="sxs-lookup"><span data-stu-id="ae304-128">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="ae304-129">Nový</span><span class="sxs-lookup"><span data-stu-id="ae304-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="ae304-130">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="ae304-130">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)
