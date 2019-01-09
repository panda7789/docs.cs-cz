---
title: set – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 0322f1bb94174dd3a0cdd2089c8626d25a80cc1c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147990"
---
# <a name="set-c-reference"></a><span data-ttu-id="b04a6-102">set (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b04a6-102">set (C# Reference)</span></span>

<span data-ttu-id="b04a6-103">`set` Definuje – klíčové slovo *přistupující objekt* metoda ve vlastnosti nebo indexovacího člena, který se přiřadí hodnotu k vlastnosti nebo elementu indexeru.</span><span class="sxs-lookup"><span data-stu-id="b04a6-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="b04a6-104">Další informace a příklady najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), a [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="b04a6-104">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="b04a6-105">Následující příklad definuje i `get` a `set` přístupový objekt pro vlastnost s názvem `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="b04a6-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="b04a6-106">Používá soukromé pole s názvem `_seconds` zálohovat hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b04a6-106">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="b04a6-107">Často se stává `set` přístupový objekt se skládá z jednoho příkazu, který přiřazuje hodnotu, stejně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b04a6-107">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="b04a6-108">Od verze C# 7.0, můžete implementovat `set` přístupového objektu jako člena s výrazem v těle.</span><span class="sxs-lookup"><span data-stu-id="b04a6-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="b04a6-109">Následující příklad implementuje oba `get` a `set` přistupující objekty jako členy s výrazem v těle.</span><span class="sxs-lookup"><span data-stu-id="b04a6-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="b04a6-110">Pro jednoduché případech, ve kterém vlastnosti `get` a `set` přistupující objekty provádět žádné jiné operace než nastavení nebo načtení hodnoty v poli privátní zálohování, můžete využít výhod podpory kompilátor jazyka C# pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b04a6-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="b04a6-111">Následující příklad implementuje `Hours` jako automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b04a6-111">The following example implements `Hours` as an auto-implemented property.</span></span> 

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="b04a6-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b04a6-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b04a6-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b04a6-113">See also</span></span>

- [<span data-ttu-id="b04a6-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b04a6-114">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="b04a6-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b04a6-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b04a6-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b04a6-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b04a6-117">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b04a6-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
