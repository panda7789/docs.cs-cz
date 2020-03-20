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
ms.openlocfilehash: ec4e96c0883489135b77f09a3c19f144cb4d30bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187396"
---
# <a name="wpf-content-model"></a>Model obsahu WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]je prezentační platforma, která poskytuje mnoho ovládacích prvků a typů podobných ovládacím prvkům, jejichž primárním účelem je zobrazení různých typů obsahu. Chcete-li zjistit, který ovládací prvek použít nebo který ovládací prvek odvodit z, měli byste pochopit druhy objektů, které může konkrétní ovládací prvek nejlépe zobrazit.  
  
 Toto téma shrnuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] model obsahu pro typy ovládacích prvku a ovládacího prvku. Model obsahu popisuje, jaký obsah lze použít v ovládacím prvku. Toto téma také uvádí vlastnosti obsahu pro každý model obsahu. Vlastnost content je vlastnost, která se používá k ukládání obsahu objektu.  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a>Třídy, které obsahují libovolný obsah  
 Některé ovládací prvky mohou obsahovat objekt libovolného <xref:System.DateTime> typu, <xref:System.Windows.UIElement> například řetězec, objekt nebo kontejner, který je kontejnerem pro další položky. Může například <xref:System.Windows.Controls.Button> obsahovat obrázek a nějaký text; nebo <xref:System.Windows.Controls.CheckBox> může obsahovat <xref:System.DateTime.Now%2A?displayProperty=nameWithType>hodnotu .  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]má čtyři třídy, které mohou obsahovat libovolný obsah. V následující tabulce jsou uvedeny <xref:System.Windows.Controls.Control>třídy, které dědí z .  
  
