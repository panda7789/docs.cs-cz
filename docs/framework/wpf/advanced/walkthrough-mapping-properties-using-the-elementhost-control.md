---
title: 'Návod: Mapování vlastností použitím ovládacího prvku ElementHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 7d1cf353f7e6c4b87c13598e7e6029960cd0f715
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197812"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>Návod: Mapování vlastností použitím ovládacího prvku ElementHost

V tomto návodu se dozvíte, jak použít vlastnost <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> k mapování [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastností na odpovídající vlastnosti u hostovaného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu.

Úlohy, které jsou znázorněné v tomto návodu, zahrnují:

- Vytváří se projekt.

- Definování nového mapování vlastností.

- Odebírá se výchozí mapování vlastností.

- Rozšíření výchozího mapování vlastností.

Úplný výpis kódu úloh, které jsou znázorněny v tomto návodu, najdete v tématu [mapování vlastností pomocí ukázky ovládacího prvku ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).

Až budete hotovi, budete moci mapovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti na odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti v hostovaném elementu.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio 2017

## <a name="creating-the-project"></a>Vytvoření projektu

### <a name="to-create-the-project"></a>Vytvoření projektu

1. Vytvořte projekt **aplikace model Windows Forms** s názvem `PropertyMappingWithElementHost`.

2. V **Průzkumník řešení**přidejte odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení.

    - PresentationCore

    - PresentationFramework

    - WindowsBase

    - WindowsFormsIntegration

3. Zkopírujte následující kód do horní části souboru kódu `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. Otevřete `Form1` v Návrhář formulářů. Dvakrát klikněte na formulář a přidejte obslužnou rutinu události pro událost <xref:System.Windows.Forms.Form.Load>.

5. Vraťte se do Návrhář formulářů a přidejte obslužnou rutinu události pro událost <xref:System.Windows.Forms.Control.Resize> formuláře. Další informace naleznete v tématu [Postupy: vytváření obslužných rutin událostí pomocí návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).

6. Deklaruje pole <xref:System.Windows.Forms.Integration.ElementHost> ve třídě `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a>Definování nových mapování vlastností

Ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> poskytuje několik výchozích mapování vlastností. Přidáte nové mapování vlastností voláním metody <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> na <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost>.

### <a name="to-define-new-property-mappings"></a>Definování nových mapování vlastností

1. Zkopírujte následující kód do definice pro třídu `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     Metoda `AddMarginMapping` přidá nové mapování pro vlastnost <xref:System.Windows.Forms.Control.Margin%2A>.

     Metoda `OnMarginChange` překládá vlastnost <xref:System.Windows.Forms.Control.Margin%2A> na vlastnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A>.

2. Zkopírujte následující kód do definice pro třídu `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     Metoda `AddRegionMapping` přidá nové mapování pro vlastnost <xref:System.Windows.Forms.Control.Region%2A>.

     Metoda `OnRegionChange` překládá vlastnost <xref:System.Windows.Forms.Control.Region%2A> na vlastnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A>.

     Metoda `Form1_Resize` zpracovává událost <xref:System.Windows.Forms.Control.Resize> formuláře a velikost oblasti oříznutí tak, aby odpovídala hostovanému elementu.

## <a name="removing-a-default-property-mapping"></a>Odebírá se výchozí mapování vlastností.

Odeberte výchozí mapování vlastností voláním metody <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> na <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost>.

### <a name="to-remove-a-default-property-mapping"></a>Odebrání výchozího mapování vlastností

- Zkopírujte následující kód do definice pro třídu `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     Metoda `RemoveCursorMapping` odstraní výchozí mapování pro vlastnost <xref:System.Windows.Forms.Control.Cursor%2A>.

## <a name="extending-a-default-property-mapping"></a>Rozšíření výchozího mapování vlastností

Můžete použít výchozí mapování vlastností a také ho roztáhnout s vlastním mapováním.

### <a name="to-extend-a-default-property-mapping"></a>Postup při rozšiřování výchozího mapování vlastností

- Zkopírujte následující kód do definice pro třídu `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     Metoda `ExtendBackColorMapping` přidá do existujícího mapování vlastností <xref:System.Windows.Forms.Control.BackColor%2A> překladatele vlastní vlastnost.

     Metoda `OnBackColorChange` přiřadí konkrétní obrázek k vlastnosti <xref:System.Windows.Controls.Control.Background%2A> hostovaného ovládacího prvku. Metoda `OnBackColorChange` je volána poté, co je použito výchozí mapování vlastností.

## <a name="initialize-your-property-mappings"></a>Inicializace mapování vlastností

1. Zkopírujte následující kód do definice pro třídu `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     Metoda `Form1_Load` zpracovává událost <xref:System.Windows.Forms.Form.Load> a provádí následující inicializaci.

    - Vytvoří prvek <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

    - Volá metody, které jste definovali dříve v návodu, aby se nastavilo mapování vlastností.

    - Přiřadí počáteční hodnoty k mapovaným vlastnostem.

2. Stisknutím klávesy F5 Sestavte a spusťte aplikaci.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Mapování vlastnosti Windows Forms a WPF](windows-forms-and-wpf-property-mapping.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
