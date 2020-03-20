---
title: GridView – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 98bc7985172cabeab19469af4b4c21e13a6bce73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181892"
---
# <a name="gridview-overview"></a>GridView – přehled
<xref:System.Windows.Controls.GridView>režim zobrazení je jedním z <xref:System.Windows.Controls.ListView> režimů zobrazení ovládacího prvku. Třída <xref:System.Windows.Controls.GridView> a její podpůrné třídy umožňují vám a vašim uživatelům zobrazit kolekce položek v tabulce, která obvykle používá tlačítka jako interaktivní záhlaví sloupců. Toto téma <xref:System.Windows.Controls.GridView> představuje třídu a popisuje jeho použití.  

<a name="DefiningaListViewthatusesGridViewView"></a>
## <a name="what-is-a-gridview-view"></a>Co je zobrazení GridView?  
 Režim <xref:System.Windows.Controls.GridView> zobrazení zobrazí seznam datových položek vazbou datových polí se sloupci a zobrazením záhlaví sloupce k identifikaci pole. Výchozí <xref:System.Windows.Controls.GridView> styl implementuje tlačítka jako záhlaví sloupců. Pomocí tlačítek pro záhlaví sloupců můžete implementovat důležité možnosti interakce uživatele; Uživatelé mohou například klepnout <xref:System.Windows.Controls.GridView> na záhlaví sloupce a seřadit data podle obsahu určitého sloupce.  
  
