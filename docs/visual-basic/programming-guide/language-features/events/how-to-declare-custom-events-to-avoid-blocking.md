---
title: 'Postupy: Deklarování vlastních událostí k zabránění blokování'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: a9f9529d468a036d81c4e436429cbdb3207efd6e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405154"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Postupy: Deklarování vlastních událostí k zabránění blokování (Visual Basic)
Je-li důležité, aby jedna obslužná rutina události neblokovala následné obslužné rutiny událostí, existuje několik okolností. Vlastní události umožňují, aby událost volala své obslužné rutiny událostí asynchronně.  
  
 Ve výchozím nastavení je zálohovacím polem pro deklaraci události delegát vícesměrového vysílání, který pomocí sériového kombinování všech obslužných rutin událostí. To znamená, že pokud dokončení jedné obslužné rutiny trvá dlouhou dobu, blokuje ostatní obslužné rutiny až do dokončení. (Správně fungující obslužné rutiny událostí by nikdy neměly provádět zdlouhavé nebo potenciálně blokující operace.)  
  
 Namísto použití výchozí implementace událostí, které Visual Basic poskytuje, můžete použít vlastní událost k asynchronnímu spuštění obslužných rutin událostí.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `AddHandler` přistupující objekt přidá delegáta pro každou obslužnou rutinu `Click` události do <xref:System.Collections.ArrayList> pole uloženého v `EventHandlerList` poli.  
  
 Když kód vyvolá `Click` událost, `RaiseEvent` přistupující objekt vyvolá veškerou delegáty obslužné rutiny události asynchronně pomocí <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> metody. Tato metoda vyvolá každou obslužnou rutinu v pracovním vlákně a vrátí ji okamžitě, takže obslužné rutiny nemohou jiné blokovat.  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [Události](index.md)
- [Postupy: Deklarování vlastních událostí pro konzervaci paměti](how-to-declare-custom-events-to-conserve-memory.md)
