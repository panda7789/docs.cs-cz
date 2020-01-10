---
title: externí odkaz na C# alias
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 86202333484933d7449b0c4d8c5a3f1a63cd7775
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713551"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="3769c-102">externí alias (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3769c-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="3769c-103">Možná budete muset odkazovat na dvě verze sestavení, které mají stejné názvy plně kvalifikovaného typu.</span><span class="sxs-lookup"><span data-stu-id="3769c-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="3769c-104">Například může být nutné použít dvě nebo více verzí sestavení ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3769c-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="3769c-105">Pomocí externího aliasu sestavení lze obory názvů z každého sestavení zabalit do oborů názvů kořenové úrovně s názvem alias, což umožňuje jejich použití ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="3769c-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3769c-106">Klíčové slovo [extern](./extern.md) se používá také jako modifikátor metody a deklaruje metodu napsanou v nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="3769c-106">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="3769c-107">Chcete-li odkazovat na dvě sestavení se stejnými názvy plně kvalifikovaného typu, je nutné zadat alias na příkazovém řádku následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="3769c-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="3769c-108">Tím se vytvoří externí aliasy `GridV1` a `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="3769c-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="3769c-109">Chcete-li tyto aliasy použít v rámci programu, odkažte je pomocí klíčového slova `extern`.</span><span class="sxs-lookup"><span data-stu-id="3769c-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="3769c-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3769c-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="3769c-111">Každá deklarace extern alias zavádí další obor názvů na úrovni root, který je souběžně (ale neleží v rámci) globálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3769c-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="3769c-112">Typy z každého sestavení lze tedy odkazovat bez nejednoznačnosti pomocí jejich plně kvalifikovaného názvu, který je rootem v příslušném oboru názvů alias.</span><span class="sxs-lookup"><span data-stu-id="3769c-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="3769c-113">V předchozím příkladu `GridV1::Grid` by byl ovládací prvek mřížky z `grid.dll`a `GridV2::Grid` by byl ovládací prvek mřížky od `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="3769c-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3769c-114">C# – jazyková specifikace</span><span class="sxs-lookup"><span data-stu-id="3769c-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3769c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3769c-115">See also</span></span>

- [<span data-ttu-id="3769c-116">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="3769c-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3769c-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3769c-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3769c-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3769c-118">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="3769c-119">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="3769c-119">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="3769c-120">-Reference (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="3769c-120">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
