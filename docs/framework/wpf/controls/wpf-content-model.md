---
title: Model obsahu WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52cb3a5391d6e24643b03a880d3695a11baceca3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="wpf-content-model"></a>Model obsahu WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]je prezentace platforma, která poskytuje mnoho ovládací prvky a typy jako ovládací prvek, jehož primárním účelem je zobrazit různé typy obsahu. Pokud chcete zjistit, který ovládací prvek použít nebo který ovládací prvek odvození od, byste měli porozumět typy objektů, které nejlépe můžete zobrazit konkrétní ovládacího prvku.  
  
 Toto téma shrnuje modelu obsahu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řízení a řízení typů. Model obsahu popisuje, jaké obsahu lze v ovládacím prvku. Toto téma obsahuje také obsahu vlastnosti pro každý model obsahu. Vlastnost obsahu je vlastnost, která se používá k uložení obsahu objektu.  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>Třídy, které obsahují libovolný obsah  
 Některé ovládací prvky může obsahovat objekt jakéhokoli typu, například řetězec, <xref:System.DateTime> objekt, nebo <xref:System.Windows.UIElement> který je kontejner pro další položky. Například <xref:System.Windows.Controls.Button> může obsahovat bitovou kopii a text; nebo <xref:System.Windows.Controls.CheckBox> může obsahovat hodnotu <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]má čtyři tříd, které může obsahovat libovolný obsah. Následující tabulka uvádí třídy, které dědí <xref:System.Windows.Controls.Control>.  
  
