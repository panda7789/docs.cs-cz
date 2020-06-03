---
title: Set – klíčové slovo – Referenční dokumentace jazyka C#
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: cdd84c824cc4dc93f4433f07e9978d22cba3f245
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795063"
---
# <a name="set-c-reference"></a><span data-ttu-id="1a3bb-102">set (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1a3bb-102">set (C# Reference)</span></span>

<span data-ttu-id="1a3bb-103">`set`Klíčové slovo definuje metodu *přistupujícího objektu* ve vlastnosti nebo indexeru, která přiřadí hodnotu vlastnosti nebo prvku indexeru.</span><span class="sxs-lookup"><span data-stu-id="1a3bb-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="1a3bb-104">Další informace a příklady najdete v tématech [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md)a [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="1a3bb-104">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="1a3bb-105">Následující příklad definuje jak `get` a `set` přístup k vlastnosti s názvem `Seconds` .</span><span class="sxs-lookup"><span data-stu-id="1a3bb-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="1a3bb-106">K zálohování hodnoty vlastnosti používá soukromé pole s názvem `_seconds` .</span><span class="sxs-lookup"><span data-stu-id="1a3bb-106">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="1a3bb-107">`set`Přistupující objekt se často skládá z jediného příkazu, který přiřadí hodnotu, stejně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1a3bb-107">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="1a3bb-108">Počínaje jazykem C# 7,0 můžete implementovat `set` přistupující objekt jako člena Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="1a3bb-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="1a3bb-109">Následující příklad implementuje jak `get` a `set` přistupující objekty jako členy Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="1a3bb-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="1a3bb-110">Pro jednoduché případy, kdy přístup k vlastnostem `get` a `set` přistupující objekty neprovádí žádnou jinou operaci než nastavení nebo načtení hodnoty v soukromém poli pro zálohování, můžete využít podporu kompilátoru C# pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1a3bb-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="1a3bb-111">Následující příklad implementuje `Hours` jako automaticky implementovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1a3bb-111">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="1a3bb-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1a3bb-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1a3bb-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a3bb-113">See also</span></span>

- [<span data-ttu-id="1a3bb-114">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1a3bb-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1a3bb-115">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="1a3bb-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1a3bb-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1a3bb-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1a3bb-117">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1a3bb-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
