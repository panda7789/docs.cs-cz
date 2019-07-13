---
title: 'Návod: Hostování ovládacího prvku ActiveX ve WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 0181093de1c40889110ab7eae75a3847a17845a9
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859939"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>Návod: Hostování ovládacího prvku ActiveX ve WPF
Chcete-li umožňují lepší interakci s prohlížeči, můžete použít ovládacími prvky ActiveX v vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace založené na. Tento návod ukazuje, jak můžete hostovat [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] jako ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky.

 Úlohy v tomto návodu zahrnují:

- Vytvoření projektu.

- Vytvoření ovládacího prvku ActiveX.

- Hostování ovládacího prvku ActiveX na stránce WPF.

 Po dokončení tohoto návodu budete rozumět použití ovládacími prvky ActiveX v vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace založené na.

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] nainstalované v počítači nainstalovanou aplikaci Visual Studio.

- Visual Studio 2010.

## <a name="creating-the-project"></a>Vytvoření projektu

### <a name="to-create-and-set-up-the-project"></a>K vytvoření a nastavení projektu

1. Vytvoření projektu aplikace WPF s názvem `HostingAxInWpf`.

2. Přidat do řešení projekt Knihovna ovládacích prvků Windows Forms a pojmenujte projekt `WmpAxLib`.

3. V projektu WmpAxLib přidejte odkaz na sestavení programu Windows Media Player, který se nazývá wmp.dll.

4. Otevřít **nástrojů**.

5. Klikněte pravým tlačítkem **nástrojů**a potom klikněte na tlačítko **zvolit položky**.

6. Klikněte na tlačítko **komponenty modelu COM** kartu, vyberte **Windows Media Player** ovládací prvek a potom klikněte na tlačítko **OK**.

     Ovládací prvek programu Windows Media Player je přidán do **nástrojů**.

7. V Průzkumníku řešení klikněte pravým tlačítkem myši **UserControl1** souboru a pak klikněte na tlačítko **přejmenovat**.

8. Změňte název na `WmpAxControl.vb` nebo `WmpAxControl.cs`, v závislosti na jazyku.

9. Pokud se zobrazí výzva k přejmenování všech odkazů, klikněte na tlačítko **Ano**.

## <a name="creating-the-activex-control"></a>Vytvoření ovládacího prvku ActiveX
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] automaticky generuje <xref:System.Windows.Forms.AxHost> obálkovou třídu pro ovládací prvek Microsoft ActiveX, když je ovládací prvek přidán na návrhovou plochu. Následujícím postupem vytvoříte spravované sestavení s názvem AxInterop.WMPLib.dll.

### <a name="to-create-the-activex-control"></a>Vytvoření ovládacího prvku ActiveX

1. Otevřete WmpAxControl.vb nebo WmpAxControl.cs v Návrháři formulářů Windows.

2. Z **nástrojů**, přidejte ovládací prvek programu Windows Media Player na návrhovou plochu.

3. V okně Vlastnosti nastavte hodnotu ovládacího prvku programu Windows Media Player <xref:System.Windows.Forms.Control.Dock%2A> vlastnost <xref:System.Windows.Forms.DockStyle.Fill>.

4. Vytvoření projektu knihovny ovládacích prvků WmpAxLib.

## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Hostování ovládacího prvku ActiveX na stránce WPF

### <a name="to-host-the-activex-control"></a>K hostování ovládacího prvku ActiveX

1. V projektu HostingAxInWpf přidáte odkaz do generovaného sestavení, vzájemná funkční spolupráce ActiveX.

     Toto sestavení je s názvem AxInterop.WMPLib.dll a byl přidán do složky ladění projektu WmpAxLib při importu ovládací prvek programu Windows Media Player.

2. Přidáte odkaz na sestavení WindowsFormsIntegration, který se nazývá WindowsFormsIntegration.dll.

3. Přidejte odkaz na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sestavení, který se nazývá System.Windows.Forms.dll.

4. Otevřete soubor MainWindow.xaml v návrháři pro WPF.

5. Název <xref:System.Windows.Controls.Grid> element `grid1`.

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. V zobrazení návrhu nebo v XAML zobrazení, vyberte <xref:System.Windows.Window> elementu.

7. V okně Vlastnosti klikněte na tlačítko **události** kartu.

8. Dvakrát klikněte <xref:System.Windows.FrameworkElement.Loaded> událostí.

9. Vložte následující kód pro zpracování <xref:System.Windows.FrameworkElement.Loaded> událostí.

     Tento kód vytvoří instanci <xref:System.Windows.Forms.Integration.WindowsFormsHost> řídit a přidá instanci `AxWindowsMediaPlayer` ovládací prvek jako jeho podřízených.

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Stisknutím klávesy F5 sestavte a spusťte aplikaci.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Návod: Hostování složeného ovládacího Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
