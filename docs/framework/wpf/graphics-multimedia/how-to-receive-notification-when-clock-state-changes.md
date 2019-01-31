---
title: 'Postupy: Obdržení oznámení při změně stavu hodin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
ms.openlocfilehash: 116647b6b7df9c012ee7d5f08abd760b7f310f71
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277105"
---
# <a name="how-to-receive-notification-when-a-clocks-state-changes"></a>Postupy: Obdržení oznámení při změně stavu hodin
Hodin <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> dojde k události při jeho <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> stává neplatným, například když jsou hodiny, spuštění nebo zastavení. Si můžete zaregistrovat přímo pomocí této události <xref:System.Windows.Media.Animation.Clock>, nebo můžete zaregistrovat pomocí <xref:System.Windows.Media.Animation.Timeline>.  
  
 V následujícím příkladu <xref:System.Windows.Media.Animation.Storyboard> a dva <xref:System.Windows.Media.Animation.DoubleAnimation> objekty se používají pro animaci šířka dvou obdélníků. <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> Událostí se používá k naslouchání pro změny stavu hodin.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 Následující obrázek znázorňuje různé stavy animací zadejte jako nadřazené časové osy (*scénáře*) průběh.  
  
 ![Hodiny pro scénáře s použitím animací dva stavy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")  
  
 Následující tabulka ukazuje dobu, jakou *Animation1*společnosti <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> dojde k aktivaci události:  
  
||||||||  
|-|-|-|-|-|-|-|  
|Doba (v sekundách)|1|10|19|21|30|39|  
|Stav|Aktivní|Aktivní|Zastaveno|Aktivní|Aktivní|Zastaveno|  
  
 Následující tabulka ukazuje dobu, jakou *Animation2*společnosti <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> dojde k aktivaci události:  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|Doba (v sekundách)|1|9|11|19|21|29|31|39|  
|Stav|Aktivní|Naplnění|Aktivní|Zastaveno|Aktivní|Naplnění|Aktivní|Zastaveno|  
  
 Všimněte si, že *Animation1*společnosti <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> událost aktivuje na 10 sekund, i v případě, že jeho stav zůstává <xref:System.Windows.Media.Animation.ClockState.Active>. Důvodem je, že jeho stav změní na 10 sekund, ale změnila z <xref:System.Windows.Media.Animation.ClockState.Active> k <xref:System.Windows.Media.Animation.ClockState.Filling> a pak zpátky <xref:System.Windows.Media.Animation.ClockState.Active> ve stejném značek.
