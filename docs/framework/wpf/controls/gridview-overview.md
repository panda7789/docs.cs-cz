---
title: GridView – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 6da556296679de1161f609a7731c6fbf14e94730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966470"
---
# <a name="gridview-overview"></a>GridView – přehled
<xref:System.Windows.Controls.GridView>režim zobrazení je jedním ze způsobů <xref:System.Windows.Controls.ListView> zobrazení ovládacího prvku. <xref:System.Windows.Controls.GridView> Třída a její podpůrné třídy vám a vašim uživatelům umožní zobrazit kolekce položek v tabulce, která obvykle používá tlačítka jako interaktivní záhlaví sloupců. Toto téma představuje <xref:System.Windows.Controls.GridView> třídu a popisuje její použití.  

<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>Co je zobrazení GridView?  
 Režim <xref:System.Windows.Controls.GridView> zobrazení zobrazuje seznam datových položek, protože datová pole jsou svázána se sloupci a zobrazením záhlaví sloupce pro identifikaci pole. Výchozí <xref:System.Windows.Controls.GridView> styl implementuje tlačítka jako záhlaví sloupců. Pomocí tlačítek pro záhlaví sloupců můžete implementovat důležité možnosti pro interakci s uživateli. Například uživatelé mohou kliknutím na záhlaví sloupce řadit <xref:System.Windows.Controls.GridView> data podle obsahu určitého sloupce.  
  
