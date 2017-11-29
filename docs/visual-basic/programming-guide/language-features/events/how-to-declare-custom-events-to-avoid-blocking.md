---
title: "Postupy: Deklarování vlastních událostí k zabránění blokování (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a36c855efb67752674615a61f2fa701974ce5f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Postupy: deklarování vlastních událostí pro konzervaci paměti](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
