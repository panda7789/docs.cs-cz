---
title: "TrackBar – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e62fc49a8a08c79138df080246b99b6fe891162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar – přehled ovládacího prvku (Windows Forms)
Windows Forms <xref:System.Windows.Forms.TrackBar> ovládací prvek (také někdy nazývané "posuvník") se používá pro procházení velké množství informací nebo vizuálně úpravě číselné nastavení. <xref:System.Windows.Forms.TrackBar> Řízení má dvě části: jezdce, také známé jako jezdce a značek. Jezdce je část, která se dá upravit. Odpovídá jeho umístění <xref:System.Windows.Forms.TrackBar.Value%2A> vlastnost. Značky jsou visual indikátory, které jsou rozmístěny v pravidelných intervalech. Pozice přesouvají v krocích, které můžete zadat a lze zarovnávat vodorovně nebo svisle. Panelu sledování můžete například použít k řízení rychlost blikání kurzoru míry nebo myš pro systém.  
  
## <a name="key-properties"></a>Klíčové vlastnosti  
 Klíčové vlastnosti <xref:System.Windows.Forms.TrackBar> řízení, představují <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, a <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>je mezery o rysky. <xref:System.Windows.Forms.TrackBar.Minimum%2A>a <xref:System.Windows.Forms.TrackBar.Maximum%2A> jsou nejnižší a nejvyšší hodnoty, které může být reprezentován na panelu sledovat.  
  
 Jsou dvě důležité vlastnosti <xref:System.Windows.Forms.TrackBar.SmallChange%2A> a <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. Hodnota <xref:System.Windows.Forms.TrackBar.SmallChange%2A> vlastnost je počet pozic úchytu přesune v reakci na LEVÉ a pravé šipky klíče stisknutí tlačítka. Hodnota <xref:System.Windows.Forms.TrackBar.LargeChange%2A> vlastnost je počet pozic úchytu přesune v reakci na situaci, kdy stisknuta klávesa PAGE UP nebo PAGE DOWN nebo v reakci na myši klikne na panelu sledovat na obou stranách od jezdce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TrackBar>  
 [Ovládací prvek TrackBar](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
