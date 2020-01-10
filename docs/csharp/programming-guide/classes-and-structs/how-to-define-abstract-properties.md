---
title: Definování abstraktních vlastností – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: c46f36133b68a550a17cf882844fd2481eee8851
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705610"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="ea2ac-102">Definování abstraktních vlastností (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="ea2ac-102">How to define abstract properties (C# Programming Guide)</span></span>
<span data-ttu-id="ea2ac-103">Následující příklad ukazuje, jak definovat [abstraktní](../../language-reference/keywords/abstract.md) vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-103">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="ea2ac-104">Deklarace abstraktní vlastnosti neposkytuje implementaci přistupujících objektů vlastnosti – deklaruje, že třída podporuje vlastnosti, ale ponechá implementaci přistupující objekty odvozeným třídám.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="ea2ac-105">Následující příklad ukazuje, jak implementovat abstraktní vlastnosti zděděné ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="ea2ac-106">Tato ukázka se skládá ze tří souborů, z nichž každá je zkompilována individuálně a na výsledné sestavení je odkazováno pomocí další kompilace:</span><span class="sxs-lookup"><span data-stu-id="ea2ac-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="ea2ac-107">abstractshape.cs: třída `Shape`, která obsahuje abstraktní vlastnost `Area`.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="ea2ac-108">shapes.cs: podtřídy třídy `Shape`.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="ea2ac-109">shapetest.cs: testovací program pro zobrazení oblastí některých objektů odvozených od `Shape`.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="ea2ac-110">Chcete-li zkompilovat příklad, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="ea2ac-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="ea2ac-111">Tím se vytvoří spustitelný soubor shapetest. exe.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea2ac-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea2ac-112">Example</span></span>  
 <span data-ttu-id="ea2ac-113">Tento soubor deklaruje třídu `Shape`, která obsahuje vlastnost `Area` typu `double`.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="ea2ac-114">Modifikátory vlastnosti jsou umístěny v samotné deklaraci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="ea2ac-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ea2ac-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="ea2ac-116">Při deklaraci abstraktní vlastnosti (například `Area` v tomto příkladu) jednoduše označíte, jaké přístupové objekty vlastnosti jsou k dispozici, ale neimplementují.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="ea2ac-117">V tomto příkladu je k dispozici pouze přistupující objekt [Get](../../language-reference/keywords/get.md) , takže vlastnost je určena jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-117">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea2ac-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea2ac-118">Example</span></span>  
 <span data-ttu-id="ea2ac-119">Následující kód ukazuje tři podtřídy `Shape` a způsob, jak přepíší vlastnost `Area` k poskytnutí vlastní implementace.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="ea2ac-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea2ac-120">Example</span></span>  
 <span data-ttu-id="ea2ac-121">Následující kód ukazuje testovací program, který vytvoří mnoho objektů odvozených od `Shape`a vytiskne své oblasti.</span><span class="sxs-lookup"><span data-stu-id="ea2ac-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ea2ac-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea2ac-122">See also</span></span>

- [<span data-ttu-id="ea2ac-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ea2ac-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ea2ac-124">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="ea2ac-124">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="ea2ac-125">Abstraktní a uzavřené třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="ea2ac-125">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="ea2ac-126">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ea2ac-126">Properties</span></span>](./properties.md)
