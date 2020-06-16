---
title: 'Postupy: Zpracování více událostí pomocí vlastností událostí'
description: Naučte se zvládnout mnoho událostí pomocí vlastností událostí. Definujte delegované kolekce, klíče událostí, vlastnosti & události. Implementujte metodu Add & Remove přistupující metody.
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
ms.openlocfilehash: 5b528aa2145ba703ce605ce22ae7d643f1e5b8d0
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769012"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a>Postupy: Zpracování více událostí pomocí vlastností událostí
Chcete-li použít vlastnosti událostí, je třeba definovat vlastnosti událostí ve třídě, která události vyvolá, a poté nastavit delegáty pro tyto vlastnosti událostí ve třídách, které události zpracovávají. Pro implementaci více vlastností události ve třídě musí třída interně ukládat a udržovat delegáty definované pro každou událost. Typickým přístupem je implementace kolekce delegátů, která je indexována klíčem události.  
  
 Chcete-li uložit delegáty pro každou událost, můžete použít <xref:System.ComponentModel.EventHandlerList> třídu nebo implementovat vlastní kolekci. Třída kolekce musí poskytovat metody pro nastavení, přístup a načtení delegáta obslužné rutiny události na základě klíče události. Můžete například použít <xref:System.Collections.Hashtable> třídu nebo z třídy odvodit vlastní třídu <xref:System.Collections.DictionaryBase> . Podrobnosti implementace kolekce delegátů nemusí být vystaveny mimo vaši třídu.  
  
 Každá vlastnost události v rámci třídy definuje metodu přistupujícího objektu Add a metodu odebrání přístupového objektu. Přístupový objekt Add pro vlastnost události přidá instanci vstupního delegáta do kolekce Delegate. Přístupový objekt Remove pro vlastnost události odebere instanci vstupního delegáta z kolekce Delegate. Přistupující objekty vlastnosti události používají předdefinovaný klíč pro vlastnost Event k přidání a odebrání instancí z kolekce delegátů.  
  
### <a name="to-handle-multiple-events-using-event-properties"></a>Postup zpracování více událostí pomocí vlastností událostí  
  
1. Definujte kolekci delegátů v rámci třídy, která vyvolá události.  
  
2. Definujte klíč pro každou událost.  
  
3. Definujte vlastnosti události ve třídě, která vyvolává události.  
  
4. Použijte kolekci Delegate k implementaci přístupových metod přidat a odebrat pro vlastnosti události.  
  
5. Pomocí vlastností veřejné události můžete přidat a odebrat delegáty obslužných rutin událostí ve třídách, které zpracovávají události.  
  
## <a name="example"></a>Příklad  
 Následující příklad jazyka C# implementuje vlastnosti události `MouseDown` a `MouseUp` pomocí <xref:System.ComponentModel.EventHandlerList> uloží delegáta každé události. Klíčová slova konstrukcí vlastností události jsou v tučném typu.  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [Události](index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [Postupy: Deklarování vlastních událostí pro konzervaci paměti](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
