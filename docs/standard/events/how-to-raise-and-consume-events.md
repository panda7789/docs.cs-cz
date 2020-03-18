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
ms.openlocfilehash: 256b5ae9ac2145e339136985872dfa5423aca730
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131586"
---
# <a name="how-to-raise-and-consume-events"></a>Postupy: Vyvolávání a zpracovávání událostí
Příklady v tomto tématu ukazují, jak pracovat s událostmi. Zahrnují příklady <xref:System.EventHandler> delegáta, <xref:System.EventHandler%601> delegáta a vlastního delegáta pro ilustraci událostí s daty a bez dat.  
  
 Příklady používají koncepty popsané v časopise [Events.](../../../docs/standard/events/index.md)  
  
## <a name="example"></a>Příklad  
 První příklad ukazuje, jak vyvolat a využívat událost, která nemá data. Obsahuje třídu `Counter` s názvem, `ThresholdReached`která má událost s názvem . Tato událost je vyvolána, když hodnota čítače rovná nebo překračuje prahovou hodnotu. Delegát <xref:System.EventHandler> je přidružen k události, protože nejsou k dispozici žádná data události.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Příklad  
 Další příklad ukazuje, jak zvýšit a spotřebovat událost, která poskytuje data. Delegát <xref:System.EventHandler%601> je přidružen k události a je k dispozici instance vlastního datového objektu události.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat delegáta pro událost. Delegát je `ThresholdReachedEventHandler`pojmenován . Tohle je jen ilustrace. Obvykle není třeba deklarovat delegáta pro událost, protože <xref:System.EventHandler> můžete <xref:System.EventHandler%601> použít buď delegáta nebo delegáta. Delegáta byste měli deklarovat pouze ve výjimečných scénářích, jako je například zpřístupnění vaší třídy staršímu kódu, který nemůže používat obecné typy.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Viz také

- [Akce](../../../docs/standard/events/index.md)
