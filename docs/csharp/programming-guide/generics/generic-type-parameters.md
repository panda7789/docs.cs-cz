---
title: Parametry obecného typu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 10feb47ce3dfe9e356da381e0d62e6d220c9452a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677419"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="09bb8-102">Parametry obecného typu (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="09bb8-102">Generic type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="09bb8-103">Parametr typu v obecném typu nebo metodě, je zástupný symbol pro konkrétní typ, že klient určuje při vytváření instance obecného typu.</span><span class="sxs-lookup"><span data-stu-id="09bb8-103">In a generic type or method definition, a type parameter is a placeholder for a specific type that a client specifies when they create an instance of the generic type.</span></span> <span data-ttu-id="09bb8-104">Obecný třídy, jako například `GenericList<T>` uvedené v [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md), nelze použít jako-totiž není ve skutečnosti typu; to je více než podrobný plán pro typ.</span><span class="sxs-lookup"><span data-stu-id="09bb8-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="09bb8-105">Chcete-li použít `GenericList<T>`, kód klienta musí deklarovat a vytvoření instance konstruovaný typ tak, že zadáte argument typu v lomených závorkách.</span><span class="sxs-lookup"><span data-stu-id="09bb8-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="09bb8-106">Argument typu pro tuto konkrétní třídu může být libovolný typ rozpoznatelným kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="09bb8-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="09bb8-107">Libovolný počet instancí konstruovaný typ nelze vytvořit, každý z nich jiný typ argumentu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="09bb8-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
<span data-ttu-id="09bb8-108">V každé z těchto instancí `GenericList<T>`, všechny výskyty `T` ve třídě nahrazeny za běhu s argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="09bb8-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class is substituted at run time with the type argument.</span></span> <span data-ttu-id="09bb8-109">Prostřednictvím této nahrazení vytvořili jsme tři samostatné zajišťující bezpečnost typů a efektivní objekty pomocí definice jednu třídu.</span><span class="sxs-lookup"><span data-stu-id="09bb8-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="09bb8-110">Další informace o jak toto nahrazení se provádí pomocí modulu CLR najdete v tématu [obecné typy v čase spuštění](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="09bb8-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="09bb8-111">Parametr typu pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="09bb8-111">Type parameter naming guidelines</span></span>  
  
- <span data-ttu-id="09bb8-112">**Proveďte** název parametry obecného typu pomocí popisných názvů, pokud je jedno písmeno názvu zcela vlastní vysvětlující a popisný název nepřispěl k vyšší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="09bb8-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- <span data-ttu-id="09bb8-113">**Vezměte v úvahu** pomocí T jako název parametru typu u typů s jedním parametrem typu jedno písmeno.</span><span class="sxs-lookup"><span data-stu-id="09bb8-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- <span data-ttu-id="09bb8-114">**Proveďte** předpony typu popisné názvy parametrů s "T".</span><span class="sxs-lookup"><span data-stu-id="09bb8-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- <span data-ttu-id="09bb8-115">**Vezměte v úvahu** označující omezení umístí na parametr typu název parametru.</span><span class="sxs-lookup"><span data-stu-id="09bb8-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="09bb8-116">Například s omezením parametru `ISession` může být volána `TSession`.</span><span class="sxs-lookup"><span data-stu-id="09bb8-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>

<span data-ttu-id="09bb8-117">Pravidel nástroje Analýza kódu [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) slouží k zajištění, že jsou správně pojmenované parametry typu.</span><span class="sxs-lookup"><span data-stu-id="09bb8-117">The code analysis rule [CA1715](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix) can be used to ensure that type parameters are named appropriately.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="09bb8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09bb8-118">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="09bb8-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="09bb8-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="09bb8-120">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="09bb8-120">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="09bb8-121">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="09bb8-121">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
