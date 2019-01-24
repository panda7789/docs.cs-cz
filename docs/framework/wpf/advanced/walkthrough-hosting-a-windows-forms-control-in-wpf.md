---
title: 'Průvodce: Hostování ovládacího prvku Windows Forms v subsystému WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 2bbc3d249504bf8bb80dd29de3110002f0fd87e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548817"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>Průvodce: Hostování ovládacího prvku Windows Forms v subsystému WPF

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabízí mnoho ovládacích prvků s bohatou sadou funkcí. Však můžete někdy chtít použít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky ve vašich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky. Například můžete mít značné investice v existujícím [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, nebo můžete mít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který poskytuje jedinečné funkce.

Tento návod ukazuje, jak hostovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> ovládání na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky pomocí kódu.

Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [hostování ovládacího prvku Windows Forms v ukázce WPF](https://go.microsoft.com/fwlink/?LinkID=160057).

## <a name="prerequisites"></a>Požadavky

Visual Studio k dokončení tohoto návodu potřebujete.

## <a name="hosting-the-windows-forms-control"></a>Hostování ovládacího prvku Windows Forms

### <a name="to-host-the-maskedtextbox-control"></a>K hostování ovládacím prvkem MaskedTextBox

1.  Vytvoření projektu aplikace WPF s názvem `HostingWfInWpf`.

2.  Přidáte odkazy na následující sestavení.

    -   WindowsFormsIntegration

    -   System.Windows.Forms

3.  Otevřete soubor MainWindow.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

4.  Název <xref:System.Windows.Controls.Grid> element `grid1`.

     [!code-xaml[HostingWfInWPF#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5.  V zobrazení návrhu nebo v XAML zobrazení, vyberte <xref:System.Windows.Window> elementu.

6.  V okně Vlastnosti klikněte na tlačítko **události** kartu.

7.  Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.

8.  Vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> událostí.

     [!code-csharp[HostingWfInWPF#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. Na začátek souboru přidejte následující `Imports` nebo `using` příkazu.

     [!code-csharp[HostingWfInWPF#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF pomocí XAML](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [Návod: Hostování složeného ovládacího Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hostování ovládacího prvku Windows Forms v ukázce WPF](https://go.microsoft.com/fwlink/?LinkID=160057)