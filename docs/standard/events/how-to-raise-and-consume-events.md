---
title: 'Postupy: Vyvolání a zpracování událostí'
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
ms.openlocfilehash: aa933e0fc589d0dbfec741e9db7fb11222cfdf38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778687"
---
# <a name="how-to-raise-and-consume-events"></a>Postupy: Vyvolání a zpracování událostí
Příklady v tomto tématu ukazují, jak pracovat s událostmi. Obsahují příklady <xref:System.EventHandler> delegovat, <xref:System.EventHandler%601> delegáta a vlastního delegáta pro ilustraci událostí, s daty a bez nich.  
  
 Příklady používají pojmy, které jsou popsané v [události](../../../docs/standard/events/index.md) článku.  
  
## <a name="example"></a>Příklad  
 První příklad ukazuje, jak vyvolat a zpracovat událost, která neobsahuje data. Obsahuje třídu s názvem `Counter` , která má událost s názvem `ThresholdReached`. Tato událost je aktivována, když hodnota čítače rovná nebo překračuje prahovou hodnotu. <xref:System.EventHandler> Delegát je přidruženo k události, protože nejsou k dispozici žádná data události.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vyvolat a zpracovat událost, která poskytuje data. <xref:System.EventHandler%601> Delegát je přidruženo k události, a je k dispozici instance datového objektu vlastní události.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat delegáta pro událost. Delegát se nazývá `ThresholdReachedEventHandler`. Jde jen o ukázku. Obvykle není nutné deklarovat delegáta pro událost, protože můžete použít buď <xref:System.EventHandler> nebo <xref:System.EventHandler%601> delegovat. By měla deklarovat delegáta pouze ve výjimečných případech, jako je například zpřístupnění vaší třídy staršímu kódu, který nemůže používat obecné typy.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- [Události](../../../docs/standard/events/index.md)
