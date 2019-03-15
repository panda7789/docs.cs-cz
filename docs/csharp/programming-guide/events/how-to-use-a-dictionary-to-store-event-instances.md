---
title: 'Postupy: použití slovníku k ukládání instancí událostí - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 03/11/2019
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: f8522e499887398402f63c7788bbc6c6c4f57782
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57845268"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="30198-102">Postupy: použití slovníku k ukládání instancí událostí (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="30198-102">How to: use a dictionary to store event instances (C# Programming Guide)</span></span>

<span data-ttu-id="30198-103">Jedním použitím `add` a `remove` vlastních přístupových objektů událostí je zveřejnit mnoho událostí bez přidělování pole pro každou událost, ale místo toho používat <xref:System.Collections.Generic.Dictionary%602> instance k ukládání instancí událostí, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="30198-103">One use for the `add` and `remove` custom event accessors is to expose many events without allocating a field for each event, but instead using a <xref:System.Collections.Generic.Dictionary%602> instance to store the event instances, as the example below demonstrates.</span></span> <span data-ttu-id="30198-104">To je užitečné pouze, pokud typ má mnoho událostí, ale očekáváte, že většina události se přihlásit k odběru.</span><span class="sxs-lookup"><span data-stu-id="30198-104">This is only useful if a type has many events, but you expect that most of the events will not be subscribed to.</span></span>

[!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]

<span data-ttu-id="30198-105">Tato implementace odpovídá chování [přidávání a odebírání delegáti](~/_csharplang/spec/delegates.md#delegate-invocation) v C# specifikace jazyka.</span><span class="sxs-lookup"><span data-stu-id="30198-105">This implementation conforms to the behavior for [adding and removing delegates](~/_csharplang/spec/delegates.md#delegate-invocation) in the C# language specification.</span></span>

<span data-ttu-id="30198-106">Všimněte si, že [Zámek](../../language-reference/keywords/lock-statement.md) prohlášení se používá jenom s *přístup* slovník s obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="30198-106">Note that the [lock](../../language-reference/keywords/lock-statement.md) statement is used only to *access* the dictionary with event handlers.</span></span> <span data-ttu-id="30198-107">Není vyvolat obslužnou rutinu události uvnitř těla `lock` příkaz, protože by mohly vést k zablokování nebo uzamknout kolize.</span><span class="sxs-lookup"><span data-stu-id="30198-107">Don't invoke an event handler inside the body of the `lock` statement, as it could lead to deadlocks or lock contention.</span></span>

## <a name="see-also"></a><span data-ttu-id="30198-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30198-108">See also</span></span>

- [<span data-ttu-id="30198-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="30198-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="30198-110">Události</span><span class="sxs-lookup"><span data-stu-id="30198-110">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="30198-111">Delegáti</span><span class="sxs-lookup"><span data-stu-id="30198-111">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
