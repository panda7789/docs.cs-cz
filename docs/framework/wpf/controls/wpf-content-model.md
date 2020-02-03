---
title: Model obsahu
ms.date: 03/30/2017
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
ms.openlocfilehash: a84ab2e66b4e373591fc9365b1c17d0bb0c66713
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738279"
---
# <a name="wpf-content-model"></a>Model obsahu WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je prezentační platforma, která poskytuje mnoho ovládacích prvků a typů podobných ovládacím prvkům, jejichž hlavním účelem je zobrazení různých typů obsahu. Chcete-li určit, který ovládací prvek použít nebo který ovládací prvek odvodit z, je vhodné pochopit druhy objektů, které může konkrétní ovládací prvek nejlépe zobrazit.  
  
 Toto téma shrnuje model obsahu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy ovládacích prvků a ovládacích prvků. Model obsahu popisuje, který obsah lze použít v ovládacím prvku. Toto téma obsahuje také seznam vlastností obsahu pro každý model obsahu. Vlastnost obsahu je vlastnost, která se používá k uložení obsahu objektu.  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>Třídy, které obsahují libovolný obsah  
 Některé ovládací prvky mohou obsahovat objekt libovolného typu, jako je například řetězec, objekt <xref:System.DateTime> nebo <xref:System.Windows.UIElement>, který je kontejnerem pro další položky. <xref:System.Windows.Controls.Button> například může obsahovat obrázek a nějaký text; nebo <xref:System.Windows.Controls.CheckBox> může obsahovat hodnotu <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má čtyři třídy, které mohou obsahovat libovolný obsah. V následující tabulce jsou uvedeny třídy, které dědí z <xref:System.Windows.Controls.Control>.  
  
