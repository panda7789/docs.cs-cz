---
title: 'Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: bf22c2029671588ab0ebaefd2554fcb2a5a1131c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719518"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)
Existují několika případech, kdy je důležité, aby aplikace byl jeho využití paměti nízké. Vlastní události, aby aplikace použít pouze pro události, které zpracovává paměti.  
  
 Ve výchozím nastavení když třída deklaruje událost, kompilátor přiděluje paměť pro pole k ukládání informací o události. Pokud třída má mnoho událostí nevyužité, zbytečně zabírají paměti.  
  
 Místo použití výchozí implementace události, které poskytuje Visual Basic, můžete použít vlastní události více pečlivě spravovat využití paměti.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída používá jednu instanci <xref:System.ComponentModel.EventHandlerList> třídy, které jsou uložené v `Events` pole k ukládání informací o událostech používá. <xref:System.ComponentModel.EventHandlerList> Třídy je třída optimalizované seznam navržených pro ukládání delegátů.  
  
 Všechny události v třídy `Events` pole, které chcete sledovat, jaké metody se zpracování každé události.  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ComponentModel.EventHandlerList>
- [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Postupy: Deklarování vlastních událostí k zabránění blokování](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
