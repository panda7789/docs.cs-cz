---
title: 'Postupy: Deklarování vlastních událostí k zabránění blokování (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 6eea47ea2c8aee697eb34ca904dad22ca88e6ce4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051894"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Postupy: Deklarování vlastních událostí k zabránění blokování (Visual Basic)
Existují několika případech, kdy je důležité, že jedna obslužná rutina události nedochází k blokování obslužné rutiny události. Vlastní události povolit událostí na asynchronní volání jeho obslužné rutiny událostí.  
  
 Ve výchozím nastavení je pole záložní úložiště pro deklaraci události vícesměrového vysílání delegát, který sériově kombinuje všechny obslužné rutiny událostí. To znamená, že pokud jednu obslužnou rutinu trvá dlouhou dobu pro dokončení, zablokuje obslužné rutiny až do dokončení. (Které jsou v pořádku obslužné by měl provádět nikdy dlouhé nebo potenciálně blokující operace.)  
  
 Místo použití výchozí implementace události, které poskytuje Visual Basic, můžete použít vlastní událost obslužné rutiny událostí spustit asynchronně.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `AddHandler` přistupující objekt přidá delegáta pro každou obslužnou rutinu z `Click` události <xref:System.Collections.ArrayList> uložené v `EventHandlerList` pole.  
  
 Kódu vyvolá `Click` událostí, `RaiseEvent` přistupující objekt vyvolává Všichni delegáti obslužné rutiny události asynchronně pomocí <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> metody. Tato metoda vyvolá každou obslužnou rutinu v pracovní podproces a vrátí hodnotu okamžitě, takže obslužné rutiny nelze blokovat mezi sebou.  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Postupy: Deklarování vlastních událostí pro konzervaci paměti](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
