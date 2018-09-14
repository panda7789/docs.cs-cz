---
title: 'Postupy: Implementace vlastních přístupových objektů událostí (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 759a7a4518a371449723a23669816bbc0fbc0dee
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45528127"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Postupy: Implementace vlastních přístupových objektů událostí (Průvodce programováním v C#)
Událost je zvláštní druh vícesměrového vysílání delegát, který lze vyvolat pouze z v rámci třídy, která je deklarována. Klientský kód se přihlásí k odběru události zadáním odkazu na metodu, která má být volána, když se aktivuje událost. Tyto metody se přidají do seznamu vyvolání tohoto delegáta prostřednictvím přístupových objektů událostí, které se podobají přistupující objekty vlastnosti, s tím rozdílem, že přístupové objekty událostí jsou pojmenovány `add` a `remove`. Ve většině případů není nutné k poskytování vlastních přístupových objektů událostí. Pokud ve vašem kódu jsou dodány žádné vlastních přístupových objektů událostí, kompilátor je přidá automaticky. Nicméně v některých případech budete muset poskytnout vlastní chování. Jeden takový případ je uveden v tématu [postupy: implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat vlastní přidávání a odebírání přístupových objektů událostí. I když můžete nahradit všechny kód uvnitř přístupové objekty, doporučujeme uzamknout událostí, než přidáte nebo odeberete nové metody obslužné rutiny události.  
  
[!code-csharp[IDrawingObject.OnDraw](codesnippet/CSharp/how-to-implement-interface-events_1.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Viz také

- [Události](../../../csharp/programming-guide/events/index.md)  
- [event](../../../csharp/language-reference/keywords/event.md)