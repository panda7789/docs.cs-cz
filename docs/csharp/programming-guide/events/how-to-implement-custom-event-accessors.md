---
title: Implementace vlastních přístupových objektů událostí – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: af44b88ddd0e34f9dfd0b56718b5bc7241ef5d03
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635454"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Implementace vlastních přístupových objektů událostí (C# Průvodce programováním)
Událost je zvláštní druh delegáta vícesměrového vysílání, který lze volat pouze z třídy, ve které je deklarována. Kód klienta se přihlašuje k odběru události tím, že poskytuje odkaz na metodu, která by měla být vyvolána při vyvolání události. Tyto metody se přidají do seznamu volání delegáta prostřednictvím přístupových objektů události, které se podobají přístupovým vlastnostem události s tím rozdílem, že přístupové objekty událostí jsou pojmenované `add` a `remove`. Ve většině případů nemusíte zadávat vlastní přistupující objekty události. Nejsou-li v kódu zadány žádné vlastní přístupové objekty události, kompilátor je přidá automaticky. V některých případech ale možná budete muset zadat vlastní chování. Takový případ je uveden v tématu [jak implementovat události rozhraní](./how-to-implement-interface-events.md).
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat vlastní přidávání a odebírání přístupových objektů událostí. I když v přístupových objektech můžete nahradit libovolný kód, doporučujeme před přidáním nebo odebráním nové metody obslužné rutiny události uzamknout událost.  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Viz také:

- [Události](./index.md)
- [event](../../language-reference/keywords/event.md)
