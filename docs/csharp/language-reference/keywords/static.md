---
title: static – modifikátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c47f4a19843039c27ef9f1602581d1004fb8fd76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="static-c-reference"></a><span data-ttu-id="d2c49-102">static – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d2c49-102">static (C# Reference)</span></span>
<span data-ttu-id="d2c49-103">Použití `static` modifikátor deklarovat statický člen, který patří k samotného typu, nikoli na konkrétní objekt.</span><span class="sxs-lookup"><span data-stu-id="d2c49-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="d2c49-104">`static` Modifikátor lze použít s třídy, pole, metody, vlastnosti, operátory, události a konstruktory, ale nedá se použít s indexery, finalizační metody nebo jiného typu než třídy.</span><span class="sxs-lookup"><span data-stu-id="d2c49-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="d2c49-105">Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="d2c49-105">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2c49-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2c49-106">Example</span></span>  
 <span data-ttu-id="d2c49-107">Následující třídy je deklarován jako `static` a obsahuje pouze `static` metody:</span><span class="sxs-lookup"><span data-stu-id="d2c49-107">The following class is declared as `static` and contains only `static` methods:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 <span data-ttu-id="d2c49-108">Konstanta nebo typ deklarace je implicitně je statický člen.</span><span class="sxs-lookup"><span data-stu-id="d2c49-108">A constant or type declaration is implicitly a static member.</span></span>  
  
 <span data-ttu-id="d2c49-109">Statický člen nemůže odkazovat pomocí instance.</span><span class="sxs-lookup"><span data-stu-id="d2c49-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="d2c49-110">Místo toho se odkazuje prostřednictvím název typu.</span><span class="sxs-lookup"><span data-stu-id="d2c49-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="d2c49-111">Zvažte například následující třídy:</span><span class="sxs-lookup"><span data-stu-id="d2c49-111">For example, consider the following class:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 <span data-ttu-id="d2c49-112">K odkazování na statický člen `x`, použijte plně kvalifikovaný název `MyBaseC.MyStruct.x`, pokud člen je přístupná ze stejného oboru:</span><span class="sxs-lookup"><span data-stu-id="d2c49-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 <span data-ttu-id="d2c49-113">Při instance třídy obsahuje kopii všechna pole instance třídy, existuje pouze jedna kopie každého statické pole.</span><span class="sxs-lookup"><span data-stu-id="d2c49-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>  
  
 <span data-ttu-id="d2c49-114">Není možné použít [to](../../../csharp/language-reference/keywords/this.md) tak, aby odkazovaly statické metody nebo vlastnosti přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="d2c49-114">It is not possible to use [this](../../../csharp/language-reference/keywords/this.md) to reference static methods or property accessors.</span></span>  
  
 <span data-ttu-id="d2c49-115">Pokud `static` – klíčové slovo použijí na třídu, musí být statické všichni členové třídy.</span><span class="sxs-lookup"><span data-stu-id="d2c49-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>  
  
 <span data-ttu-id="d2c49-116">Statické konstruktory mohou mít třídy a statické třídy.</span><span class="sxs-lookup"><span data-stu-id="d2c49-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="d2c49-117">Statické konstruktory jsou volány v určitém okamžiku mezi při spuštění programu a vytvoření instance třídy.</span><span class="sxs-lookup"><span data-stu-id="d2c49-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2c49-118">`static` – Klíčové slovo má více omezenou používá než v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="d2c49-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="d2c49-119">K porovnání s – klíčové slovo C++, najdete v části [třídy úložiště (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="d2c49-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>
  
 <span data-ttu-id="d2c49-120">K předvedení statické členy, zvažte třída, která představuje zaměstnanci společnosti.</span><span class="sxs-lookup"><span data-stu-id="d2c49-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="d2c49-121">Předpokládejme, že třída obsahuje metody pro počet zaměstnanci a pole slouží k uložení počet zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="d2c49-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="d2c49-122">Metoda a pole nepatří do žádné instance zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="d2c49-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="d2c49-123">Místo toho, které patří třída společnosti.</span><span class="sxs-lookup"><span data-stu-id="d2c49-123">Instead they belong to the company class.</span></span> <span data-ttu-id="d2c49-124">Proto že by měl deklarované jako statické členy třídy.</span><span class="sxs-lookup"><span data-stu-id="d2c49-124">Therefore, they should be declared as static members of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2c49-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2c49-125">Example</span></span>  
 <span data-ttu-id="d2c49-126">Tento příklad načte název a ID nové zaměstnance, zvýší čítač zaměstnanec jedním a zobrazí informace o nové zaměstnance a nové číslo zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="d2c49-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="d2c49-127">Tento program pro jednoduchost, čte aktuální počet zaměstnanci z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="d2c49-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="d2c49-128">V reálné aplikaci musí být tyto informace čtení ze souboru.</span><span class="sxs-lookup"><span data-stu-id="d2c49-128">In a real application, this information should be read from a file.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="d2c49-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2c49-129">Example</span></span>  
 <span data-ttu-id="d2c49-130">Tento příklad ukazuje, že i když můžete inicializovat statické pole s použitím jiné statické pole ještě nebyla deklarována, výsledky se nedefinované dokud explicitně přiřadit hodnotu statické pole.</span><span class="sxs-lookup"><span data-stu-id="d2c49-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d2c49-131">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2c49-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d2c49-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2c49-132">See Also</span></span>  
 [<span data-ttu-id="d2c49-133">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2c49-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d2c49-134">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d2c49-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d2c49-135">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2c49-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d2c49-136">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="d2c49-136">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="d2c49-137">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="d2c49-137">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
