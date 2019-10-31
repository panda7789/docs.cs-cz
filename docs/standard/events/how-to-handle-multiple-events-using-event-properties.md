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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124772"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a>Postupy: Zpracování více událostí pomocí vlastností událostí
Chcete-li použít vlastnosti událostí, je třeba definovat vlastnosti událostí ve třídě, která události vyvolá, a poté nastavit delegáty pro tyto vlastnosti událostí ve třídách, které události zpracovávají. Pro implementaci více vlastností události ve třídě musí třída interně ukládat a udržovat delegáty definované pro každou událost. Typickým přístupem je implementace kolekce delegátů, která je indexována klíčem události.  
  
 Chcete-li uložit delegáty pro každou událost, můžete použít třídu <xref:System.ComponentModel.EventHandlerList> nebo implementovat vlastní kolekci. Třída kolekce musí poskytovat metody pro nastavení, přístup a načtení delegáta obslužné rutiny události na základě klíče události. Můžete například použít třídu <xref:System.Collections.Hashtable> nebo odvodit vlastní třídu z třídy <xref:System.Collections.DictionaryBase>. Podrobnosti implementace kolekce delegátů nemusí být vystaveny mimo vaši třídu.  
  
 Každá vlastnost události v rámci třídy definuje metodu přistupujícího objektu Add a metodu odebrání přístupového objektu. Přístupový objekt Add pro vlastnost události přidá instanci vstupního delegáta do kolekce Delegate. Přístupový objekt Remove pro vlastnost události odebere instanci vstupního delegáta z kolekce Delegate. Přistupující objekty vlastnosti události používají předdefinovaný klíč pro vlastnost Event k přidání a odebrání instancí z kolekce delegátů.  
  
### <a name="to-handle-multiple-events-using-event-properties"></a>Postup zpracování více událostí pomocí vlastností událostí  
  
1. Definujte kolekci delegátů v rámci třídy, která vyvolá události.  
  
2. Definujte klíč pro každou událost.  
  
3. Definujte vlastnosti události ve třídě, která vyvolává události.  
  
4. Použijte kolekci Delegate k implementaci přístupových metod přidat a odebrat pro vlastnosti události.  
  
5. Pomocí vlastností veřejné události můžete přidat a odebrat delegáty obslužných rutin událostí ve třídách, které zpracovávají události.  
  
## <a name="example"></a>Příklad  
 Následující C# příklad implementuje vlastnosti události `MouseDown` a `MouseUp`pomocí <xref:System.ComponentModel.EventHandlerList> k uložení delegáta každé události. Klíčová slova konstrukcí vlastností události jsou v tučném typu.  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [Události](../../../docs/standard/events/index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [Postupy: Deklarování vlastních událostí pro konzervaci paměti](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
