---
title: 'Postupy: Vyvolávání a zpracovávání událostí'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: efeed61c5748a0a6ac731cdcfce1a110982b2941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-raise-and-consume-events"></a>Postupy: Vyvolávání a zpracovávání událostí
V příkladech v tomto tématu ukazují, jak pracovat s událostmi. Patří mezi ně příklady <xref:System.EventHandler> delegovat, <xref:System.EventHandler%601> delegáta a vlastní delegáta, ke znázornění událostí s i bez data.  
  
 Příklady použití konceptů popsaných v [události](../../../docs/standard/events/index.md) článku.  
  
## <a name="example"></a>Příklad  
 V prvním příkladu ukazuje, jak vyvolávání a zpracovávání událost, která nemá data. Obsahuje třídy s názvem `Counter` s událost s názvem `ThresholdReached`. Tato událost se vyvolá, když hodnota čítače se rovná nebo překračuje prahovou hodnotu. <xref:System.EventHandler> Delegát je přidruženo k události, protože je k dispozici žádná data.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Příklad  
 Další příklad ukazuje, jak vyvolávání a zpracovávání událost, který poskytuje data. <xref:System.EventHandler%601> Delegát je přidruženo k události, a je k dispozici instance objektu dat vlastní události.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Příklad  
 Další příklad ukazuje, jak delegáta pro událost deklarovat. Delegát jmenuje `ThresholdReachedEventHandler`. Toto je právě obrázek. Obvykle není nutné deklarovat delegát pro událost, protože můžete použít buď <xref:System.EventHandler> nebo <xref:System.EventHandler%601> delegovat. Delegát pouze ve výjimečných případech, například zpřístupnění třídě starší verze kódu, které nemůže používat obecné typy by měly deklarovat.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../docs/standard/events/index.md)
