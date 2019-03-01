---
title: Parametry obecného typu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: f6acbfee5c6b5ec426076d7bf766a3c6894b736f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972180"
---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="d056d-102">Parametry obecného typu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d056d-102">Generic Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="d056d-103">Parametry typu v obecném typu nebo metodě, je zástupný symbol pro konkrétní typ klienta Určuje, kdy se vytvořit instanci proměnné obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d056d-103">In a generic type or method definition, a type parameters is a placeholder for a specific type that a client specifies when they instantiate a variable of the generic type.</span></span> <span data-ttu-id="d056d-104">Obecný třídy, jako například `GenericList<T>` uvedené v [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md), nelze použít jako-totiž není ve skutečnosti typu; to je více než podrobný plán pro typ.</span><span class="sxs-lookup"><span data-stu-id="d056d-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="d056d-105">Chcete-li použít `GenericList<T>`, kód klienta musí deklarovat a vytvoření instance konstruovaný typ tak, že zadáte argument typu v lomených závorkách.</span><span class="sxs-lookup"><span data-stu-id="d056d-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="d056d-106">Argument typu pro tuto konkrétní třídu může být libovolný typ rozpoznatelným kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="d056d-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="d056d-107">Libovolný počet instancí konstruovaný typ nelze vytvořit, každý z nich jiný typ argumentu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d056d-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
 <span data-ttu-id="d056d-108">V každé z těchto instancí `GenericList<T>`, všechny výskyty `T` ve třídě, bude nahrazena v době běhu s argumentem typu.</span><span class="sxs-lookup"><span data-stu-id="d056d-108">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class will be substituted at run time with the type argument.</span></span> <span data-ttu-id="d056d-109">Prostřednictvím této nahrazení vytvořili jsme tři samostatné zajišťující bezpečnost typů a efektivní objekty pomocí definice jednu třídu.</span><span class="sxs-lookup"><span data-stu-id="d056d-109">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="d056d-110">Další informace o jak toto nahrazení se provádí pomocí modulu CLR najdete v tématu [obecné typy v čase spuštění](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="d056d-110">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="d056d-111">Parametr typu pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="d056d-111">Type Parameter Naming Guidelines</span></span>  
  
-   <span data-ttu-id="d056d-112">**Proveďte** název parametry obecného typu pomocí popisných názvů, pokud je jedno písmeno názvu zcela vlastní vysvětlující a popisný název nepřispěl k vyšší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d056d-112">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
-   <span data-ttu-id="d056d-113">**Vezměte v úvahu** pomocí T jako název parametru typu u typů s jedním parametrem typu jedno písmeno.</span><span class="sxs-lookup"><span data-stu-id="d056d-113">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
     [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
-   <span data-ttu-id="d056d-114">**Proveďte** předpony typu popisné názvy parametrů s "T".</span><span class="sxs-lookup"><span data-stu-id="d056d-114">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
     [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
-   <span data-ttu-id="d056d-115">**Vezměte v úvahu** označující omezení umístí na parametr typu název parametru.</span><span class="sxs-lookup"><span data-stu-id="d056d-115">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="d056d-116">Například s omezením parametru `ISession` může být volána `TSession`.</span><span class="sxs-lookup"><span data-stu-id="d056d-116">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d056d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d056d-117">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="d056d-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d056d-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d056d-119">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="d056d-119">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="d056d-120">Rozdíly mezi šablonami C++ a obecnými typy C#</span><span class="sxs-lookup"><span data-stu-id="d056d-120">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
