---
title: "externí alias (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e995586c08659853538726a12679770cd1ada37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="b5019-102">externí alias (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b5019-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="b5019-103">Máte tak, aby odkazovaly dvě verze sestavení, které mají stejné názvy plně kvalifikovaný typ.</span><span class="sxs-lookup"><span data-stu-id="b5019-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="b5019-104">Například budete muset použít dvě nebo více verzí sestavení, ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b5019-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="b5019-105">Pomocí externí sestavení alias obory názvů v každé sestavení může zalomit uvnitř obory názvů kořenové úrovně s názvem podle alias, který umožňuje jim použít ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="b5019-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5019-106">[Extern](../../../csharp/language-reference/keywords/extern.md) – klíčové slovo slouží také jako metoda modifikátor, deklarace metodu napsané v nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="b5019-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="b5019-107">Chcete-li dvou sestavení se stejnými názvy plně kvalifikovaný typ, musí být zadán alias v příkazovém řádku následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b5019-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="b5019-108">Tím se vytvoří externí aliasy `GridV1` a `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="b5019-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="b5019-109">Pokud chcete použít tyto aliasy z v rámci programu, odkaz je pomocí `extern` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b5019-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="b5019-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b5019-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="b5019-111">Každý extern alias deklarace zavádí další kořenové úrovni oboru názvů, který je paralelní (ale není v rámci) globální obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b5019-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="b5019-112">Proto typů z každé sestavení lze odkazovat bez nejednoznačnosti pomocí jejich plně kvalifikovaný název root v příslušné alias oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b5019-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="b5019-113">V předchozím příkladu `GridV1::Grid` by být z ovládacího prvku mřížky `grid.dll`, a `GridV2::Grid` by být z ovládacího prvku mřížky `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="b5019-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b5019-114">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b5019-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b5019-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5019-115">See Also</span></span>  
 [<span data-ttu-id="b5019-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b5019-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b5019-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b5019-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b5019-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b5019-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b5019-119">Namespace klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b5019-119">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="b5019-120">:: – Operátor</span><span class="sxs-lookup"><span data-stu-id="b5019-120">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="b5019-121">/ Reference (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="b5019-121">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
