---
title: Konstruktory instancí – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 621b8ca7510b0b9916c9c46f201ff77402c3c655
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964740"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="2bbf0-102">Konstruktory instancí (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="2bbf0-102">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="2bbf0-103">Konstruktory instancí slouží k vytvoření a inicializaci všech proměnných členů instance při použití [nového](../../language-reference/operators/new-operator.md) výrazu pro vytvoření objektu [třídy](../../language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="2bbf0-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="2bbf0-104">Chcete-li inicializovat [statickou](../../language-reference/keywords/static.md) třídu nebo statické proměnné v nestatické třídě, Definujte statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-104">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="2bbf0-105">Další informace naleznete v tématu [statické konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="2bbf0-105">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="2bbf0-106">Následující příklad ukazuje konstruktor instance:</span><span class="sxs-lookup"><span data-stu-id="2bbf0-106">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> <span data-ttu-id="2bbf0-107">Pro přehlednost Tato třída obsahuje veřejná pole.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-107">For clarity, this class contains public fields.</span></span> <span data-ttu-id="2bbf0-108">Použití veřejných polí není doporučeným způsobem programování, protože umožňuje libovolné metodě kdekoli v programu neomezený a neověřený přístup k vnitřním pracovním postupům objektu.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-108">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="2bbf0-109">Datové členy by měly být obecně soukromé a měly by být k dispozici pouze prostřednictvím metod a vlastností třídy.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-109">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="2bbf0-110">Tento konstruktor instance se volá vždycky, když se vytvoří objekt založený na třídě `Coords`.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-110">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="2bbf0-111">Konstruktor podobný tomuto typu, který nepřijímá žádné argumenty, se nazývá *konstruktor bez parametrů*.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-111">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="2bbf0-112">Je však často užitečné poskytnout další konstruktory.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-112">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="2bbf0-113">Do třídy `Coords` můžeme například přidat konstruktor, který nám umožňuje zadat počáteční hodnoty pro datové členy:</span><span class="sxs-lookup"><span data-stu-id="2bbf0-113">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="2bbf0-114">To umožňuje `Coords` objekty vytvořit s výchozími nebo konkrétními počátečními hodnotami, jako je:</span><span class="sxs-lookup"><span data-stu-id="2bbf0-114">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="2bbf0-115">Pokud třída nemá konstruktor, konstruktor bez parametrů se automaticky vygeneruje a k inicializaci polí objektu se použijí výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-115">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="2bbf0-116">Například hodnota [int](../../language-reference/builtin-types/integral-numeric-types.md) je inicializována na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-116">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="2bbf0-117">Informace o výchozích hodnotách typu naleznete v tématu [výchozí hodnoty C# typů](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="2bbf0-117">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="2bbf0-118">Proto vzhledem k tomu, že konstruktor bez parametrů `Coords` inicializuje všechny datové členy na nulu, lze jej odebrat zcela, aniž by bylo nutné měnit způsob fungování třídy.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-118">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="2bbf0-119">Kompletní příklad použití více konstruktorů je uveden v příkladu 1 dále v tomto tématu a příklad automaticky generovaného konstruktoru je uveden v příkladu 2.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-119">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="2bbf0-120">Konstruktory instancí lze také použít k volání konstruktorů instancí základních tříd.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-120">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="2bbf0-121">Konstruktor třídy může vyvolat konstruktor základní třídy prostřednictvím inicializátoru následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2bbf0-121">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="2bbf0-122">V tomto příkladu třída `Circle` předává hodnoty reprezentující poloměr a výšku do konstruktoru poskytnutého `Shape`, ze kterého je odvozen `Circle`.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-122">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="2bbf0-123">Úplný příklad použití `Shape` a `Circle` se zobrazí v tomto tématu jako příklad 3.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-123">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="2bbf0-124">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="2bbf0-124">Example 1</span></span>  
 <span data-ttu-id="2bbf0-125">Následující příklad ukazuje třídu se dvěma konstruktory třídy, jedna bez argumentů a jedna se dvěma argumenty.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-125">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="2bbf0-126">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="2bbf0-126">Example 2</span></span>  
 <span data-ttu-id="2bbf0-127">V tomto příkladu třída `Person` nemá žádné konstruktory. v takovém případě je konstruktor bez parametrů automaticky zadán a pole jsou inicializována na jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-127">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="2bbf0-128">Všimněte si, že výchozí hodnota `age` je `0` a výchozí hodnota `name` je `null`.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-128">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="2bbf0-129">Příklad 3</span><span class="sxs-lookup"><span data-stu-id="2bbf0-129">Example 3</span></span>  
 <span data-ttu-id="2bbf0-130">Následující příklad ukazuje použití inicializátoru základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-130">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="2bbf0-131">Třída `Circle` je odvozena od obecné `Shape`třídy a třída `Cylinder` je odvozena od třídy `Circle`.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-131">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="2bbf0-132">Konstruktor u každé odvozené třídy používá svůj inicializátor základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2bbf0-132">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="2bbf0-133">Další příklady vyvolání konstruktorů základní třídy naleznete v tématu [Virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md)a [Base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="2bbf0-133">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bbf0-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bbf0-134">See also</span></span>

- [<span data-ttu-id="2bbf0-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2bbf0-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2bbf0-136">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="2bbf0-136">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="2bbf0-137">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="2bbf0-137">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="2bbf0-138">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="2bbf0-138">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="2bbf0-139">static</span><span class="sxs-lookup"><span data-stu-id="2bbf0-139">static</span></span>](../../language-reference/keywords/static.md)
