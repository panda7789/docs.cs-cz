---
title: 'Průvodce: Mapování vlastností použitím ovládacího prvku ElementHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: bb418b725afd0c38a39e42e50511147d0f616059
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623214"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>Průvodce: Mapování vlastností použitím ovládacího prvku ElementHost

Tento návod ukazuje, jak používat <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> vlastnost mapovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti odpovídající vlastnosti na hostovaný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu.

Úlohy v tomto návodu zahrnují:

-   Vytvoření projektu.

-   Definování nového mapování vlastností.

-   Odebrání výchozí mapování vlastností.

-   Rozšíření výchozí mapování vlastností.

Kompletní výpis kódu úloh v tomto návodu, naleznete v tématu [mapování vlastností použitím Ukázka ovládacího prvku ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).

Až budete hotovi, budete moci mapovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti k odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností hostované elementu.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

-   Visual Studio 2017

## <a name="creating-the-project"></a>Vytvoření projektu

### <a name="to-create-the-project"></a>Vytvoření projektu

1.  Vytvoření **aplikace Windows Forms** projekt s názvem `PropertyMappingWithElementHost`.

2.  V **Průzkumníka řešení**, přidejte odkazy na následující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení.

    -   PresentationCore

    -   PresentationFramework

    -   WindowsBase

    -   WindowsFormsIntegration

3.  Zkopírujte následující kód do horní části `Form1` soubor kódu.

     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4.  Otevřít `Form1` v Návrháři formulářů Windows. Klikněte dvakrát na formuláři pro přidání obslužné rutiny události <xref:System.Windows.Forms.Form.Load> událostí.

5.  Vraťte se do Návrháře formulářů Windows a přidejte obslužnou rutinu události pro daný formulář <xref:System.Windows.Forms.Control.Resize> událostí. Další informace najdete v tématu [jak: Vytváření obslužných rutin událostí pomocí návrháře](https://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).

6.  Deklarovat <xref:System.Windows.Forms.Integration.ElementHost> pole `Form1` třídy.

     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a>Definování nového mapování vlastností

<xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek obsahuje několik výchozích mapování vlastností. Přidat nové mapování vlastností pomocí volání <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodu <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.

### <a name="to-define-new-property-mappings"></a>Chcete-li definovat nové mapování vlastností

1.  Zkopírujte následující kód do definice pro `Form1` třídy.

     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     `AddMarginMapping` Metoda přidá nové mapování <xref:System.Windows.Forms.Control.Margin%2A> vlastnost.

     `OnMarginChange` Metoda překládá <xref:System.Windows.Forms.Control.Margin%2A> vlastnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost.

2.  Zkopírujte následující kód do definice pro `Form1` třídy.

     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     `AddRegionMapping` Metoda přidá nové mapování <xref:System.Windows.Forms.Control.Region%2A> vlastnost.

     `OnRegionChange` Metoda překládá <xref:System.Windows.Forms.Control.Region%2A> vlastnost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> vlastnost.

     `Form1_Resize` Obsluhovala formuláře <xref:System.Windows.Forms.Control.Resize> události a velikosti oblast ořezu podle hostovaný prvek.

## <a name="removing-a-default-property-mapping"></a>Odebrání výchozí mapování vlastností

Odeberte výchozí mapování vlastností pomocí volání <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metodu <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.

### <a name="to-remove-a-default-property-mapping"></a>Chcete-li odebrat výchozí mapování vlastností

-   Zkopírujte následující kód do definice pro `Form1` třídy.

     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     `RemoveCursorMapping` Metoda odstraní výchozí mapování <xref:System.Windows.Forms.Control.Cursor%2A> vlastnost.

## <a name="extending-a-default-property-mapping"></a>Rozšíření výchozí mapování vlastností

Můžete použít výchozí mapování vlastností a také rozšířit o vlastní mapování.

### <a name="to-extend-a-default-property-mapping"></a>Chcete-li rozšířit výchozí mapování vlastností

-   Zkopírujte následující kód do definice pro `Form1` třídy.

     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     `ExtendBackColorMapping` Metoda přidá převaděče vlastní vlastnost do existující <xref:System.Windows.Forms.Control.BackColor%2A> mapování vlastností.

     `OnBackColorChange` Metoda přiřadí hostovaného ovládacího prvku konkrétní image <xref:System.Windows.Controls.Control.Background%2A> vlastnost. `OnBackColorChange` Metoda se volá, když se použije výchozí mapování vlastností.

## <a name="initialize-your-property-mappings"></a>Inicializovat mapování vlastností

1.  Zkopírujte následující kód do definice pro `Form1` třídy.

     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     `Form1_Load` Metoda obslužné rutiny <xref:System.Windows.Forms.Form.Load> událostí a provádí následující inicializace.

    -   Vytvoří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> elementu.

    -   Volá metody, které jste definovali dříve v návodu k nastavení mapování vlastností.

    -   Přiřadí počáteční hodnoty pro mapovanou vlastnosti.

2.  Stisknutím klávesy F5 sestavte a spusťte aplikaci.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Mapování vlastnosti Windows Forms a WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
- [Návrh kódu XAML v sadě Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)