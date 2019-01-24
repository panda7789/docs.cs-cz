---
title: 'Postupy: Implementace vlastních přístupových objektů událostí - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: cdae5222cfe435142d93f222d140bd41ecf2c5c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643478"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Postupy: Implementace vlastních přístupových objektů událostí (C# Průvodce programováním v)
Událost je zvláštní druh vícesměrového vysílání delegát, který lze vyvolat pouze z v rámci třídy, která je deklarována. Klientský kód se přihlásí k odběru události zadáním odkazu na metodu, která má být volána, když se aktivuje událost. Tyto metody se přidají do seznamu vyvolání tohoto delegáta prostřednictvím přístupových objektů událostí, které se podobají přistupující objekty vlastnosti, s tím rozdílem, že přístupové objekty událostí jsou pojmenovány `add` a `remove`. Ve většině případů není nutné k poskytování vlastních přístupových objektů událostí. Pokud ve vašem kódu jsou dodány žádné vlastních přístupových objektů událostí, kompilátor je přidá automaticky. Nicméně v některých případech budete muset poskytnout vlastní chování. Jeden takový případ je uveden v tématu [jak:  Implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat vlastní přidávání a odebírání přístupových objektů událostí. I když můžete nahradit všechny kód uvnitř přístupové objekty, doporučujeme uzamknout událostí, než přidáte nebo odeberete nové metody obslužné rutiny události.  
  
[!code-csharp[IDrawingObject.OnDraw](codesnippet/CSharp/how-to-implement-interface-events_1.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Viz také:

- [Události](../../../csharp/programming-guide/events/index.md)
- [event](../../../csharp/language-reference/keywords/event.md)
