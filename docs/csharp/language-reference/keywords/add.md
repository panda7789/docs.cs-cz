---
title: přidat - C# Odkaz
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 323064dcbe7596b5f1d2f0f6aa566b07cee45789
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713812"
---
# <a name="add-c-reference"></a>add (Referenční dokumentace jazyka C#)
Kontextové `add` klíčové slovo se používá k definování vlastního přistupujícího objektu události, který je vyvolán při přihlášení kódu klienta k odběru [události](./event.md). Pokud zadáte vlastní `add` přistupující objekt, musíte také zadat [odebrat](./remove.md) přistupující objekt.  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje událost, `add` která má vlastní a [odebrat](./remove.md) přístupové objekty. Úplný příklad naleznete v tématu [Jak implementovat události rozhraní](../../programming-guide/events/how-to-implement-interface-events.md).
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Obvykle není nutné zadat vlastní přístupové objekty událostí. Přístupové objekty, které jsou automaticky generovány kompilátoru při deklarování události jsou dostatečné pro většinu scénářů.  
  
## <a name="see-also"></a>Viz také

- [Akce](../../programming-guide/events/index.md)
