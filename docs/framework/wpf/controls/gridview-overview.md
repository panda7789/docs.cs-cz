---
title: GridView – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 776897d490b2748e240cf7b9a4ea21364284c4c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="gridview-overview"></a>GridView – přehled
<xref:System.Windows.Controls.GridView> režim zobrazení je jeden z režimů zobrazení pro <xref:System.Windows.Controls.ListView> ovládacího prvku. <xref:System.Windows.Controls.GridView> Třídy a jeho podpůrné povolit vás a uživatele zobrazit položky kolekce v tabulce, která tlačítka se většinou používá jako záhlaví sloupců interaktivní. Toto téma představuje <xref:System.Windows.Controls.GridView> třídy a popisuje jeho použití.  
  
  
  
<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>Co je rutina GridView zobrazení?  
 <xref:System.Windows.Controls.GridView> Zobrazení režimu zobrazí seznam datových položek, vazby dat pole na sloupce a zobrazením záhlaví sloupce k identifikaci pole. Výchozí hodnota <xref:System.Windows.Controls.GridView> styl implementuje tlačítka jako záhlaví sloupců. Pomocí tlačítka pro záhlaví sloupců, můžete implementovat důležité uživatelské interakce možnosti; například mohou uživatelé kliknout na záhlaví sloupce seřadíte <xref:System.Windows.Controls.GridView> dat podle obsahu konkrétní sloupce.  
  
