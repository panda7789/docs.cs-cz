---
title: Definování abstraktních vlastností – Průvodce programováním v C#
description: Naučte se definovat abstraktní vlastnosti v jazyce C#. Deklarace abstraktní vlastnosti znamená, že třída podporuje vlastnost. Odvozené třídy implementují přistupující objekty.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 4db71721495857c634e8090b986704d8a592b4e2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864394"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="bc3a1-105">Definování abstraktních vlastností (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="bc3a1-105">How to define abstract properties (C# Programming Guide)</span></span>
<span data-ttu-id="bc3a1-106">Následující příklad ukazuje, jak definovat [abstraktní](../../language-reference/keywords/abstract.md) vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bc3a1-106">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="bc3a1-107">Deklarace abstraktní vlastnosti neposkytuje implementaci přistupujících objektů vlastnosti – deklaruje, že třída podporuje vlastnosti, ale ponechá implementaci přistupující objekty odvozeným třídám.</span><span class="sxs-lookup"><span data-stu-id="bc3a1-107">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="bc3a1-108">Následující příklad ukazuje, jak implementovat abstraktní vlastnosti zděděné ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="bc3a1-108">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="bc3a1-109">Tato ukázka se skládá ze tří souborů, z nichž každá je zkompilována individuálně a na výsledné sestavení je odkazováno pomocí další kompilace:</span><span class="sxs-lookup"><span data-stu-id="bc3a1-109">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="bc3a1-110">abstractshape.cs: `Shape` třída, která obsahuje abstraktní `Area` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bc3a1-110">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="bc3a1-111">shapes.cs: podtřídy `Shape` třídy.</span><span class="sxs-lookup"><span data-stu-id="bc3a1-111">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="bc3a1-112">shapetest.cs: testovací program pro zobrazení oblastí `Shape` objektů odvozených od sebe.</span><span class="sxs-lookup"><span data-stu-id="bc3a1-112">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="bc3a1-113">Chcete-li zkompilovat příklad, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="bc3a1-113">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="bc3a1-114">Tím se vytvoří spustitelný soubor shapetest.exe.</span><span class="sxs-lookup"><span data-stu-id="bc3a1-114">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc3a1-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc3a1-115">Example</span></span>  
 <span data-ttu-id="bc3a1-116">Tento soubor deklaruje `Shape` třídu, která obsahuje `Area` vlastnost typu `double` .</span><span class="sxs-lookup"><span data-stu-id="bc3a1-116">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="bc3a1-117">Modifikátory vlastnosti jsou umístěny v samotné deklaraci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bc3a1-117">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="bc3a1-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bc3a1-118">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="bc3a1-119">Při deklaraci abstraktní vlastnosti (jako `Area` v tomto příkladu) jednoduše označíte, jaké přístupové objekty vlastnosti jsou k dispozici, ale neimplementují.</span><span class="sxs-lookup"><span data-stu-id="bc3a1-119">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="bc3a1-120">V tomto příkladu je k dispozici pouze přistupující objekt [Get](../../language-reference/keywords/get.md) , takže vlastnost je určena jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="bc3a1-120">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc3a1-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc3a1-121">Example</span></span>  
 <span data-ttu-id="bc3a1-122">Následující kód ukazuje tři podtřídy `Shape` a způsob, jak přepisují `Area` vlastnost k poskytnutí vlastní implementace.</span><span class="sxs-lookup"><span data-stu-id="bc3a1-122">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="bc3a1-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc3a1-123">Example</span></span>  
 <span data-ttu-id="bc3a1-124">Následující kód ukazuje testovací program, který vytváří mnoho `Shape` objektů odvozených a tiskne jejich oblasti.</span><span class="sxs-lookup"><span data-stu-id="bc3a1-124">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="bc3a1-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc3a1-125">See also</span></span>

- [<span data-ttu-id="bc3a1-126">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="bc3a1-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bc3a1-127">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="bc3a1-127">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="bc3a1-128">Abstraktní a uzavřené třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="bc3a1-128">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="bc3a1-129">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bc3a1-129">Properties</span></span>](./properties.md)
