---
title: "Postupy: Povolení vizuálních stylů v hybridní aplikaci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e628835f0e5fb315f15b9e9946c48f7017092bae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Postupy: Povolení vizuálních stylů v hybridní aplikaci
Toto téma ukazuje, jak povolit [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual styly na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení hostované v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě aplikace.  
  
 Pokud aplikace zavolá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda, většina vaše [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky automaticky použije vizuální styly, když aplikace běží na [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]. Další informace najdete v tématu [vykreslování ovládacích prvků s vizuálními styly](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Seznam dokončení kódu úkoly popsané v tomto tématu najdete v tématu [povolení vizuální styly v ukázku hybridní aplikace](http://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Povolení Windows Forms vizuální styly  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Chcete-li povolit vizuální styly Windows Forms  
  
1.  Vytvoření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projekt aplikace s názvem `HostingWfWithVisualStyles`.  
  
2.  V Průzkumníku řešení přidejte odkazy na následující sestavení.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  V sadě nástrojů, dvakrát klikněte <xref:System.Windows.Controls.Grid> ikonu umístit <xref:System.Windows.Controls.Grid> elementu na návrhovou plochu.  
  
4.  V okně vlastností nastavte hodnoty <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> vlastnosti, které chcete **automaticky**.  
  
5.  V návrhovém zobrazení nebo zobrazení jazyka XAML, vyberte <xref:System.Windows.Window>.  
  
6.  V okně vlastností klikněte **události** kartě.  
  
7.  Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.
  
8.  V MainWindow.xaml.vb nebo MainWindow.xaml.cs, vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> událostí.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Vykreslení ovládacího prvku s vizuálními styly.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Zakázání Windows Forms vizuální styly  
 Zakázání stylů, stačí odstranit volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda.  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Zakázání Windows Forms stylů  
  
1.  Otevřete MainWindow.xaml.vb nebo MainWindow.xaml.cs v editoru kódu.  
  
2.  Komentář volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda.  
  
3.  Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Vykreslení ovládacího prvku s výchozí styl systému.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Vykreslení ovládacích prvků s vizuálními styly](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [Postupy: Hostování ovládacího prvku Windows Forms v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
