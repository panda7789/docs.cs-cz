---
title: Přidat C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 937e12b813d96a0ea7e02ee70d3033f4a3b8e7f4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636130"
---
# <a name="add-c-reference"></a>add (Referenční dokumentace jazyka C#)
Klíčové slovo `add` slouží k definování vlastního přístupového objektu události, který je vyvolán, když se kód klienta přihlašuje k odběru [události](./event.md). Pokud zadáte vlastní přistupující objekt `add`, musíte také předat přistupující objekt pro [Odebrání](./remove.md) .  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje událost, která má vlastní `add` a [Odebrat](./remove.md) přistupující objekty. Úplný příklad naleznete v tématu [jak implementovat události rozhraní](../../programming-guide/events/how-to-implement-interface-events.md).
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Většinou nemusíte poskytovat vlastní přístupové objekty vlastních událostí. Přistupující objekty, které kompilátor generuje automaticky při deklaraci události, jsou pro většinu scénářů dostačující.  
  
## <a name="see-also"></a>Viz také:

- [Události](../../programming-guide/events/index.md)
