---
title: Hostování ovládacího prvku model Windows Forms v subsystému WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 2ed4e153a2513dc99d22a1538399156c138eb9e5
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123828"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje mnoho ovládacích prvků s bohatou sadou funkcí. Někdy ale můžete chtít použít model Windows Forms ovládací prvky na stránkách [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Například můžete mít významnou investici do stávajících model Windows Formsch ovládacích prvků, nebo můžete mít ovládací prvek model Windows Forms, který poskytuje jedinečné funkce.

Tento návod ukazuje, jak hostovat model Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> ovládací prvek na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránce pomocí kódu.

Úplný výpis kódu úloh uvedených v tomto návodu naleznete v tématu [hostování ovládacího prvku model Windows Forms v UKÁZCE WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).

## <a name="prerequisites"></a>Předpoklady

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="hosting-the-windows-forms-control"></a>Hostování ovládacího prvku model Windows Forms

### <a name="to-host-the-maskedtextbox-control"></a>Hostování ovládacího prvku ovládacím MaskedTextBox

1. Vytvořte projekt aplikace WPF s názvem `HostingWfInWpf`.

2. Přidejte odkazy na následující sestavení.

    - WindowsFormsIntegration

    - System.Windows.Forms

3. Otevřete MainWindow. XAML v Návrháři WPF.

4. Pojmenujte <xref:System.Windows.Controls.Grid> element `grid1`.

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. V zobrazení zobrazení Návrh nebo XAML vyberte prvek <xref:System.Windows.Window>.

6. V okno Vlastnosti klikněte na kartu **události** .

7. Dvakrát klikněte na událost <xref:System.Windows.FrameworkElement.Loaded>.

8. Vložte následující kód pro zpracování události <xref:System.Windows.FrameworkElement.Loaded>.

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. V horní části souboru přidejte následující `Imports` nebo příkaz `using`.

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF pomocí kódu XAML](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hostování ovládacího prvku model Windows Forms v ukázce WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
