---
title: 'Postupy: příjem oznámení, když hodiny, které&#39;s změny stavu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
ms.openlocfilehash: d0eaca4d2a05d01e686efc15dfceebb6de4f4b64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561170"
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a>Postupy: příjem oznámení, když hodiny, které&#39;s změny stavu
Hodiny <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> dojde k události při jeho <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> stává neplatným, například když hodiny spuštění nebo zastavení. Můžete zaregistrovat pro tuto událost s přímo pomocí <xref:System.Windows.Media.Animation.Clock>, nebo můžete zaregistrovat pomocí <xref:System.Windows.Media.Animation.Timeline>.  
  
 V následujícím příkladu <xref:System.Windows.Media.Animation.Storyboard> a dvě <xref:System.Windows.Media.Animation.DoubleAnimation> objekty se používají k animace šířku dvou tvaru. <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> Událostí se používá k naslouchání hodiny změny stavu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 Následující obrázek ukazuje různé stavy animací zadejte jako nadřazené časové osy (*Storyboard*) postupuje.  
  
 ![Clock stavy pro scénář se dvěma animací](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")  
  
 Následující tabulka uvádí dobu, kdy *Animation1*na <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> aktivuje událost:  
  
||||||||  
|-|-|-|-|-|-|-|  
|Doba (v sekundách)|1|10|19|21|30|39|  
|Stav|Aktivní|Aktivní|Byla zastavena|Aktivní|Aktivní|Byla zastavena|  
  
 Následující tabulka uvádí dobu, kdy *Animation2*na <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> aktivuje událost:  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|Doba (v sekundách)|1|9|11|19|21|29|31|39|  
|Stav|Aktivní|Naplnění|Aktivní|Byla zastavena|Aktivní|Naplnění|Aktivní|Byla zastavena|  
  
 Všimněte si, že *Animation1*na <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> událost aktivuje na 10 sekund, i když zůstane stav <xref:System.Windows.Media.Animation.ClockState.Active>. Důvodem je, že došlo ke změně jeho stavu na 10 sekund, ale změnit z <xref:System.Windows.Media.Animation.ClockState.Active> k <xref:System.Windows.Media.Animation.ClockState.Filling> a pak zpátky na <xref:System.Windows.Media.Animation.ClockState.Active> ve stejné značek.
