---
title: 'Postupy: Zpracování více událostí pomocí vlastností událostí'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET Framework]
- multiple events [.NET Framework]
- event handling [.NET Framework], with multiple events
- events [.NET Framework], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
ms.openlocfilehash: f74d75a09da350b34dfb067c3d0db8fc669116ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124772"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a>Postupy: Zpracování více událostí pomocí vlastností událostí
Chcete-li použít vlastnosti událostí, je třeba definovat vlastnosti událostí ve třídě, která události vyvolá, a poté nastavit delegáty pro tyto vlastnosti událostí ve třídách, které události zpracovávají. Chcete-li implementovat více vlastností událostí ve třídě, musí třída interně ukládat a udržovat delegáta definovaného pro každou událost. Typickým přístupem je implementace kolekce delegátů, která je indexována klíčem události.  
  
 Chcete-li uložit delegáty pro každou <xref:System.ComponentModel.EventHandlerList> událost, můžete použít třídu nebo implementovat vlastní kolekci. Třída kolekce musí poskytovat metody pro nastavení, přístup a načítání delegáta obslužné rutiny události na základě klíče události. Můžete například použít <xref:System.Collections.Hashtable> třídu nebo odvodit <xref:System.Collections.DictionaryBase> vlastní třídu z třídy. Podrobnosti implementace kolekce delegáta nemusí být vystaveny mimo vaši třídu.  
  
 Každá vlastnost události v rámci třídy definuje metodu přistupujícího objektu add a metodu odebrat přístupový objekt. Přistupující objekt pro vlastnost události přidá instanci vstupního delegáta do kolekce delegáta. Odebrat přistupující objekt pro vlastnost události odebere instanci vstupního delegáta z kolekce delegáta. Přistupující objekty vlastnosti události používají předdefinovaný klíč pro vlastnost události k přidání a odebrání instancí z kolekce delegáta.  
  
### <a name="to-handle-multiple-events-using-event-properties"></a>Zpracování více událostí pomocí vlastností událostí  
  
1. Definujte kolekci delegáta v rámci třídy, která vyvolává události.  
  
2. Definujte klíč pro každou událost.  
  
3. Definujte vlastnosti události ve třídě, která vyvolává události.  
  
4. Pomocí kolekce delegáta implementujte metody přistupujícího objektu pro vlastnosti události.  
  
5. Pomocí vlastností veřejné události můžete přidat a odebrat delegáty obslužné rutiny události ve třídách, které zpracovávají události.  
  
## <a name="example"></a>Příklad  
 Následující příklad jazyka C# implementuje vlastnosti `MouseDown` události a `MouseUp`pomocí delegáta <xref:System.ComponentModel.EventHandlerList> každé události. Klíčová slova konstrukce vlastností události jsou tučným písmem.  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [Akce](../../../docs/standard/events/index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [Postupy: Deklarování vlastních událostí pro konzervaci paměti](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