|Třída, která obsahuje libovolný obsah|Obsah|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Jeden libovolný objekt.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Záhlaví a jedna položka, které jsou libovolné objekty.|  
|<xref:System.Windows.Controls.ItemsControl>|Kolekce libovolných objektů.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Záhlaví a kolekce položek, z nichž všechny jsou libovolné objekty.|  
  
 Ovládací prvky, které dědí z těchto tříd, mohou obsahovat stejný typ obsahu a zacházet s obsahem stejným způsobem. Následující obrázek znázorňuje jeden ovládací prvek z každého modelu obsahu, který obsahuje obrázek a některý text:  
  
 ![Snímek obrazovky, který zobrazuje čtyři různé ovládací prvky, jeden z každého modelu obsahu.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Ovládací prvky, které obsahují jeden libovolný objekt  
 Třída <xref:System.Windows.Controls.ContentControl> obsahuje jeden kus libovolného obsahu. Jeho vlastnost <xref:System.Windows.Controls.ContentControl.Content%2A>obsahu je . Následující ovládací prvky dědí z <xref:System.Windows.Controls.ContentControl> a používají jeho model obsahu:  
  
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
  
 Následující obrázek znázorňuje čtyři <xref:System.Windows.Controls.ContentControl.Content%2A> tlačítka, <xref:System.DateTime> jejichž je <xref:System.Windows.Shapes.Rectangle>nastavena na řetězec, objekt, a , <xref:System.Windows.Controls.Panel> a, který obsahuje <xref:System.Windows.Shapes.Ellipse> a a : <xref:System.Windows.Controls.TextBlock>  
  
 ![Snímek obrazovky, který zobrazuje čtyři tlačítka s různými typy obsahu.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 Příklad nastavení vlastnosti naleznete <xref:System.Windows.Controls.ContentControl.Content%2A> v <xref:System.Windows.Controls.ContentControl>tématu .  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Ovládací prvky, které obsahují záhlaví a jeden libovolný objekt  
 Třída <xref:System.Windows.Controls.HeaderedContentControl> dědí <xref:System.Windows.Controls.ContentControl> a zobrazuje obsah s hlavičkou. Dědí vlastnost content <xref:System.Windows.Controls.ContentControl.Content%2A>, <xref:System.Windows.Controls.ContentControl> z a <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> definuje vlastnost, <xref:System.Object>která je typu ; proto oba může být libovolný objekt.  
  
 Následující ovládací prvky dědí z <xref:System.Windows.Controls.HeaderedContentControl> a používají jeho model obsahu:  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 Následující obrázek <xref:System.Windows.Controls.TabItem> znázorňuje dva objekty. První <xref:System.Windows.Controls.TabItem> má <xref:System.Windows.UIElement> objekty <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> jako <xref:System.Windows.Controls.ContentControl.Content%2A>a . Je <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> nastavena <xref:System.Windows.Controls.StackPanel> na, <xref:System.Windows.Shapes.Ellipse> která <xref:System.Windows.Controls.TextBlock>obsahuje a . Je <xref:System.Windows.Controls.ContentControl.Content%2A> nastavena <xref:System.Windows.Controls.StackPanel> na, <xref:System.Windows.Controls.TextBlock> která <xref:System.Windows.Controls.Label>obsahuje a . Druhý <xref:System.Windows.Controls.TabItem> má řetězec v <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.TextBlock> v <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![TabControl, který používá různé typy v Header vlastnost.](./media/wpf-content-model/control-content-model-tab.png)  
  
 Příklad vytváření <xref:System.Windows.Controls.TabItem> objektů naleznete v <xref:System.Windows.Controls.HeaderedContentControl>tématu .  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Ovládací prvky, které obsahují kolekci libovolných objektů  
 Třída <xref:System.Windows.Controls.ItemsControl> dědí <xref:System.Windows.Controls.Control> z a může obsahovat více položek, jako jsou řetězce, objekty nebo jiné prvky. Jeho vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A>obsahu jsou a . <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>se obvykle používá k <xref:System.Windows.Controls.ItemsControl> naplnění shromažďování dat. Pokud nechcete použít kolekci k <xref:System.Windows.Controls.ItemsControl>naplnění , můžete přidat <xref:System.Windows.Controls.ItemsControl.Items%2A> položky pomocí vlastnosti.  
  
 Následující ovládací prvky dědí z <xref:System.Windows.Controls.ItemsControl> a používají jeho model obsahu:  
  
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
  
 Následující obrázek <xref:System.Windows.Controls.ListBox> znázorňuje, který obsahuje tyto typy položek:  
  
- Řetězec.  
  
- Objekt. <xref:System.DateTime>  
  
- Úloha <xref:System.Windows.UIElement>.  
  
- A, <xref:System.Windows.Controls.Panel> který <xref:System.Windows.Shapes.Ellipse> obsahuje <xref:System.Windows.Controls.TextBlock>a .  
  
 ![Snímek obrazovky, který zobrazuje listbox se čtyřmi typy obsahu.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Ovládací prvky, které obsahují záhlaví a kolekce libovolných objektů  
 Třída <xref:System.Windows.Controls.HeaderedItemsControl> dědí <xref:System.Windows.Controls.ItemsControl> z a může obsahovat více položek, jako jsou řetězce, objekty nebo jiné prvky a záhlaví. Zdědí <xref:System.Windows.Controls.ItemsControl> vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>obsahu <xref:System.Windows.Controls.ItemsControl.Items%2A>, a , <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> a definuje vlastnost, která může být libovolný objekt.  
  
 Následující ovládací prvky dědí z <xref:System.Windows.Controls.HeaderedItemsControl> a používají jeho model obsahu:  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Třídy, které obsahují kolekci objektů UIElement  
 Třída <xref:System.Windows.Controls.Panel> umístí a uspořádá podřízené <xref:System.Windows.UIElement> objekty. Jeho vlastnost <xref:System.Windows.Controls.Panel.Children%2A>obsahu je .  
  
 Následující třídy dědí z <xref:System.Windows.Controls.Panel> třídy a používají její model obsahu:  
  
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
  
 Další informace naleznete v [tématu Přehled panelů](panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Třídy, které ovlivňují vzhled prvku UIElement  
 Třída <xref:System.Windows.Controls.Decorator> aplikuje vizuální efekty na jedno <xref:System.Windows.UIElement>dítě nebo kolem jednoho dítěte . Jeho vlastnost <xref:System.Windows.Controls.Decorator.Child%2A>obsahu je . Následující třídy <xref:System.Windows.Controls.Decorator> dědí z a používat jeho model obsahu:  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 Následující obrázek <xref:System.Windows.Controls.TextBox> znázorňuje, který má <xref:System.Windows.Controls.Border> (je zdoben) kolem něj.  
  
 ![Textbox s černým ohraničením](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
TextBlock, který má ohraničení  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Třídy, které poskytují vizuální zpětnou vazbu o Prvku UI  
 Třída <xref:System.Windows.Documents.Adorner> poskytuje vizuální podněty pro uživatele. Například použijte <xref:System.Windows.Documents.Adorner> přidat funkční popisovače prvků nebo poskytnout informace o stavu ovládacího prvku. Třída <xref:System.Windows.Documents.Adorner> poskytuje rámec, takže můžete vytvořit vlastní adorners. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]neposkytuje žádné implementované adorners. Další informace naleznete v tématu [Adorners Overview](adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a>Třídy, které umožňují uživatelům zadávat text  
 WPF poskytuje tři primární ovládací prvky, které umožňují uživatelům zadávat text. Každý ovládací prvek zobrazí text jinak. V následující tabulce jsou uvedeny tyto tři ovládací prvky související s textem, jejich možnosti při zobrazení textu a jejich vlastnosti, které obsahují text ovládacího prvku.  
  
|Řízení|Text je zobrazen jako|Vlastnost obsahu|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Prostý text|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Formátovaný text|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Skrytý text (znaky jsou maskované)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a>Třídy, které zobrazují váš text  
 K zobrazení prostého nebo formátovaného textu lze použít několik tříd. Můžete použít <xref:System.Windows.Controls.TextBlock> k zobrazení malého množství textu. Chcete-li zobrazit velké množství textu, <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer>použijte <xref:System.Windows.Controls.FlowDocumentScrollViewer> ovládací prvky , nebo .  
  
 Má <xref:System.Windows.Controls.TextBlock> dvě vlastnosti <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock.Inlines%2A>obsahu: a . Pokud chcete zobrazit text, který používá konzistentní <xref:System.Windows.Controls.TextBlock.Text%2A> formátování, vlastnost je často nejlepší volbou. Pokud plánujete v celém textu používat jiné <xref:System.Windows.Controls.TextBlock.Inlines%2A> formátování, použijte vlastnost. Vlastnost <xref:System.Windows.Controls.TextBlock.Inlines%2A> je kolekce <xref:System.Windows.Documents.Inline> objektů, které určují, jak formátovat text.  
  
 V následující tabulce je <xref:System.Windows.Controls.FlowDocumentReader>uvedena <xref:System.Windows.Controls.FlowDocumentPageViewer>vlastnost <xref:System.Windows.Controls.FlowDocumentScrollViewer> obsahu pro , a třídy.  
  
|Řízení|Vlastnost obsahu|Typ vlastnosti obsahu|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Dokument|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Dokument|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Dokument|<xref:System.Windows.Documents.FlowDocument>|  
  
 Implementuje <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Documents.IDocumentPaginatorSource> rozhraní; proto všechny tři třídy <xref:System.Windows.Documents.FlowDocument> může trvat jako obsah.  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a>Třídy, které formátují text  
 <xref:System.Windows.Documents.TextElement>a jeho související třídy umožňují formátovat text. <xref:System.Windows.Documents.TextElement>objekty obsahují a <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Documents.FlowDocument> formátují text a objekty. Dva primární typy <xref:System.Windows.Documents.TextElement> objektů <xref:System.Windows.Documents.Block> jsou <xref:System.Windows.Documents.Inline> prvky a prvky. Prvek <xref:System.Windows.Documents.Block> představuje blok textu, například odstavec nebo seznam. Prvek <xref:System.Windows.Documents.Inline> představuje část textu v bloku. Mnoho <xref:System.Windows.Documents.Inline> tříd určuje formátování textu, na který jsou použity. Každý <xref:System.Windows.Documents.TextElement> z nich má svůj vlastní model obsahu. Další informace naleznete v tématu [Přehled modelu obsahu TextElement](../advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Viz také

- [Pokročilé](../advanced/index.md)