> [!NOTE]
> Ovládací prvky <xref:System.Windows.Controls.GridView> tlačítka, které používají záhlaví <xref:System.Windows.Controls.Primitives.ButtonBase>sloupců, jsou odvozeny od .  
  
 Následující obrázek <xref:System.Windows.Controls.GridView> znázorňuje zobrazení <xref:System.Windows.Controls.ListView> obsahu.  

 ![Snímek obrazovky, který zobrazuje zobrazení GridView obsahu ListView.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>sloupce jsou <xref:System.Windows.Controls.GridViewColumn> reprezentovány objekty, které mohou automaticky měnit velikost jejich obsahu. Volitelně můžete explicitně <xref:System.Windows.Controls.GridViewColumn> nastavit a na určitou šířku. Velikost sloupců můžete změnit přetažením úchytu mezi záhlavími sloupců. Můžete také dynamicky přidávat, odebírat, nahrazovat a měnit <xref:System.Windows.Controls.GridView>pořadí sloupců, protože tato funkce je integrována do aplikace . Nelze <xref:System.Windows.Controls.GridView> však přímo aktualizovat data, která se zobrazí.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.GridView> definovat, který zobrazuje data zaměstnanců. V tomto <xref:System.Windows.Controls.ListView> příkladu `EmployeeInfoDataSource` definuje <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>jako . Definice vlastností <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> obsahu <xref:System.Windows.Controls.GridViewColumn> vazby na `EmployeeInfoDataSource` kategorie dat.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Následující obrázek znázorňuje tabulku, kterou vytvoří předchozí příklad. Ovládací prvek GridView zobrazuje data z objektu ItemsSource:

 ![Snímek obrazovky, který zobrazuje ListView s výstupem GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>
## <a name="gridview-layout-and-style"></a>Rozložení a styl GridView  
 Buňky sloupců a záhlaví <xref:System.Windows.Controls.GridViewColumn> sloupce mají stejnou šířku. Ve výchozím nastavení má každý sloupec velikost šířky tak, aby odpovídala jeho obsahu. Volitelně můžete nastavit sloupec na pevnou šířku.  
  
 Související obsah dat se zobrazí v vodorovných řádcích. Na předchozím obrázku jsou například příjmení, jméno a identifikační číslo každého zaměstnance zobrazeny jako sada, protože se zobrazují ve vodorovném řádku.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>
### <a name="defining-and-styling-columns-in-a-gridview"></a>Definování a stylingových sloupců v zobrazení gridu  
 Při definování datového pole, <xref:System.Windows.Controls.GridViewColumn>které se <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>má <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> zobrazit v oblasti , použijte vlastnosti nebo vlastnosti . Vlastnost <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> má přednost před některou z vlastností šablony.  
  
 Chcete-li určit zarovnání obsahu <xref:System.Windows.Controls.GridView>ve <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>sloupci , definujte . Nepoužívejte <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> vlastnosti <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> a <xref:System.Windows.Controls.ListView> pro obsah, který <xref:System.Windows.Controls.GridView>je zobrazen pomocí rozhraní .  
  
 Chcete-li určit vlastnosti šablony a <xref:System.Windows.Controls.GridView>stylu <xref:System.Windows.Controls.GridViewColumn>pro <xref:System.Windows.Controls.GridViewColumnHeader> záhlaví sloupců, použijte třídy , a třídy. Další informace naleznete v tématu [GridView Column Header Styles and Templates Overview](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>
### <a name="adding-visual-elements-to-a-gridview"></a>Přidání vizuálních prvků do zobrazení gridu  
 Chcete-li do <xref:System.Windows.Controls.CheckBox> režimu <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.GridView> zobrazení přidat vizuální prvky, například a ovládací prvky, použijte šablony nebo styly.  
  
 Pokud explicitně definujete vizuální prvek jako datovou položku, <xref:System.Windows.Controls.GridView>může se zobrazit pouze jednou v aplikaci . Toto omezení existuje, protože prvek může mít pouze jeden nadřazený prvek, a proto se může zobrazit pouze jednou ve vizuálním stromu.  
  
<a name="StylingRowsinaGridViewView"></a>
### <a name="styling-rows-in-a-gridview"></a>Stylování řádků v zobrazení mřížky  
 Třídy <xref:System.Windows.Controls.GridViewRowPresenter> <xref:System.Windows.Controls.GridViewHeaderRowPresenter> a slouží k formátování a <xref:System.Windows.Controls.GridView>zobrazení řádků . Příklad, jak styl řádků v <xref:System.Windows.Controls.GridView> režimu zobrazení, naleznete v [tématu Styl řádek v ListView, který implementuje GridView](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Problémy se zarovnáním při použití itemcontainerstyle  
 Chcete-li zabránit problémům se zarovnáním mezi záhlavími sloupců a buňkami, <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>nenastavovat vlastnost ani nezadávat šablonu, která ovlivňuje šířku položky v . Například nenastavovat <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost nebo <xref:System.Windows.Controls.ControlTemplate> zadejte, který přidá <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> do, který je definován na ovládací prvek. <xref:System.Windows.Controls.ListView> Místo toho zadejte vlastnosti a šablony, které ovlivňují <xref:System.Windows.Controls.GridView> šířku sloupce přímo na třídách, které definují režim zobrazení.  
  
 Chcete-li například <xref:System.Windows.Controls.CheckBox> přidat a <xref:System.Windows.Controls.GridView> do řádků <xref:System.Windows.Controls.CheckBox> v <xref:System.Windows.DataTemplate>režimu zobrazení, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> přidejte <xref:System.Windows.DataTemplate>do a a nastavte vlastnost na tuto vlastnost .  
  
<a name="InteractingwithaGridViewControl"></a>
## <a name="user-interactions-with-a-gridview"></a>Interakce uživatele s gridview  
 Při použití <xref:System.Windows.Controls.GridView> v aplikaci mohou uživatelé pracovat s a <xref:System.Windows.Controls.GridView>upravovat formátování . Uživatelé mohou například změnit pořadí sloupců, změnit velikost sloupce, vybrat položky v tabulce a procházet obsah. Můžete také definovat obslužnou rutinu události, která reaguje, když uživatel klepne na tlačítko záhlaví sloupce. Obslužná rutina události může provádět operace, <xref:System.Windows.Controls.GridView> jako je řazení dat, která je zobrazena v podle obsahu sloupce.  
  
 Následující seznam podrobněji popisuje možnosti <xref:System.Windows.Controls.GridView> použití pro interakci s uživatelem:  
  
- **Při objednání sloupců pomocí metody přetažení.**  
  
     Uživatelé mohou změnit <xref:System.Windows.Controls.GridView> pořadí sloupců v a stisknutím levého tlačítka myši, zatímco je přes záhlaví sloupce a pak přetažením tohoto sloupce na novou pozici. Zatímco uživatel přetáhne záhlaví sloupce, zobrazí se plovoucí verze záhlaví a plná černá čára, která ukazuje, kam vložit sloupec.  
  
     Pokud chcete změnit výchozí styl pro plovoucí verzi záhlaví, <xref:System.Windows.Controls.ControlTemplate> zadejte pro <xref:System.Windows.Controls.GridViewColumnHeader> typ, <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> který se <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>aktivuje, když je vlastnost nastavena na . Další informace naleznete [v tématu Vytvoření stylu pro záhlaví sloupce Přetažená mřížka](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **Změňte velikost sloupce na jeho obsah.**  
  
     Uživatelé mohou poklepat na úchyt vpravo od záhlaví sloupce, aby velikost sloupce odpovídala jeho obsahu.  
  
    > [!NOTE]
    > Vlastnost můžete <xref:System.Windows.Controls.GridViewColumn.Width%2A> nastavit `Double.NaN` tak, aby vyvolála stejný efekt.  
  
- **Vyberte položky řádků.**  
  
     Uživatelé mohou vybrat jednu <xref:System.Windows.Controls.GridView>nebo více položek v .  
  
     Pokud chcete změnit <xref:System.Windows.Style> vybranou položku, přečtěte si část Použití [aktivačních událostí k nastavení stylu vybraných položek v listovém zobrazení](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **Posunutím zobrazíte obsah, který není zpočátku viditelný na obrazovce.**  
  
     Pokud velikost <xref:System.Windows.Controls.GridView> není dostatečně velká pro zobrazení všech položek, uživatelé mohou posouvat vodorovně nebo svisle pomocí posuvníků, které jsou poskytovány ovládacím <xref:System.Windows.Controls.ScrollViewer> prvkem. A <xref:System.Windows.Controls.Primitives.ScrollBar> je skrytý, pokud je veškerý obsah viditelný v určitém směru. Záhlaví sloupců se neposouvají se svislým posuvníkem, ale posouvají se vodorovně.  
  
- **Pracujte se sloupci kliknutím na tlačítka záhlaví sloupce.**  
  
     Když uživatelé kliknou na tlačítko záhlaví sloupce, mohou seřadit data zobrazená ve sloupci, pokud jste poskytli algoritmus řazení.  
  
     <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Událost pro tlačítka záhlaví sloupce můžete zpracovat, abyste mohli poskytovat funkce, jako je algoritmus řazení. Chcete-li <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zpracovat událost pro záhlaví jednoho sloupce, nastavte obslužnou rutinu události na . <xref:System.Windows.Controls.GridViewColumnHeader> Chcete-li nastavit obslužnou rutinu události, která <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zpracovává <xref:System.Windows.Controls.ListView> událost pro všechna záhlaví sloupců, nastavte obslužnou rutinu ovládacího prvku.  
  
<a name="Obtaining_Other_Custom_Views"></a>
## <a name="obtaining-other-custom-views"></a>Získání dalších vlastních zobrazení  
 Třída, <xref:System.Windows.Controls.GridView> která je odvozena <xref:System.Windows.Controls.ViewBase> z abstraktní třídy, je pouze <xref:System.Windows.Controls.ListView> jedním z možných režimů zobrazení pro třídu. Můžete vytvořit další vlastní <xref:System.Windows.Controls.ListView> zobrazení pro odvození <xref:System.Windows.Controls.ViewBase> mj. Příklad vlastního režimu zobrazení naleznete v [tématu Vytvoření vlastního režimu zobrazení pro listview](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>
## <a name="gridview-supporting-classes"></a>GridView Podpůrné třídy  
 Následující třídy <xref:System.Windows.Controls.GridView> podporují režim zobrazení.  
  
- <xref:System.Windows.Controls.GridViewColumn>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GridViewRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewColumnCollection>  
  
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>Viz také

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
