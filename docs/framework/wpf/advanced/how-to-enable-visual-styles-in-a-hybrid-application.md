---
title: 'Postupy: Povolení vizuálních stylů v hybridní aplikaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: f4684e277335a119d41d5bd79d504ed37a76d6fc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44179452"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Postupy: Povolení vizuálních stylů v hybridní aplikaci
Toto téma ukazuje, jak povolit [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] styly vizuál na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] konání ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace založené na.  
  
 Pokud vaše aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda, většina vašich [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky budou automaticky používat vizuální styly, když vaše aplikace běží na [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]. Další informace najdete v tématu [vykreslování ovládacích prvků s vizuálními styly](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Výpis úplného kódu úkoly uvedené v tomto tématu, naleznete v tématu [povolení vizuálních stylů v hybridní aplikace ukázku](https://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Povolení Windows Forms vizuální styly  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>K povolení vizuálních stylů Windows Forms  
  
1.  Vytvoření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projekt aplikace s názvem `HostingWfWithVisualStyles`.  
  
2.  V Průzkumníku řešení přidejte odkazy na následující sestavení.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  V sadě nástrojů klikněte dvakrát na <xref:System.Windows.Controls.Grid> ikonu umístit <xref:System.Windows.Controls.Grid> prvek na návrhové ploše.  
  
4.  V okně Vlastnosti nastavte hodnoty <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> vlastností **automaticky**.  
  
5.  V zobrazení návrhu nebo v XAML zobrazení, vyberte <xref:System.Windows.Window>.  
  
6.  V okně Vlastnosti klikněte na tlačítko **události** kartu.  
  
7.  Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.
  
8.  V souboru MainWindow.xaml.vb nebo MainWindow.xaml.cs, vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> událostí.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Vymalování s vizuálními styly ovládacího prvku.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Zakázání Windows Forms vizuální styly  
 Zakázat vizuálních stylů, jednoduše odeberte volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Chcete-li zakázat vizuálních stylů Windows Forms  
  
1.  Otevřete soubor MainWindow.xaml.vb nebo MainWindow.xaml.cs v editoru kódu.  
  
2.  Odkomentujte volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.  
  
3.  Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Vymalování ovládací prvek se stylem systému výchozí.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Vykreslování ovládacích prvků s vizuálními styly](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
