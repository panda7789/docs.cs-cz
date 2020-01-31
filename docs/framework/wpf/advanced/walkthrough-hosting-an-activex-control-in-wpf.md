---
title: Hostování ovládacího prvku ActiveX v subsystému WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 4ca40c0f6e62fd413e7f305649c5c01ddc152b2a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794138"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>Návod: Hostování ovládacího prvku ActiveX v objektu WPF
Chcete-li povolit vylepšenou interakci s prohlížeči, můžete v aplikaci založené na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]použít ovládací prvky Microsoft ActiveX. Tento návod ukazuje, jak můžete hostovat Microsoft Windows Media Player jako ovládací prvek na stránce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytváří se projekt.

- Vytvoření ovládacího prvku ActiveX.

- Hostování ovládacího prvku ActiveX na stránce WPF.

 Po dokončení tohoto návodu budete pochopit, jak používat ovládací prvky Microsoft ActiveX ve vaší aplikaci založené na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- V počítači, kde je nainstalována aplikace Visual Studio, je nainstalována aplikace Microsoft Windows Media Player.

- Visual Studio 2010.

## <a name="creating-the-project"></a>Vytvoření projektu

### <a name="to-create-and-set-up-the-project"></a>Vytvoření a nastavení projektu

1. Vytvořte projekt aplikace WPF s názvem `HostingAxInWpf`.

2. Přidejte do řešení projekt knihovny ovládacích prvků model Windows Forms a pojmenujte projekt `WmpAxLib`.

3. V projektu WmpAxLib přidejte odkaz na sestavení Windows Media Player, které je pojmenované WMP. dll.

4. Otevřete **sadu nástrojů**.

5. Klikněte pravým tlačítkem myši na **panel nástrojů**a potom klikněte na příkaz **zvolit položky**.

6. Klikněte na kartu **komponenty modelu COM** , vyberte ovládací prvek **Windows Media Player** a pak klikněte na tlačítko **OK**.

     Do **sady nástrojů**se přidá ovládací prvek Windows Media Player.

7. V Průzkumník řešení klikněte pravým tlačítkem na soubor **UserControl1** a pak klikněte na **Přejmenovat**.

8. Změňte název na `WmpAxControl.vb` nebo `WmpAxControl.cs`v závislosti na jazyku.

9. Pokud se zobrazí výzva k přejmenování všech odkazů, klikněte na **Ano**.

## <a name="creating-the-activex-control"></a>Vytvoření ovládacího prvku ActiveX
Když je ovládací prvek přidán na návrhovou plochu, Visual Studio automaticky vygeneruje <xref:System.Windows.Forms.AxHost> obálkovou třídu pro ovládací prvek Microsoft ActiveX. Následující postup vytvoří spravované sestavení s názvem AxInterop. WMPLib. dll.

### <a name="to-create-the-activex-control"></a>Vytvoření ovládacího prvku ActiveX

1. Otevřete WmpAxControl. vb nebo WmpAxControl.cs v Návrhář formulářů.

2. Z **panelu nástrojů**přidejte ovládací prvek Windows Media Player na návrhovou plochu.

3. V okno Vlastnosti nastavte hodnotu vlastnosti <xref:System.Windows.Forms.Control.Dock%2A> ovládacího prvku Windows Media Player na <xref:System.Windows.Forms.DockStyle.Fill>.

4. Sestavte projekt knihovny ovládacích prvků WmpAxLib.

## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Hostování ovládacího prvku ActiveX na stránce WPF

### <a name="to-host-the-activex-control"></a>Hostování ovládacího prvku ActiveX

1. V projektu HostingAxInWpf přidejte odkaz na vygenerované sestavení interoperability ActiveX.

     Toto sestavení má název AxInterop. WMPLib. dll a bylo přidáno do složky ladění projektu WmpAxLib při importu ovládacího prvku Windows Media Player.

2. Přidejte odkaz na sestavení WindowsFormsIntegration, které má název WindowsFormsIntegration. dll.

3. Přidejte odkaz na sestavení model Windows Forms, které má název System. Windows. Forms. dll.

4. Otevřete MainWindow. XAML v Návrháři WPF.

5. Pojmenujte <xref:System.Windows.Controls.Grid> element `grid1`.

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. V zobrazení zobrazení Návrh nebo XAML vyberte prvek <xref:System.Windows.Window>.

7. V okno Vlastnosti klikněte na kartu **události** .

8. Dvakrát klikněte na událost <xref:System.Windows.FrameworkElement.Loaded>.

9. Vložte následující kód pro zpracování události <xref:System.Windows.FrameworkElement.Loaded>.

     Tento kód vytvoří instanci ovládacího prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost> a přidá instanci ovládacího prvku `AxWindowsMediaPlayer` jako jeho podřízenou položku.

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Stisknutím klávesy F5 Sestavte a spusťte aplikaci.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
