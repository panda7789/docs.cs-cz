---
title: "Konstruktory instancí (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: efb82128ffc27a7c065d2ba12bfc08396d3b5cf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="ff9c4-102">Konstruktory instancí (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ff9c4-102">Instance Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="ff9c4-103">Konstruktory instancí se používají k vytvoření a inicializace žádné proměnné členů instance při použití [nové](../../../csharp/language-reference/keywords/new.md) výraz, který se vytvořit objekt [třída](../../../csharp/language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="ff9c4-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../../csharp/language-reference/keywords/new.md) expression to create an object of a [class](../../../csharp/language-reference/keywords/class.md).</span></span> <span data-ttu-id="ff9c4-104">K chybě při inicializaci [statické](../../../csharp/language-reference/keywords/static.md) třídu nebo statické proměnné v třídě nestatické, je nutné definovat statického konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-104">To initialize a [static](../../../csharp/language-reference/keywords/static.md) class, or static variables in a non-static class, you must define a static constructor.</span></span> <span data-ttu-id="ff9c4-105">Další informace najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="ff9c4-105">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
 <span data-ttu-id="ff9c4-106">Následující příklad ukazuje konstruktoru instance:</span><span class="sxs-lookup"><span data-stu-id="ff9c4-106">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="ff9c4-107">Pro přehlednost Tato třída obsahuje veřejná pole.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-107">For clarity, this class contains public fields.</span></span> <span data-ttu-id="ff9c4-108">Použití veřejná pole není doporučený postup programování, protože umožňuje libovolné metody kdekoli v programu neomezený a neověřených přístup k objektu vnitřního chodu.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-108">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="ff9c4-109">Datové členy obecně by měly být privátní a by měly být dostupné pouze prostřednictvím metody třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-109">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="ff9c4-110">Tento konstruktor instance je volána, když na základě objektu `CoOrds` vytvořit třídu.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-110">This instance constructor is called whenever an object based on the `CoOrds` class is created.</span></span> <span data-ttu-id="ff9c4-111">Konstruktor jako tento jeden, které nepřijímá žádné argumenty, se nazývá *výchozí konstruktor*.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-111">A constructor like this one, which takes no arguments, is called a *default constructor*.</span></span> <span data-ttu-id="ff9c4-112">Často je však vhodné, když poskytují další konstruktory.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-112">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="ff9c4-113">Například nyní můžete přidat konstruktor k `CoOrds` třídu, která umožňuje zadat počáteční hodnoty pro datové členy:</span><span class="sxs-lookup"><span data-stu-id="ff9c4-113">For example, we can add a constructor to the `CoOrds` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 <span data-ttu-id="ff9c4-114">To umožňuje `CoOrd` objekty, které chcete vytvořit výchozí nebo konkrétní počáteční hodnoty, jako jsou to:</span><span class="sxs-lookup"><span data-stu-id="ff9c4-114">This allows `CoOrd` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 <span data-ttu-id="ff9c4-115">Pokud třídu nemá konstruktor, výchozí konstruktor je automaticky vygenerováno a použijí se výchozí hodnoty k chybě při inicializaci pole objektů.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-115">If a class does not have a constructor, a default constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="ff9c4-116">Například [int](../../../csharp/language-reference/keywords/int.md) je inicializován na 0.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-116">For example, an [int](../../../csharp/language-reference/keywords/int.md) is initialized to 0.</span></span> <span data-ttu-id="ff9c4-117">Další informace o výchozí hodnoty, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="ff9c4-117">For more information on default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="ff9c4-118">Proto protože `CoOrds` třída výchozí konstruktor inicializuje všechny datové členy na nulu, můžete ji úplně odebrat beze změny, jak funguje třídy.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-118">Therefore, because the `CoOrds` class default constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="ff9c4-119">Kompletní příklad použití více konstruktorů je uveden v příkladu 1 později v tomto tématu a příklad automaticky generované konstruktor je uvedený v příkladu 2.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-119">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="ff9c4-120">Konstruktory instancí lze také volání konstruktory instancí základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-120">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="ff9c4-121">Konstruktoru třídy můžete vyvolat konstruktor základní třídy pomocí inicializátoru, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ff9c4-121">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 <span data-ttu-id="ff9c4-122">V tomto příkladu `Circle` třída předá hodnoty představující radius a výšky konstruktoru poskytované `Shape` ze kterého `Circle` je odvozený.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-122">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="ff9c4-123">Úplný příklad pomocí `Shape` a `Circle` se zobrazí v tomto tématu jako příklad 3.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-123">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="ff9c4-124">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="ff9c4-124">Example 1</span></span>  
 <span data-ttu-id="ff9c4-125">Následující příklad ukazuje třídu s třída dva konstruktory, jeden bez argumentů a s dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-125">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="ff9c4-126">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="ff9c4-126">Example 2</span></span>  
 <span data-ttu-id="ff9c4-127">V tomto příkladu třída `Person` nemá žádné konstruktory, ve kterých případě výchozí konstruktor je automaticky poskytnuty a pole jsou inicializovány na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-127">In this example, the class `Person` does not have any constructors, in which case, a default constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 <span data-ttu-id="ff9c4-128">Všimněte si, že na výchozí hodnotu `age` je `0` a výchozí hodnota `name` je `null`.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-128">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span> <span data-ttu-id="ff9c4-129">Další informace o výchozí hodnoty, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="ff9c4-129">For more information on default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="ff9c4-130">Příklad 3</span><span class="sxs-lookup"><span data-stu-id="ff9c4-130">Example 3</span></span>  
 <span data-ttu-id="ff9c4-131">Následující příklad ukazuje použití inicializátoru základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="ff9c4-132">`Circle` Třída je odvozena od třídy Obecné `Shape`a `Cylinder` je třída odvozená z `Circle` třídy.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="ff9c4-133">Konstruktor na každý odvozená třída používá jeho základní třída inicializátoru.</span><span class="sxs-lookup"><span data-stu-id="ff9c4-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 <span data-ttu-id="ff9c4-134">Další příklady vyvolání konstruktory základní třídy, v tématu [virtuální](../../../csharp/language-reference/keywords/virtual.md), [přepsat](../../../csharp/language-reference/keywords/override.md), a [základní](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="ff9c4-134">For more examples on invoking the base class constructors, see [virtual](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md), and [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff9c4-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff9c4-135">See Also</span></span>  
 [<span data-ttu-id="ff9c4-136">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ff9c4-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ff9c4-137">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="ff9c4-137">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="ff9c4-138">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="ff9c4-138">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="ff9c4-139">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="ff9c4-139">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [<span data-ttu-id="ff9c4-140">statické</span><span class="sxs-lookup"><span data-stu-id="ff9c4-140">static</span></span>](../../../csharp/language-reference/keywords/static.md)
