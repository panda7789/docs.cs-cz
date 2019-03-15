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
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Postupy: použití slovníku k ukládání instancí událostí (C# Programming Guide)

Jedním použitím `add` a `remove` vlastních přístupových objektů událostí je zveřejnit mnoho událostí bez přidělování pole pro každou událost, ale místo toho používat <xref:System.Collections.Generic.Dictionary%602> instance k ukládání instancí událostí, jak ukazuje následující příklad. To je užitečné pouze, pokud typ má mnoho událostí, ale očekáváte, že většina události se přihlásit k odběru.

[!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]

Tato implementace odpovídá chování [přidávání a odebírání delegáti](~/_csharplang/spec/delegates.md#delegate-invocation) v C# specifikace jazyka.

Všimněte si, že [Zámek](../../language-reference/keywords/lock-statement.md) prohlášení se používá jenom s *přístup* slovník s obslužných rutin událostí. Není vyvolat obslužnou rutinu události uvnitř těla `lock` příkaz, protože by mohly vést k zablokování nebo uzamknout kolize.

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Události](../../../csharp/programming-guide/events/index.md)
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)
