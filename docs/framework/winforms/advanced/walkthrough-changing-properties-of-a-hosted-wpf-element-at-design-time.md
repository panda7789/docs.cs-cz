---
title: "Návod: Změna vlastností hostovaného prvku WPF během návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 027fb2efaff5cfdd4d6962798a85923631fa4e9b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a>Návod: Změna vlastností hostovaného prvku WPF během návrhu
Tento návod ukazuje, jak změnit hodnoty vlastností ovládacího prvku Windows Presentation Foundation (WPF) hostované ve formuláři Windows.  
  
 V tomto návodu můžete provádět následující úlohy:  
  
-   Vytvoření projektu.  
  
-   Vytvoření ovládacího prvku WPF.  
  
-   Hostování ovládacích prvků WPF ve formuláři Windows.  
  
-   WPF Designer pro aplikaci Visual Studio použijte ke změně hodnot vlastností.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu modelu Windows Forms.  
  
> [!NOTE]
>  Pokud hostování obsahu subsystému WPF, jsou podporovány pouze projekty C# a Visual Basic.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte nový projekt aplikace Windows Forms v jazyce Visual Basic a Visual C# s názvem `WpfHost`.  
  
## <a name="creating-the-wpf-control"></a>Vytvoření ovládacího prvku WPF  
 Po přidání ovládací prvek WPF do projektu, můžete ho uspořádat na formuláři.  
  
#### <a name="to-create-wpf-controls"></a>Chcete-li vytvořit ovládacích prvků WPF  
  
1.  Přidat nové WPF <xref:System.Windows.Controls.UserControl> do projektu. Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [návod: vytvoření nové WPF obsahu v aplikaci Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Blue`.  
  
3.  Sestavte projekt.  
  
## <a name="changing-property-values-on-the-wpf-control"></a>Změna hodnot vlastností na ovládací prvek WPF  
 <xref:System.Windows.Forms.Integration.ElementHost> Inteligentních značek umožňuje snadno změnit vlastnosti hostované WPF obsahu pomocí Návrháře WPF.  
  
#### <a name="to-host-a-wpf-control"></a>K hostování ovládací prvek WPF  
  
1.  Otevřete `Form1` v Návrháři formulářů.  
  
2.  V **sada nástrojů**v **uživatelských ovládacích prvků WPF** kartě, dvakrát klikněte na `UserControl1` k vytvoření instance `UserControl1` na formuláři.  
  
     Instance `UserControl1` je hostován v nové <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.  
  
3.  V **ElementHost úlohy** inteligentní panel, vyberte **upravit hostované obsah**.  
  
     UserControl1.xaml otevře v Návrháři WPF.  
  
4.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Red`.  
  
5.  Znovu sestavte projekt.  
  
6.  Otevřete `Form1` v Návrháři formulářů.  
  
     Instance `UserControl1` má red pozadí.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Používání ovládacích prvků WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Návrhář WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
