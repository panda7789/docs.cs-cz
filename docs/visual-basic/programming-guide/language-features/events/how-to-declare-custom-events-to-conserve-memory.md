---
title: 'Postupy: Deklarování vlastních událostí pro konzervaci paměti'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: c9a049d3f15d5620152f064888a97bd0be5d46b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405128"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)
V některých případech je důležité, aby aplikace zachovala využití paměti nízké. Vlastní události umožňují, aby aplikace používala paměť pouze pro události, které zpracovává.  
  
 Ve výchozím nastavení, když třída deklaruje událost, kompilátor přiděluje paměť pro pole k uložení informací o události. Pokud má třída mnoho nepoužívaných událostí, zbytečně zabírat paměť.  
  
 Místo použití výchozí implementace událostí, které Visual Basic poskytuje, můžete použít vlastní události a pečlivě spravovat využití paměti.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída používá jednu instanci <xref:System.ComponentModel.EventHandlerList> třídy uloženou v `Events` poli pro ukládání informací o používaných událostech. <xref:System.ComponentModel.EventHandlerList>Třída je optimalizovaná třída seznamu navržená tak, aby obsahovala delegáty.  
  
 Všechny události ve třídě používají `Events` pole k udržení přehledu o tom, jaké metody zpracovávají jednotlivé události.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.EventHandlerList>
- [Události](index.md)
- [Postupy: Deklarování vlastních událostí k zabránění blokování](how-to-declare-custom-events-to-avoid-blocking.md)
