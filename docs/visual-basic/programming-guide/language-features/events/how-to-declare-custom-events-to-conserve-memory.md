---
title: "Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)"
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
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eec9a2fc687f481ab40313e35cbde81c25b81ae8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)
Pokud je důležité, aby aplikace byl jeho využití paměti nízkou existuje několik okolností. Vlastní události povolit aplikaci používat pouze pro události, které zpracovává paměti.  
  
 Ve výchozím nastavení když třída deklaruje událost, kompilátor přidělí paměť pro pole pro uložení informací o události. Pokud třída má mnoho nepoužívané událostí, zbytečnému zabírají paměť.  
  
 Místo použití výchozí implementace událostí, které poskytuje jazyka Visual Basic, můžete použít vlastní události ke správě více pečlivě využití paměti.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída používá jednu instanci <xref:System.ComponentModel.EventHandlerList> třídy, které jsou uložené v `Events` pro ukládání informací o událostech v použití pole. <xref:System.ComponentModel.EventHandlerList> Třídy je třída optimalizované seznamu navržený tak, aby udržení delegáti.  
  
 Všechny události v použití třídy `Events` pole ke sledování jaké metody se zpracování jednotlivých událostí.  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.EventHandlerList>  
 [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Postupy: deklarování vlastních událostí k zabránění blokování](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
