---
description: Reference Get-C#
title: Reference Get-C#
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 7e13dc3ed6577717c64b4e36000a9e090f7b4751
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139733"
---
# <a name="get-c-reference"></a><span data-ttu-id="dc72b-103">get (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="dc72b-103">get (C# Reference)</span></span>

<span data-ttu-id="dc72b-104">`get`Klíčové slovo definuje metodu *přístupového objektu* ve vlastnosti nebo indexeru, který vrací hodnotu vlastnosti nebo prvek indexeru.</span><span class="sxs-lookup"><span data-stu-id="dc72b-104">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="dc72b-105">Další informace najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md) a [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="dc72b-105">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="dc72b-106">Následující příklad definuje jak `get` a `set` přístup k vlastnosti s názvem `Seconds` .</span><span class="sxs-lookup"><span data-stu-id="dc72b-106">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="dc72b-107">K zálohování hodnoty vlastnosti používá soukromé pole s názvem `_seconds` .</span><span class="sxs-lookup"><span data-stu-id="dc72b-107">It uses a private field named `_seconds` to back the property value.</span></span>  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="dc72b-108">`get`Přistupující objekt se často skládá z jediného příkazu, který vrací hodnotu, stejně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="dc72b-108">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="dc72b-109">Počínaje jazykem C# 7,0 můžete implementovat `get` přistupující objekt jako člena Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="dc72b-109">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="dc72b-110">Následující příklad implementuje rozhraní `get` a `set` přístup jako členy Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="dc72b-110">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

<span data-ttu-id="dc72b-111">Pro jednoduché případy, kdy přístup k vlastnostem `get` a `set` přistupující objekty neprovádí žádnou jinou operaci než nastavení nebo načtení hodnoty v soukromém poli pro zálohování, můžete využít podporu kompilátoru C# pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dc72b-111">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="dc72b-112">Následující příklad implementuje `Hours` jako automaticky implementovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dc72b-112">The following example implements `Hours` as an auto-implemented property.</span></span>
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="dc72b-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dc72b-113">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dc72b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc72b-114">See also</span></span>

- [<span data-ttu-id="dc72b-115">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dc72b-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dc72b-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="dc72b-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dc72b-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dc72b-117">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="dc72b-118">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dc72b-118">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
