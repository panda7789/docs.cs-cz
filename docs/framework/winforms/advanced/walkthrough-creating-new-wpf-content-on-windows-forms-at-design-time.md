---
title: "Návod: Vytvoření nového obsahu WPF ve Windows Forms během návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba7731456cfcf35cd16b1df304fee4f4c138db84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time"></a>Návod: Vytvoření nového obsahu WPF ve Windows Forms během návrhu
Toto téma ukazuje, jak vytvořit ovládací prvek Windows Presentation Foundation (WPF) pro použití v aplikacích Windows formulářů.  
  
 V tomto návodu můžete provádět následující úlohy:  
  
-   Vytvoření projektu.  
  
-   Vytvořte nový ovládací prvek WPF.  
  
-   Přidejte nové ovládací prvek WPF do formuláře systému Windows. Ovládací prvek WPF je hostován v <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu modelu Windows Forms.  
  
> [!NOTE]
>  Pokud hostování obsahu subsystému WPF, jsou podporovány pouze projekty C# a Visual Basic.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
-   Vytvořte nový projekt aplikace Windows Forms v jazyce Visual Basic a Visual C# s názvem `HostingWpf`.  
  
## <a name="creating-a-new-wpf-control"></a>Vytvoření nové ovládací prvek WPF  
 Vytvoření nové ovládací prvek WPF a její přidání do projektu je stejně snadná jako přidávání dalších položek do projektu. Návrhář formulářů Windows funguje s konkrétní typ ovládací prvek s názvem *složeného ovládacího prvku*, nebo *uživatelský ovládací prvek*. Další informace o uživatelských ovládacích prvků WPF najdete v tématu <xref:System.Windows.Controls.UserControl>.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> Typ pro WPF se liší od typ ovládacího prvku uživatele poskytované Windows Forms, který je také název <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.  
  
#### <a name="to-create-a-new-wpf-control"></a>Chcete-li vytvořit nový ovládací prvek WPF  
  
1.  V **Průzkumníku řešení**, přidejte nový **knihovny ovládací prvek WPF uživatelského** projektu k řešení. Použít výchozí název pro knihovnu řízení `WpfControlLibrary1`. Výchozí název ovládacího prvku je `UserControl1.xaml`.  
  
     Přidání nového ovládacího prvku má tyto důsledky.  
  
    -   Soubor UserControl1.xaml je přidána.  
  
    -   Soubor UserControl1.xaml.cs nebo UserControl1.xaml.vb přidán. Tento soubor obsahuje kódu pro obslužné rutiny událostí a jiné implementace.  
  
    -   Odkazy na sestavení WPF jsou přidány.  
  
    -   UserControl1.xaml soubor se otevře v [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].  
  
2.  V návrhovém zobrazení, ujistěte se, že `UserControl1` je vybrána. Další informace najdete v tématu [postup: vyberte a přesunout elementů na návrhovou plochu](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti, které chcete `200`.  
  
4.  Z **sada nástrojů**, přetáhněte ji <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> ovládacího prvku na návrhovou plochu.  
  
5.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost **hostované obsahu**.  
  
    > [!NOTE]
    >  Obecně platí by měl hostitel sofistikovanější obsahu WPF. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Řízení tady je použita pouze pro ilustraci.  
  
6.  Sestavte projekt.  
  
## <a name="adding-a-wpf-control-to-a-windows-form"></a>Přidání ovládacího prvku WPF na formuláři Windows  
 Nový ovládací prvek WPF je připravený k použití na formuláři. Windows Forms používá <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek jako hostitele obsahu WPF  
  
#### <a name="to-add-a-wpf-control-to-a-windows-form"></a>Přidání ovládacího prvku WPF do formuláře Windows  
  
1.  Otevřete `Form1` v Návrháři formulářů.  
  
2.  V **sada nástrojů**, najít na kartě s názvem bez přípony **WPFUserControlLibrary WPF uživatelské ovládací prvky**.  
  
3.  Přetáhněte instanci `UserControl1` do formuláře.  
  
    -   <xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek je automaticky vytvořen ve formuláři pro hostování ovládací prvek WPF.  
  
    -   <xref:System.Windows.Forms.Integration.ElementHost> Řízení jmenuje `elementHost1` a v **vlastnosti** okně uvidíte jeho <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> je nastavena na **UserControl1**.  
  
    -   Odkazy na sestavení WPF jsou přidány do projektu.  
  
    -   `elementHost1` Má ovládací prvek inteligentního panelu, které jsou uvedené dostupné možnosti hostování.  
  
4.  V **ElementHost úlohy** inteligentní panel, vyberte **ukotvení v nadřazený kontejner**.  
  
5.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
## <a name="next-steps"></a>Další kroky  
 Windows Forms a WPF jsou různých technologií, ale jsou navrženy úzce spolupracovat. Pokud chcete zadat bohatší vzhled a chování v aplikacích, zkuste následující postup.  
  
-   Hostování ovládacího prvku Windows Forms na stránce WPF. Další informace najdete v tématu [návod: hostování ovládacího prvku Windows Forms v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).  
  
-   Vizuální styly Windows Forms použijte k vašemu obsahu WPF. Další informace najdete v tématu [postupy: povolení vizuální styly v hybridní aplikace](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
-   Změna stylu obsahu WPF. Další informace najdete v tématu [návod: určení stylu obsahu WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migrace a interoperabilita](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Používání ovládacích prvků WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Návrhář WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
