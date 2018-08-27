---
title: set (Referenční dokumentace jazyka C#)
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 1a79dfb07ee28aaa203e648d50344bfe39c84d88
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934068"
---
# <a name="set-c-reference"></a><span data-ttu-id="b2043-102">set (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b2043-102">set (C# Reference)</span></span>
<span data-ttu-id="b2043-103">`set` Definuje – klíčové slovo *přistupující objekt* metoda ve vlastnosti nebo indexovacího člena, který se přiřadí hodnotu k vlastnosti nebo elementu indexeru.</span><span class="sxs-lookup"><span data-stu-id="b2043-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="b2043-104">Další informace a příklady najdete v tématu [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md), [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), a [indexery](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="b2043-104">For more information and examples, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="b2043-105">Následující příklad definuje i `get` a `set` přístupový objekt pro vlastnost s názvem `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="b2043-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="b2043-106">Používá soukromé pole s názvem `_seconds` zálohovat hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b2043-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

<span data-ttu-id="b2043-107">Často se stává `set` přístupový objekt se skládá z jednoho příkazu, který vrací hodnotu, stejně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b2043-107">Often, the `set` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="b2043-108">Od verze C# 7.0, můžete implementovat `set` přístupového objektu jako člena s výrazem v těle.</span><span class="sxs-lookup"><span data-stu-id="b2043-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="b2043-109">Následující příklad implementuje oba `get` a `set` přistupující objekty jako členy s výrazem v těle.</span><span class="sxs-lookup"><span data-stu-id="b2043-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

 [!code-csharp[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
<span data-ttu-id="b2043-110">Pro jednoduché případech, ve kterém vlastnosti `get` a `set` přistupující objekty provádět žádné jiné operace než nastavení nebo načtení hodnoty v poli privátní zálohování, můžete využít výhod podpory kompilátor jazyka C# pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b2043-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="b2043-111">Následující příklad implementuje `Hours` jako automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b2043-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a><span data-ttu-id="b2043-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b2043-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b2043-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2043-113">See Also</span></span>

- [<span data-ttu-id="b2043-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b2043-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b2043-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b2043-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b2043-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b2043-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="b2043-117">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b2043-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
