---
title: GridView – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 9457430ab61681ad154aba98d72850f19d30280d
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185438"
---
# <a name="gridview-overview"></a>GridView – přehled
<xref:System.Windows.Controls.GridView> režim zobrazení je jeden z režimů zobrazení pro <xref:System.Windows.Controls.ListView> ovládacího prvku. <xref:System.Windows.Controls.GridView> Třída a její podpůrnou třídy povolit vy a vaši uživatelé zobrazit položky kolekce tabulku, která se obvykle používá jako záhlaví sloupců interaktivní tlačítka. Toto téma představuje <xref:System.Windows.Controls.GridView> třídy a popisuje jejich použití.  
  
  
  
<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>Co je zobrazení GridView?  
 <xref:System.Windows.Controls.GridView> Zobrazení režimu zobrazí seznam datových položek vazby datová pole pro sloupce a záhlaví sloupce a identifikovat oblasti zobrazení. Výchozí hodnota <xref:System.Windows.Controls.GridView> styl implementuje tlačítka jako záhlaví sloupců. Pomocí tlačítka pro záhlaví sloupců, můžete implementovat důležité uživatelské interakce možnosti; Například můžete uživatele klikněte na záhlaví sloupce seřadíte <xref:System.Windows.Controls.GridView> dat podle obsah v určitém sloupci.  
  
