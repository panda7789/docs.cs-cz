---
description: Set – klíčové slovo – Referenční dokumentace jazyka C#
title: Set – klíčové slovo – Referenční dokumentace jazyka C#
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: ff0c99e5d4d6271351783befd6650d9a77f39886
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136912"
---
# <a name="set-c-reference"></a><span data-ttu-id="c911b-103">set (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c911b-103">set (C# Reference)</span></span>

<span data-ttu-id="c911b-104">`set`Klíčové slovo definuje metodu *přistupujícího objektu* ve vlastnosti nebo indexeru, která přiřadí hodnotu vlastnosti nebo prvku indexeru.</span><span class="sxs-lookup"><span data-stu-id="c911b-104">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="c911b-105">Další informace a příklady najdete v tématech [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md)a [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="c911b-105">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="c911b-106">Následující příklad definuje jak `get` a `set` přístup k vlastnosti s názvem `Seconds` .</span><span class="sxs-lookup"><span data-stu-id="c911b-106">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="c911b-107">K zálohování hodnoty vlastnosti používá soukromé pole s názvem `_seconds` .</span><span class="sxs-lookup"><span data-stu-id="c911b-107">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="c911b-108">`set`Přistupující objekt se často skládá z jediného příkazu, který přiřadí hodnotu, stejně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c911b-108">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="c911b-109">Počínaje jazykem C# 7,0 můžete implementovat `set` přistupující objekt jako člena Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="c911b-109">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="c911b-110">Následující příklad implementuje jak `get` a `set` přistupující objekty jako členy Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="c911b-110">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="c911b-111">Pro jednoduché případy, kdy přístup k vlastnostem `get` a `set` přistupující objekty neprovádí žádnou jinou operaci než nastavení nebo načtení hodnoty v soukromém poli pro zálohování, můžete využít podporu kompilátoru C# pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c911b-111">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="c911b-112">Následující příklad implementuje `Hours` jako automaticky implementovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c911b-112">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="c911b-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c911b-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c911b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c911b-114">See also</span></span>

- [<span data-ttu-id="c911b-115">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c911b-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c911b-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c911b-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c911b-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c911b-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c911b-118">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c911b-118">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
