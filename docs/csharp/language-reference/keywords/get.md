---
title: get - C# Reference
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 61d8c02aaf13f43ff8ea17c1e868ea9fd52893c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173624"
---
# <a name="get-c-reference"></a><span data-ttu-id="0fc30-102">get (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0fc30-102">get (C# Reference)</span></span>

<span data-ttu-id="0fc30-103">Klíčové `get` slovo definuje *přistupující* metodu ve vlastnosti nebo indexeru, který vrací hodnotu vlastnosti nebo prvek indexeru.</span><span class="sxs-lookup"><span data-stu-id="0fc30-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="0fc30-104">Další informace naleznete [v tématu Vlastnosti](../../programming-guide/classes-and-structs/properties.md), [Automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md) a [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fc30-104">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="0fc30-105">Následující příklad definuje jak `get` a `set` a a přistupující objekt pro vlastnost s názvem `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="0fc30-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="0fc30-106">Používá soukromé pole `_seconds` s názvem zpět hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0fc30-106">It uses a private field named `_seconds` to back the property value.</span></span>  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="0fc30-107">Často přistupující `get` ho se skládá z jednoho příkazu, který vrátí hodnotu, jako tomu bylo v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0fc30-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="0fc30-108">Počínaje C# 7.0, můžete `get` implementovat přistupující objekt jako člen s výrazem.</span><span class="sxs-lookup"><span data-stu-id="0fc30-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="0fc30-109">Následující příklad implementuje `get` i `set` a přistupující ho jako členy s výrazem.</span><span class="sxs-lookup"><span data-stu-id="0fc30-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

<span data-ttu-id="0fc30-110">Pro jednoduché případy, ve `get` kterých vlastnosti a `set` přistupující objekty provádět žádné jiné operace než nastavení nebo načítání hodnoty v soukromém záložním poli, můžete využít podpory kompilátoru Jazyka C# pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0fc30-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="0fc30-111">Následující příklad implementuje `Hours` jako automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0fc30-111">The following example implements `Hours` as an auto-implemented property.</span></span>
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0fc30-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0fc30-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0fc30-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0fc30-113">See also</span></span>

- [<span data-ttu-id="0fc30-114">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0fc30-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0fc30-115">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0fc30-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0fc30-116">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="0fc30-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="0fc30-117">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0fc30-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