> [!NOTE]
> Ovládací prvky tlačítek, <xref:System.Windows.Controls.GridView> které jsou používány pro záhlaví sloupců, <xref:System.Windows.Controls.Primitives.ButtonBase>jsou odvozeny z.  
  
 Následující obrázek znázorňuje <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView> zobrazení obsahu.  
    
 ![Snímek obrazovky zobrazující zobrazení prvku ListView obsahu ListView](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>sloupce jsou reprezentovány <xref:System.Windows.Controls.GridViewColumn> objekty, které se mohou automaticky měnit podle jejich obsahu. Volitelně můžete explicitně nastavit <xref:System.Windows.Controls.GridViewColumn> na určitou šířku. Sloupce můžete změnit přetažením úchytu mezi záhlaví sloupců. Sloupce můžete také dynamicky přidávat, odebírat, nahrazovat a měnit jejich pořadí, protože tato funkce je integrovaná <xref:System.Windows.Controls.GridView>. Data, <xref:System.Windows.Controls.GridView> která se zobrazí, ale nelze přímo aktualizovat.  
  
 Následující příklad ukazuje, jak definovat, který <xref:System.Windows.Controls.GridView> zobrazuje údaje o zaměstnancích. V tomto příkladu <xref:System.Windows.Controls.ListView> `EmployeeInfoDataSource` definuje jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Definice <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vlastností obsahu vazby <xref:System.Windows.Controls.GridViewColumn> k `EmployeeInfoDataSource` kategoriím dat  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Následující ilustrace znázorňuje tabulku, kterou předchozí příklad vytvoří. Ovládací prvek GridView zobrazuje data z objektu ItemsSource:
    
 ![Snímek obrazovky zobrazující zobrazení ListView s výstupem prvku GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>Rozložení a styl prvku GridView  
 Buňky sloupce a záhlaví <xref:System.Windows.Controls.GridViewColumn> sloupce mají stejnou šířku. Ve výchozím nastavení každý sloupec má šířku velikosti podle jeho obsahu. Volitelně můžete nastavit sloupec na pevnou šířku.  
  
 Obsah souvisejícího data se zobrazí ve vodorovném řádku. Například na předchozím obrázku se jméno a příjmení každého zaměstnance zobrazí jako sada, protože se zobrazují na vodorovném řádku.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>Definování a stylování sloupců v prvku GridView  
 Při definování pole <xref:System.Windows.Controls.GridViewColumn>data pro zobrazení v <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>použijte vlastnosti, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>nebo <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> . <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Vlastnost má přednost před kteroukoli z vlastností šablony.  
  
 Chcete-li určit zarovnání obsahu ve sloupci <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>definujte. Nepoužívejte <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> vlastnosti a <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> pro <xref:System.Windows.Controls.ListView> obsah, který je zobrazen pomocí <xref:System.Windows.Controls.GridView>.  
  
 Chcete-li určit vlastnosti šablony a stylu pro záhlaví sloupců, <xref:System.Windows.Controls.GridView>použijte <xref:System.Windows.Controls.GridViewColumn>třídy, <xref:System.Windows.Controls.GridViewColumnHeader> a. Další informace naleznete v tématu [Přehled stylů a šablon záhlaví sloupců GridView](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>Přidání vizuálních prvků do prvku GridView.  
 Chcete-li přidat vizuální prvky, <xref:System.Windows.Controls.CheckBox> jako <xref:System.Windows.Controls.Button> například a ovládací prvky <xref:System.Windows.Controls.GridView> , do režimu zobrazení, použijte šablony nebo styly.  
  
 Pokud jste prvek vizuálu definovali explicitně jako datovou položku, může se objevit pouze jednou v <xref:System.Windows.Controls.GridView>. Toto omezení existuje, protože element může mít pouze jeden nadřazený prvek, a proto může být ve vizuálním stromu použit pouze jednou.  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>Stylování řádků v prvku GridView  
 Použijte třídy <xref:System.Windows.Controls.GridViewHeaderRowPresenter> <xref:System.Windows.Controls.GridView>a k naformátování a zobrazení řádků. <xref:System.Windows.Controls.GridViewRowPresenter> Příklad, jak stylovat řádky v <xref:System.Windows.Controls.GridView> režimu zobrazení, naleznete v tématu [Style a Row in objektu ListView, který implementuje prvek GridView](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Problémy s zarovnáním při použití ItemContainerStyle  
 Chcete-li zabránit problémům se zarovnáním mezi záhlavími sloupců a buňkami, nenastavujte vlastnost ani Neurčovat šablonu, která má vliv na šířku <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>položky v. <xref:System.Windows.FrameworkElement.Margin%2A> Například nenastavte vlastnost nebo <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.ControlTemplate> Zadejte<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> , která přidá do, který je definován v ovládacím prvku. Místo toho zadejte vlastnosti a šablony, které mají vliv na šířku sloupce přímo na třídy, <xref:System.Windows.Controls.GridView> které definují režim zobrazení.  
  
 Například chcete- <xref:System.Windows.Controls.CheckBox> li přidat do řádků v <xref:System.Windows.Controls.GridView> režimu <xref:System.Windows.Controls.CheckBox> zobrazení <xref:System.Windows.DataTemplate>, přidejte do a a pak nastavte <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> vlastnost na <xref:System.Windows.DataTemplate>hodnotu.  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>Interakce uživatele s GridView  
 Při použití <xref:System.Windows.Controls.GridView> v aplikaci mohou uživatelé pracovat s formátováním <xref:System.Windows.Controls.GridView>a upravovat je. Uživatelé mohou například měnit uspořádání sloupců, změnit velikost sloupce, vybrat položky v tabulce a procházet obsah. Můžete také definovat obslužnou rutinu události, která reaguje, když uživatel klikne na tlačítko záhlaví sloupce. Obslužná rutina události může provádět operace, jako je řazení dat zobrazených v <xref:System.Windows.Controls.GridView> závislosti na obsahu sloupce.  
  
 Následující seznam podrobněji popisuje možnosti použití <xref:System.Windows.Controls.GridView> pro interakci s uživatelem:  
  
- **Změna pořadí sloupců pomocí metody přetažení.**  
  
     Uživatelé mohou změnit uspořádání sloupců <xref:System.Windows.Controls.GridView> kliknutím levým tlačítkem myši na záhlaví sloupce a přetažením tohoto sloupce na novou pozici. Když uživatel přetáhne záhlaví sloupce, zobrazí se plovoucí verze záhlaví a také plná černá čára, která ukazuje, kde vložit sloupec.  
  
     Pokud chcete upravit výchozí styl pro plovoucí <xref:System.Windows.Controls.ControlTemplate> verzi hlavičky, zadejte <xref:System.Windows.Controls.GridViewColumnHeader> pro typ, který <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> se aktivuje, když je vlastnost nastavena na <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>. Další informace naleznete v tématu [vytvoření stylu pro přetažené záhlaví sloupce GridView](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **Změňte velikost sloupce na jeho obsah.**  
  
     Uživatelé mohou dvakrát kliknout na úchyt napravo od záhlaví sloupce, aby bylo možné změnit velikost sloupce tak, aby odpovídal jeho obsahu.  
  
    > [!NOTE]
    > <xref:System.Windows.Controls.GridViewColumn.Width%2A> Vlastnost můžete nastavit na `Double.NaN` , aby vytvořila stejný efekt.  
  
- **Vyberte položky řádku.**  
  
     Uživatelé mohou vybrat jednu nebo více položek v <xref:System.Windows.Controls.GridView>.  
  
     Pokud chcete změnit <xref:System.Windows.Style> vybranou položku, přečtěte si téma [použití triggerů k výběru stylu vybraných položek v zobrazení ListView](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **Posuňte zobrazení obsahu, který není na obrazovce původně viditelný.**  
  
     Pokud velikost <xref:System.Windows.Controls.GridView> není dostatečně velká pro zobrazení všech položek, mohou uživatelé posouvat vodorovně nebo svisle pomocí posuvníků, které jsou poskytovány <xref:System.Windows.Controls.ScrollViewer> ovládacím prvkem. A <xref:System.Windows.Controls.Primitives.ScrollBar> je skrytý, pokud se veškerý obsah zobrazuje v určitém směru. Záhlaví sloupců se neposouvá se svislým posuvníkem, ale posuňte se vodorovně.  
  
- **Chcete-li pracovat se sloupci, klikněte na tlačítko záhlaví sloupce.**  
  
     Když uživatel klikne na tlačítko záhlaví sloupce, může seřadit data zobrazená ve sloupci, pokud jste zadali algoritmus řazení.  
  
     <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Událost pro tlačítka záhlaví sloupců můžete zpracovat tak, aby poskytovala funkce jako algoritmus řazení. Chcete-li <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zpracovat událost pro záhlaví s jedním sloupcem, nastavte obslužnou rutinu <xref:System.Windows.Controls.GridViewColumnHeader>události v. Chcete-li nastavit obslužnou rutinu události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> , která zpracovává událost pro všechna záhlaví sloupců, nastavte obslužnou <xref:System.Windows.Controls.ListView> rutinu ovládacího prvku.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>Získání dalších vlastních zobrazení  
 Třída, která je odvozena <xref:System.Windows.Controls.ViewBase> z abstraktní třídy, je pouze jedním z <xref:System.Windows.Controls.ListView> možných režimů zobrazení pro třídu. <xref:System.Windows.Controls.GridView> Můžete vytvořit další vlastní zobrazení pro <xref:System.Windows.Controls.ListView> odvozením <xref:System.Windows.Controls.ViewBase> z třídy. Příklad vlastního režimu zobrazení najdete v tématu [Vytvoření vlastního režimu zobrazení pro ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>Třídy podpory GridView  
 Následující třídy podporují <xref:System.Windows.Controls.GridView> režim zobrazení.  
  
- <xref:System.Windows.Controls.GridViewColumn>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GridViewRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewColumnCollection>  
  
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
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
