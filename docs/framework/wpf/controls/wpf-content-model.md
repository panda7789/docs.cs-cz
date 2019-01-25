---
title: Model obsahu WPF
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
ms.openlocfilehash: 751cbcc3a3b70f0937a8fe84c0fad5d8771a32ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718153"
---
# <a name="wpf-content-model"></a>Model obsahu WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je prezentační platforma, která nabízí mnoho ovládacích prvků a typů ovládacího prvku, jejichž primárním účelem je zobrazit různé typy obsahu. Pokud chcete zjistit, který ovládací prvek použít nebo který ovládací prvek k odvození z, měli byste porozumět typy objektů, které nejlépe můžete zobrazit konkrétní ovládací prvek.  
  
 Toto téma obsahuje souhrn obsahu modelu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku a typů ovládacího prvku. Model obsahu popisuje, jaký obsah je možné v ovládacím prvku. Toto téma obsahuje také seznam obsahu vlastnosti pro každý model obsahu. Vlastnost obsahu má vlastnost, která se používá k ukládání obsahu objektu.  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>Třídy, které obsahují libovolný obsah  
 Některé ovládací prvky mohou obsahovat objekt typu, jako je řetězec, <xref:System.DateTime> objektu, nebo <xref:System.Windows.UIElement> , který je kontejnerem pro další položky. Například <xref:System.Windows.Controls.Button> může obsahovat obrázek a text; nebo <xref:System.Windows.Controls.CheckBox> může obsahovat hodnotu <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má čtyři třídy, které mohou obsahovat libovolný obsah. V následující tabulce jsou uvedeny třídy, které dědí nastavení z <xref:System.Windows.Controls.Control>.  
  
