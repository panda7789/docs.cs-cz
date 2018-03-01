---
title: "sealed (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8248b451f0431286fdaba3583fc2031eb6cdbcd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sealed-c-reference"></a><span data-ttu-id="c71c5-102">sealed (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c71c5-102">sealed (C# Reference)</span></span>
<span data-ttu-id="c71c5-103">Při použití třídy, `sealed` modifikátor zabrání ostatním třídám dědění z něj.</span><span class="sxs-lookup"><span data-stu-id="c71c5-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="c71c5-104">V následujícím příkladu třída `B` dědí z třídy `A`, ale neexistuje žádná třída může dědit vlastnosti z třídy `B`.</span><span class="sxs-lookup"><span data-stu-id="c71c5-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>  
  
```  
class A {}      
sealed class B : A {}  
```  
  
 <span data-ttu-id="c71c5-105">Můžete také `sealed` modifikátor na metody nebo vlastnosti, která přepisuje virtuální metody nebo vlastnosti v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="c71c5-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="c71c5-106">Umožňuje povolit třídy odvozovat z vaší třídy a zabránit přepsání konkrétní virtuální metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c71c5-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c71c5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="c71c5-107">Example</span></span>  
 <span data-ttu-id="c71c5-108">V následujícím příkladu `Z` dědí z `Y` ale `Z` nelze přepsat virtuální funkce `F` deklarovaného v souboru `X` a uzavřené v `Y`.</span><span class="sxs-lookup"><span data-stu-id="c71c5-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]  
  
 <span data-ttu-id="c71c5-109">Když definujete nové metody nebo vlastnosti ve třídě, můžete zabránit v odvozující třídy je přepsání není deklarativně jako pomocí [virtuální](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="c71c5-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
 <span data-ttu-id="c71c5-110">Jedná se o chybu používat [abstraktní](../../../csharp/language-reference/keywords/abstract.md) modifikátor pomocí zapečetěné třídy, protože je abstraktní třída musí být zdědí třídu, která poskytuje implementaci abstraktní metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c71c5-110">It is an error to use the [abstract](../../../csharp/language-reference/keywords/abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>  
  
 <span data-ttu-id="c71c5-111">Při použití metody nebo vlastnosti, `sealed` modifikátor musí být vždy používá s [přepsat](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="c71c5-111">When applied to a method or property, the `sealed` modifier must always be used with [override](../../../csharp/language-reference/keywords/override.md).</span></span>  
  
 <span data-ttu-id="c71c5-112">Protože struktury jsou implicitně zapečetěná, nelze zděděná.</span><span class="sxs-lookup"><span data-stu-id="c71c5-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>  
  
 <span data-ttu-id="c71c5-113">Další informace najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="c71c5-113">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="c71c5-114">Další příklady najdete v tématu [abstraktní a zapečetěné třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="c71c5-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c71c5-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="c71c5-115">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]  
  
 <span data-ttu-id="c71c5-116">V předchozím příkladu mohou zkuste zapečetěné třídy dědí pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="c71c5-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 <span data-ttu-id="c71c5-117">Výsledkem je chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="c71c5-117">The result is an error message:</span></span>  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="c71c5-118">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c71c5-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="c71c5-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c71c5-119">Remarks</span></span>  
 <span data-ttu-id="c71c5-120">Pokud chcete zjistit, jestli se má zapečetit třídy, metody nebo vlastnosti, obecně je třeba zvážit následující dva body:</span><span class="sxs-lookup"><span data-stu-id="c71c5-120">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>  
  
-   <span data-ttu-id="c71c5-121">Potenciální výhody, že odvozování tříd může získat prostřednictvím přizpůsobit třídu.</span><span class="sxs-lookup"><span data-stu-id="c71c5-121">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>  
  
-   <span data-ttu-id="c71c5-122">Potenciální odvozování tříd může změnit třídy v například tak, by přestane fungovat správně, nebo jako očekává.</span><span class="sxs-lookup"><span data-stu-id="c71c5-122">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71c5-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c71c5-123">See Also</span></span>  
 [<span data-ttu-id="c71c5-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c71c5-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c71c5-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c71c5-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c71c5-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c71c5-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c71c5-127">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="c71c5-127">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="c71c5-128">Abstraktní a uzavřené třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="c71c5-128">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [<span data-ttu-id="c71c5-129">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="c71c5-129">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="c71c5-130">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="c71c5-130">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="c71c5-131">přepsání</span><span class="sxs-lookup"><span data-stu-id="c71c5-131">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="c71c5-132">virtuální</span><span class="sxs-lookup"><span data-stu-id="c71c5-132">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)
