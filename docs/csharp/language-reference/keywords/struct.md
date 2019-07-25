---
title: struktura – C# referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 1f1c512e1995df07fc4b9e18e34a85119e270bda
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433773"
---
# <a name="struct-c-reference"></a><span data-ttu-id="8d642-102">struct (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8d642-102">struct (C# Reference)</span></span>

<span data-ttu-id="8d642-103">`struct` Typ je typ hodnoty, který se obvykle používá k zapouzdření malých skupin souvisejících proměnných, například souřadnicích obdélníku nebo vlastností položky v inventáři.</span><span class="sxs-lookup"><span data-stu-id="8d642-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="8d642-104">Následující příklad ukazuje jednoduchou deklaraci struktury:</span><span class="sxs-lookup"><span data-stu-id="8d642-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="8d642-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d642-105">Remarks</span></span>

<span data-ttu-id="8d642-106">Struktury mohou také obsahovat [konstruktory](../../programming-guide/classes-and-structs/constructors.md), [konstanty](../../programming-guide/classes-and-structs/constants.md), [pole](../../programming-guide/classes-and-structs/fields.md), [metody](../../programming-guide/classes-and-structs/methods.md), [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [indexery](../../programming-guide/indexers/index.md), [operátory](../../programming-guide/statements-expressions-operators/operators.md), [události](../../programming-guide/events/index.md)a [vnořené typy](../../programming-guide/classes-and-structs/nested-types.md), i když je několik takových členů požadováno, měli byste zvážit, že místo toho napište třídu typu.</span><span class="sxs-lookup"><span data-stu-id="8d642-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../../programming-guide/statements-expressions-operators/operators.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="8d642-107">Příklady najdete v tématu [použití struktur](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="8d642-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="8d642-108">Struktury můžou implementovat rozhraní, ale nemůžou dědit z jiné struktury.</span><span class="sxs-lookup"><span data-stu-id="8d642-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="8d642-109">Z tohoto důvodu členy struktury nelze deklarovat jako `protected`.</span><span class="sxs-lookup"><span data-stu-id="8d642-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="8d642-110">Další informace najdete v tématu [struktury](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="8d642-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="8d642-111">Příklady</span><span class="sxs-lookup"><span data-stu-id="8d642-111">Examples</span></span>

<span data-ttu-id="8d642-112">Příklady a další informace najdete v tématu [použití struktur](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="8d642-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8d642-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8d642-113">C# language specification</span></span>

<span data-ttu-id="8d642-114">Příklady najdete v tématu [použití struktur](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="8d642-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d642-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d642-115">See also</span></span>

- [<span data-ttu-id="8d642-116">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="8d642-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8d642-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8d642-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8d642-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8d642-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8d642-119">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="8d642-119">Default Values Table</span></span>](default-values-table.md)
- [<span data-ttu-id="8d642-120">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="8d642-120">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="8d642-121">Typy</span><span class="sxs-lookup"><span data-stu-id="8d642-121">Types</span></span>](types.md)
- [<span data-ttu-id="8d642-122">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="8d642-122">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="8d642-123">class</span><span class="sxs-lookup"><span data-stu-id="8d642-123">class</span></span>](class.md)
- [<span data-ttu-id="8d642-124">interface</span><span class="sxs-lookup"><span data-stu-id="8d642-124">interface</span></span>](interface.md)
- [<span data-ttu-id="8d642-125">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="8d642-125">Classes and Structs</span></span>](../../programming-guide/classes-and-structs/index.md)
