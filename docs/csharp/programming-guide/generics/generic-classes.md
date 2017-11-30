---
title: "Obecné třídy (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c92efd63f7b24917dc50ca0864f1a132c5c2bf00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="generic-classes-c-programming-guide"></a><span data-ttu-id="f7109-102">Obecné třídy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f7109-102">Generic Classes (C# Programming Guide)</span></span>
<span data-ttu-id="f7109-103">Obecné třídy zapouzdřovat operace, které nejsou specifické pro určitý datový typ.</span><span class="sxs-lookup"><span data-stu-id="f7109-103">Generic classes encapsulate operations that are not specific to a particular data type.</span></span> <span data-ttu-id="f7109-104">Nejčastěji používá pro obecné třídy je ke kolekcím, jako jsou propojené seznamy, zatřiďovacích tabulkách, zásobníky, fronty, stromy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="f7109-104">The most common use for generic classes is with collections like linked lists, hash tables, stacks, queues, trees, and so on.</span></span> <span data-ttu-id="f7109-105">Operace, jako je například přidávání a odebírání položek z kolekce se provádějí v bez ohledu na typ uložení dat v podstatě stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="f7109-105">Operations such as adding and removing items from the collection are performed in basically the same way regardless of the type of data being stored.</span></span>  
  
 <span data-ttu-id="f7109-106">Doporučený postup pro většinu scénářů, které vyžadují třídy kolekce, je použití těm, které jsou uvedené v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7109-106">For most scenarios that require collection classes, the recommended approach is to use the ones provided in the .NET Framework class library.</span></span> <span data-ttu-id="f7109-107">Další informace o použití těchto tříd naleznete v tématu [obecné typy v knihovně tříd rozhraní .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="f7109-107">For more information about using these classes, see [Generics in the .NET Framework Class Library](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span></span>  
  
 <span data-ttu-id="f7109-108">Obecné třídy obvykle vytvoříte tak, že počínaje existující konkrétní třídy a změna typy parametrů typu jeden v době, dokud se nedostanete optimální rovnováha mezi počtem Generalizace a použitelnost.</span><span class="sxs-lookup"><span data-stu-id="f7109-108">Typically, you create generic classes by starting with an existing concrete class, and changing types into type parameters one at a time until you reach the optimal balance of generalization and usability.</span></span> <span data-ttu-id="f7109-109">Při vytváření vlastní obecné třídy, je důležité zvážit zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="f7109-109">When creating your own generic classes, important considerations include the following:</span></span>  
  
-   <span data-ttu-id="f7109-110">Jaké typy generalize do parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="f7109-110">Which types to generalize into type parameters.</span></span>  
  
     <span data-ttu-id="f7109-111">Jako pravidlo, další typy, které můžete parametrizovat, více flexibilní a opakovaně použitelný kód změní.</span><span class="sxs-lookup"><span data-stu-id="f7109-111">As a rule, the more types you can parameterize, the more flexible and reusable your code becomes.</span></span> <span data-ttu-id="f7109-112">Příliš mnoho generalizace však můžete vytvořit kód, který je složité jiné vývojářům pro čtení nebo pochopit.</span><span class="sxs-lookup"><span data-stu-id="f7109-112">However, too much generalization can create code that is difficult for other developers to read or understand.</span></span>  
  
-   <span data-ttu-id="f7109-113">Jaké omezení, pokud existuje, které chcete použít pro parametry typu (viz [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="f7109-113">What constraints, if any, to apply to the type parameters (See [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)).</span></span>  
  
     <span data-ttu-id="f7109-114">Doporučujeme použít maximální možné omezení, která bude stále umožňují zpracování typy, které je nutné zpracovat.</span><span class="sxs-lookup"><span data-stu-id="f7109-114">A good rule is to apply the maximum constraints possible that will still let you handle the types you must handle.</span></span> <span data-ttu-id="f7109-115">Například pokud jste si jisti, že obecná třída je určena pro použití jenom s typy odkazů, platí omezení třídy.</span><span class="sxs-lookup"><span data-stu-id="f7109-115">For example, if you know that your generic class is intended for use only with reference types, apply the class constraint.</span></span> <span data-ttu-id="f7109-116">Který zabrání neúmyslnému použití třídě s typy hodnot a budete moci použít `as` operátor na `T`a zkontrolujte hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="f7109-116">That will prevent unintended use of your class with value types, and will enable you to use the `as` operator on `T`, and check for null values.</span></span>  
  
-   <span data-ttu-id="f7109-117">Určuje, zda zohlednit obecné chování do základní třídy a podtřídy.</span><span class="sxs-lookup"><span data-stu-id="f7109-117">Whether to factor generic behavior into base classes and subclasses.</span></span>  
  
     <span data-ttu-id="f7109-118">Protože obecné třídy může sloužit jako základní třídy, stejné aspekty návrhu zde platí stejně jako u neobecné třídy.</span><span class="sxs-lookup"><span data-stu-id="f7109-118">Because generic classes can serve as base classes, the same design considerations apply here as with non-generic classes.</span></span> <span data-ttu-id="f7109-119">Najdete v části pravidla o tom, která dědí z obecné základní třídy později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="f7109-119">See the rules about inheriting from generic base classes later in this topic.</span></span>  
  
-   <span data-ttu-id="f7109-120">Určuje, zda implementovat jednu nebo více obecná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7109-120">Whether to implement one or more generic interfaces.</span></span>  
  
     <span data-ttu-id="f7109-121">Například pokud navrhujete třídu, která se použije k vytvoření položek v kolekci na základě obecné typy, budete muset implementovat rozhraní, jako <xref:System.IComparable%601> kde `T` je typ třídě.</span><span class="sxs-lookup"><span data-stu-id="f7109-121">For example, if you are designing a class that will be used to create items in a generics-based collection, you may have to implement an interface such as <xref:System.IComparable%601> where `T` is the type of your class.</span></span>  
  
 <span data-ttu-id="f7109-122">Příklad jednoduchého obecné třídy, naleznete v části [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="f7109-122">For an example of a simple generic class, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span>  
  
 <span data-ttu-id="f7109-123">Pravidla pro parametry typu a omezení mají několik vliv na chování obecná třída, zejména pokud jde o dědičnosti a člen usnadnění.</span><span class="sxs-lookup"><span data-stu-id="f7109-123">The rules for type parameters and constraints have several implications for generic class behavior, especially regarding inheritance and member accessibility.</span></span> <span data-ttu-id="f7109-124">Než budete pokračovat, měli byste pochopit některé podmínky.</span><span class="sxs-lookup"><span data-stu-id="f7109-124">Before proceeding, you should understand some terms.</span></span> <span data-ttu-id="f7109-125">Pro obecné třídy `Node<T>,` kód klienta může odkazovat na třídu buď tak, že zadáte argument typu, k vytvoření typu uzavřené vytvořený (`Node<int>`).</span><span class="sxs-lookup"><span data-stu-id="f7109-125">For a generic class `Node<T>,` client code can reference the class either by specifying a type argument, to create a closed constructed type (`Node<int>`).</span></span> <span data-ttu-id="f7109-126">Případně ho můžete nechat parametr typu Tento parametr nezadáte, například když zadáte obecné základní třídy, k vytvoření otevřenou sestavený typu (`Node<T>`).</span><span class="sxs-lookup"><span data-stu-id="f7109-126">Alternatively, it can leave the type parameter unspecified, for example when you specify a generic base class, to create an open constructed type (`Node<T>`).</span></span> <span data-ttu-id="f7109-127">Obecné třídy může dědit vlastnosti z konkrétní, uzavřené vytvořený nebo otevřené sestavené základní třídy:</span><span class="sxs-lookup"><span data-stu-id="f7109-127">Generic classes can inherit from concrete, closed constructed, or open constructed base classes:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#16](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_1.cs)]  
  
 <span data-ttu-id="f7109-128">Jinými slovy, konkrétní non Obecné, třídy můžete dědění z uzavřených vytvořený základní třídy, ale není z otevřené sestavené třídy nebo z parametrů typu, protože neexistuje žádný způsob v době běhu kódu klienta zadat argument typu potřebné k vytváření instancí Základní třída.</span><span class="sxs-lookup"><span data-stu-id="f7109-128">Non-generic, in other words, concrete, classes can inherit from closed constructed base classes, but not from open constructed classes or from type parameters because there is no way at run time for client code to supply the type argument required to instantiate the base class.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#17](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_2.cs)]  
  
 <span data-ttu-id="f7109-129">Obecné třídy, které dědí od otevřené sestavené typy musíte zadat argumenty typu pro všechny parametry typu základní třídy, které nejsou sdíleny dědičných třídu, jak je ukázáno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="f7109-129">Generic classes that inherit from open constructed types must supply type arguments for any base class type parameters that are not shared by the inheriting class, as demonstrated in the following code:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#18](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_3.cs)]  
  
 <span data-ttu-id="f7109-130">Obecné třídy, které dědí od otevřené sestavené typy musíte zadat omezení, která je nadmnožinou nebo implikují omezení u základního typu:</span><span class="sxs-lookup"><span data-stu-id="f7109-130">Generic classes that inherit from open constructed types must specify constraints that are a superset of, or imply, the constraints on the base type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#19](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_4.cs)]  
  
 <span data-ttu-id="f7109-131">Obecné typy můžete použít několik parametrů typu a omezení, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f7109-131">Generic types can use multiple type parameters and constraints, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#20](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_5.cs)]  
  
 <span data-ttu-id="f7109-132">Otevřené sestavené typy vytvořený a uzavřené lze použít jako parametry metody:</span><span class="sxs-lookup"><span data-stu-id="f7109-132">Open constructed and closed constructed types can be used as method parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#21](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-classes_6.cs)]  
  
 <span data-ttu-id="f7109-133">Pokud obecná třída implementuje rozhraní, všechny instance této třídy lze převést na tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7109-133">If a generic class implements an interface, all instances of that class can be cast to that interface.</span></span>  
  
 <span data-ttu-id="f7109-134">Obecné třídy jsou neutrální.</span><span class="sxs-lookup"><span data-stu-id="f7109-134">Generic classes are invariant.</span></span> <span data-ttu-id="f7109-135">Jinými slovy Pokud určuje vstupní parametr `List<BaseClass>`, kompilaci chyba se zobrazí, pokud se pokusíte poskytují `List<DerivedClass>`.</span><span class="sxs-lookup"><span data-stu-id="f7109-135">In other words, if an input parameter specifies a `List<BaseClass>`, you will get a compile-time error if you try to provide a `List<DerivedClass>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7109-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7109-136">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="f7109-137">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f7109-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f7109-138">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="f7109-138">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="f7109-139">Uložení stavu výčty</span><span class="sxs-lookup"><span data-stu-id="f7109-139">Saving the State of Enumerators</span></span>](http://go.microsoft.com/fwlink/?LinkId=112390)  
 [<span data-ttu-id="f7109-140">Stavebnice dědičnosti první část</span><span class="sxs-lookup"><span data-stu-id="f7109-140">An Inheritance Puzzle, Part One</span></span>](http://go.microsoft.com/fwlink/?LinkId=112380)
