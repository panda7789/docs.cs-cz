---
description: odebrat kontextové klíčové slovo – Reference jazyka C#
title: odebrat kontextové klíčové slovo – Reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: a5514e72a04daa1232dbdf9a37813f09de791590
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136951"
---
# <a name="remove-c-reference"></a>remove (Referenční dokumentace jazyka C#)

`remove`Kontextové klíčové slovo slouží k definování vlastního přístupového objektu události, který je vyvolán, když se kód klienta odhlásí od vaší [události](event.md). Pokud zadáte vlastní `remove` přistupující objekt, musíte také zadat přistupující objekt [Add](add.md) .

## <a name="example"></a>Příklad

Následující příklad ukazuje událost s vlastními [přidanými](add.md) a `remove` přistupujícími objekty. Úplný příklad naleznete v tématu [jak implementovat události rozhraní](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Většinou nemusíte poskytovat vlastní přístupové objekty vlastních událostí. Přistupující objekty, které kompilátor generuje automaticky při deklaraci události, jsou pro většinu scénářů dostačující.

## <a name="see-also"></a>Viz také

- [Události](../../programming-guide/events/index.md)
