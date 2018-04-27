---
title: 'Návod: Hostování ovládacího prvku ActiveX v objektu WPF'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fc4f577da04fb8ed15bae3c0497b35803a46f08f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>Návod: Hostování ovládacího prvku ActiveX v objektu WPF
Chcete-li umožnit lepší interakci s prohlížeči, můžete použít [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] ovládacích prvků do vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě aplikace. Tento návod ukazuje, jak můžete hostovat [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] jako ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytváření projektu.  
  
-   Vytvoření ovládacího prvku ActiveX.  
  
-   Hostování ovládacího prvku ActiveX na stránce WPF.  
  
 Po dokončení tohoto průvodce můžete bude pochopit, jak používat [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] ovládacích prvků do vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě aplikace.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] v počítači, kde je nainstalována sada Visual Studio nainstalována.  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
  
#### <a name="to-create-and-set-up-the-project"></a>Vytvoření a nastavení projektu  
  
1.  Vytvořte projekt aplikace WPF s názvem `HostingAxInWpf`.  
  
2.  Přidejte projektu knihovny ovládacích prvků Windows Forms k řešení a název projektu `WmpAxLib`.  
  
3.  V projektu WmpAxLib přidáte odkaz na sestavení program Windows Media Player, která se nazývá wmp.dll.  
  
4.  Otevřete **sada nástrojů**.  
  
5.  Klikněte pravým tlačítkem myši **sada nástrojů**a potom klikněte na **zvolit položky**.  
  
6.  Klikněte na tlačítko **COM – součásti** vyberte **program Windows Media Player** řízení a pak klikněte na tlačítko **OK**.  
  
     Ovládací prvek Windows Media Player je přidán do **sada nástrojů**.  
  
7.  V Průzkumníku řešení klikněte pravým tlačítkem myši **UserControl1** souboru a potom klikněte na **přejmenovat**.  
  
8.  Změňte název `WmpAxControl.vb` nebo `WmpAxControl.cs`, v závislosti na jazyce.  
  
9. Pokud se zobrazí výzva k přejmenování všech odkazů, klikněte na tlačítko **Ano**.  
  
## <a name="creating-the-activex-control"></a>Vytvoření ovládacího prvku ActiveX  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] automaticky generuje <xref:System.Windows.Forms.AxHost> obálkovou třídu pro [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] řízení, když je ovládací prvek přidán na návrhovou plochu. Následující postup vytvoří spravované sestavení s názvem AxInterop.WMPLib.dll.  
  
#### <a name="to-create-the-activex-control"></a>Vytvoření ovládacího prvku ActiveX  
  
1.  Otevřete WmpAxControl.vb nebo WmpAxControl.cs v Návrháři formulářů.  
  
2.  Z **sada nástrojů**, přidání ovládacího prvku Windows Media Player na návrhovou plochu.  
  
3.  V okně vlastnosti nastavit hodnotu ovládacího prvku Windows Media Player <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.  
  
4.  Sestavení projektu knihovny WmpAxLib ovládacího prvku.  
  
## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Hostování ovládacího prvku ActiveX na stránce WPF  
  
#### <a name="to-host-the-activex-control"></a>K hostování ovládacího prvku ActiveX  
  
1.  V projektu HostingAxInWpf přidat odkaz na vygenerovaného [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] interoperabilita sestavení.  
  
     Toto sestavení jmenuje AxInterop.WMPLib.dll a byla přidána do složky ladění projektu WmpAxLib při importu ovládacího prvku Windows Media Player.  
  
2.  Přidáte odkaz na sestavení WindowsFormsIntegration, která se nazývá WindowsFormsIntegration.dll.  
  
3.  Přidat odkaz na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sestavení, která se nazývá System.Windows.Forms.dll.  
  
4.  Otevřete MainWindow.xaml v Návrháři WPF.  
  
5.  Název <xref:System.Windows.Controls.Grid> element `grid1`.  
  
     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  V návrhovém zobrazení nebo zobrazení jazyka XAML, vyberte <xref:System.Windows.Window> elementu.  
  
7.  V okně vlastností klikněte **události** kartě.  
  
8.  Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.  
  
9. Vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> událostí.  
  
     Tento kód vytvoří instanci <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení a přidá instanci `AxWindowsMediaPlayer` ovládací prvek, jeho dceřiný.  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návrhář WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
