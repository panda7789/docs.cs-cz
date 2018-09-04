---
title: Provedení levých vnějších spojení (LINQ v JAZYKU C#)
description: Zjistěte, jak provedení levých vnějších spojení pomocí jazyka LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: 329fe9e17640931c5eb39b33b791a7a77a6f7b89
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506593"
---
# <a name="perform-left-outer-joins"></a>Provedení levých vnějších spojení

Levé vnější spojení je spojení ve kterém každý prvek první kolekce, kterou je vrácen, bez ohledu na to, jestli má korelační elementy v druhé kolekci. Je možné použít k provedení levé vnější spojení voláním LINQ <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metodu na výsledky spojení skupiny.

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metodu na výsledky spojení skupiny k provedení levé vnější spojení.

Prvním krokem při vytváření levé vnější spojení dvou kolekcí je provedení vnitřního spojení pomocí spojení skupiny. (Viz [provádění vnitřních spojení](perform-inner-joins.md) vysvětlení tohoto procesu.) V tomto příkladu seznam `Person` objekty je vnitřní připojené k seznamu `Pet` na základě objektů `Person` objekt, který odpovídá `Pet.Owner`.

Druhým krokem je zahrnout všechny prvky objektu první (vlevo) kolekce i v případě, že tento element nemá žádné odpovídající položky v kolekci správné sady výsledků. To lze provést zavoláním <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> na každou sekvenci odpovídající prvky ze skupiny spojení. V tomto příkladu <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> volat pro každou sekvenci odpovídající `Pet` objekty. Metoda vrátí kolekci, která obsahuje pouze jednu, výchozí hodnotu, pokud posloupnost odpovídající `Pet` objekty je prázdný na žádném `Person` objektu, a zajistí tak každý `Person` objekt je reprezentován v kolekci výsledek.

> [!NOTE]
> Výchozí hodnota pro typ odkazu je `null`; proto příklad vyhledává odkaz s hodnotou null před přístupem k každý prvek každého `Pet` kolekce.

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a>Viz také:

- <xref:System.Linq.Enumerable.Join%2A>  
- <xref:System.Linq.Enumerable.GroupJoin%2A>  
- [Provádění vnitřních spojení](perform-inner-joins.md)  
- [Provádění seskupených spojení](perform-grouped-joins.md)  
- [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)  