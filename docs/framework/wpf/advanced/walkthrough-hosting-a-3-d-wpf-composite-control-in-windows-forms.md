---
title: 'Průvodce: Hostování složeného ovládacího prvku 3D WPF ve Windows Forms'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: b4c5001e671db9d615f3bcbc0a35b7b36b45bb01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506859"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>Průvodce: Hostování složeného ovládacího prvku 3D WPF ve Windows Forms

Tento návod ukazuje, jak můžete vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] složený ovládací prvek a hostujte ho v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky a formuláře pomocí <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.

V tomto návodu budete implementovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> , který obsahuje dva podřízené ovládací prvky. <xref:System.Windows.Controls.UserControl> Zobrazí trojrozměrného kužel (3D). Vykreslování 3D objekty je mnohem snazší díky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] než s [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Proto je vhodné na hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> třídy za účelem vytvoření 3D grafiky v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

Úlohy v tomto návodu zahrnují:

-   Vytváří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

-   Vytvoření projektu Windows Forms hostitele.

-   Hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

-   Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>Vytvořte uživatelský ovládací prvek

1.  Vytvoření **Knihovna uživatelských ovládacích prvků WPF** projekt s názvem `HostingWpfUserControlInWf`.

2.  Otevřete UserControl1.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

3.  Generovaného kódu nahraďte následujícím kódem:

     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     Tento kód definuje <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> , který obsahuje dva podřízené ovládací prvky. První podřízený ovládací prvek je <xref:System.Windows.Controls.Label?displayProperty=nameWithType> ovládacího prvku; druhá je <xref:System.Windows.Controls.Viewport3D> ovládací prvek, který zobrazí 3D kužel.

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>Vytvoření projektu hostitel

1.  Přidat **aplikace WPF (.NET Framework)** projekt s názvem `WpfUserControlHost` do řešení. Další informace najdete v tématu [jak: Vytvoření nového projektu aplikace WPF](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).

2.  V **Průzkumníka řešení**, přidejte odkaz na sestavení WindowsFormsIntegration, který se nazývá WindowsFormsIntegration.dll.

3.  Přidat odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení:

    -   PresentationCore

    -   PresentationFramework

    -   WindowsBase

4.  Přidejte odkaz na `HostingWpfUserControlInWf` projektu.

5.  V Průzkumníku řešení nastavte `WpfUserControlHost` projekt jako spouštěný projekt.

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>Hostování uživatelský ovládací prvek

1.  V Návrháři formulářů Windows otevřete Form1.

2.  V okně Vlastnosti klikněte na tlačítko **události**a potom dvakrát klikněte <xref:System.Windows.Forms.Form.Load> událost k vytvoření obslužné rutiny události.

     Otevře se Editor kódu do nově vytvořeného `Form1_Load` obslužné rutiny události.

3.  Nahraďte kód v Form1.cs s následujícím kódem.

     `Form1_Load` Obslužná rutina události vytvoří instanci `UserControl1` a přidá itto <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku kolekce podřízených ovládacích prvků. <xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek je přidán do kolekce podřízených ovládacích prvků formuláře.

     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4.  Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Návod: Hostování složeného ovládacího Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Hostování složeného ovládacího prvku WPF ve Windows Forms vzorku](https://go.microsoft.com/fwlink/?LinkID=160001)