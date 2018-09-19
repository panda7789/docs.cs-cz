---
title: get (Referenční dokumentace jazyka C#)
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 182f7164ad929232c185903a3dbf024a2e5d22a7
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45987783"
---
# <a name="get-c-reference"></a><span data-ttu-id="67fe4-102">get (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="67fe4-102">get (C# Reference)</span></span>

<span data-ttu-id="67fe4-103">`get` Definuje – klíčové slovo *přistupující objekt* metoda ve vlastnosti nebo indexeru, které vrací hodnotu vlastnosti nebo elementu indexeru.</span><span class="sxs-lookup"><span data-stu-id="67fe4-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="67fe4-104">Další informace najdete v tématu [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md), [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) a [indexery](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="67fe4-104">For more information, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="67fe4-105">Následující příklad definuje i `get` a `set` přístupový objekt pro vlastnost s názvem `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="67fe4-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="67fe4-106">Používá soukromé pole s názvem `_seconds` zálohovat hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="67fe4-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="67fe4-107">Často se stává `get` přístupový objekt se skládá z jednoho příkazu, který vrací hodnotu, stejně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="67fe4-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="67fe4-108">Od verze C# 7.0, můžete implementovat `get` přístupového objektu jako člena s výrazem v těle.</span><span class="sxs-lookup"><span data-stu-id="67fe4-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="67fe4-109">Následující příklad implementuje oba `get` a `set` přístupového objektu jako členy s výrazem v těle.</span><span class="sxs-lookup"><span data-stu-id="67fe4-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="67fe4-110">Pro jednoduché případech, ve kterém vlastnosti `get` a `set` přistupující objekty provádět žádné jiné operace než nastavení nebo načtení hodnoty v poli privátní zálohování, můžete využít výhod podpory kompilátor jazyka C# pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="67fe4-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="67fe4-111">Následující příklad implementuje `Hours` jako automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="67fe4-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="67fe4-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67fe4-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="67fe4-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="67fe4-113">See Also</span></span>

- [<span data-ttu-id="67fe4-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67fe4-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="67fe4-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="67fe4-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="67fe4-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67fe4-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="67fe4-117">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="67fe4-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