> [!NOTE]
>  Tlačítko prvky, které <xref:System.Windows.Controls.GridView> používá pro záhlaví sloupců jsou odvozeny od <xref:System.Windows.Controls.Primitives.ButtonBase>.  
  
 Následující obrázek znázorňuje <xref:System.Windows.Controls.GridView> zobrazení <xref:System.Windows.Controls.ListView> obsahu.  
  
 **Rutina GridView zobrazení obsahu ListView**  
  
 ![Ve ListView](../../../../docs/framework/wpf/controls/media/styledlistview.PNG "StyledListView")  
  
 <xref:System.Windows.Controls.GridView> sloupce jsou reprezentované pomocí <xref:System.Windows.Controls.GridViewColumn> objekty, které lze automaticky velikost na jejich obsah. Volitelně můžete explicitně nastavit <xref:System.Windows.Controls.GridViewColumn> konkrétní šířky. Změna velikosti sloupců přetažením úchytu mezi záhlaví sloupců. Můžete také dynamicky přidat, odebrat, nahraďte a změnit pořadí sloupců, protože tato funkce je integrovaná do <xref:System.Windows.Controls.GridView>. Ale <xref:System.Windows.Controls.GridView> nelze přímo aktualizovat data, která se zobrazí.  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridView> , zobrazí data o zaměstnancích. V tomto příkladu <xref:System.Windows.Controls.ListView> definuje `EmployeeInfoDataSource` jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Vlastnost definice <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vazby <xref:System.Windows.Controls.GridViewColumn> obsah `EmployeeInfoDataSource` kategorie dat.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Následující obrázek znázorňuje tabulky, v předchozím příkladu se vytváří.  
  
 **Rutina GridView, která zobrazuje data ze ItemsSource**  
  
 ![ListView s výstupem GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>Rutina GridView rozvržení a stylu  
 Sloupec buněk a záhlaví sloupce <xref:System.Windows.Controls.GridViewColumn> mít stejné šířky. Ve výchozím nastavení každý sloupec velikostí šířku podle jeho obsahu. Volitelně můžete nastavit sloupec na pevnou šířku.  
  
 Související data obsahu se zobrazí ve vodorovném řádků. Například na předchozím obrázku, každý zaměstnanec příjmení, křestní jméno a identifikační číslo se zobrazí jako sada vzhledem k tomu, že se objeví na vodorovném řádku.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>Definování a styly sloupce v GridView  
 Při definování datové pole, které chcete zobrazit v <xref:System.Windows.Controls.GridViewColumn>, použijte <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>, nebo <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> vlastnosti. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Vlastnost má přednost před buď ve vlastnostech šablony.  
  
 K určení zarovnání obsahu ve sloupci <xref:System.Windows.Controls.GridView>, definovat <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>. Nepoužívejte <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> a <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> vlastnosti <xref:System.Windows.Controls.ListView> obsah, který se zobrazí pomocí <xref:System.Windows.Controls.GridView>.  
  
 Chcete-li zadat vlastnosti šablony a stylu pro záhlaví sloupců, použijte <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn>, a <xref:System.Windows.Controls.GridViewColumnHeader> třídy. Další informace najdete v tématu [GridView styly záhlaví sloupců a Přehled šablon](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>Přidávání do GridView vizuální prvky  
 Chcete-li přidat vizuální prvky, jako například <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.Button> řídí, na <xref:System.Windows.Controls.GridView> zobrazit režimu, používají šablony nebo styly.  
  
 Pokud je explicitně definovat vizuální prvek jako položku dat, může se objevit pouze jednou v <xref:System.Windows.Controls.GridView>. Toto omezení existuje, protože element může mít jen jednu nadřazenou položku a proto může vyskytovat pouze jednou v vizuálním stromu.  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>Stylů řádků v GridView  
 Použití <xref:System.Windows.Controls.GridViewRowPresenter> a <xref:System.Windows.Controls.GridViewHeaderRowPresenter> třídy pro formátování a zobrazení řádky <xref:System.Windows.Controls.GridView>. Příklad toho, jak na styl řádky v <xref:System.Windows.Controls.GridView> zobrazit režimu, najdete v části [styl řádek v ListView, implementuje GridView](../../../../docs/framework/wpf/controls/how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Zarovnání problémy při použití ItemContainerStyle  
 Aby se zabránilo problémům zarovnání mezi záhlaví sloupců a buněk, nezadávejte nastavení vlastnosti nebo zadejte šablonu, která má vliv na šířku položky v <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Například nenastavujte <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost, nebo zadejte <xref:System.Windows.Controls.ControlTemplate> doplňuje <xref:System.Windows.Controls.CheckBox> k <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> který je definován na <xref:System.Windows.Controls.ListView> ovládacího prvku. Místo toho zadejte vlastnosti a šablony, které ovlivňují šířka sloupce přímo na třídy, které definují <xref:System.Windows.Controls.GridView> režimu zobrazení.  
  
 Například přidat <xref:System.Windows.Controls.CheckBox> na řádky v <xref:System.Windows.Controls.GridView> režimu zobrazení, přidat <xref:System.Windows.Controls.CheckBox> k <xref:System.Windows.DataTemplate>a poté nastavte <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> s vlastností <xref:System.Windows.DataTemplate>.  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>Interakce uživatele s GridView  
 Při použití <xref:System.Windows.Controls.GridView> ve vaší aplikaci, uživatelé mohou pracovat s nebo změnit formátování <xref:System.Windows.Controls.GridView>. Například uživatel může změnit pořadí sloupců, velikosti sloupce, vyberte položky v tabulce a procházení obsahu. Můžete také definovat obslužné rutiny události, který reagovat, když uživatel klikne na tlačítko záhlaví sloupce. Obslužné rutiny události můžete provádět operace, jako je řazení data, která se zobrazí v <xref:System.Windows.Controls.GridView> podle obsahu sloupce.  
  
 Následující seznam popisuje podrobněji možnosti použití <xref:System.Windows.Controls.GridView> pro interakci s uživatelem:  
  
-   **Změna pořadí sloupců pomocí metody přetažení myší.**  
  
     Uživatelé mohou změnit pořadí sloupců v <xref:System.Windows.Controls.GridView> stisknutím klávesy levým tlačítkem myši, i když je přes záhlaví sloupce a potom přetažením sloupce do nového umístění. Když uživatel nastavuje tažením na záhlaví sloupce, zobrazí se plovoucí verze hlavičky i plnou černá čára o tom, kam chcete vložit sloupec.  
  
     Pokud chcete upravit výchozí styl pro plovoucí verzi záhlaví, zadejte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.GridViewColumnHeader> typ, který je při aktivaci <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> je nastavena na <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>. Další informace najdete v tématu [vytvořit styl pro přetáhnout záhlaví sloupce GridView](../../../../docs/framework/wpf/controls/how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
-   **Přizpůsobit sloupec na jeho obsah.**  
  
     Uživatelé poklepáním na úchyt napravo od záhlaví sloupce, aby bylo možné velikosti sloupce podle jeho obsahu.  
  
    > [!NOTE]
    >  Můžete nastavit <xref:System.Windows.Controls.GridViewColumn.Width%2A> vlastnost `Double.NaN` k vytvoření stejného efektu.  
  
-   **Vyberte řádek položky.**  
  
     Uživatele můžete vybrat jednu nebo více položek v <xref:System.Windows.Controls.GridView>.  
  
     Pokud chcete změnit <xref:System.Windows.Style> vybrané položky, najdete v části [použít aktivační procedury styl vybrané položky v prvku ListView](../../../../docs/framework/wpf/controls/how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
-   **Posuňte se k zobrazení obsahu, který není zobrazené na obrazovce.**  
  
     Pokud velikost <xref:System.Windows.Controls.GridView> není dostatečně velký pro zobrazení všech položek, uživatelé mohou posunutím vodorovně nebo svisle pomocí posuvníky, které jsou poskytovány <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku. A <xref:System.Windows.Controls.Primitives.ScrollBar> je skrytý, pokud se zobrazí na konkrétní směr veškerý obsah. Záhlaví sloupců neposouvá s svislý posuvník, ale vodorovný posun.  
  
-   **Zasahovat sloupce klepnutím na záhlaví sloupce.**  
  
     Když uživatel klikne na tlačítko záhlaví sloupce, budou řadit data, která se zobrazí ve sloupci, pokud jste zadali řazení algoritmus.  
  
     Může zpracovat <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost pro tlačítka záhlaví sloupce s cílem poskytnout funkcí jako řazení algoritmus. Zpracování <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost pro hlavičku jeden sloupec nastavit obslužnou rutinu události <xref:System.Windows.Controls.GridViewColumnHeader>. Chcete-li nastavit obslužnou rutinu události, která zpracovává <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost pro všechny záhlaví sloupců, nastavování obslužné rutiny na <xref:System.Windows.Controls.ListView> ovládací prvek.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>Získání dalších vlastních zobrazení  
 <xref:System.Windows.Controls.GridView> Třídy, která je odvozená od <xref:System.Windows.Controls.ViewBase> abstraktní třída, je právě jeden z režimů možné zobrazení pro <xref:System.Windows.Controls.ListView> třídy. Můžete vytvořit další vlastní zobrazení pro <xref:System.Windows.Controls.ListView> odvozené z <xref:System.Windows.Controls.ViewBase> třídy. Příklad režimu vlastní zobrazení, naleznete v části [vytvořit vlastní režim zobrazení pro prvku ListView](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>Rutina GridView podpora třídy  
 Následující třídy podpory <xref:System.Windows.Controls.GridView> režimu zobrazení.  
  
-   <xref:System.Windows.Controls.GridViewColumn>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GridViewRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewColumnCollection>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Controls.GridViewColumn>  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.ViewBase>  
 [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Řazení sloupce GridView při kliknutí na záhlaví](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
