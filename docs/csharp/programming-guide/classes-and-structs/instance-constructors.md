---
title: Instance konstruktory - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: b4257cfa1f50ebd9ce821fff2a0bfa15fae4ac2f
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398440"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="5479f-102">Konstruktory instancí (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5479f-102">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="5479f-103">Konstruktory instancí se používají k vytváření a inicializace žádné proměnné členů instance při použití [nové](../../../csharp/language-reference/operators/new-operator.md) výraz, který se vytvoří objekt [třídy](../../../csharp/language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="5479f-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../../csharp/language-reference/operators/new-operator.md) expression to create an object of a [class](../../../csharp/language-reference/keywords/class.md).</span></span> <span data-ttu-id="5479f-104">Inicializace [statické](../../../csharp/language-reference/keywords/static.md) třídy nebo statické proměnné v nestatické třídy, můžete definovat statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5479f-104">To initialize a [static](../../../csharp/language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="5479f-105">Další informace najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="5479f-105">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
 <span data-ttu-id="5479f-106">Následující příklad ukazuje konstruktor instance:</span><span class="sxs-lookup"><span data-stu-id="5479f-106">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
>  <span data-ttu-id="5479f-107">Pro přehlednost Tato třída obsahuje veřejná pole.</span><span class="sxs-lookup"><span data-stu-id="5479f-107">For clarity, this class contains public fields.</span></span> <span data-ttu-id="5479f-108">Použití veřejná pole není doporučený postup programování, protože umožňuje libovolné metody kdekoli v programu neomezený i neověřených přístup k objektu vnitřní fungování.</span><span class="sxs-lookup"><span data-stu-id="5479f-108">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="5479f-109">Datové členy obecně by měly být privátní a by měl mít přístup jenom prostřednictvím metody třídy a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5479f-109">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="5479f-110">Tento konstruktor instance je volána pokaždé, když se na základě objektu `Coords` je vytvořená třída.</span><span class="sxs-lookup"><span data-stu-id="5479f-110">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="5479f-111">Jako tohoto objektu, která nepřijímá žádné argumenty, se nazývá konstruktor *konstruktor bez parametrů*.</span><span class="sxs-lookup"><span data-stu-id="5479f-111">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="5479f-112">Často je však užitečný k zadání dalších konstruktory.</span><span class="sxs-lookup"><span data-stu-id="5479f-112">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="5479f-113">Například můžeme přidat konstruktoru `Coords` třídu, která umožňuje zadat počáteční hodnoty pro datové členy:</span><span class="sxs-lookup"><span data-stu-id="5479f-113">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="5479f-114">Díky tomu `Coords` objekty vytvořené pomocí výchozí nebo konkrétní počáteční hodnoty tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="5479f-114">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="5479f-115">Pokud třída nemá konstruktor, konstruktor není automaticky vygenerován a výchozí hodnoty se používají k inicializaci pole objektů.</span><span class="sxs-lookup"><span data-stu-id="5479f-115">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="5479f-116">Například [int](../../../csharp/language-reference/keywords/int.md) je inicializován na hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="5479f-116">For example, an [int](../../../csharp/language-reference/keywords/int.md) is initialized to 0.</span></span> <span data-ttu-id="5479f-117">Další informace o výchozí hodnoty, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="5479f-117">For more information on default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="5479f-118">Proto protože `Coords` třída konstruktor inicializuje všechny datové členy na hodnotu nula, je možné odebrat úplně beze změny, jak funguje třídy.</span><span class="sxs-lookup"><span data-stu-id="5479f-118">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="5479f-119">V příkladu 1 dále v tomto tématu poskytuje kompletní příklad použití více konstruktorů a příklad o automaticky generovaný konstruktor je k dispozici v příkladu 2.</span><span class="sxs-lookup"><span data-stu-id="5479f-119">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="5479f-120">Konstruktory instancí lze také volat konstruktor instance základní třídy.</span><span class="sxs-lookup"><span data-stu-id="5479f-120">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="5479f-121">Konstruktor třídy lze vyvolat konstruktor základní třídy pomocí inicializátoru, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5479f-121">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="5479f-122">V tomto příkladu `Circle` třídy předá hodnoty představující radius a výšku konstruktoru poskytované `Shape` odkud `Circle` je odvozen.</span><span class="sxs-lookup"><span data-stu-id="5479f-122">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="5479f-123">Úplný příklad použití `Shape` a `Circle` se zobrazí v tomto tématu jako příklad 3.</span><span class="sxs-lookup"><span data-stu-id="5479f-123">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="5479f-124">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="5479f-124">Example 1</span></span>  
 <span data-ttu-id="5479f-125">Následující příklad ukazuje třídu s dvěma třídami konstruktory, jeden bez argumentů a druhý se dvěma argumenty.</span><span class="sxs-lookup"><span data-stu-id="5479f-125">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="5479f-126">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="5479f-126">Example 2</span></span>  
 <span data-ttu-id="5479f-127">V tomto příkladu třída `Person` nemá žádné konstruktory, ve kterých případu, konstruktor bez parametrů je poskytována automaticky a pole jsou inicializovány na výchozích hodnotách.</span><span class="sxs-lookup"><span data-stu-id="5479f-127">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="5479f-128">Všimněte si, že výchozí hodnota `age` je `0` a výchozí hodnota `name` je `null`.</span><span class="sxs-lookup"><span data-stu-id="5479f-128">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span> <span data-ttu-id="5479f-129">Další informace o výchozí hodnoty, najdete v části [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="5479f-129">For more information on default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="5479f-130">Příklad 3</span><span class="sxs-lookup"><span data-stu-id="5479f-130">Example 3</span></span>  
 <span data-ttu-id="5479f-131">Následující příklad ukazuje použití inicializátoru pro základní třídu.</span><span class="sxs-lookup"><span data-stu-id="5479f-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="5479f-132">`Circle` Třídy je odvozen od obecné třídy `Shape`a `Cylinder` je třída odvozena z `Circle` třídy.</span><span class="sxs-lookup"><span data-stu-id="5479f-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="5479f-133">Konstruktor pro jednotlivé odvozené třídy používá inicializátor její základní třídy.</span><span class="sxs-lookup"><span data-stu-id="5479f-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="5479f-134">Další příklady vyvolání konstruktory základní třídy naleznete v tématu [virtuální](../../../csharp/language-reference/keywords/virtual.md), [přepsat](../../../csharp/language-reference/keywords/override.md), a [základní](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="5479f-134">For more examples on invoking the base class constructors, see [virtual](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md), and [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5479f-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5479f-135">See also</span></span>

- [<span data-ttu-id="5479f-136">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5479f-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5479f-137">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="5479f-137">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="5479f-138">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="5479f-138">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="5479f-139">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="5479f-139">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="5479f-140">static</span><span class="sxs-lookup"><span data-stu-id="5479f-140">static</span></span>](../../../csharp/language-reference/keywords/static.md)
