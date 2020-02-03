---
title: struktura – C# referenční informace
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 8d9a23a0813423571c894758257b284ad67a72e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744644"
---
# <a name="struct-c-reference"></a><span data-ttu-id="359ef-102">struct (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="359ef-102">struct (C# Reference)</span></span>

<span data-ttu-id="359ef-103">Typ `struct` je typ hodnoty, který se obvykle používá k zapouzdření malých skupin souvisejících proměnných, například souřadnicích obdélníku nebo vlastností položky v inventáři.</span><span class="sxs-lookup"><span data-stu-id="359ef-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="359ef-104">Následující příklad ukazuje jednoduchou deklaraci struktury:</span><span class="sxs-lookup"><span data-stu-id="359ef-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="359ef-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="359ef-105">Remarks</span></span>

<span data-ttu-id="359ef-106">Struktury mohou také obsahovat [konstruktory](../../programming-guide/classes-and-structs/constructors.md), [konstanty](../../programming-guide/classes-and-structs/constants.md), [pole](../../programming-guide/classes-and-structs/fields.md), [metody](../../programming-guide/classes-and-structs/methods.md), [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [indexery](../../programming-guide/indexers/index.md), [operátory](../operators/index.md), [události](../../programming-guide/events/index.md)a [vnořené typy](../../programming-guide/classes-and-structs/nested-types.md), i když Pokud je vyžadováno několik takových členů, měli byste zvážit místo toho, aby typ obsahoval třídu.</span><span class="sxs-lookup"><span data-stu-id="359ef-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../operators/index.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="359ef-107">Příklady najdete v tématu [použití struktur](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="359ef-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="359ef-108">Struktury můžou implementovat rozhraní, ale nemůžou dědit z jiné struktury.</span><span class="sxs-lookup"><span data-stu-id="359ef-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="359ef-109">Z tohoto důvodu členy struktury nelze deklarovat jako `protected`.</span><span class="sxs-lookup"><span data-stu-id="359ef-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="359ef-110">Další informace najdete v tématu [struktury](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="359ef-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="359ef-111">Příklady</span><span class="sxs-lookup"><span data-stu-id="359ef-111">Examples</span></span>

<span data-ttu-id="359ef-112">Příklady a další informace najdete v tématu [použití struktur](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="359ef-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="359ef-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="359ef-113">C# language specification</span></span>

<span data-ttu-id="359ef-114">Příklady najdete v tématu [použití struktur](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="359ef-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="359ef-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="359ef-115">See also</span></span>

- [<span data-ttu-id="359ef-116">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="359ef-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="359ef-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="359ef-117">C# keywords</span></span>](index.md)
- [<span data-ttu-id="359ef-118">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="359ef-118">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="359ef-119">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="359ef-119">Value types</span></span>](../builtin-types/value-types.md)
- [<span data-ttu-id="359ef-120">class</span><span class="sxs-lookup"><span data-stu-id="359ef-120">class</span></span>](class.md)
- [<span data-ttu-id="359ef-121">interface</span><span class="sxs-lookup"><span data-stu-id="359ef-121">interface</span></span>](interface.md)
- [<span data-ttu-id="359ef-122">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="359ef-122">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
