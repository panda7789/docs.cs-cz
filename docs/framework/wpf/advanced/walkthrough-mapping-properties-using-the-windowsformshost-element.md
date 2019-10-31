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
ms.openlocfilehash: c8a83dd3f7327d00979431ca7fa801ff642a4eef
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197809"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>Návod: Mapování vlastností použitím elementu WindowsFormsHost

Tento návod ukazuje, jak použít vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> k mapování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností na odpovídající vlastnosti v hostovaném ovládacím prvku [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytváří se projekt.

- Definování rozložení aplikace.

- Definování nového mapování vlastností.

- Odebírá se výchozí mapování vlastností.

- Nahrazuje se výchozí mapování vlastností.

- Rozšíření výchozího mapování vlastností.

Úplný výpis kódu úloh, které jsou znázorněny v tomto návodu, najdete v tématu [mapování vlastností pomocí ukázky elementu WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).

Až budete hotovi, budete moci mapovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti na odpovídající vlastnosti v hostovaném ovládacím prvku [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>Vytvoření a nastavení projektu

1. Vytvořte projekt **aplikace WPF** s názvem `PropertyMappingWithWfhSample`.

2. V **Průzkumník řešení**přidejte odkaz na sestavení WindowsFormsIntegration, které má název WindowsFormsIntegration. dll.

3. V **Průzkumník řešení**přidejte odkazy na sestavení System. Drawing a System. Windows. Forms.

## <a name="defining-the-application-layout"></a>Definování rozložení aplikace

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikace používá <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek pro hostování ovládacího prvku [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

### <a name="to-define-the-application-layout"></a>Definování rozložení aplikace

1. Otevřete Window1. XAML v [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

2. Nahraďte existující kód následujícím kódem.

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. Otevřete Window1.xaml.cs v editoru kódu.

4. V horní části souboru importujte následující obory názvů.

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>Definování nového mapování vlastností

Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> poskytuje několik výchozích mapování vlastností. Přidáte nové mapování vlastností voláním metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

### <a name="to-define-a-new-property-mapping"></a>Definování nového mapování vlastností

- Zkopírujte následující kód do definice pro třídu `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     Metoda `AddClipMapping` přidá nové mapování pro vlastnost <xref:System.Windows.UIElement.Clip%2A>.

     Metoda `OnClipChange` překládá vlastnost <xref:System.Windows.UIElement.Clip%2A> na vlastnost [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A>.

     Metoda `Window1_SizeChanged` zpracovává událost <xref:System.Windows.FrameworkElement.SizeChanged> okna a velikost oblasti oříznutí tak, aby odpovídala oknu aplikace.

## <a name="removing-a-default-property-mapping"></a>Odebírá se výchozí mapování vlastností.

Odeberte výchozí mapování vlastností voláním metody <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

### <a name="to-remove-a-default-property-mapping"></a>Odebrání výchozího mapování vlastností

- Zkopírujte následující kód do definice pro třídu `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     Metoda `RemoveCursorMapping` odstraní výchozí mapování pro vlastnost <xref:System.Windows.FrameworkElement.Cursor%2A>.

## <a name="replacing-a-default-property-mapping"></a>Nahrazení výchozího mapování vlastností

Nahraďte výchozí mapování vlastností odebráním výchozího mapování a voláním metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

### <a name="to-replace-a-default-property-mapping"></a>Nahrazení výchozího mapování vlastností

- Zkopírujte následující kód do definice pro třídu `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     Metoda `ReplaceFlowDirectionMapping` nahrazuje výchozí mapování pro vlastnost <xref:System.Windows.FrameworkElement.FlowDirection%2A>.

     Metoda `OnFlowDirectionChange` překládá vlastnost <xref:System.Windows.FrameworkElement.FlowDirection%2A> na vlastnost [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A>.

     Metoda `cb_CheckedChanged` zpracovává událost <xref:System.Windows.Forms.CheckBox.CheckedChanged> v ovládacím prvku <xref:System.Windows.Forms.CheckBox>. Přiřadí vlastnost <xref:System.Windows.FrameworkElement.FlowDirection%2A> na základě hodnoty vlastnosti <xref:System.Windows.Forms.CheckBox.CheckState%2A>

## <a name="extending-a-default-property-mapping"></a>Rozšíření výchozího mapování vlastností

Můžete použít výchozí mapování vlastností a také ho roztáhnout s vlastním mapováním.

### <a name="to-extend-a-default-property-mapping"></a>Postup při rozšiřování výchozího mapování vlastností

- Zkopírujte následující kód do definice pro třídu `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     Metoda `ExtendBackgroundMapping` přidá do existujícího mapování vlastností <xref:System.Windows.Controls.Control.Background%2A> překladatele vlastní vlastnost.

     Metoda `OnBackgroundChange` přiřadí konkrétní obrázek k vlastnosti <xref:System.Windows.Forms.Control.BackgroundImage%2A> hostovaného ovládacího prvku. Metoda `OnBackgroundChange` je volána poté, co je použito výchozí mapování vlastností.

## <a name="initializing-your-property-mappings"></a>Inicializuje se mapování vlastností.

Nastavte mapování vlastností voláním dříve popsaných metod v obslužné rutině události <xref:System.Windows.FrameworkElement.Loaded>.

### <a name="to-initialize-your-property-mappings"></a>Inicializace mapování vlastností

1. Zkopírujte následující kód do definice pro třídu `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     Metoda `WindowLoaded` zpracovává událost <xref:System.Windows.FrameworkElement.Loaded> a provádí následující inicializaci.

    - Vytvoří ovládací prvek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox>.

    - Volá metody, které jste definovali dříve v návodu, aby se nastavilo mapování vlastností.

    - Přiřadí počáteční hodnoty k mapovaným vlastnostem.

2. Stisknutím klávesy **F5** Sestavte a spusťte aplikaci. Kliknutím na zaškrtávací políčko zobrazíte efekt mapování <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Když kliknete na zaškrtávací políčko, rozložení obrátí svou orientaci zleva doprava.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Mapování vlastnosti Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
