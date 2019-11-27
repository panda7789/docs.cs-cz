---
title: 'Postupy: Deklarování vlastních událostí pro konzervaci paměti'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3cc2d3ea57f1a8daf704c2c929baf3f2acf78c17
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345133"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)
V některých případech je důležité, aby aplikace zachovala využití paměti nízké. Vlastní události umožňují, aby aplikace používala paměť pouze pro události, které zpracovává.  
  
 Ve výchozím nastavení, když třída deklaruje událost, kompilátor přiděluje paměť pro pole k uložení informací o události. Pokud má třída mnoho nepoužívaných událostí, zbytečně zabírat paměť.  
  
 Místo použití výchozí implementace událostí, které Visual Basic poskytuje, můžete použít vlastní události a pečlivě spravovat využití paměti.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída používá jednu instanci třídy <xref:System.ComponentModel.EventHandlerList>, uloženou v poli `Events` pro ukládání informací o používaných událostech. Třída <xref:System.ComponentModel.EventHandlerList> je optimalizovaná třída seznamu navržená tak, aby obsahovala delegáty.  
  
 Všechny události ve třídě používají pole `Events` k udržení přehledu o tom, jaké metody zpracovávají jednotlivé události.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.EventHandlerList>
- [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Postupy: Deklarování vlastních událostí k zabránění blokování](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
