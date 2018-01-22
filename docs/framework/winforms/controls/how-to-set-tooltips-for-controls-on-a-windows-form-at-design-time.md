---
title: "Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows v době návrhu"
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
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28a83a623329a7bf0162bb9feb0dc21bb73611cf
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows v době návrhu
Můžete nastavit <xref:System.Windows.Forms.ToolTip> řetězec v kódu nebo v Návrháři formulářů. Další informace o <xref:System.Windows.Forms.ToolTip> součást, najdete v části [ToolTip – přehled komponenty](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-a-tooltip-programmatically"></a>Chcete-li nastavit popisek prostřednictvím kódu programu  
  
1.  Přidání ovládacího prvku, který se zobrazí popisek.  
  
2.  Použití <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu <xref:System.Windows.Forms.ToolTip> součásti.  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a>Chcete-li nastavit popisek v Návrháři  
  
1.  Přidat <xref:System.Windows.Forms.ToolTip> součásti pro formulář.  
  
2.  Vyberte ovládací prvek, který se zobrazí popisek nebo ho přidat do formuláře.  
  
3.  V **vlastnosti** nastavte **popis tlačítka na ToolTip1** hodnotu na odpovídající řetězec textu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled komponenty ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [Postupy: Změna zpoždění komponenty Windows Forms ToolTip](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [Komponenta ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