|Třída, která obsahuje libovolný obsah|Obsah|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Jeden libovolný objekt.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Záhlaví a jednu položku, které jsou libovolné objekty.|  
|<xref:System.Windows.Controls.ItemsControl>|Kolekci libovolného objektů.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Záhlaví a kolekci položek, z nichž všechny jsou libovolné objekty.|  
  
 Ovládací prvky, které dědí z těchto tříd může obsahovat stejné typu obsahu a zpracovávat obsah stejným způsobem. Následující obrázek znázorňuje jeden ovládací prvek z každé obsahu modelu, který obsahuje bitovou kopii a nějakým textem.  
  
 ![Button, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Ovládací prvky, které obsahují jednoho libovolného objektu  
 <xref:System.Windows.Controls.ContentControl> Třída obsahuje jediný libovolný obsah. Jeho vlastnost obsahu má <xref:System.Windows.Controls.ContentControl.Content%2A>. Následující ovládací prvky automaticky dědí z <xref:System.Windows.Controls.ContentControl> a použijte svůj model obsahu:  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 Následující obrázek znázorňuje čtyři tlačítka, jehož <xref:System.Windows.Controls.ContentControl.Content%2A> nastavený na řetězec, <xref:System.DateTime> objektu, <xref:System.Windows.Shapes.Rectangle>a <xref:System.Windows.Controls.Panel> , který obsahuje <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>.  
  
 ![Čtyři tlačítka](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")  
Čtyři tlačítka, které mají různé typy obsahu  
  
 Příklad toho, jak nastavit <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost, naleznete v tématu <xref:System.Windows.Controls.ContentControl>.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Ovládací prvky, které obsahují záhlaví a jednoho libovolného objektu  
 <xref:System.Windows.Controls.HeaderedContentControl> Třída dědí z <xref:System.Windows.Controls.ContentControl> a zobrazí obsah s hlavičkou. Dědí vlastnost obsahu <xref:System.Windows.Controls.ContentControl.Content%2A>, z <xref:System.Windows.Controls.ContentControl> a definuje <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> vlastnost, která je typu <xref:System.Object>, proto může být libovolný objekt.  
  
 Následující ovládací prvky automaticky dědí z <xref:System.Windows.Controls.HeaderedContentControl> a použijte svůj model obsahu:  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 Následující obrázek ukazuje dva <xref:System.Windows.Controls.TabItem> objekty. První <xref:System.Windows.Controls.TabItem> má <xref:System.Windows.UIElement> objektů, jako <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.ContentControl.Content%2A>. <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> Je nastavena na <xref:System.Windows.Controls.StackPanel> , který obsahuje <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Controls.ContentControl.Content%2A> Je nastavena na <xref:System.Windows.Controls.StackPanel> , která obsahuje <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.Label>. Druhá <xref:System.Windows.Controls.TabItem> má řetězec <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.TextBlock> v <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")  
TabControl –, který používá různé typy ve vlastnosti hlavička  
  
 Příklad toho, jak vytvořit <xref:System.Windows.Controls.TabItem> objekty, najdete <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Ovládací prvky, které obsahují kolekci libovolného objektů  
 <xref:System.Windows.Controls.ItemsControl> Třída dědí z <xref:System.Windows.Controls.Control> a může obsahovat několik položek, jako je například řetězce, objekty nebo další prvky. Jsou jeho vlastnosti obsahu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> a <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Obvykle se používá k naplnění <xref:System.Windows.Controls.ItemsControl> se shromažďováním dat. Pokud nechcete používat kolekce k naplnění <xref:System.Windows.Controls.ItemsControl>, můžete přidat položky pomocí <xref:System.Windows.Controls.ItemsControl.Items%2A> vlastnost.  
  
 Následující ovládací prvky automaticky dědí z <xref:System.Windows.Controls.ItemsControl> a použijte svůj model obsahu:  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 Následující ilustrace ukazuje <xref:System.Windows.Controls.ListBox> , která obsahuje tyto typy položek:  
  
-   Řetězec.  
  
-   A <xref:System.DateTime> objektu.  
  
-   A <xref:System.Windows.UIElement>.  
  
-   A <xref:System.Windows.Controls.Panel> , který obsahuje <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>.  
  
 ![ListBox – čtyři typy obsahu](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")  
ListBox –, který obsahuje více typů objektů  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Ovládací prvky, které obsahují záhlaví a kolekce objektů libovolného  
 <xref:System.Windows.Controls.HeaderedItemsControl> Třída dědí z <xref:System.Windows.Controls.ItemsControl> a může obsahovat několik položek, jako jsou řetězce, objekty, nebo další prvky a záhlaví. Dědí <xref:System.Windows.Controls.ItemsControl> obsah vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, a <xref:System.Windows.Controls.ItemsControl.Items%2A>, a definuje <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> vlastnost, která může být libovolný objekt.  
  
 Následující ovládací prvky automaticky dědí z <xref:System.Windows.Controls.HeaderedItemsControl> a použijte svůj model obsahu:  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Třídy, které obsahují kolekci objektů UIElement  
 <xref:System.Windows.Controls.Panel> Třídy umístění a uspořádá podřízené <xref:System.Windows.UIElement> objekty. Jeho vlastnost obsahu má <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 Následující třídy dědí <xref:System.Windows.Controls.Panel> třídy a použijte svůj model obsahu:  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 Další informace najdete v tématu [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Třídy, které mají vliv na vzhled elementu UIElement  
 <xref:System.Windows.Controls.Decorator> Použije vizuální efekty na nebo okolo jednu podřízenou třídu <xref:System.Windows.UIElement>. Jeho vlastnost obsahu má <xref:System.Windows.Controls.Decorator.Child%2A>. Následující třídy dědí <xref:System.Windows.Controls.Decorator> a použijte svůj model obsahu:  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 Následující ilustrace ukazuje <xref:System.Windows.Controls.TextBox> , který má (je doplněn) <xref:System.Windows.Controls.Border> kolem něj.  
  
 ![Textové pole s černým ohraničením](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
TextBlock –, který má ohraničení  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Třídy, které poskytují vizuální zpětnou vazbu o prvku UIElement  
 <xref:System.Windows.Documents.Adorner> Třída poskytuje vizuální upozornění na uživatele. Například použít <xref:System.Windows.Documents.Adorner> přidat funkční zpracovává na prvky nebo poskytují informace o ovládací prvek stavu. <xref:System.Windows.Documents.Adorner> Třída poskytuje rozhraní, takže můžete vytvářet vlastní doplňky pro úpravy. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] neposkytuje žádné implementované doplňků pro úpravy. Další informace najdete v tématu [přehled doplňků pro úpravy](../../../../docs/framework/wpf/controls/adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>Třídy, které umožňují uživatelům zadávat Text  
 WPF poskytuje tři primární ovládací prvky, které umožňují uživatelům zadávat text. Každý ovládací prvek zobrazí text jiným způsobem. V následující tabulce jsou uvedeny tyto tři text související ovládací prvky, jejich možnosti při jejich zobrazení textu a jejich vlastností, které obsahují text ovládacího prvku.  
  
|Ovládací prvek|Text se zobrazí jako|Vlastnost obsahu|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Prostý text|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Formátovaný text|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Skrytý text (znaky jsou maskována)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>Třídy, které se zobrazí váš Text  
 Několik tříd lze použít k zobrazení prostý nebo formátovaný text. Můžete použít <xref:System.Windows.Controls.TextBlock> zobrazíte malé množství textu. Pokud chcete pro zobrazení velkého množství textu, použijte <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, nebo <xref:System.Windows.Controls.FlowDocumentScrollViewer> ovládacích prvků.  
  
 <xref:System.Windows.Controls.TextBlock> Má dvě vlastnosti obsahu: <xref:System.Windows.Controls.TextBlock.Text%2A> a <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Pokud chcete zobrazit text, který používá formátování konzistentní vzhledem k aplikacím <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost je často nejlepší volbou. Pokud budete chtít použít odlišné formátování všude v textu, použijte <xref:System.Windows.Controls.TextBlock.Inlines%2A> vlastnost. <xref:System.Windows.Controls.TextBlock.Inlines%2A> Vlastnost je kolekce <xref:System.Windows.Documents.Inline> objekty, které určují způsob formátování textu.  
  
 V následující tabulce jsou uvedeny vlastnost obsahu pro <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, a <xref:System.Windows.Controls.FlowDocumentScrollViewer> třídy.  
  
|Ovládací prvek|Vlastnost obsahu|Typ obsahu vlastnosti|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Dokument|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Dokument|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Dokument|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.FlowDocument> Implementuje <xref:System.Windows.Documents.IDocumentPaginatorSource> rozhraní; proto můžete provést všechny třídy <xref:System.Windows.Documents.FlowDocument> jako obsah.  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>Třídy, které formátování textu  
 <xref:System.Windows.Documents.TextElement> a její související třídy umožňují formátování textu. <xref:System.Windows.Documents.TextElement> objekty obsahují a formátování textu v <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument> objekty. Dva hlavní typy <xref:System.Windows.Documents.TextElement> objekty jsou <xref:System.Windows.Documents.Block> elementy a <xref:System.Windows.Documents.Inline> elementy. A <xref:System.Windows.Documents.Block> element reprezentuje blok textu, jako jsou odstavce nebo seznamu. <xref:System.Windows.Documents.Inline> Element reprezentuje část textu v bloku. Mnoho <xref:System.Windows.Documents.Inline> třídy určit formátování textu, do které se použijí. Každý <xref:System.Windows.Documents.TextElement> má svůj vlastní model obsahu. Další informace najdete v tématu [přehled modelu obsahu TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Viz také:
- [Pokročilé](../../../../docs/framework/wpf/advanced/index.md)
