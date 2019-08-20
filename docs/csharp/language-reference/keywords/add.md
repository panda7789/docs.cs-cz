---
title: Přidat C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 1cf82e3d048e465d533e87dc639a13071b41544a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606039"
---
# <a name="add-c-reference"></a>add (Referenční dokumentace jazyka C#)
Kontextové klíčové slovo slouží k definování vlastního přístupového objektu události, který je vyvolán, když se kód klienta přihlašuje k odběru [události.](./event.md) `add` Pokud zadáte vlastní `add` přistupující objekt, je nutné také předat přístup pro [Odebrání](./remove.md) .  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje událost, která má vlastní `add` a [Odebrat](./remove.md) přistupující objekty. Úplný příklad naleznete v tématu [How to:  Implementujte události](../../programming-guide/events/how-to-implement-interface-events.md)rozhraní.  
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Většinou nemusíte poskytovat vlastní přístupové objekty vlastních událostí. Přistupující objekty, které kompilátor generuje automaticky při deklaraci události, jsou pro většinu scénářů dostačující.  
  
## <a name="see-also"></a>Viz také:

- [Události](../../programming-guide/events/index.md)
