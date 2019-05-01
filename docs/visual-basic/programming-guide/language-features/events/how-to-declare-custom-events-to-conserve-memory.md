---
title: 'Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: e4132f51f4dd85ad964042d05f7c5bc0a2e6e3cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973157"
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
