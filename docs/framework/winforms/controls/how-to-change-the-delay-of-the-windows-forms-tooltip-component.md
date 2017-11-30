---
title: "Postupy: Změna zpoždění součásti Windows Forms ToolTip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48bb8c08fa02a54f9bfd3febbe99f683fd68d7f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Postupy: Změna zpoždění součásti Windows Forms ToolTip
Existuje více hodnot zpoždění, které se dají nastavit pro Windows Forms <xref:System.Windows.Forms.ToolTip> součásti. Jednotka měření pro tyto vlastnosti je milisekundách. <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> Vlastnost určuje, jak dlouho musí odkazovat uživatele na související ovládací prvek pro text popisu tlačítka se objeví. <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> Vlastnost nastaví počet milisekund, po je potřebná pro následné řetězce popisu tlačítka se objeví při pohybu myší z jednoho popisku přidruženého ovládacího prvku do jiného. <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> Vlastnost určuje dobu, se zobrazí řetězec popisku. Tyto hodnoty lze nastavit samostatně, nebo nastavením hodnoty <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnost; ostatní vlastnosti jsou nastavené na hodnotu přiřazenou základě zpoždění <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnost. Například, když <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> je nastavená na hodnotu N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> je nastaven na N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> je nastaven na hodnotu <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> rozdělený podle pět (nebo N/5), a <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> nastavena na hodnotu, která je pětkrát hodnota <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> vlastnost (nebo 5N).  
  
### <a name="to-set-the-delay"></a>Chcete-li nastavit zpoždění  
  
1.  Jak je znázorněno v tomto příkladu, nastavte následující vlastnosti.  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a>Viz také  
 [ToolTip – přehled komponenty](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [Postupy: nastavení ToolTips pro ovládací prvky na formuláři Windows v době návrhu](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [ToolTip – komponenta](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
