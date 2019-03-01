---
title: 'Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3bd58a09d016d818c4cc88c1d2527e81a95411e6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967123"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)
Existují několika případech, kdy je důležité, aby aplikace byl jeho využití paměti nízké. Vlastní události, aby aplikace použít pouze pro události, které zpracovává paměti.  
  
 Ve výchozím nastavení když třída deklaruje událost, kompilátor přiděluje paměť pro pole k ukládání informací o události. Pokud třída má mnoho událostí nevyužité, zbytečně zabírají paměti.  
  
 Místo použití výchozí implementace události, které poskytuje Visual Basic, můžete použít vlastní události více pečlivě spravovat využití paměti.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída používá jednu instanci <xref:System.ComponentModel.EventHandlerList> třídy, které jsou uložené v `Events` pole k ukládání informací o událostech používá. <xref:System.ComponentModel.EventHandlerList> Třídy je třída optimalizované seznam navržených pro ukládání delegátů.  
  
 Všechny události v třídy `Events` pole, které chcete sledovat, jaké metody se zpracování každé události.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ComponentModel.EventHandlerList>
- [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Postupy: Deklarování vlastních událostí k zabránění blokování](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
