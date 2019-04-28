---
title: Provedení levých vnějších spojení (LINQ v JAZYKU C#)
description: Zjistěte, jak provedení levých vnějších spojení pomocí jazyka LINQ v jazyce C#.
ms.date: 12/01/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: cc08a1c8670623a10d1e0bf10221d02037a8d7bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688576"
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="c29bc-103">Provedení levých vnějších spojení</span><span class="sxs-lookup"><span data-stu-id="c29bc-103">Perform left outer joins</span></span>

<span data-ttu-id="c29bc-104">Levé vnější spojení je spojení ve kterém každý prvek první kolekce, kterou je vrácen, bez ohledu na to, jestli má korelační elementy v druhé kolekci.</span><span class="sxs-lookup"><span data-stu-id="c29bc-104">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="c29bc-105">Je možné použít k provedení levé vnější spojení voláním LINQ <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metodu na výsledky spojení skupiny.</span><span class="sxs-lookup"><span data-stu-id="c29bc-105">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>

## <a name="example"></a><span data-ttu-id="c29bc-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c29bc-106">Example</span></span>

<span data-ttu-id="c29bc-107">Následující příklad ukazuje způsob použití <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metodu na výsledky spojení skupiny k provedení levé vnější spojení.</span><span class="sxs-lookup"><span data-stu-id="c29bc-107">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>

<span data-ttu-id="c29bc-108">Prvním krokem při vytváření levé vnější spojení dvou kolekcí je provedení vnitřního spojení pomocí spojení skupiny.</span><span class="sxs-lookup"><span data-stu-id="c29bc-108">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="c29bc-109">(Viz [provádění vnitřních spojení](perform-inner-joins.md) vysvětlení tohoto procesu.) V tomto příkladu seznam `Person` objekty je vnitřní připojené k seznamu `Pet` na základě objektů `Person` objekt, který odpovídá `Pet.Owner`.</span><span class="sxs-lookup"><span data-stu-id="c29bc-109">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>

<span data-ttu-id="c29bc-110">Druhým krokem je zahrnout všechny prvky objektu první (vlevo) kolekce i v případě, že tento element nemá žádné odpovídající položky v kolekci správné sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="c29bc-110">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="c29bc-111">To lze provést zavoláním <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> na každou sekvenci odpovídající prvky ze skupiny spojení.</span><span class="sxs-lookup"><span data-stu-id="c29bc-111">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="c29bc-112">V tomto příkladu <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> volat pro každou sekvenci odpovídající `Pet` objekty.</span><span class="sxs-lookup"><span data-stu-id="c29bc-112">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="c29bc-113">Metoda vrátí kolekci, která obsahuje pouze jednu, výchozí hodnotu, pokud posloupnost odpovídající `Pet` objekty je prázdný na žádném `Person` objektu, a zajistí tak každý `Person` objekt je reprezentován v kolekci výsledek.</span><span class="sxs-lookup"><span data-stu-id="c29bc-113">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>

> [!NOTE]
> <span data-ttu-id="c29bc-114">Výchozí hodnota pro typ odkazu je `null`; proto příklad vyhledává odkaz s hodnotou null před přístupem k každý prvek každého `Pet` kolekce.</span><span class="sxs-lookup"><span data-stu-id="c29bc-114">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a><span data-ttu-id="c29bc-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c29bc-115">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="c29bc-116">Provádění vnitřních spojení</span><span class="sxs-lookup"><span data-stu-id="c29bc-116">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="c29bc-117">Provádění seskupených spojení</span><span class="sxs-lookup"><span data-stu-id="c29bc-117">Perform grouped joins</span></span>](perform-grouped-joins.md)
- [<span data-ttu-id="c29bc-118">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="c29bc-118">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
