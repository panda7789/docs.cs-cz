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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280150"
---
# <a name="override-c-reference"></a><span data-ttu-id="1013a-102">override (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1013a-102">override (C# Reference)</span></span>
<span data-ttu-id="1013a-103">`override` Modifikátor je potřeba rozšířit nebo změnit abstraktní nebo virtuální implementace zděděné metoda, vlastnost, indexer nebo událostí.</span><span class="sxs-lookup"><span data-stu-id="1013a-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1013a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1013a-104">Example</span></span>  
 <span data-ttu-id="1013a-105">V tomto příkladu `Square` třída musí obsahovat přepsaného implementace `Area` protože `Area` dědí z abstraktní `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="1013a-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 <span data-ttu-id="1013a-106">`override` Metoda poskytuje nové implementaci člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="1013a-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="1013a-107">Metoda, která je přepsat `override` deklarace se označuje jako přepsaného základní metody.</span><span class="sxs-lookup"><span data-stu-id="1013a-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="1013a-108">Přepsané základní metody musí mít stejný podpis jako `override` metoda.</span><span class="sxs-lookup"><span data-stu-id="1013a-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="1013a-109">Informace o dědičnosti najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="1013a-109">For information about inheritance, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="1013a-110">Nejde přepsat bez virtuální nebo statické metody.</span><span class="sxs-lookup"><span data-stu-id="1013a-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="1013a-111">Přepsané základní metody musí být `virtual`, `abstract`, nebo `override`.</span><span class="sxs-lookup"><span data-stu-id="1013a-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="1013a-112">`override` Deklarace nelze změnit usnadnění přístupu `virtual` metoda.</span><span class="sxs-lookup"><span data-stu-id="1013a-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="1013a-113">Obě `override` metoda a `virtual` metoda musí mít stejnou [úrovně – modifikátor přístupu](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="1013a-113">Both the `override` method and the `virtual` method must have the same [access level modifier](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="1013a-114">Nelze použít `new`, `static`, nebo `virtual` modifikátory upravit `override` metoda.</span><span class="sxs-lookup"><span data-stu-id="1013a-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>  
  
 <span data-ttu-id="1013a-115">Přepsání deklarace vlastnosti musíte zadat přesně stejný – modifikátor přístupu, typ a název jako zděděnou vlastnost a musí být vlastnost přepsaného `virtual`, `abstract`, nebo `override`.</span><span class="sxs-lookup"><span data-stu-id="1013a-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="1013a-116">Další informace o tom, jak používat `override` – klíčové slovo, najdete v části [Správa verzí pomocí nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="1013a-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1013a-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="1013a-117">Example</span></span>  
 <span data-ttu-id="1013a-118">Tento příklad definuje základní třídu s názvem `Employee`a odvozené třídy s názvem `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="1013a-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="1013a-119">`SalesEmployee` Třída obsahuje doplňující vlastnosti, `salesbonus`a přepíše metodu `CalculatePay` Chcete-li vzít v úvahu.</span><span class="sxs-lookup"><span data-stu-id="1013a-119">The `SalesEmployee` class includes an extra property, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1013a-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1013a-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1013a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="1013a-121">See Also</span></span>  
 [<span data-ttu-id="1013a-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1013a-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1013a-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1013a-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1013a-124">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="1013a-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [<span data-ttu-id="1013a-125">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1013a-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1013a-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="1013a-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="1013a-127">abstract</span><span class="sxs-lookup"><span data-stu-id="1013a-127">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
 [<span data-ttu-id="1013a-128">virtual</span><span class="sxs-lookup"><span data-stu-id="1013a-128">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="1013a-129">new</span><span class="sxs-lookup"><span data-stu-id="1013a-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="1013a-130">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="1013a-130">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)
