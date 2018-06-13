---
title: struct (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: ddea59e76835ccccd07c299f819796336cddada8
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172146"
---
# <a name="struct-c-reference"></a><span data-ttu-id="9cae4-102">struct (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9cae4-102">struct (C# Reference)</span></span>
<span data-ttu-id="9cae4-103">A `struct` typ je typ hodnoty, které se obvykle používá k zapouzdření malé skupiny související proměnných, například souřadnice obdélníku nebo charakteristiky položky v inventář.</span><span class="sxs-lookup"><span data-stu-id="9cae4-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="9cae4-104">Následující příklad ukazuje deklaraci jednoduchá struktura:</span><span class="sxs-lookup"><span data-stu-id="9cae4-104">The following example shows a simple struct declaration:</span></span>  
  
```csharp  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="9cae4-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9cae4-105">Remarks</span></span>  
 <span data-ttu-id="9cae4-106">Struktury může také obsahovat [konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md), [konstanty](../../../csharp/programming-guide/classes-and-structs/constants.md), [pole](../../../csharp/programming-guide/classes-and-structs/fields.md), [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexery](../../../csharp/programming-guide/indexers/index.md), [operátory](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [události](../../../csharp/programming-guide/events/index.md), a [vnořené typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md), i když je-li několik tito členové jsou povinné, můžete Zvažte, Příprava vašeho typu třídy místo.</span><span class="sxs-lookup"><span data-stu-id="9cae4-106">Structs can also contain [constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constants](../../../csharp/programming-guide/classes-and-structs/constants.md), [fields](../../../csharp/programming-guide/classes-and-structs/fields.md), [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexers](../../../csharp/programming-guide/indexers/index.md), [operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [events](../../../csharp/programming-guide/events/index.md), and [nested types](../../../csharp/programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>  
  
 <span data-ttu-id="9cae4-107">Příklady najdete v tématu [pomocí struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="9cae4-107">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
 <span data-ttu-id="9cae4-108">Struktury můžete implementovat rozhraní, ale nemohou dědit z jiné struktury.</span><span class="sxs-lookup"><span data-stu-id="9cae4-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="9cae4-109">Z tohoto důvodu členy struktury nelze deklarovat jako `protected`.</span><span class="sxs-lookup"><span data-stu-id="9cae4-109">For that reason, struct members cannot be declared as `protected`.</span></span>  
  
 <span data-ttu-id="9cae4-110">Další informace najdete v tématu [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="9cae4-110">For more information, see [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9cae4-111">Příklady</span><span class="sxs-lookup"><span data-stu-id="9cae4-111">Examples</span></span>  
 <span data-ttu-id="9cae4-112">Příklady a další informace najdete v tématu [pomocí struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="9cae4-112">For examples and more information, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9cae4-113">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9cae4-113">C# Language Specification</span></span>  
 <span data-ttu-id="9cae4-114">Příklady najdete v tématu [pomocí struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="9cae4-114">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cae4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cae4-115">See Also</span></span>  
 [<span data-ttu-id="9cae4-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9cae4-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9cae4-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9cae4-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9cae4-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9cae4-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9cae4-119">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="9cae4-119">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="9cae4-120">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="9cae4-120">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="9cae4-121">Typy</span><span class="sxs-lookup"><span data-stu-id="9cae4-121">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="9cae4-122">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="9cae4-122">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="9cae4-123">class</span><span class="sxs-lookup"><span data-stu-id="9cae4-123">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="9cae4-124">interface</span><span class="sxs-lookup"><span data-stu-id="9cae4-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
 [<span data-ttu-id="9cae4-125">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="9cae4-125">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
