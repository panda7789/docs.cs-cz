---
title: 'Návod: Hostování složeného ovládacího prvku 3D WPF ve Windows Forms'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: a35f2b4062edb18914c55046a69dcd9b8825d778
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353851"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>Návod: Hostování složeného ovládacího prvku 3D WPF ve Windows Forms

Tento návod ukazuje, jak lze vytvořit složený ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a hostovat ho v ovládacích prvcích a formulářích [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pomocí ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost>.

V tomto návodu implementujete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>, který obsahuje dva podřízené ovládací prvky. @No__t-0 zobrazí trojrozměrné (3D) kužel. Vykreslování 3D objektů je mnohem snazší s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] než s [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Proto má smysl hostovat třídu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> k vytváření 3D grafiky v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytváří se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

- Vytváří se projekt hostitele model Windows Forms.

- Hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>Vytvoření prvku UserControl

1. Vytvořte projekt **knihovny uživatelských ovládacích prvků WPF** s názvem `HostingWpfUserControlInWf`.

2. Otevřete UserControl1. XAML v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

3. Vygenerovaný kód nahraďte následujícím kódem:

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     Tento kód definuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>, který obsahuje dva podřízené ovládací prvky. První podřízený ovládací prvek je ovládací prvek @no__t 0; druhým je ovládací prvek <xref:System.Windows.Controls.Viewport3D>, který zobrazuje prostorový kuželový.

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>Vytvořit hostitelský projekt

1. Přidejte do řešení projekt **aplikace model Windows Forms (.NET Framework)** s názvem `WpfUserControlHost`.

2. V **Průzkumník řešení**přidejte odkaz na sestavení WindowsFormsIntegration, které má název WindowsFormsIntegration. dll.

3. Přidejte odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení:

    - PresentationCore

    - PresentationFramework

    - WindowsBase

4. Přidejte odkaz na projekt `HostingWpfUserControlInWf`.

5. V Průzkumník řešení nastavte projekt `WpfUserControlHost` na spouštěný projekt.

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>Hostování prvku UserControl

1. V Návrhář formulářů otevřete Form1.

2. V okno Vlastnosti klikněte na položku **události**a potom poklikejte na událost <xref:System.Windows.Forms.Form.Load> a vytvořte obslužnou rutinu události.

     Editor kódu se otevře nově vygenerované obslužné rutiny události `Form1_Load`.

3. Nahraďte kód v Form1.cs následujícím kódem.

     Obslužná rutina události `Form1_Load` vytvoří instanci `UserControl1` a přidá tovární kolekci podřízených ovládacích prvků <xref:System.Windows.Forms.Integration.ElementHost>. Ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> se přidá do kolekce podřízených ovládacích prvků formuláře.

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Návod: Hostování složeného ovládacího prvku WPF v model Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Návod: Hostování model Windows Forms složeného ovládacího prvku v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Hostování složeného ovládacího prvku WPF v model Windows Forms Sample](https://go.microsoft.com/fwlink/?LinkID=160001)
