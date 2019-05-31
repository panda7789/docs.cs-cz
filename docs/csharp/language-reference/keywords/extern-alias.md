---
title: externí alias - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: d2ecd566731c3d2d472034ecb6412432af24c847
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422054"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="081ef-102">externí alias (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="081ef-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="081ef-103">Budete muset odkazovat na dvě verze sestavení, která mají stejné názvy plně kvalifikovaných typů.</span><span class="sxs-lookup"><span data-stu-id="081ef-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="081ef-104">Například budete muset použít dvě nebo více verzí sestavení ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="081ef-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="081ef-105">Obory názvů v každé sestavení dá zabalit pomocí alias externího sestavení v úrovni kořenového adresáře obory názvů s názvem podle aliasu, odkud můžou použít ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="081ef-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="081ef-106">[Extern](../../../csharp/language-reference/keywords/extern.md) – klíčové slovo se také používá jako metodu modifikátoru deklarace metody napsanou v nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="081ef-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="081ef-107">Odkazování na dvou sestavení se stejnými názvy plně kvalifikovaný typ, je nutné zadat alias příkazového řádku, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="081ef-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="081ef-108">Tím se vytvoří externí aliasy `GridV1` a `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="081ef-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="081ef-109">Pokud chcete použít tyto aliasy z v rámci programu, je odkazovat pomocí `extern` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="081ef-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="081ef-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="081ef-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="081ef-111">Zavádí další úrovni pro kořenový obor názvů služby, která parallels (ale neleží v) každé externí deklarace aliasu globálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="081ef-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="081ef-112">Proto typy z každé sestavení lze odkazovat na bez nejednoznačnost pomocí jejich plně kvalifikovaný název v příslušné aliasu oboru názvů root.</span><span class="sxs-lookup"><span data-stu-id="081ef-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="081ef-113">V předchozím příkladu `GridV1::Grid` bude ovládací prvek mřížky z `grid.dll`, a `GridV2::Grid` bude ovládací prvek mřížky z `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="081ef-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="081ef-114">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="081ef-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="081ef-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="081ef-115">See also</span></span>

- [<span data-ttu-id="081ef-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="081ef-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="081ef-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="081ef-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="081ef-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="081ef-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="081ef-119">:: – operátor</span><span class="sxs-lookup"><span data-stu-id="081ef-119">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)
- [<span data-ttu-id="081ef-120">/ Reference (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="081ef-120">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
