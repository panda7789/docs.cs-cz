---
title: 'Návod: Mapování vlastností použitím elementu WindowsFormsHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: 86a7a8a937b9407690d7f1981b91857d1b44ded1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373878"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>Návod: Mapování vlastností použitím elementu WindowsFormsHost

Tento návod ukazuje, jak používat <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> vlastnost mapovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti odpovídající vlastnosti na hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.

Úlohy v tomto návodu zahrnují:

-   Vytvoření projektu.

-   Definování rozložení aplikace.

-   Definování nového mapování vlastností.

-   Odebrání výchozí mapování vlastností.

-   Nahraďte výchozí mapování vlastností.

-   Rozšíření výchozí mapování vlastností.

Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [mapování vlastností použitím ukázka elementu WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).

Až budete hotovi, budete moci mapovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti odpovídající vlastnosti na hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

-   Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>Vytvoření a nastavení projektu

1.  Vytvoření **aplikace WPF** projekt s názvem `PropertyMappingWithWfhSample`.

2.  V **Průzkumníka řešení**, přidejte odkaz na sestavení WindowsFormsIntegration, který se nazývá WindowsFormsIntegration.dll.

3.  V **Průzkumníka řešení**, přidejte odkazy na sestavení System.Drawing a System.Windows.Forms.

## <a name="defining-the-application-layout"></a>Definování rozložení aplikace

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– Na základě aplikace používá <xref:System.Windows.Forms.Integration.WindowsFormsHost> element na hostitele [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.

### <a name="to-define-the-application-layout"></a>Pokud chcete definovat rozložení aplikace

1.  Otevřete Window1.xaml v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

2.  Nahraďte stávající kód následujícím kódem.

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3.  Otevřete Window1.xaml.cs v editoru kódu.

4.  V horní části souboru importujte následující obory názvů.

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>Definování nového mapování vlastností

<xref:System.Windows.Forms.Integration.WindowsFormsHost> Element poskytuje několik výchozích mapování vlastností. Přidat nové mapování vlastností pomocí volání <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-define-a-new-property-mapping"></a>Chcete-li definovat nové mapování vlastností

-   Zkopírujte následující kód do definice pro `Window1` třídy.

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     `AddClipMapping` Metoda přidá nové mapování <xref:System.Windows.UIElement.Clip%2A> vlastnost.

     `OnClipChange` Metoda překládá <xref:System.Windows.UIElement.Clip%2A> vlastnost [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> vlastnost.

     `Window1_SizeChanged` Obsluhovala v okně <xref:System.Windows.FrameworkElement.SizeChanged> události a velikosti oblast ořezu podle okna aplikace.

## <a name="removing-a-default-property-mapping"></a>Odebrání výchozí mapování vlastností

Odebrání výchozí mapování vlastností pomocí volání <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metodu na <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-remove-a-default-property-mapping"></a>Chcete-li odebrat výchozí mapování vlastností

-   Zkopírujte následující kód do definice pro `Window1` třídy.

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     `RemoveCursorMapping` Metoda odstraní výchozí mapování <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost.

## <a name="replacing-a-default-property-mapping"></a>Nahraďte výchozí mapování vlastností

Nahraďte výchozí mapování vlastnosti tak, že odeberete výchozí mapování a volání <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-replace-a-default-property-mapping"></a>Chcete-li nahradit výchozí mapování vlastností

-   Zkopírujte následující kód do definice pro `Window1` třídy.

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     `ReplaceFlowDirectionMapping` Metoda nahradí výchozí mapování <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost.

     `OnFlowDirectionChange` Metoda překládá <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost.

     `cb_CheckedChanged` Metoda obslužné rutiny <xref:System.Windows.Forms.CheckBox.CheckedChanged> událostí na <xref:System.Windows.Forms.CheckBox> ovládacího prvku. Přiřazuje <xref:System.Windows.FrameworkElement.FlowDirection%2A> nastavenou na hodnotu <xref:System.Windows.Forms.CheckBox.CheckState%2A> vlastnost

## <a name="extending-a-default-property-mapping"></a>Rozšíření výchozí mapování vlastností

Můžete použít výchozí mapování vlastností a také rozšířit o vlastní mapování.

### <a name="to-extend-a-default-property-mapping"></a>Chcete-li rozšířit výchozí mapování vlastností

-   Zkopírujte následující kód do definice pro `Window1` třídy.

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     `ExtendBackgroundMapping` Metoda přidá převaděče vlastní vlastnost do existující <xref:System.Windows.Controls.Control.Background%2A> mapování vlastností.

     `OnBackgroundChange` Metoda přiřadí hostovaného ovládacího prvku konkrétní image <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost. `OnBackgroundChange` Metoda se volá, když se použije výchozí mapování vlastností.

## <a name="initializing-your-property-mappings"></a>Inicializuje se mapování vlastností

Nastavení mapování vlastností pomocí volání metody bylo popsáno dříve <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.

### <a name="to-initialize-your-property-mappings"></a>Inicializace mapování vlastností

1.  Zkopírujte následující kód do definice pro `Window1` třídy.

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     `WindowLoaded` Metoda obslužné rutiny <xref:System.Windows.FrameworkElement.Loaded> událostí a provádí následující inicializace.

    -   Vytvoří [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> ovládacího prvku.

    -   Volá metody, které jste definovali dříve v návodu k nastavení mapování vlastností.

    -   Přiřadí počáteční hodnoty pro mapovanou vlastnosti.

2.  Stisknutím klávesy **F5** sestavíte a spustíte aplikaci. Klikněte na zaškrtávací políčko na vliv <xref:System.Windows.FrameworkElement.FlowDirection%2A> mapování. Po kliknutí na zaškrtávací políčko obrátí rozložení zleva doprava orientace.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Mapování vlastnosti Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)