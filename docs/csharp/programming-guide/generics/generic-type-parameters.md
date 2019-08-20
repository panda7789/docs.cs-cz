---
title: Parametry obecného typu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 27cd89c8e82036bf6353030b4f235c2ebe738e6d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589686"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="b1dde-102">Parametry obecného typu (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="b1dde-102">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="b1dde-103">V definici obecného typu nebo metody je parametr typu zástupný symbol pro konkrétní typ, který klient určí při vytvoření instance obecného typu.</span><span class="sxs-lookup"><span data-stu-id="b1dde-103">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="b1dde-104">Obecnou třídu, `GenericList<T>` jako je například uvedená v [úvodu do obecných typů](./index.md), nelze použít, protože není ve skutečnosti typu; je více podobně jako podrobný plán pro typ.</span><span class="sxs-lookup"><span data-stu-id="b1dde-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](./index.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="b1dde-105">Chcete- `GenericList<T>`li použít, kód klienta musí deklarovat a vytvořit instanci konstruovaného typu zadáním argumentu typu uvnitř lomených závorek.</span><span class="sxs-lookup"><span data-stu-id="b1dde-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="b1dde-106">Argument typu pro tuto konkrétní třídu může být jakýkoli typ rozpoznávaný kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="b1dde-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="b1dde-107">Lze vytvořit libovolný počet instancí konstruovaného typu, přičemž každý z nich používá jiný argument typu, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b1dde-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="b1dde-108">V každé z těchto instancí `GenericList<T>`je každý `T` výskyt ve třídě nahrazen v době běhu pomocí argumentu typu.</span><span class="sxs-lookup"><span data-stu-id="b1dde-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="b1dde-109">Prostřednictvím této náhrady jsme vytvořili tři samostatné typy bezpečné a efektivní objekty pomocí definice jediné třídy.</span><span class="sxs-lookup"><span data-stu-id="b1dde-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="b1dde-110">Další informace o tom, jak tato náhrada provádí modulem CLR, naleznete v tématu [Obecné typy v době běhu](./generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="b1dde-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](./generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="b1dde-111">Pokyny pro pojmenovávání parametrů typu</span><span class="sxs-lookup"><span data-stu-id="b1dde-111">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="b1dde-112">Pojmenujte parametry obecného typu s popisnými názvy, pokud je název jednoho písmene zcela zřejmý a popisný název nepřidá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b1dde-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="b1dde-113">**Zvažte** použití parametru T jako názvu parametru typu pro typ s jedním parametrem typu písmene Single.</span><span class="sxs-lookup"><span data-stu-id="b1dde-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="b1dde-114">**Udělejte** prefix názvů parametrů popisného typu s "T".</span><span class="sxs-lookup"><span data-stu-id="b1dde-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="b1dde-115">**Zvažte** označení omezení umístěných u parametru typu v názvu parametru.</span><span class="sxs-lookup"><span data-stu-id="b1dde-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="b1dde-116">Například parametr omezený na `ISession` může být volán. `TSession`</span><span class="sxs-lookup"><span data-stu-id="b1dde-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="b1dde-117">Pravidlo analýzy kódu [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) lze použít k zajištění toho, že parametry typu jsou pojmenovány správně.</span><span class="sxs-lookup"><span data-stu-id="b1dde-117">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b1dde-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1dde-118">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="b1dde-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b1dde-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b1dde-120">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="b1dde-120">Generics</span></span>](./index.md)
- [<span data-ttu-id="b1dde-121">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="b1dde-121">Differences Between C++ Templates and C# Generics</span></span>](./differences-between-cpp-templates-and-csharp-generics.md)
