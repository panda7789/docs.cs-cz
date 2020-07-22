---
title: Konstruktory instancí – Průvodce programováním v C#
description: Konstruktory instancí v jazyce C# vytvoří a inicializují všechny proměnné členů instance při použití nového výrazu pro vytvoření objektu třídy.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: d70e786446fb198afb4e0311757cacb65b706f47
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864199"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="e8771-103">Konstruktory instancí (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e8771-103">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="e8771-104">Konstruktory instancí slouží k vytvoření a inicializaci všech proměnných členů instance při použití [nového](../../language-reference/operators/new-operator.md) výrazu pro vytvoření objektu [třídy](../../language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="e8771-104">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="e8771-105">Chcete-li inicializovat [statickou](../../language-reference/keywords/static.md) třídu nebo statické proměnné v nestatické třídě, Definujte statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e8771-105">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="e8771-106">Další informace naleznete v tématu [statické konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="e8771-106">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="e8771-107">Následující příklad ukazuje konstruktor instance:</span><span class="sxs-lookup"><span data-stu-id="e8771-107">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> <span data-ttu-id="e8771-108">Pro přehlednost Tato třída obsahuje veřejná pole.</span><span class="sxs-lookup"><span data-stu-id="e8771-108">For clarity, this class contains public fields.</span></span> <span data-ttu-id="e8771-109">Použití veřejných polí není doporučeným způsobem programování, protože umožňuje libovolné metodě kdekoli v programu neomezený a neověřený přístup k vnitřním pracovním postupům objektu.</span><span class="sxs-lookup"><span data-stu-id="e8771-109">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="e8771-110">Datové členy by měly být obecně soukromé a měly by být k dispozici pouze prostřednictvím metod a vlastností třídy.</span><span class="sxs-lookup"><span data-stu-id="e8771-110">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="e8771-111">Tento konstruktor instance se volá vždycky, když se vytvoří objekt založený na `Coords` třídě.</span><span class="sxs-lookup"><span data-stu-id="e8771-111">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="e8771-112">Konstruktor podobný tomuto typu, který nepřijímá žádné argumenty, se nazývá *konstruktor bez parametrů*.</span><span class="sxs-lookup"><span data-stu-id="e8771-112">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="e8771-113">Je však často užitečné poskytnout další konstruktory.</span><span class="sxs-lookup"><span data-stu-id="e8771-113">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="e8771-114">Například můžeme přidat konstruktor do `Coords` třídy, která nám umožní zadat počáteční hodnoty pro datové členy:</span><span class="sxs-lookup"><span data-stu-id="e8771-114">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="e8771-115">To umožňuje `Coords` vytvářet objekty s výchozími nebo konkrétními počátečními hodnotami, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="e8771-115">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="e8771-116">Pokud třída nemá konstruktor, konstruktor bez parametrů se automaticky vygeneruje a k inicializaci polí objektu se použijí výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8771-116">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="e8771-117">Například hodnota [int](../../language-reference/builtin-types/integral-numeric-types.md) je inicializována na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="e8771-117">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="e8771-118">Informace o výchozích hodnotách typů naleznete v tématu [výchozí hodnoty typů jazyka C#](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="e8771-118">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="e8771-119">Proto vzhledem k tomu, že `Coords` konstruktor bez parametrů třídy inicializuje všechny datové členy na nulu, lze jej odebrat zcela, aniž by bylo nutné měnit způsob fungování třídy.</span><span class="sxs-lookup"><span data-stu-id="e8771-119">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="e8771-120">Kompletní příklad použití více konstruktorů je uveden v příkladu 1 dále v tomto tématu a příklad automaticky generovaného konstruktoru je uveden v příkladu 2.</span><span class="sxs-lookup"><span data-stu-id="e8771-120">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="e8771-121">Konstruktory instancí lze také použít k volání konstruktorů instancí základních tříd.</span><span class="sxs-lookup"><span data-stu-id="e8771-121">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="e8771-122">Konstruktor třídy může vyvolat konstruktor základní třídy prostřednictvím inicializátoru následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e8771-122">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="e8771-123">V tomto příkladu `Circle` Třída předává hodnoty reprezentující poloměr a výšku do konstruktoru poskytnutého z, `Shape` který `Circle` je odvozen.</span><span class="sxs-lookup"><span data-stu-id="e8771-123">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="e8771-124">Úplný příklad s využitím `Shape` a `Circle` se zobrazí v tomto tématu jako příklad 3.</span><span class="sxs-lookup"><span data-stu-id="e8771-124">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="e8771-125">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="e8771-125">Example 1</span></span>  
 <span data-ttu-id="e8771-126">Následující příklad ukazuje třídu se dvěma konstruktory třídy, jedna bez argumentů a jedna se dvěma argumenty.</span><span class="sxs-lookup"><span data-stu-id="e8771-126">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="e8771-127">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="e8771-127">Example 2</span></span>  
 <span data-ttu-id="e8771-128">V tomto příkladu třída nemá `Person` žádné konstruktory. v takovém případě je konstruktor bez parametrů k dispozici automaticky a pole jsou inicializována na výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8771-128">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="e8771-129">Všimněte si, že výchozí hodnota `age` je `0` a výchozí hodnota `name` je `null` .</span><span class="sxs-lookup"><span data-stu-id="e8771-129">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="e8771-130">Příklad 3</span><span class="sxs-lookup"><span data-stu-id="e8771-130">Example 3</span></span>  
 <span data-ttu-id="e8771-131">Následující příklad ukazuje použití inicializátoru základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e8771-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="e8771-132">`Circle`Třída je odvozena z obecné třídy `Shape` a `Cylinder` Třída je odvozena z `Circle` třídy.</span><span class="sxs-lookup"><span data-stu-id="e8771-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="e8771-133">Konstruktor u každé odvozené třídy používá svůj inicializátor základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e8771-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="e8771-134">Další příklady vyvolání konstruktorů základní třídy naleznete v tématu [Virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md)a [Base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="e8771-134">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8771-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8771-135">See also</span></span>

- [<span data-ttu-id="e8771-136">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e8771-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e8771-137">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="e8771-137">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="e8771-138">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="e8771-138">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="e8771-139">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="e8771-139">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="e8771-140">static</span><span class="sxs-lookup"><span data-stu-id="e8771-140">static</span></span>](../../language-reference/keywords/static.md)
