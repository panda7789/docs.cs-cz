---
title: extern alias – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 891e56b064f8a327abe28293223a85b9d95e8fd3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301811"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="67275-102">externí alias (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="67275-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="67275-103">Možná budete muset odkazovat na dvě verze sestavení, které mají stejné názvy plně kvalifikovaného typu.</span><span class="sxs-lookup"><span data-stu-id="67275-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="67275-104">Například může být nutné použít dvě nebo více verzí sestavení ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="67275-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="67275-105">Pomocí externího aliasu sestavení lze obory názvů z každého sestavení zabalit do oborů názvů kořenové úrovně s názvem alias, což umožňuje jejich použití ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="67275-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67275-106">Klíčové slovo [extern](./extern.md) se používá také jako modifikátor metody a deklaruje metodu napsanou v nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="67275-106">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="67275-107">Chcete-li odkazovat na dvě sestavení se stejnými názvy plně kvalifikovaného typu, je nutné zadat alias na příkazovém řádku následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="67275-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="67275-108">Tím se vytvoří externí aliasy `GridV1` a `GridV2` .</span><span class="sxs-lookup"><span data-stu-id="67275-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="67275-109">Chcete-li tyto aliasy použít v rámci programu, odkažte je pomocí `extern` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="67275-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="67275-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="67275-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="67275-111">Každá deklarace extern alias zavádí další obor názvů na úrovni root, který je souběžně (ale neleží v rámci) globálního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="67275-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="67275-112">Typy z každého sestavení lze tedy odkazovat bez nejednoznačnosti pomocí jejich plně kvalifikovaného názvu, který je rootem v příslušném oboru názvů alias.</span><span class="sxs-lookup"><span data-stu-id="67275-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="67275-113">V předchozím příkladu by byl `GridV1::Grid` ovládací prvek mřížky z `grid.dll` a `GridV2::Grid` by byl ovládací prvek mřížky z `grid20.dll` .</span><span class="sxs-lookup"><span data-stu-id="67275-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="using-visual-studio"></a><span data-ttu-id="67275-114">Pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67275-114">Using Visual Studio</span></span>

<span data-ttu-id="67275-115">Pokud používáte aplikaci Visual Studio, mohou být aliasy poskytovány podobným způsobem.</span><span class="sxs-lookup"><span data-stu-id="67275-115">If you are using Visual Studio, aliases can be provided in similar way.</span></span>

<span data-ttu-id="67275-116">Přidejte odkaz na *grid.dll* a *grid20.dll* do projektu v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67275-116">Add reference of *grid.dll* and *grid20.dll* to your project in Visual Studio.</span></span> <span data-ttu-id="67275-117">Otevřete kartu vlastnost a změňte aliasy z Global na GridV1 a GridV2.</span><span class="sxs-lookup"><span data-stu-id="67275-117">Open a property tab and change the Aliases from global to GridV1 and GridV2 respectively.</span></span>

<span data-ttu-id="67275-118">Používat tyto aliasy stejným způsobem jako výše</span><span class="sxs-lookup"><span data-stu-id="67275-118">Use these aliases the same way above</span></span>

```csharp
 extern alias GridV1;  
  
 extern alias GridV2;  
```

<span data-ttu-id="67275-119">Nyní můžete vytvořit alias pro obor názvů nebo typ *pomocí direktivy alias*.</span><span class="sxs-lookup"><span data-stu-id="67275-119">Now you can create alias for a namespace or a type by *using alias directive*.</span></span> <span data-ttu-id="67275-120">Další informace najdete v tématu [použití direktivy](using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="67275-120">For more information, see [using directive](using-directive.md).</span></span>

```csharp
using Class1V1 = GridV1::Namespace.Class1;

using Class1V2 = GridV2::Namespace.Class1;
```

## <a name="c-language-specification"></a><span data-ttu-id="67275-121">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67275-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="67275-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67275-122">See also</span></span>

- [<span data-ttu-id="67275-123">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67275-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="67275-124">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="67275-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="67275-125">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67275-125">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="67275-126">:: – Operátor</span><span class="sxs-lookup"><span data-stu-id="67275-126">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="67275-127">-Reference (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="67275-127">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
