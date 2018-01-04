---
title: "Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffe7d050de84eba8c7962a62a8604a72f78bc2bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a>Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu
Tento postup ukazuje, jak zkopírovat ovládacího prvku Windows Presentation Foundation (WPF) ve formuláři Windows.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a>Zkopírování a vložení ovládacího prvku ElementHost během návrhu  
  
1.  Přidat nové WPF <xref:System.Windows.Controls.UserControl> do projektu Windows Forms. Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [návod: vytvoření nové WPF obsahu v aplikaci Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti `UserControl1` k `200`.  
  
3.  Nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Blue`.  
  
4.  Sestavte projekt.  
  
5.  Otevřete `Form1` v Návrháři formulářů.  
  
6.  Z **sada nástrojů**, přetáhněte instanci `UserControl1` do formuláře.  
  
     Instance `UserControl1` je hostován v nové <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.  
  
7.  S `elementHost1` vybrána, stiskněte CTRL + C zkopírujte jej do schránky.  
  
8.  Stisknutím kombinace kláves CTRL + V vložte zkopírovaný ovládací prvek na formuláři.  
  
     Nový <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost2` je vytvořena na formuláři.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návod: Zkopírování a vložení ovládacího prvku ElementHost do samostatného modelu Windows Forms](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Používání ovládacích prvků WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Návrhář WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