|Třída, která obsahuje libovolné obsahu|Obsah|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Jeden libovolný objekt.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|Záhlaví a jednu položku, obě tyto položky jsou libovolné objekty.|  
|<xref:System.Windows.Controls.ItemsControl>|Kolekce libovolné objekty.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|Záhlaví a kolekce položek, které jsou libovolné objekty.|  
  
 Ovládací prvky, které dědí od tyto třídy může obsahovat stejného typu obsahu a považovat obsah stejným způsobem. Následující obrázek znázorňuje jeden ovládací prvek z každé obsahu model, který obsahuje bitovou kopii a text.  
  
 ![Tlačítko, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Ovládací prvky, které obsahují jeden libovolný objekt  
 <xref:System.Windows.Controls.ContentControl> Třída obsahuje jediný libovolný obsah. Vlastnost jeho obsahu je <xref:System.Windows.Controls.ContentControl.Content%2A>. Ovládací prvky dědí <xref:System.Windows.Controls.ContentControl> a použít jeho modelu obsahu:  
  
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
  
 Následující ilustrace znázorňuje čtyři tlačítka, jehož <xref:System.Windows.Controls.ContentControl.Content%2A> je nastaven na řetězec, <xref:System.DateTime> objekt, <xref:System.Windows.Shapes.Rectangle>a <xref:System.Windows.Controls.Panel> obsahující <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>.  
  
 ![Čtyři tlačítka](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")  
Čtyři tlačítka, které mají různé typy obsahu  
  
 Příklad toho, jak nastavit <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost, najdete v části <xref:System.Windows.Controls.ContentControl>.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Ovládací prvky, které obsahují záhlaví a jeden libovolný objekt  
 <xref:System.Windows.Controls.HeaderedContentControl> Třída dědí z <xref:System.Windows.Controls.ContentControl> a zobrazí obsah s hlavičku. Dědí vlastnost obsahu <xref:System.Windows.Controls.ContentControl.Content%2A>, z <xref:System.Windows.Controls.ContentControl> a definuje <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> vlastnost, která je typu <xref:System.Object>; proto může být libovolný objekt.  
  
 Ovládací prvky dědí <xref:System.Windows.Controls.HeaderedContentControl> a použít jeho modelu obsahu:  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 Následující obrázek ukazuje dva <xref:System.Windows.Controls.TabItem> objekty. První <xref:System.Windows.Controls.TabItem> má <xref:System.Windows.UIElement> objekty, jako <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.ContentControl.Content%2A>. <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> Je nastaven na <xref:System.Windows.Controls.StackPanel> obsahující <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Controls.ContentControl.Content%2A> Je nastaven na <xref:System.Windows.Controls.StackPanel> obsahující <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.Label>. Druhý <xref:System.Windows.Controls.TabItem> má řetězec <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.TextBlock> v <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")  
TabControl používající různé typy ve vlastnosti záhlaví  
  
 Příklad vytvoření <xref:System.Windows.Controls.TabItem> objekty, najdete v části <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Ovládací prvky, které obsahují skupiny libovolný objekty  
 <xref:System.Windows.Controls.ItemsControl> Třída dědí z <xref:System.Windows.Controls.Control> a může obsahovat více položek, jako je například řetězce, objekty nebo jiných prvků. Jeho obsahu vlastnosti jsou <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> a <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>Obvykle se používá k naplnění <xref:System.Windows.Controls.ItemsControl> se shromažďováním dat. Pokud nechcete použít kolekci k naplnění <xref:System.Windows.Controls.ItemsControl>, můžete přidat položky pomocí <xref:System.Windows.Controls.ItemsControl.Items%2A> vlastnost.  
  
 Ovládací prvky dědí <xref:System.Windows.Controls.ItemsControl> a použít jeho modelu obsahu:  
  
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
  
 Následující obrázek znázorňuje <xref:System.Windows.Controls.ListBox> obsahující tyto typy položek:  
  
-   Řetězec.  
  
-   A <xref:System.DateTime> objektu.  
  
-   A <xref:System.Windows.UIElement>.  
  
-   A <xref:System.Windows.Controls.Panel> obsahující <xref:System.Windows.Shapes.Ellipse> a <xref:System.Windows.Controls.TextBlock>.  
  
 ![ListBox – s čtyři typy obsahu](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")  
ListBox –, který obsahuje více typů objektů  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Ovládací prvky záhlaví a kolekce libovolný objektů  
 <xref:System.Windows.Controls.HeaderedItemsControl> Třída dědí z <xref:System.Windows.Controls.ItemsControl> a může obsahovat více položek, jako je například řetězce, objekty, nebo další prvky a hlavičku. Zdědil <xref:System.Windows.Controls.ItemsControl> obsahu vlastnosti, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, a <xref:System.Windows.Controls.ItemsControl.Items%2A>, a definuje, <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> vlastnost, která může být libovolný objekt.  
  
 Ovládací prvky dědí <xref:System.Windows.Controls.HeaderedItemsControl> a použít jeho modelu obsahu:  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Třídy, které obsahují kolekce objektů prvků uživatelského rozhraní  
 <xref:System.Windows.Controls.Panel> Třídy umisťuje a uspořádá podřízené <xref:System.Windows.UIElement> objekty. Vlastnost jeho obsahu je <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 Následující třídy dědí <xref:System.Windows.Controls.Panel> třídy a použít jeho modelu obsahu:  
  
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
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Třídy, které ovlivňují vzhled prvků uživatelského rozhraní  
 <xref:System.Windows.Controls.Decorator> Třída platí vizuálních efektů na nebo kolem jednu podřízenou <xref:System.Windows.UIElement>. Vlastnost jeho obsahu je <xref:System.Windows.Controls.Decorator.Child%2A>. Následující třídy dědí <xref:System.Windows.Controls.Decorator> a použít jeho modelu obsahu:  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 Následující obrázek znázorňuje <xref:System.Windows.Controls.TextBox> má (opatřen s) <xref:System.Windows.Controls.Border> kolem něj.  
  
 ![Textové pole s černým ohraničení](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
TextBlock, který má ohraničení  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Třídy, které poskytují vizuální zpětnou vazbu o prvků uživatelského rozhraní  
 <xref:System.Windows.Documents.Adorner> Třída poskytuje vizuální upozornění na uživatele. Například použít <xref:System.Windows.Documents.Adorner> přidat funkční obslužné rutiny na elementy nebo zadejte informace o prvku stavu. <xref:System.Windows.Documents.Adorner> Třída poskytuje rozhraní, takže můžete vytvořit vlastní ozdobného prvku. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]neposkytuje žádné implementovaná ozdobného prvku. Další informace najdete v tématu [ozdobného prvku přehled](../../../../docs/framework/wpf/controls/adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>Třídy, které umožňují uživatelům zadávat Text  
 WPF poskytuje tři primární ovládací prvky, které umožňují uživatelům zadávat text. Každý ovládací prvek zobrazí text jinak. Následující tabulka uvádí tyto tři související s textem ovládací prvky, jejich schopnosti, při které se zobrazuje text a jejich vlastnosti, které obsahují text ovládacího prvku.  
  
|Ovládací prvek|Text se zobrazuje jako|Vlastnost obsahu|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Prostý text|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Formátovaný text|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Skrytý text (znaky jsou maskována)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>Třídy, které zobrazí Text  
 Několik tříd lze zobrazit prostý nebo formátovaný text. Můžete použít <xref:System.Windows.Controls.TextBlock> zobrazíte malé množství textu. Pokud chcete zobrazit velké množství textu, použijte <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, nebo <xref:System.Windows.Controls.FlowDocumentScrollViewer> ovládací prvky.  
  
 <xref:System.Windows.Controls.TextBlock> Má dvě vlastnosti obsahu: <xref:System.Windows.Controls.TextBlock.Text%2A> a <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Pokud chcete zobrazit text, který používá konzistentní formátování <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost je často nejlepší volbou. Pokud budete chtít použít jiné formátování v celém textu, použijte <xref:System.Windows.Controls.TextBlock.Inlines%2A> vlastnost. <xref:System.Windows.Controls.TextBlock.Inlines%2A> Vlastnost je kolekce <xref:System.Windows.Documents.Inline> objekty, které určují způsob formátování textu.  
  
 Následující tabulka uvádí vlastnost obsahu pro <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, a <xref:System.Windows.Controls.FlowDocumentScrollViewer> třídy.  
  
|Ovládací prvek|Vlastnost obsahu|Typ obsahu vlastnosti|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Dokument|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Dokument|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Dokument|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.FlowDocument> Implementuje <xref:System.Windows.Documents.IDocumentPaginatorSource> rozhraní; proto může trvat všechny tři třídy <xref:System.Windows.Documents.FlowDocument> jako obsah.  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>Třídy, které formátování textu  
 <xref:System.Windows.Documents.TextElement>a jeho souvisejících tříd umožňují formátování textu. <xref:System.Windows.Documents.TextElement>objekty obsahovat a formátování textu v <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument> objekty. Oba typy primární <xref:System.Windows.Documents.TextElement> objekty jsou <xref:System.Windows.Documents.Block> elementy a <xref:System.Windows.Documents.Inline> elementy. A <xref:System.Windows.Documents.Block> element reprezentuje blok textu, například odstavce nebo seznamu. <xref:System.Windows.Documents.Inline> Element reprezentuje část textu v bloku. Mnoho <xref:System.Windows.Documents.Inline> třídy zadejte formátování textu, do které se použijí. Každý <xref:System.Windows.Documents.TextElement> má svou vlastní modelu obsahu. Další informace najdete v tématu [přehled modelu obsahu TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Upřesnit](../../../../docs/framework/wpf/advanced/index.md)
