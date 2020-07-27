---
title: Hostování ovládacího prvku model Windows Forms v subsystému WPF
description: Naučte se hostovat ovládací prvky model Windows Forms v Windows Presentation Foundation, které už poskytují mnoho ovládacích prvků s bohatou sadou funkcí.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: ec67cf9fabaa5b7aadbb2a3c21ebf8dd828ee20f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164974"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>Návod: Hostování ovládacího prvku Windows Forms ve WPF

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje mnoho ovládacích prvků s bohatou sadou funkcí. V některých případech však můžete chtít použít model Windows Forms ovládací prvky na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránkách. Například můžete mít významnou investici do stávajících model Windows Formsch ovládacích prvků, nebo můžete mít ovládací prvek model Windows Forms, který poskytuje jedinečné funkce.

V tomto návodu se dozvíte, jak hostovat <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> ovládací prvek model Windows Forms na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránce pomocí kódu.

Úplný výpis kódu úloh uvedených v tomto návodu naleznete v tématu [hostování ovládacího prvku model Windows Forms v UKÁZCE WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="hosting-the-windows-forms-control"></a>Hostování ovládacího prvku model Windows Forms

### <a name="to-host-the-maskedtextbox-control"></a>Hostování ovládacího prvku ovládacím MaskedTextBox

1. Vytvořte projekt aplikace WPF s názvem `HostingWfInWpf` .

2. Přidejte odkazy na následující sestavení.

    - WindowsFormsIntegration

    - System. Windows. Forms

3. Otevřete MainWindow. XAML v Návrháři WPF.

4. Pojmenujte <xref:System.Windows.Controls.Grid> element `grid1` .

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. V zobrazení zobrazení Návrh nebo XAML vyberte <xref:System.Windows.Window> prvek.

6. V okno Vlastnosti klikněte na kartu **události** .

7. Dvakrát klikněte na <xref:System.Windows.FrameworkElement.Loaded> událost.

8. Vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> události.

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. V horní části souboru přidejte následující `Imports` `using` příkaz nebo.

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. Stiskněte **F5**, aby se aplikace sestavila a spustila.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Návod: Hostování ovládacího prvku Windows Forms ve WPF pomocí XAML](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [Návod: Hostování složeného ovládacího prvku Windows Forms ve WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hostování ovládacího prvku model Windows Forms v ukázce WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
