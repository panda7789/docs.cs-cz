---
title: 'Návod: Změna vlastností hostovaného prvku WPF během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
ms.openlocfilehash: 15cab9266af5840aa4b37a62b71bd5010b7a859a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741017"
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a>Návod: Změna vlastností hostovaného prvku WPF během návrhu
Tento návod ukazuje, jak změnit hodnoty vlastností ovládací prvek Windows Presentation Foundation (WPF), který je hostován ve formuláři Windows.  
  
 V tomto podrobném návodu můžete provádět následující úlohy:  
  
-   Vytvoření projektu.  
  
-   Vytvoření ovládacího prvku WPF.  
  
-   Hostování ovládacích prvků WPF na formuláři Windows.  
  
-   WPF Designer pro Visual Studio použijte ke změně hodnot vlastností.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu Windows Forms.  
  
> [!NOTE]
>  Při hostování obsahu WPF, jsou podporovány pouze projekty C# a Visual Basic.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte nový projekt Formulářové aplikace Windows v jazyce Visual Basic nebo Visual C# s názvem `WpfHost`.  
  
## <a name="creating-the-wpf-control"></a>Vytvoření ovládacího prvku WPF  
 Po přidání ovládacího prvku WPF do projektu, můžete je nastavit na formuláři.  
  
#### <a name="to-create-wpf-controls"></a>Chcete-li vytvořit ovládací prvky WPF  
  
1.  Přidat nový WPF <xref:System.Windows.Controls.UserControl> do projektu. Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`. Další informace najdete v tématu [návod: vytváření nových WPF obsahu ve Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Blue`.  
  
3.  Sestavte projekt.  
  
## <a name="changing-property-values-on-the-wpf-control"></a>Změny hodnot vlastností ovládacího prvku WPF  
 <xref:System.Windows.Forms.Integration.ElementHost> Inteligentních značek umožňuje snadno změnit vlastnosti z prostředí WPF obsahu pomocí Návrháře WPF.  
  
#### <a name="to-host-a-wpf-control"></a>K hostování ovládacího prvku WPF  
  
1.  Otevřít `Form1` v Návrháři formulářů Windows.  
  
2.  V **nástrojů**v **uživatelské ovládací prvky WPF** kartu, dvakrát klikněte na panel `UserControl1` k vytvoření instance `UserControl1` ve formuláři.  
  
     Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.  
  
3.  V **ElementHost úlohy** panelu inteligentních značek, vyberte **upravit hostovaný obsah**.  
  
     UserControl1.xaml se otevře v Návrháři WPF.  
  
4.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Red`.  
  
5.  Sestavte projekt znovu.  
  
6.  Otevřít `Form1` v Návrháři formulářů Windows.  
  
     Instance `UserControl1` má červené na pozadí.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Postupy: Zarovnání ovládacího prvku k okrajům formulářů během návrhu](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Používání ovládacích prvků WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
