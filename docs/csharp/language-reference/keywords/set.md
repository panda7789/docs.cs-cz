---
title: set (Referenční dokumentace jazyka C#)
ms.date: 03/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b095520326c439601caa8fefa458dda75ba603e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="set-c-reference"></a><span data-ttu-id="5a5e1-102">set (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5a5e1-102">set (C# Reference)</span></span>
<span data-ttu-id="5a5e1-103">`set` Definuje – klíčové slovo *přistupujícího objektu* metoda ve vlastnosti nebo indexer, který přiřazuje hodnotu pro vlastnost nebo indexer element.</span><span class="sxs-lookup"><span data-stu-id="5a5e1-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="5a5e1-104">Další informace a příklady naleznete v tématu [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), a [indexery](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a5e1-104">For more information and examples, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="5a5e1-105">V následujícím příkladu definuje, jak `get` a `set` přistupující objekt pro vlastnost s názvem `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="5a5e1-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="5a5e1-106">Používá soukromé pole s názvem `_seconds` zálohovat hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5a5e1-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

<span data-ttu-id="5a5e1-107">Často `set` přistupujícího objektu se skládá z jednoho příkazu, který vrátí hodnotu, stejně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5a5e1-107">Often, the `set` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="5a5e1-108">Od verze 7.0 C#, můžete implementovat `set` přistupujícího objektu jako výraz vozidlo člena.</span><span class="sxs-lookup"><span data-stu-id="5a5e1-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="5a5e1-109">Následující příklad implementuje i `get` a `set` přístupových objektů jako výraz vozidlo členy.</span><span class="sxs-lookup"><span data-stu-id="5a5e1-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

 [!code-csharp[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
<span data-ttu-id="5a5e1-110">Pro jednoduché případy, kdy vlastnost `get` a `set` přístupové objekty provádět žádné operace, než nastavení nebo načtení hodnotu v poli privátní zálohování, můžete využít výhod podpory kompilátoru C# pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5a5e1-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="5a5e1-111">Následující příklad implementuje `Hours` jako ve automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5a5e1-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a><span data-ttu-id="5a5e1-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5a5e1-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5a5e1-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a5e1-113">See Also</span></span>  
 [<span data-ttu-id="5a5e1-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5a5e1-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5a5e1-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5a5e1-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5a5e1-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5a5e1-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5a5e1-117">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5a5e1-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
