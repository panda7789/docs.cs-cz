---
title: struct (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 46cf0b66a50685a717818fe762ad4f1de36d6156
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185742"
---
# <a name="struct-c-reference"></a><span data-ttu-id="fe643-102">struct (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fe643-102">struct (C# Reference)</span></span>

<span data-ttu-id="fe643-103">A `struct` typ je typ hodnoty, které se obvykle používá k zapouzdření malé skupiny příbuzných proměnných, jako je například souřadnice obdélník nebo vlastnosti položky v inventář.</span><span class="sxs-lookup"><span data-stu-id="fe643-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="fe643-104">Následující příklad ukazuje deklaraci jednoduchá struktura:</span><span class="sxs-lookup"><span data-stu-id="fe643-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="fe643-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe643-105">Remarks</span></span>

<span data-ttu-id="fe643-106">Struktury mohou také obsahovat [konstruktory](../../programming-guide/classes-and-structs/constructors.md), [konstanty](../../programming-guide/classes-and-structs/constants.md), [pole](../../programming-guide/classes-and-structs/fields.md), [metody](../../programming-guide/classes-and-structs/methods.md), [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [indexery](../../programming-guide/indexers/index.md), [operátory](../../programming-guide/statements-expressions-operators/operators.md), [události](../../programming-guide/events/index.md), a [vnořené typy](../../programming-guide/classes-and-structs/nested-types.md), i když je-li několik těchto členů jsou povinné, můžete Zvažte, Příprava vašeho typu třídy místo toho.</span><span class="sxs-lookup"><span data-stu-id="fe643-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../../programming-guide/statements-expressions-operators/operators.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="fe643-107">Příklady najdete v tématu [pomocí struktury](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="fe643-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="fe643-108">Struktury můžou implementovat rozhraní, ale nemůže dědit z jiné struktury.</span><span class="sxs-lookup"><span data-stu-id="fe643-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="fe643-109">Z tohoto důvodu členy struktury nelze deklarovat jako `protected`.</span><span class="sxs-lookup"><span data-stu-id="fe643-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="fe643-110">Další informace najdete v tématu [struktury](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="fe643-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="fe643-111">Příklady</span><span class="sxs-lookup"><span data-stu-id="fe643-111">Examples</span></span>

<span data-ttu-id="fe643-112">Příklady a další informace najdete v tématu [pomocí struktury](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="fe643-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fe643-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fe643-113">C# language specification</span></span>

<span data-ttu-id="fe643-114">Příklady najdete v tématu [pomocí struktury](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="fe643-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe643-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe643-115">See also</span></span>

- [<span data-ttu-id="fe643-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fe643-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fe643-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fe643-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fe643-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fe643-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fe643-119">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="fe643-119">Default Values Table</span></span>](default-values-table.md)
- [<span data-ttu-id="fe643-120">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="fe643-120">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="fe643-121">Typy</span><span class="sxs-lookup"><span data-stu-id="fe643-121">Types</span></span>](types.md)
- [<span data-ttu-id="fe643-122">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="fe643-122">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="fe643-123">class</span><span class="sxs-lookup"><span data-stu-id="fe643-123">class</span></span>](class.md)
- [<span data-ttu-id="fe643-124">interface</span><span class="sxs-lookup"><span data-stu-id="fe643-124">interface</span></span>](interface.md)
- [<span data-ttu-id="fe643-125">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="fe643-125">Classes and Structs</span></span>](../../programming-guide/classes-and-structs/index.md)