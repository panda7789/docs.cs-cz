---
title: static – modifikátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: db12ef80752bba913e6792ccb38f598a664efb0b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397664"
---
# <a name="static-c-reference"></a><span data-ttu-id="f9f9d-102">static – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f9f9d-102">static (C# Reference)</span></span>
<span data-ttu-id="f9f9d-103">Použití `static` modifikátor deklarovat statický člen, který patří do samotného typu, nikoli s určitým objektem.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="f9f9d-104">`static` Modifikátor lze použít s třídami, pole, metody, vlastnosti, operátory, události a konstruktory, ale nelze použít s indexery, finalizační metody nebo jiné typy než třídy.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="f9f9d-105">Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="f9f9d-105">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9f9d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9f9d-106">Example</span></span>  
 <span data-ttu-id="f9f9d-107">Následující třída je deklarována jako `static` a obsahuje pouze `static` metody:</span><span class="sxs-lookup"><span data-stu-id="f9f9d-107">The following class is declared as `static` and contains only `static` methods:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 <span data-ttu-id="f9f9d-108">Deklarace konstanty nebo typu je implicitně statický člen.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-108">A constant or type declaration is implicitly a static member.</span></span>  
  
 <span data-ttu-id="f9f9d-109">Statický člen se nedá odkazovat prostřednictvím instance.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="f9f9d-110">Místo toho se odkazuje pomocí názvu typu.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="f9f9d-111">Představte si třeba následující třídy:</span><span class="sxs-lookup"><span data-stu-id="f9f9d-111">For example, consider the following class:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 <span data-ttu-id="f9f9d-112">Odkazovat na statického člena `x`, použijte plně kvalifikovaný název `MyBaseC.MyStruct.x`, pokud člen není přístupný ze stejného oboru:</span><span class="sxs-lookup"><span data-stu-id="f9f9d-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 <span data-ttu-id="f9f9d-113">Zatímco instance třídy obsahuje kopii všechna pole instancí třídy, je jenom jednu kopii každého statické pole.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>  
  
 <span data-ttu-id="f9f9d-114">Není možné použít [to](../../../csharp/language-reference/keywords/this.md) odkazovat statické metody nebo přistupující objekty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-114">It is not possible to use [this](../../../csharp/language-reference/keywords/this.md) to reference static methods or property accessors.</span></span>  
  
 <span data-ttu-id="f9f9d-115">Pokud `static` – klíčové slovo je aplikován na třídu, musí být statické členy třídy.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>  
  
 <span data-ttu-id="f9f9d-116">Statické třídy a třídy mohou mít statické konstruktory.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="f9f9d-117">Statické konstruktory jsou volány v určitém okamžiku mezi při spuštění programu a je vytvořena instance třídy.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9f9d-118">`static` – Klíčové slovo má omezenější použití než v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="f9f9d-119">Porovnat s klíčovým slovem C++, naleznete v tématu [třídy úložiště (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="f9f9d-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>
  
 <span data-ttu-id="f9f9d-120">Abychom si předvedli statické členy, vezměte v úvahu třídu, která představuje zaměstnance společnosti.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="f9f9d-121">Předpokládejme, že třída obsahuje metody pro počet zaměstnanců a pole pro uložení tohoto čísla zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="f9f9d-122">Metody a pole nepatří do jakékoli instance zaměstnance.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="f9f9d-123">Místo toho patří do třídy společnosti.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-123">Instead they belong to the company class.</span></span> <span data-ttu-id="f9f9d-124">Proto by měly být deklarovány jako statické členy třídy.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-124">Therefore, they should be declared as static members of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9f9d-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9f9d-125">Example</span></span>  
 <span data-ttu-id="f9f9d-126">Tento příklad načte název a ID nového zaměstnance, zvýší čítač zaměstnance jednou a zobrazí informace o nových zaměstnanců a nový počet zaměstnanců.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="f9f9d-127">Pro zjednodušení tento program přečte aktuální počet zaměstnanců z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="f9f9d-128">V reálné aplikaci by měli číst tyto informace ze souboru.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-128">In a real application, this information should be read from a file.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="f9f9d-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9f9d-129">Example</span></span>  
 <span data-ttu-id="f9f9d-130">Tento příklad ukazuje, že i když inicializujete statické pole pomocí jiné statické pole ještě nebyla deklarována, budou výsledky nedefinované dokud explicitně přiřadit hodnotu statické pole.</span><span class="sxs-lookup"><span data-stu-id="f9f9d-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f9f9d-131">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f9f9d-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f9f9d-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9f9d-132">See Also</span></span>

- [<span data-ttu-id="f9f9d-133">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f9f9d-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="f9f9d-134">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f9f9d-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f9f9d-135">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f9f9d-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="f9f9d-136">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="f9f9d-136">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="f9f9d-137">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="f9f9d-137">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
