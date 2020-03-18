---
title: Jak implementovat vlastní přístupové objekty událostí – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 34e816799f472e8945962e334b9a90b2582e0393
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705350"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Jak implementovat vlastní přístupové objekty událostí (Průvodce programováním jazyka C#)
Událost je zvláštní druh delegáta vícesměrového vysílání, který lze vyvolat pouze z třídy, ve které je deklarována. Klientský kód se přihlásí k události tím, že poskytuje odkaz na metodu, která by měla být vyvolána při vyvolání události. Tyto metody jsou přidány do seznamu vyvolání delegáta prostřednictvím přístupových objektů událostí, které se `add` `remove`podobají přistupující objekty vlastností, s tím rozdílem, že přístupové objekty události jsou pojmenovány a . Ve většině případů není třeba zadat vlastní přístupové objekty událostí. Pokud jsou ve vašem kódu zadány žádné vlastní přístupové objekty událostí, kompilátor je přidá automaticky. V některých případech však bude pravděpodobně muset poskytnout vlastní chování. Jeden takový případ je uveden v tématu [Jak implementovat události rozhraní](./how-to-implement-interface-events.md).
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat vlastní přistupující a odebrané přistupovače událostí. Přestože můžete nahradit libovolný kód uvnitř přistupujících operátorů, doporučujeme zamknout událost před přidáním nebo odebráním nové metody obslužné rutiny události.  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Viz také

- [Akce](./index.md)
- [Událost](../../language-reference/keywords/event.md)