|Třída, která obsahuje libovolný obsah|Obsah|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Jeden libovolný objekt.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Záhlaví a jedna položka, z nichž obě jsou libovolné objekty.|  
|<xref:System.Windows.Controls.ItemsControl>|Kolekce libovolných objektů.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Záhlaví a kolekce položek, všechny, které jsou libovolnými objekty.|  
  
 Ovládací prvky, které dědí z těchto tříd, mohou obsahovat stejný typ obsahu a zpracovávat obsah stejným způsobem. Následující ilustrace znázorňuje jeden ovládací prvek z každého modelu obsahu, který obsahuje obrázek a nějaký text:  
  
 ![Snímek obrazovky zobrazující čtyři různé ovládací prvky, jeden z každého modelu obsahu.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Ovládací prvky, které obsahují jediný libovolný objekt  
 Třída <xref:System.Windows.Controls.ContentControl> obsahuje jednu část libovolného obsahu. Vlastnost obsahu je <xref:System.Windows.Controls.ContentControl.Content%2A>. Následující ovládací prvky dědí z <xref:System.Windows.Controls.ContentControl> a používají svůj model obsahu:  
  
- <xref:System.Windows.Controls.Button>  
  
- <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
- <xref:System.Windows.Controls.CheckBox>  
  
- <xref:System.Windows.Controls.ComboBoxItem>  
  
- <xref:System.Windows.Controls.ContentControl>  
  
- <xref:System.Windows.Controls.Frame>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GroupItem>  
  
- <xref:System.Windows.Controls.Label>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Navigation.NavigationWindow>  
  
- <xref:System.Windows.Controls.RadioButton>  
  
- <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
- <xref:System.Windows.Controls.ScrollViewer>  
  
- <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
- <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
- <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.UserControl>  
  
- <xref:System.Windows.Window>  
  
 Následující ilustrace znázorňuje čtyři tlačítka, jejichž <xref:System.Windows.Controls.ContentControl.Content%2A> je nastavené na řetězec, <xref:System.DateTime> objekt, <xref:System.Windows.Shapes.Rectangle>a <xref:System.Windows.Controls.Panel> obsahující <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>:  
  
 ![Snímek obrazovky, který zobrazuje čtyři tlačítka s různými typy obsahu.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 Příklad nastavení vlastnosti <xref:System.Windows.Controls.ContentControl.Content%2A> naleznete v tématu <xref:System.Windows.Controls.ContentControl>.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Ovládací prvky, které obsahují záhlaví a jeden libovolný objekt  
 Třída <xref:System.Windows.Controls.HeaderedContentControl> dědí z <xref:System.Windows.Controls.ContentControl> a zobrazí obsah s hlavičkou. Dědí vlastnost obsahu, <xref:System.Windows.Controls.ContentControl.Content%2A>, z <xref:System.Windows.Controls.ContentControl> a definuje vlastnost <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>, která je typu <xref:System.Object>; Proto obojí může být libovolný objekt.  
  
 Následující ovládací prvky dědí z <xref:System.Windows.Controls.HeaderedContentControl> a používají svůj model obsahu:  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 Následující ilustrace znázorňuje dva objekty <xref:System.Windows.Controls.TabItem>. První <xref:System.Windows.Controls.TabItem> má <xref:System.Windows.UIElement> objekty jako <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.ContentControl.Content%2A>. <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> je nastaveno na <xref:System.Windows.Controls.StackPanel> obsahující <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Controls.ContentControl.Content%2A> je nastaveno na <xref:System.Windows.Controls.StackPanel> obsahující <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.Label>. Druhý <xref:System.Windows.Controls.TabItem> obsahuje řetězec v <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.TextBlock> v <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![TabControl, který ve vlastnosti Header používá jiné typy.](./media/wpf-content-model/control-content-model-tab.png)  
  
 Příklad vytváření <xref:System.Windows.Controls.TabItem> objektů naleznete v tématu <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Ovládací prvky, které obsahují kolekci libovolných objektů  
 Třída <xref:System.Windows.Controls.ItemsControl> dědí z <xref:System.Windows.Controls.Control> a může obsahovat více položek, jako jsou například řetězce, objekty nebo jiné prvky. Vlastnosti obsahu jsou <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> a <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> se obvykle používá k naplnění <xref:System.Windows.Controls.ItemsControl> kolekcí dat. Pokud nechcete použít kolekci k naplnění <xref:System.Windows.Controls.ItemsControl>, můžete přidat položky pomocí vlastnosti <xref:System.Windows.Controls.ItemsControl.Items%2A>.  
  
 Následující ovládací prvky dědí z <xref:System.Windows.Controls.ItemsControl> a používají svůj model obsahu:  
  
- <xref:System.Windows.Controls.Menu>  
  
- <xref:System.Windows.Controls.Primitives.MenuBase>  
  
- <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Controls.ComboBox>  
  
- <xref:System.Windows.Controls.ItemsControl>  
  
- <xref:System.Windows.Controls.ListBox>  
  
- <xref:System.Windows.Controls.ListView>  
  
- <xref:System.Windows.Controls.TabControl>  
  
- <xref:System.Windows.Controls.TreeView>  
  
- <xref:System.Windows.Controls.Primitives.Selector>  
  
- <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 Následující obrázek ukazuje <xref:System.Windows.Controls.ListBox>, který obsahuje tyto typy položek:  
  
- Řetězec.  
  
- Objekt <xref:System.DateTime>.  
  
- Úloha <xref:System.Windows.UIElement>.  
  
- <xref:System.Windows.Controls.Panel> obsahující <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>.  
  
 ![Snímek obrazovky, který zobrazuje seznam se čtyřmi typy obsahu.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Ovládací prvky, které obsahují záhlaví a kolekci libovolných objektů  
 Třída <xref:System.Windows.Controls.HeaderedItemsControl> dědí z <xref:System.Windows.Controls.ItemsControl> a může obsahovat více položek, jako jsou například řetězce, objekty nebo jiné prvky a záhlaví. Zdědí <xref:System.Windows.Controls.ItemsControl> vlastnosti obsahu, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>a <xref:System.Windows.Controls.ItemsControl.Items%2A>a definuje vlastnost <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>, která může být libovolný objekt.  
  
 Následující ovládací prvky dědí z <xref:System.Windows.Controls.HeaderedItemsControl> a používají svůj model obsahu:  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Třídy, které obsahují kolekci objektů UIElement  
 Třída <xref:System.Windows.Controls.Panel> umisťuje a uspořádá podřízené objekty <xref:System.Windows.UIElement>. Vlastnost obsahu je <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 Následující třídy dědí z třídy <xref:System.Windows.Controls.Panel> a používají svůj obsahový model:  
  
- <xref:System.Windows.Controls.Canvas>  
  
- <xref:System.Windows.Controls.DockPanel>  
  
- <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.Primitives.TabPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
- <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
- <xref:System.Windows.Controls.StackPanel>  
  
- <xref:System.Windows.Controls.VirtualizingPanel>  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
- <xref:System.Windows.Controls.WrapPanel>  
  
 Další informace najdete v tématu [Přehled panelů](panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Třídy, které mají vliv na vzhled prvku UIElement  
 Třída <xref:System.Windows.Controls.Decorator> aplikuje vizuální efekty na nebo kolem jedné podřízené <xref:System.Windows.UIElement>. Vlastnost obsahu je <xref:System.Windows.Controls.Decorator.Child%2A>. Následující třídy dědí z <xref:System.Windows.Controls.Decorator> a používají svůj obsahový model:  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 Následující obrázek ukazuje <xref:System.Windows.Controls.TextBox>, který má (je upravený s) <xref:System.Windows.Controls.Border> kolem něj.  
  
 ![Textové pole s černým ohraničením](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
TextBlock s ohraničením  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Třídy, které poskytují vizuální zpětnou vazbu k prvku UIElement  
 Třída <xref:System.Windows.Documents.Adorner> poskytuje uživatelům vizuální pomůcky. Například použijte <xref:System.Windows.Documents.Adorner> k přidání funkčních obslužných rutin do prvků nebo poskytnutí informací o stavu ovládacího prvku. Třída <xref:System.Windows.Documents.Adorner> poskytuje rozhraní, abyste mohli vytvářet vlastní doplňky. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] neposkytuje žádné implementované doplňky. Další informace najdete v tématu [Přehled doplňků](adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>Třídy, které umožňují uživatelům zadat text  
 WPF poskytuje tři primární ovládací prvky, které umožňují uživatelům zadat text. Každý ovládací prvek zobrazuje text odlišně. Následující tabulka uvádí tyto tři ovládací prvky související s textem, jejich možnosti, když zobrazují text a jejich vlastnosti, které obsahují text ovládacího prvku.  
  
|Řízení|Text se zobrazí jako|Vlastnost obsahu|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Prostý text|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Formátovaný text|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Skrytý text (znaky jsou maskovány)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>Třídy, které zobrazují váš text  
 K zobrazení prostého nebo formátovaného textu lze použít několik tříd. K zobrazení malých objemů textu můžete použít <xref:System.Windows.Controls.TextBlock>. Chcete-li zobrazit velké množství textu, použijte ovládací prvky <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>nebo <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 <xref:System.Windows.Controls.TextBlock> má dvě vlastnosti obsahu: <xref:System.Windows.Controls.TextBlock.Text%2A> a <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Pokud chcete zobrazit text, který používá konzistentní formátování, je často nejlepší volbou vlastnost <xref:System.Windows.Controls.TextBlock.Text%2A>. Pokud plánujete použít jiné formátování v celém textu, použijte vlastnost <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Vlastnost <xref:System.Windows.Controls.TextBlock.Inlines%2A> je kolekcí objektů <xref:System.Windows.Documents.Inline>, které určují způsob formátování textu.  
  
 V následující tabulce je uveden seznam vlastností obsahu pro třídy <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>a <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
|Řízení|Vlastnost obsahu|Typ vlastnosti obsahu|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Dokument|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Dokument|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Dokument|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.FlowDocument> implementuje rozhraní <xref:System.Windows.Documents.IDocumentPaginatorSource>; Proto všechny tři třídy mohou přijmout <xref:System.Windows.Documents.FlowDocument> jako obsah.  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>Třídy, které naformátují text  
 <xref:System.Windows.Documents.TextElement> a související třídy umožňují formátovat text. <xref:System.Windows.Documents.TextElement> objekty obsahují a naformátují text v objektech <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument>. Dva primární typy objektů <xref:System.Windows.Documents.TextElement> jsou <xref:System.Windows.Documents.Block> elementy a prvky <xref:System.Windows.Documents.Inline>. Element <xref:System.Windows.Documents.Block> představuje blok textu, jako je například odstavec nebo seznam. Element <xref:System.Windows.Documents.Inline> představuje část textu v bloku. Mnoho tříd <xref:System.Windows.Documents.Inline> určuje formátování textu, na který jsou aplikovány. Každý <xref:System.Windows.Documents.TextElement> má svůj vlastní model obsahu. Další informace najdete v tématu [Přehled modelu obsahu TextElement](../advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Viz také

- [Pokročilé](../advanced/index.md)
