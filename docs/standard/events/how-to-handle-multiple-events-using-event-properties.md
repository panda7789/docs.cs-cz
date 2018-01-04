---
title: "Postupy: Zpracování více událostí pomocí vlastností událostí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f0069c827bbc88b5ec5184f491b811a66955adbb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a>Postupy: Zpracování více událostí pomocí vlastností událostí
Chcete-li použít vlastnosti událostí, je třeba definovat vlastnosti událostí ve třídě, která události vyvolá, a poté nastavit delegáty pro tyto vlastnosti událostí ve třídách, které události zpracovávají. Pokud chcete implementovat několik vlastností události ve třídě, musí třída interně ukládat a udržovat delegáta definovaného pro každou jednotlivou událost. Typickým přístupem je implementace delegáta kolekce, která je indexovat pomocí klíče události.  
  
 Chcete-li uložit delegáty pro každou jednotlivou událost, můžete použít <xref:System.ComponentModel.EventHandlerList> třídy, nebo jsou implementovány vlastní kolekce. Třída kolekce musí poskytovat metody pro nastavení, přístup a načítání delegát obslužná rutina události na základě klíče události. Například můžete použít <xref:System.Collections.Hashtable> třídy nebo odvodit vlastní třídu z <xref:System.Collections.DictionaryBase> třídy. Podrobnosti implementace kolekce delegáta nemusíte být nezveřejní třídě.  
  
 Každá vlastnost události v rámci třídy definuje přístupovou metodu přidat a odebrat metodu přistupujícího objektu. Přidat přistupující objekt vlastnosti události přidá do kolekce delegáta instanci vstupního delegáta. Odebrat přistupující objekt vlastnosti události odebere instanci vstupního delegáta z kolekce delegáta. Přístupové objekty událostí vlastnosti pomocí předdefinované klíče vlastnosti události k přidání a odebrání instance z kolekce delegáta.  
  
### <a name="to-handle-multiple-events-using-event-properties"></a>Pro zpracování více událostí pomocí vlastností událostí  
  
1.  Definujte kolekci delegátů v rámci třídy, která vyvolává události.  
  
2.  Definujte klíč pro každou jednotlivou událost.  
  
3.  Definujte vlastnosti události ve třídě, která vyvolává události.  
  
4.  Použití delegáta kolekce k implementaci přidat a odebrat přístupových metod vlastností události.  
  
5.  Veřejné vlastnosti události použijte k přidání a odebrání delegátů obslužných rutin událostí v třídách, které zpracovávají události.  
  
## <a name="example"></a>Příklad  
 Následující příklad jazyka C# implementuje vlastnosti události `MouseDown` a `MouseUp`, použije <xref:System.ComponentModel.EventHandlerList> k uložení delegáta každé události. Klíčová slova konstrukce vlastnosti události jsou tučně.  
  
> [!NOTE]
>  Vlastnosti události nejsou podporovány v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)].  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>  
 [Události](../../../docs/standard/events/index.md)  
 <xref:System.Web.UI.Control.Events%2A>  
 [Postupy: Deklarování vlastních událostí pro konzervaci paměti](~/docs/visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
