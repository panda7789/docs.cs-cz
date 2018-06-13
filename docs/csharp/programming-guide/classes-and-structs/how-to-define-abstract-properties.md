---
title: 'Postupy: Definování abstraktních vlastností (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: aa9006b6864b9b6b129eed323b0d6d7b29064189
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172058"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="211f3-102">Postupy: Definování abstraktních vlastností (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="211f3-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="211f3-103">Následující příklad ukazuje, jak definovat [abstraktní](../../../csharp/language-reference/keywords/abstract.md) vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="211f3-103">The following example shows how to define [abstract](../../../csharp/language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="211f3-104">Deklarace abstraktní vlastnosti neposkytuje implementace přístupové objekty vlastnosti – deklaruje, že podporuje vlastnosti třídy, ale ponechá přistupujícího objektu implementaci do odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="211f3-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="211f3-105">Následující příklad ukazuje, jak implementovat abstraktní vlastnosti zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="211f3-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="211f3-106">Tato ukázka se skládá ze tří souborů, z nichž každý jednotlivě kompiluje a jeho výsledná sestavení odkazuje další kompilace:</span><span class="sxs-lookup"><span data-stu-id="211f3-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
-   <span data-ttu-id="211f3-107">abstractshape.cs: `Shape` třídu, která obsahuje abstraktní `Area` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="211f3-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
-   <span data-ttu-id="211f3-108">Shapes.cs: podtříd `Shape` třídy.</span><span class="sxs-lookup"><span data-stu-id="211f3-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
-   <span data-ttu-id="211f3-109">shapetest.cs: test program k zobrazení oblastí některých `Shape`-odvozené objekty.</span><span class="sxs-lookup"><span data-stu-id="211f3-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="211f3-110">Kompilace v příkladu, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="211f3-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="211f3-111">Tím se vytvoří shapetest.exe spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="211f3-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="211f3-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="211f3-112">Example</span></span>  
 <span data-ttu-id="211f3-113">Tento soubor deklaruje `Shape` třídu, která obsahuje `Area` vlastnost typu `double`.</span><span class="sxs-lookup"><span data-stu-id="211f3-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   <span data-ttu-id="211f3-114">Modifikátory na vlastnosti jsou umístěny v deklaraci vlastnost sám sebe.</span><span class="sxs-lookup"><span data-stu-id="211f3-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="211f3-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="211f3-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
-   <span data-ttu-id="211f3-116">Pokud deklarace abstraktních vlastností (například `Area` v tomto příkladu), můžete jednoduše označují jaké přístupové objekty vlastnosti jsou k dispozici, ale není jejich implementaci.</span><span class="sxs-lookup"><span data-stu-id="211f3-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="211f3-117">V tomto příkladu pouze [získat](../../../csharp/language-reference/keywords/get.md) přistupujícího objektu je k dispozici, takže vlastnost je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="211f3-117">In this example, only a [get](../../../csharp/language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="211f3-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="211f3-118">Example</span></span>  
 <span data-ttu-id="211f3-119">Následující kód ukazuje tři měly podtřídy `Shape` a jak se přepsat `Area` vlastností a zadejte vlastní implementaci.</span><span class="sxs-lookup"><span data-stu-id="211f3-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="211f3-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="211f3-120">Example</span></span>  
 <span data-ttu-id="211f3-121">Následující kód ukazuje program test, který vytvoří několik `Shape`-odvozené objekty a vytiskne jejich oblasti.</span><span class="sxs-lookup"><span data-stu-id="211f3-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="211f3-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="211f3-122">See Also</span></span>  
 [<span data-ttu-id="211f3-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="211f3-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="211f3-124">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="211f3-124">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="211f3-125">Abstraktní a uzavřené třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="211f3-125">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [<span data-ttu-id="211f3-126">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="211f3-126">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="211f3-127">Postupy: Vytváření a použití sestavení s pomocí příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="211f3-127">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)
