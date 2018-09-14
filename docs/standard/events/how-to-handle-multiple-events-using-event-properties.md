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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e16270fd900c1c786cfd74f484455481d91e5b52
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569434"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a>Postupy: Zpracování více událostí pomocí vlastností událostí
Chcete-li použít vlastnosti událostí, je třeba definovat vlastnosti událostí ve třídě, která události vyvolá, a poté nastavit delegáty pro tyto vlastnosti událostí ve třídách, které události zpracovávají. Implementovat více vlastnosti událostí ve třídě, musí třída interně ukládání a udržovat delegáta definované pro každou jednotlivou událost. Typický přístup je pro implementaci delegátů kolekce, která je indexované podle klíče události.  
  
 K ukládání delegátů pro každou událost, můžete použít <xref:System.ComponentModel.EventHandlerList> třídy nebo implementovat vlastní kolekce. Třída kolekce musí poskytovat metody pro nastavení, přístupu a načítání delegát obslužné rutiny události na základě klíče události. Například můžete použít <xref:System.Collections.Hashtable> třídy nebo odvodit vlastní třídu z <xref:System.Collections.DictionaryBase> třídy. Podrobnosti implementace delegáta kolekce nemusíte být vystavený mimo vaši třídu.  
  
 Každá vlastnost událostí v rámci třídy definuje přístupové metody přidat a odebrat přístupové metody. Přidat přístupový objekt pro vlastnost události přidá do kolekce delegáta instance vstupu delegáta. Odebrat přístupový objekt vlastnosti události dojde k odebrání instance vstupního delegáta z kolekce delegátů. Přistupující objekty vlastnosti události používá předdefinované vlastnosti události k přidání a odebrání instance z kolekce delegátů.  
  
### <a name="to-handle-multiple-events-using-event-properties"></a>Pro zpracování více událostí pomocí vlastností událostí  
  
1.  Definování kolekce delegátů v rámci třídy, která vyvolává události.  
  
2.  Definujte klíč pro každou jednotlivou událost.  
  
3.  Definujte vlastnosti událostí ve třídě, která vyvolává události.  
  
4.  Kolekce delegátů použijte k implementaci přidat a odebrat přístupové metody pro tyto vlastnosti událostí.  
  
5.  Veřejné vlastnosti události použijte k přidání a odebrání delegátů obslužných rutin událostí ve třídách, které události zpracovávají.  
  
## <a name="example"></a>Příklad  
 Následující příklad jazyka C# implementuje vlastnosti události `MouseDown` a `MouseUp`s použitím <xref:System.ComponentModel.EventHandlerList> ukládat každé události delegáta. Klíčová slova konstruktorů vlastnosti událostí jsou tučně.  
  
> [!NOTE]
>  Vlastnosti události nejsou podporovány v [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)].  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>  
- [Události](../../../docs/standard/events/index.md)  
- <xref:System.Web.UI.Control.Events%2A>  
- [Postupy: Deklarování vlastních událostí pro konzervaci paměti](~/docs/visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
