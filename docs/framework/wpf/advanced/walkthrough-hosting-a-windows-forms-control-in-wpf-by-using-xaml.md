---
title: 'Návod: Hostování ovládacího prvku Windows Forms v objektu WPF použitím kódu XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 10596f3ec89a5dc8bb7c20274b697d2592ad93d5
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197886"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>Návod: Hostování ovládacího prvku Windows Forms v objektu WPF použitím kódu XAML
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje mnoho ovládacích prvků s bohatou sadou funkcí. Někdy ale můžete chtít použít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky na stránkách [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Například můžete mít významnou investici do stávajících [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ch ovládacích prvků, nebo můžete mít ovládací prvek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], který poskytuje jedinečné funkce.  
  
 V tomto návodu se dozvíte, jak hostovat model Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> ovládacím prvku na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránce pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Úplný výpis kódu úloh uvedených v tomto návodu naleznete v tématu [hostování ovládacího prvku model Windows Forms v prostředí WPF pomocí ukázky XAML](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).
  
## <a name="prerequisites"></a>Požadavky  

K dokončení tohoto Názorného postupu potřebujete Visual Studio.  
  
## <a name="hosting-the-windows-forms-control"></a>Hostování ovládacího prvku model Windows Forms  
  
#### <a name="to-host-the-maskedtextbox-control"></a>Hostování ovládacího prvku ovládacím MaskedTextBox  
  
1. Vytvořte projekt aplikace WPF s názvem `HostingWfInWpfWithXaml`.  
  
2. Přidejte odkazy na následující sestavení.  
  
    - WindowsFormsIntegration  
  
    - System. Windows. Forms  
  
3. Otevřete MainWindow. XAML v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4. V elementu <xref:System.Windows.Window> přidejte následující mapování oboru názvů. Mapování oboru názvů `wf` vytvoří odkaz na sestavení, které obsahuje ovládací prvek model Windows Forms.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. Do elementu <xref:System.Windows.Controls.Grid> přidejte následující XAML.  
  
     <xref:System.Windows.Forms.MaskedTextBox> ovládací prvek je vytvořen jako podřízený ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. Stisknutím klávesy F5 Sestavte a spusťte aplikaci.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hostování ovládacího prvku model Windows Forms v subsystému WPF pomocí ukázky XAML](https://go.microsoft.com/fwlink/?LinkID=160000)
