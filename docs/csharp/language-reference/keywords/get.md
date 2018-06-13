---
title: get (Referenční dokumentace jazyka C#)
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 671cadce0bd120ec0728562ec448b2ce6edf2dd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216106"
---
# <a name="get-c-reference"></a><span data-ttu-id="9a2b6-102">get (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9a2b6-102">get (C# Reference)</span></span>

<span data-ttu-id="9a2b6-103">`get` Definuje – klíčové slovo *přistupujícího objektu* metoda ve vlastnosti nebo indexer, který vrací hodnoty vlastnosti nebo indexer element.</span><span class="sxs-lookup"><span data-stu-id="9a2b6-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="9a2b6-104">Další informace najdete v tématu [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) a [indexery](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="9a2b6-104">For more information, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="9a2b6-105">V následujícím příkladu definuje, jak `get` a `set` přistupující objekt pro vlastnost s názvem `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="9a2b6-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="9a2b6-106">Používá soukromé pole s názvem `_seconds` zálohovat hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9a2b6-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="9a2b6-107">Často `get` přistupujícího objektu se skládá z jednoho příkazu, který vrátí hodnotu, stejně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9a2b6-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="9a2b6-108">Od verze 7.0 C#, můžete implementovat `get` přistupujícího objektu jako výraz vozidlo člena.</span><span class="sxs-lookup"><span data-stu-id="9a2b6-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="9a2b6-109">Následující příklad implementuje i `get` a `set` přistupujícího objektu jako výraz vozidlo členy.</span><span class="sxs-lookup"><span data-stu-id="9a2b6-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="9a2b6-110">Pro jednoduché případy, kdy vlastnost `get` a `set` přístupové objekty provádět žádné operace, než nastavení nebo načtení hodnotu v poli privátní zálohování, můžete využít výhod podpory kompilátoru C# pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9a2b6-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="9a2b6-111">Následující příklad implementuje `Hours` jako ve automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9a2b6-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9a2b6-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a2b6-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a2b6-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a2b6-113">See Also</span></span>  
 [<span data-ttu-id="9a2b6-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a2b6-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9a2b6-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9a2b6-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 <span data-ttu-id="9a2b6-116">[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md) [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)</span><span class="sxs-lookup"><span data-stu-id="9a2b6-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md)</span></span>
