---
title: extern alias - C# Reference
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 86202333484933d7449b0c4d8c5a3f1a63cd7775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713551"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="35d9d-102">externí alias (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="35d9d-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="35d9d-103">Je možné, že budete muset odkazovat na dvě verze sestavení, které mají stejné plně kvalifikované názvy typů.</span><span class="sxs-lookup"><span data-stu-id="35d9d-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="35d9d-104">Například může být možné použít dvě nebo více verzí sestavení ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="35d9d-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="35d9d-105">Pomocí aliasu externího sestavení mohou být obory názvů z každého sestavení zabaleny do oborů názvů kořenové úrovně pojmenovaných aliasem, což umožňuje jejich použití ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="35d9d-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35d9d-106">Klíčové slovo [extern](./extern.md) se také používá jako modifikátor metody, deklarující metodu napsanou v nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="35d9d-106">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="35d9d-107">Chcete-li odkazovat na dvě sestavení se stejnými plně kvalifikovanými názvy typů, musí být na příkazovém řádku zadán alias takto:</span><span class="sxs-lookup"><span data-stu-id="35d9d-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="35d9d-108">Tím se vytvoří `GridV1` externí `GridV2`aliasy a .</span><span class="sxs-lookup"><span data-stu-id="35d9d-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="35d9d-109">Chcete-li použít tyto aliasy z programu, `extern` odkazovat na ně pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="35d9d-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="35d9d-110">Například:</span><span class="sxs-lookup"><span data-stu-id="35d9d-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="35d9d-111">Každá deklarace aliasu extern zavádí další obor názvů na kořenové úrovni, který paraleluje (ale neleží uvnitř) globálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="35d9d-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="35d9d-112">Typy z každého sestavení tedy mohou být odkazovány bez nejednoznačnosti pomocí jejich plně kvalifikovaný název, zakořeněné v příslušném alias oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="35d9d-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="35d9d-113">V předchozím `GridV1::Grid` příkladu by bylo `grid.dll`řízení `GridV2::Grid` mřížky z , `grid20.dll`a bude řídicí mřížky z .</span><span class="sxs-lookup"><span data-stu-id="35d9d-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="35d9d-114">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="35d9d-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35d9d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="35d9d-115">See also</span></span>

- [<span data-ttu-id="35d9d-116">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="35d9d-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="35d9d-117">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="35d9d-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="35d9d-118">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="35d9d-118">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="35d9d-119">:: Operátor</span><span class="sxs-lookup"><span data-stu-id="35d9d-119">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="35d9d-120">-reference (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="35d9d-120">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
