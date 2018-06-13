---
title: 'Postupy: Deklarování vlastních událostí k zabránění blokování (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 3cb66aed71195d2fd2335fbd59cc499b3dbf808e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646923"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Postupy: Deklarování vlastních událostí k zabránění blokování (Visual Basic)
Existují několika případech, kdy je důležité, že jedna obslužná rutina není blokovat obslužné rutiny události. Vlastní události povolit události na asynchronní volání jeho obslužné rutiny událostí.  
  
 Ve výchozím nastavení je pole úložiště zálohování pro deklaraci události vícesměrového vysílání delegáta, který sériově kombinuje všechny obslužné rutiny událostí. To znamená, že pokud jeden obslužná rutina trvá dlouhou dobu pro dokončení, zablokuje ostatních obslužných rutin až do dokončení. (Které jsou v pořádku obslužných rutin by měl provést nikdy zdlouhavé nebo potenciálně blokování operací.)  
  
 Místo použití výchozí implementace událostí, které poskytuje jazyka Visual Basic, můžete použít vlastní události asynchronně spuštění obslužné rutiny událostí.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `AddHandler` přistupujícího objektu přidá delegát pro každou obslužnou rutinu `Click` událost, která má <xref:System.Collections.ArrayList> uložené v `EventHandlerList` pole.  
  
 Pokud kód vyvolá `Click` událostí, `RaiseEvent` všechny delegátů obslužných rutin událostí pomocí asynchronně vyvolá přístupového objektu <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> metoda. Dané metody vyvolá každé obslužné rutiny na pracovní vlákno a vrátí okamžitě, takže obslužné rutiny nelze blokovat jednu na druhou.  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.ArrayList>  
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>  
 [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Postupy: Deklarování vlastních událostí pro konzervaci paměti](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
