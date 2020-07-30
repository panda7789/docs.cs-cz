---
title: Parametry obecného typu – Průvodce programováním v C#
description: Informace o definici obecného typu v jazyce C#, kde parametr typu je zástupný symbol pro typ, který klient Určuje pro instanci obecného typu.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: dc37029378ac1e9ec194d95b561787761d69a9fd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299250"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="eda1d-103">Parametry obecného typu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="eda1d-103">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="eda1d-104">V definici obecného typu nebo metody je parametr typu zástupný symbol pro konkrétní typ, který klient určí při vytvoření instance obecného typu.</span><span class="sxs-lookup"><span data-stu-id="eda1d-104">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="eda1d-105">Obecnou třídu, jako `GenericList<T>` je například uvedená v [úvodu do obecných typů](./index.md), nelze použít, protože není ve skutečnosti typu; je více podobně jako podrobný plán pro typ.</span><span class="sxs-lookup"><span data-stu-id="eda1d-105">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](./index.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="eda1d-106">Chcete-li použít `GenericList<T>` , kód klienta musí deklarovat a vytvořit instanci konstruovaného typu zadáním argumentu typu uvnitř lomených závorek.</span><span class="sxs-lookup"><span data-stu-id="eda1d-106">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="eda1d-107">Argument typu pro tuto konkrétní třídu může být jakýkoli typ rozpoznávaný kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="eda1d-107">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="eda1d-108">Lze vytvořit libovolný počet instancí konstruovaného typu, přičemž každý z nich používá jiný argument typu, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="eda1d-108">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="eda1d-109">V každé z těchto instancí `GenericList<T>` je každý výskyt `T` ve třídě nahrazen v době běhu pomocí argumentu typu.</span><span class="sxs-lookup"><span data-stu-id="eda1d-109">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="eda1d-110">Prostřednictvím této náhrady jsme vytvořili tři samostatné typy bezpečné a efektivní objekty pomocí definice jediné třídy.</span><span class="sxs-lookup"><span data-stu-id="eda1d-110">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="eda1d-111">Další informace o tom, jak tato náhrada provádí modulem CLR, naleznete v tématu [Obecné typy v době běhu](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="eda1d-111">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="eda1d-112">Pokyny pro pojmenovávání parametrů typu</span><span class="sxs-lookup"><span data-stu-id="eda1d-112">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="eda1d-113">Pojmenujte parametry obecného typu s popisnými názvy, pokud **je název jednoho** písmene zcela zřejmý a popisný název nepřidá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="eda1d-113">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="eda1d-114">**Zvažte** použití parametru T jako názvu parametru typu pro typ s jedním parametrem typu písmene Single.</span><span class="sxs-lookup"><span data-stu-id="eda1d-114">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="eda1d-115">**Udělejte** prefix názvů parametrů popisného typu s "T".</span><span class="sxs-lookup"><span data-stu-id="eda1d-115">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="eda1d-116">**Zvažte** označení omezení umístěných u parametru typu v názvu parametru.</span><span class="sxs-lookup"><span data-stu-id="eda1d-116">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="eda1d-117">Například parametr omezený na `ISession` může být volán `TSession` .</span><span class="sxs-lookup"><span data-stu-id="eda1d-117">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="eda1d-118">Pravidlo analýzy kódu [CA1715](/visualstudio/code-quality/ca1715) lze použít k zajištění toho, že parametry typu jsou pojmenovány správně.</span><span class="sxs-lookup"><span data-stu-id="eda1d-118">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="eda1d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eda1d-119">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="eda1d-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="eda1d-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="eda1d-121">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="eda1d-121">Generics</span></span>](./index.md)
- [<span data-ttu-id="eda1d-122">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="eda1d-122">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)
