---
title: Obecné parametry typu – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 8412980d35989c445d2e0a44c0b9f35e6087bb8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712179"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="6a004-102">Parametry obecného typu (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6a004-102">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="6a004-103">V definici obecného typu nebo metody je parametr typu zástupným symbolem pro určitý typ, který klient určí při vytváření instance obecného typu.</span><span class="sxs-lookup"><span data-stu-id="6a004-103">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="6a004-104">Obecná třída, například `GenericList<T>` uvedená v [úvodu k obecným typům](./index.md), nelze použít jako-je, protože není ve skutečnosti typ; je to spíš jako plán pro typ.</span><span class="sxs-lookup"><span data-stu-id="6a004-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](./index.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="6a004-105">Chcete-li použít `GenericList<T>`, klientský kód musí deklarovat a konkretizovat vytvořený typ zadáním argumentu typu uvnitř úhlových závorek.</span><span class="sxs-lookup"><span data-stu-id="6a004-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="6a004-106">Argument typu pro tuto konkrétní třídu může být libovolný typ rozpoznaný kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="6a004-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="6a004-107">Lze vytvořit libovolný počet instancí konstruovaného typu, z nichž každá používá jiný argument typu, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="6a004-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="6a004-108">V každé z těchto `GenericList<T>`instancí `T` , každý výskyt ve třídě je nahrazen za běhu s argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="6a004-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="6a004-109">Pomocí této náhrady jsme vytvořili tři samostatné typově bezpečné a efektivní objekty pomocí jedné definice třídy.</span><span class="sxs-lookup"><span data-stu-id="6a004-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="6a004-110">Další informace o tom, jak je toto nahrazení provádí CLR, naleznete [v tématu Obecné typy v době spuštění](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="6a004-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="6a004-111">Pokyny pro pojmenování parametrů typu</span><span class="sxs-lookup"><span data-stu-id="6a004-111">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="6a004-112">**Do** name generic type parameters with descriptive names, unless jeden název písmene je zcela vysvětlující a popisný název by nepřidal hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6a004-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="6a004-113">**Zvažte** použití T jako názvu parametru typu pro typy s jedním parametrem typu s jedním písmenem.</span><span class="sxs-lookup"><span data-stu-id="6a004-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="6a004-114">**Proveďte** názvy parametrů popisného typu předpony s písmenem "T".</span><span class="sxs-lookup"><span data-stu-id="6a004-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="6a004-115">**Zvažte** označení omezení umístěných na parametr typu v názvu parametru.</span><span class="sxs-lookup"><span data-stu-id="6a004-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="6a004-116">Například parametr omezen na `ISession` může být `TSession`volána .</span><span class="sxs-lookup"><span data-stu-id="6a004-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="6a004-117">Pravidlo analýzy kódu [CA1715](/visualstudio/code-quality/ca1715) lze použít k zajištění, že parametry typu jsou pojmenovány odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="6a004-117">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6a004-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a004-118">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="6a004-119">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6a004-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6a004-120">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="6a004-120">Generics</span></span>](./index.md)
- [<span data-ttu-id="6a004-121">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="6a004-121">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)