> [!NOTE]
>  Tlačítko – ovládací prvky, které <xref:System.Windows.Controls.GridView> používá pro záhlaví sloupců jsou odvozeny z <xref:System.Windows.Controls.Primitives.ButtonBase>.  
  
 Následující ilustrace ukazuje <xref:System.Windows.Controls.GridView> zobrazení <xref:System.Windows.Controls.ListView> obsah.  
    
 ![Snímek obrazovky zobrazující GridView zobrazení obsahu ListView.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView> sloupce jsou reprezentovány <xref:System.Windows.Controls.GridViewColumn> objekty, které lze automaticky velikosti jejich obsahu. Volitelně můžete explicitně nastavit <xref:System.Windows.Controls.GridViewColumn> určité šířce. Změna velikosti sloupců přetažením úchytu mezi záhlaví sloupců. Můžete taky dynamicky přidat, odebrat, nahraďte a změnit uspořádání sloupců, protože tato funkce je integrovaná do <xref:System.Windows.Controls.GridView>. Ale <xref:System.Windows.Controls.GridView> nelze přímo aktualizovat data, která se zobrazí.  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridView> , která zobrazuje data zaměstnanců. V tomto příkladu <xref:System.Windows.Controls.ListView> definuje `EmployeeInfoDataSource` jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Definice vlastnosti <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> svázat <xref:System.Windows.Controls.GridViewColumn> obsahu `EmployeeInfoDataSource` kategorie dat.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Následující obrázek ukazuje tabulku, že v předchozím příkladu vytvoří. Ovládací prvek GridView zobrazí data z objektu vlastnost ItemsSource:
    
 ![Snímek obrazovky zobrazující ListView s výstupem ovládacího prvku GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>Rozložení ovládacího prvku GridView a stylu  
 Buňky sloupce a záhlaví sloupce <xref:System.Windows.Controls.GridViewColumn> mají stejnou šířku. Ve výchozím nastavení každý sloupec velikosti jeho šířka podle jeho obsahu. Volitelně můžete nastavit sloupec na pevnou šířku.  
  
 Související data obsahu se zobrazí horizontální řádků. Například na předchozím obrázku, příjmení, křestního jména a identifikační číslo jednotliví zaměstnanci se zobrazují jako sada vzhledem k tomu, že se zobrazují ve vodorovném řádku.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>Definování a používání stylů pro sloupce v GridView  
 Při definování datového pole k zobrazení v <xref:System.Windows.Controls.GridViewColumn>, použijte <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>, nebo <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> vlastnosti. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Vlastnost má přednost před buď ve vlastnostech šablony.  
  
 K určení zarovnání obsahu ve sloupci <xref:System.Windows.Controls.GridView>, definovat <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>. Nepoužívejte <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> a <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> vlastnosti <xref:System.Windows.Controls.ListView> obsah, který se zobrazí při použití <xref:System.Windows.Controls.GridView>.  
  
 Pokud chcete nastavit vlastnosti šablony a styl záhlaví sloupců, použijte <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn>, a <xref:System.Windows.Controls.GridViewColumnHeader> třídy. Další informace najdete v tématu [GridView styly záhlaví sloupců a Přehled šablon](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>Přidání vizuální prvky GridView  
 Chcete-li přidat vizuální prvky, jako například <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.Button> ovládací prvky, na <xref:System.Windows.Controls.GridView> režimu zobrazení, použijte šablony stylů.  
  
 Pokud explicitně definovat vizuální prvek jako datové položky, může se objevit pouze jednou <xref:System.Windows.Controls.GridView>. Toto omezení existuje, protože element může mít pouze jeden nadřazený prvek a proto se může objevit pouze jednou v vizuálního stromu.  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>Používání stylů pro řádky GridView  
 Použití <xref:System.Windows.Controls.GridViewRowPresenter> a <xref:System.Windows.Controls.GridViewHeaderRowPresenter> třídy pro formátování a zobrazení řádky <xref:System.Windows.Controls.GridView>. Příklad toho, jak pro styl řádky v <xref:System.Windows.Controls.GridView> zobrazení režimu naleznete v tématu [stylu řádku v ListView, že implementuje GridView](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Zarovnání problémy při použití ItemContainerStyle  
 Aby se zabránilo problémům zarovnání mezi záhlaví sloupců a buněk, není nastavení vlastnosti nebo zadejte šablonu, která má vliv na šířku položky v <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Například nenastavujte <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost nebo zadejte <xref:System.Windows.Controls.ControlTemplate> , který přidá <xref:System.Windows.Controls.CheckBox> do <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> , který je definován na <xref:System.Windows.Controls.ListView> ovládacího prvku. Místo toho zadejte vlastnosti a šablony, které ovlivňují šířku sloupce přímo u třídy, které definují <xref:System.Windows.Controls.GridView> režim zobrazení.  
  
 Například, chcete-li přidat <xref:System.Windows.Controls.CheckBox> pro řádky v <xref:System.Windows.Controls.GridView> režimu zobrazení, přidat <xref:System.Windows.Controls.CheckBox> k <xref:System.Windows.DataTemplate>a pak nastavte <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> vlastnost, která <xref:System.Windows.DataTemplate>.  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>Interakce uživatele s GridView  
 Při použití <xref:System.Windows.Controls.GridView> ve vaší aplikaci, uživatelé mohou pracovat a úprava formátování <xref:System.Windows.Controls.GridView>. Například uživatel může změnit uspořádání sloupců, změna velikosti sloupce, vyberte v tabulce a projděte si obsah položky. Můžete také definovat obslužnou rutinu události, které reaguje, když uživatel klikne na tlačítko záhlaví sloupce. Obslužná rutina události můžete provádět operace, jako je řazení dat, který se zobrazí v <xref:System.Windows.Controls.GridView> podle obsahu sloupce.  
  
 Následující seznam popisuje podrobněji možnosti použití <xref:System.Windows.Controls.GridView> pro interakci s uživatelem:  
  
-   **Změnit uspořádání sloupců pomocí metody přetahování myší.**  
  
     Uživatelé mohou změnit pořadí sloupců v <xref:System.Windows.Controls.GridView> klávesy levé tlačítko myši, zatímco je nad záhlaví sloupce a následným přetažením sloupce do nového umístění. Když uživatel přetáhne záhlaví sloupce, zobrazí se plovoucí verze hlavičky a také pevné černá čára, která ukazuje, kam chcete vložit sloupec.  
  
     Pokud chcete změnit výchozí styl plovoucí verze záhlaví, zadejte <xref:System.Windows.Controls.ControlTemplate> pro <xref:System.Windows.Controls.GridViewColumnHeader> typ, který je při aktivaci <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> je nastavena na <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>. Další informace najdete v tématu [vytvoření stylu pro záhlaví sloupce GridView kvůli usnadnění použití vypsány](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
-   **Změnit velikost sloupce na jeho obsah.**  
  
     Uživatelům můžete dvakrát kliknout na úchytu napravo od záhlaví sloupce, aby bylo možné změnit velikost sloupce podle jeho obsahu.  
  
    > [!NOTE]
    >  Můžete nastavit <xref:System.Windows.Controls.GridViewColumn.Width%2A> vlastnost `Double.NaN` k dosažení stejného efektu.  
  
-   **Vyberte položky na řádcích.**  
  
     Uživatelé mohou vybrat jednu nebo více položek v <xref:System.Windows.Controls.GridView>.  
  
     Pokud chcete změnit <xref:System.Windows.Style> vybrané položky, naleznete v tématu [stylu vybraných položek v ListView použitím aktivačních procedur](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
-   **Přejděte do zobrazení obsahu, který není zpočátku viditelné na obrazovce.**  
  
     Pokud velikost <xref:System.Windows.Controls.GridView> není dostatečně velký pro zobrazení všech položek, uživatelům umožní posouvání, vodorovně nebo svisle pomocí posuvníků, které jsou poskytovány <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku. A <xref:System.Windows.Controls.Primitives.ScrollBar> je skrytý, pokud veškerý obsah, který je viditelný v konkrétní směr. Záhlaví sloupců neposouvají svislý posuvník, ale posouvat vodorovně.  
  
-   **Zasahovat sloupce kliknutím na příslušné záhlaví sloupce.**  
  
     Když uživatelé kliknou na tlačítko záhlaví sloupců, jsou data, která se zobrazí ve sloupci, pokud jste zadali řadicího algoritmu řazení.  
  
     Dokáže zpracovat <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události pro tlačítka záhlaví sloupce negace funkce, jako jsou řadicího algoritmu. Zpracování <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost pro hlavičku jednoho sloupce nastavit obslužné rutiny události <xref:System.Windows.Controls.GridViewColumnHeader>. Chcete-li nastavit obslužnou rutinu události, která zpracovává <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události pro všechna záhlaví sloupců, nastavování obslužné rutiny na <xref:System.Windows.Controls.ListView> ovládacího prvku.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>Získání dalších vlastních zobrazení  
 <xref:System.Windows.Controls.GridView> Třídu, která je odvozena od <xref:System.Windows.Controls.ViewBase> abstraktní třídu, je právě jeden z režimů zobrazení možných pro <xref:System.Windows.Controls.ListView> třídy. Můžete vytvořit další vlastní zobrazení pro <xref:System.Windows.Controls.ListView> odvozením z <xref:System.Windows.Controls.ViewBase> třídy. Příklad vlastního režimu zobrazení najdete v tématu [vytvoření vlastního režimu zobrazení pro ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>Podpora třídy GridView  
 Následující třídy podporu <xref:System.Windows.Controls.GridView> režim zobrazení.  
  
-   <xref:System.Windows.Controls.GridViewColumn>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GridViewRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewColumnCollection>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Controls.GridViewColumn>
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.ViewBase>
- [ListView – přehled](listview-overview.md)
- [Řazení sloupce GridView při kliknutí na záhlaví](how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Témata s postupy](listview-how-to-topics.md)
