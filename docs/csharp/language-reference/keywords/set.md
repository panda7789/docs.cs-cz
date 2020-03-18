---
title: nastavit klíčové slovo - C# Reference
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 0b293709abe64a0a82d8575f6793a07ca6c9533b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173494"
---
# <a name="set-c-reference"></a><span data-ttu-id="d33ca-102">set (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d33ca-102">set (C# Reference)</span></span>

<span data-ttu-id="d33ca-103">Klíčové `set` slovo definuje *přistupující* metodu ve vlastnosti nebo indexeru, který přiřadí hodnotu vlastnosti nebo prvku indexeru.</span><span class="sxs-lookup"><span data-stu-id="d33ca-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="d33ca-104">Další informace a příklady naleznete [v tématu Vlastnosti](../../programming-guide/classes-and-structs/properties.md), [Automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md)a [Indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="d33ca-104">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="d33ca-105">Následující příklad definuje jak `get` a `set` a a přistupující objekt pro vlastnost s názvem `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="d33ca-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="d33ca-106">Používá soukromé pole `_seconds` s názvem zpět hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d33ca-106">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="d33ca-107">Často přistupující `set` ho se skládá z jednoho příkazu, který přiřadí hodnotu, stejně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d33ca-107">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="d33ca-108">Počínaje C# 7.0, můžete `set` implementovat přistupující objekt jako člen s výrazem.</span><span class="sxs-lookup"><span data-stu-id="d33ca-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="d33ca-109">Následující příklad implementuje `get` a `set` přístupové prvky jako členy s výrazem.</span><span class="sxs-lookup"><span data-stu-id="d33ca-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="d33ca-110">Pro jednoduché případy, ve `get` kterých vlastnosti a `set` přistupující objekty provádět žádné jiné operace než nastavení nebo načítání hodnoty v soukromém záložním poli, můžete využít podpory kompilátoru Jazyka C# pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d33ca-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="d33ca-111">Následující příklad implementuje `Hours` jako automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d33ca-111">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="d33ca-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d33ca-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d33ca-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d33ca-113">See also</span></span>

- [<span data-ttu-id="d33ca-114">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d33ca-114">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="d33ca-115">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d33ca-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d33ca-116">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d33ca-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d33ca-117">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d33ca-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
