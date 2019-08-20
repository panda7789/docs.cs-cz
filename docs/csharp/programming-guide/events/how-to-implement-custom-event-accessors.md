---
title: 'Postupy: Implementace vlastních přístupových objektů událostí C# – Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 4eaf8b4c3038d07d5b0fc021e21c7f1a2de85d74
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590527"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Postupy: Implementace vlastních přístupových objektů událostíC# (Průvodce programováním)
Událost je zvláštní druh delegáta vícesměrového vysílání, který lze volat pouze z třídy, ve které je deklarována. Kód klienta se přihlašuje k odběru události tím, že poskytuje odkaz na metodu, která by měla být vyvolána při vyvolání události. Tyto metody jsou přidány do seznamu volání delegáta prostřednictvím přístupových objektů, které se podobají přístupovým vlastnostem události, s tím rozdílem, že přistupující `add` objekty `remove`události jsou pojmenované a. Ve většině případů nemusíte zadávat vlastní přistupující objekty události. Nejsou-li v kódu zadány žádné vlastní přístupové objekty události, kompilátor je přidá automaticky. V některých případech ale možná budete muset zadat vlastní chování. Takový případ je uvedený v tématu [postupy:  Implementujte události](./how-to-implement-interface-events.md)rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat vlastní přidávání a odebírání přístupových objektů událostí. I když v přístupových objektech můžete nahradit libovolný kód, doporučujeme před přidáním nebo odebráním nové metody obslužné rutiny události uzamknout událost.  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Viz také:

- [Události](./index.md)
- [event](../../language-reference/keywords/event.md)
