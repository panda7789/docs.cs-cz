---
title: Provedení levých vnějších spojení (LINQ v C#)
description: Zjistěte, jak provádět levé vnější spojení pomocí LINQ v C#.
ms.date: 12/01/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: cc08a1c8670623a10d1e0bf10221d02037a8d7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688576"
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="32858-103">Provedení levých vnějších spojení</span><span class="sxs-lookup"><span data-stu-id="32858-103">Perform left outer joins</span></span>

<span data-ttu-id="32858-104">Levé vnější spojení je spojení, ve kterém je vrácena každý prvek první kolekce, bez ohledu na to, zda má všechny korelované prvky v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="32858-104">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="32858-105">Linq můžete použít k provedení levé vnější <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> spojení voláním metody na výsledky spojení skupiny.</span><span class="sxs-lookup"><span data-stu-id="32858-105">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>

## <a name="example"></a><span data-ttu-id="32858-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="32858-106">Example</span></span>

<span data-ttu-id="32858-107">Následující příklad ukazuje, jak <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> použít metodu na výsledky spojení skupiny k provedení levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="32858-107">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>

<span data-ttu-id="32858-108">Prvním krokem při vytváření levé vnější spojení dvou kolekcí je provést vnitřní spojení pomocí spojení skupiny.</span><span class="sxs-lookup"><span data-stu-id="32858-108">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="32858-109">(Vysvětlení tohoto procesu naleznete v tématu [Provedení vnitřních spojení.)](perform-inner-joins.md) V tomto příkladu `Person` je seznam objektů vnitřní připojen `Pet` k seznamu `Person` objektů `Pet.Owner`na základě objektu, který odpovídá .</span><span class="sxs-lookup"><span data-stu-id="32858-109">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>

<span data-ttu-id="32858-110">Druhým krokem je zahrnout každý prvek první (vlevo) kolekce v sadě výsledků i v případě, že tento prvek nemá žádné shody v pravé kolekci.</span><span class="sxs-lookup"><span data-stu-id="32858-110">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="32858-111">Toho je dosaženo <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> voláním na každou sekvenci odpovídající prvky ze skupiny spojení.</span><span class="sxs-lookup"><span data-stu-id="32858-111">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="32858-112">V tomto <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> příkladu se nazývá `Pet` na každé sekvenci odpovídající objekty.</span><span class="sxs-lookup"><span data-stu-id="32858-112">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="32858-113">Metoda vrátí kolekci, která obsahuje jednu výchozí `Pet` hodnotu, pokud `Person` je posloupnost odpovídajících objektů prázdná pro libovolný objekt, čímž zajistí, že každý `Person` objekt je reprezentován v kolekci výsledků.</span><span class="sxs-lookup"><span data-stu-id="32858-113">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>

> [!NOTE]
> <span data-ttu-id="32858-114">Výchozí hodnota pro typ `null`odkazu je ; proto příklad zkontroluje null odkaz před přístupem každý `Pet` prvek každé kolekce.</span><span class="sxs-lookup"><span data-stu-id="32858-114">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a><span data-ttu-id="32858-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="32858-115">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="32858-116">Provádění vnitřních spojení</span><span class="sxs-lookup"><span data-stu-id="32858-116">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="32858-117">Provádění seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="32858-117">Perform grouped joins</span></span>](perform-grouped-joins.md)
- [<span data-ttu-id="32858-118">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="32858-118">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
