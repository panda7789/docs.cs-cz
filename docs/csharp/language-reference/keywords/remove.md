---
title: odebrat kontextové klíčové slovo C# – odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 568b979c8b2e859dcfa87a3c3446132c740ff14c
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635909"
---
# <a name="remove-c-reference"></a>remove (Referenční dokumentace jazyka C#)

Klíčové slovo `remove` slouží k definování vlastního přístupového objektu události, který je vyvolán, když se kód klienta odhlásí od vaší [události](event.md). Pokud zadáte vlastní přistupující objekt `remove`, musíte také zadat přistupující objekt [Add](add.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje událost s vlastními přistupujícími objekty [Add](add.md) a `remove`. Úplný příklad naleznete v tématu [jak implementovat události rozhraní](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Většinou nemusíte poskytovat vlastní přístupové objekty vlastních událostí. Přistupující objekty, které kompilátor generuje automaticky při deklaraci události, jsou pro většinu scénářů dostačující.

## <a name="see-also"></a>Viz také:

- [Události](../../programming-guide/events/index.md)
