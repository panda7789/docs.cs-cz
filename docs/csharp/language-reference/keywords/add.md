---
description: 'Naučte se vytvářet vlastní přistupující objekty událostí pomocí klíčového slova Add v jazyce C. #'
title: Add – Reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 520267574320af7f85f2ee07e2778f8bebd01e4b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127006"
---
# <a name="add-c-reference"></a>add (Referenční dokumentace jazyka C#)
`add`Kontextové klíčové slovo slouží k definování vlastního přístupového objektu události, který je vyvolán, když se kód klienta přihlašuje k odběru [události](./event.md). Pokud zadáte vlastní `add` přistupující objekt, je nutné také předat přístup pro [Odebrání](./remove.md) .  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje událost, která má vlastní `add` a [Odebrat](./remove.md) přistupující objekty. Úplný příklad naleznete v tématu [jak implementovat události rozhraní](../../programming-guide/events/how-to-implement-interface-events.md).
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Většinou nemusíte poskytovat vlastní přístupové objekty vlastních událostí. Přistupující objekty, které kompilátor generuje automaticky při deklaraci události, jsou pro většinu scénářů dostačující.  
  
## <a name="see-also"></a>Viz také

- [Události](../../programming-guide/events/index.md)
