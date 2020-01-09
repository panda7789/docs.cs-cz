---
title: odebrat kontextové klíčové slovo C# – odkaz
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 8ea3ea1910e28c03b2a894c64415cb2ccff942d0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713141"
---
# <a name="remove-c-reference"></a>remove (Referenční dokumentace jazyka C#)

Klíčové slovo `remove` slouží k definování vlastního přístupového objektu události, který je vyvolán, když se kód klienta odhlásí od vaší [události](event.md). Pokud zadáte vlastní přistupující objekt `remove`, musíte také zadat přistupující objekt [Add](add.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje událost s vlastními přistupujícími objekty [Add](add.md) a `remove`. Úplný příklad naleznete v tématu [jak implementovat události rozhraní](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Většinou nemusíte poskytovat vlastní přístupové objekty vlastních událostí. Přistupující objekty, které kompilátor generuje automaticky při deklaraci události, jsou pro většinu scénářů dostačující.

## <a name="see-also"></a>Viz také:

- [Události](../../programming-guide/events/index.md)
