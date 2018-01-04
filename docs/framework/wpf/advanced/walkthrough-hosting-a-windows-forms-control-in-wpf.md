---
title: "Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF"
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
helpviewer_keywords: hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38b50c90f653238d44401bac917645cd7f293681
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje mnoho ovládacích prvků bohaté sadě funkcí. Ale v některých případech můžete použít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky na vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky. Například můžete mít významné investice v existující [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, nebo může mít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který poskytuje jedinečné funkce.  
  
 Tento návod ukazuje, jak hostovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> řízení na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky pomocí kódu.  
  
 Kompletní kód tak seznam úloh v tomto návodu najdete v tématu [hostování ovládacího prvku Windows Forms v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=160057).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="hosting-the-windows-forms-control"></a>Hostování ovládacího prvku Windows Forms  
  
#### <a name="to-host-the-maskedtextbox-control"></a>K hostování MaskedTextBox – ovládací prvek  
  
1.  Vytvořte projekt aplikace WPF s názvem `HostingWfInWpf`.  
  
2.  Přidejte odkazy na následující sestavení.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Otevřete MainWindow.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  Název <xref:System.Windows.Controls.Grid> element `grid1`.  
  
     [!code-xaml[HostingWfInWPF#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]  
  
5.  V návrhovém zobrazení nebo zobrazení jazyka XAML, vyberte <xref:System.Windows.Window> elementu.  
  
6.  V okně vlastností klikněte **události** kartě.  
  
7.  Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.  
  
8.  Vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> událostí.  
  
     [!code-csharp[HostingWfInWPF#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]  
  
9. Na začátek souboru přidejte následující `Imports` nebo `using` příkaz.  
  
     [!code-csharp[HostingWfInWPF#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]  
  
10. Stisknutím klávesy F5 sestavení a spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návrhář WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF pomocí kódu XAML](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)  
 [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [Hostování ovládacího prvku Windows Forms v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=160057)
