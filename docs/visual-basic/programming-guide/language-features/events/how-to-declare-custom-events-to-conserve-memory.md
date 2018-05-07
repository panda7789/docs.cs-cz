---
title: 'Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: d19c91d66e458ca2317dc049d517b92fa7406ef6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Postupy: Deklarování vlastních událostí k zabránění blokování](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
