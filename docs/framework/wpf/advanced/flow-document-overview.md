---
title: Přehled toku dokumentů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], flow documents [WPF], , '
- ', '
- flow documents [WPF]
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
ms.openlocfilehash: 0cf8944298af62a512599fc52998a046c66fed9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549734"
---
# <a name="flow-document-overview"></a>Přehled toku dokumentů
Tok dokumenty jsou navrženy pro optimalizaci zobrazení a přehlednosti. Místo je nastavená na jednu předdefinované rozložení, dokumenty toku dynamicky upravit a přeformátování obsah na základě proměnných runtime například volitelné uživatelské předvolby, řešení zařízení a velikost okna. Kromě toho dokumenty toku nabízejí dokumentu pokročilé funkce, jako je stránkování a sloupců. Toto téma obsahuje přehled toku dokumentů a postup jejich vytvoření.  
  

  
<a name="what_is_a_flow_document"></a>   
## <a name="what-is-a-flow-document"></a>Co je toku dokumentu  
 Tok dokumentu je určena pro "přeformátování obsah" v závislosti na velikosti okna, zařízení řešení a jiné proměnné prostředí. Kromě toho mít toku dokumenty počet součástí funkce včetně vyhledávání, zobrazování režimy, které optimalizovat přehlednosti a možnost změny velikosti a vzhled písma. Tok dokumenty jsou nejlépe využít v případě snadnější čtení je tento scénář spotřeby primární dokumentu. Naproti tomu pevné dokumenty určené k statické prezentace. Opravené dokumenty jsou užitečné, pokud je nezbytné, přesnost zdrojový obsah. V tématu [dokumenty v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md) Další informace o různých typů dokumentů.  
  
 Následující obrázek znázorňuje ukázkové toku dokument zobrazit ve windows několik různých velikostí. V oblasti změn ve obsah přeteče co nejlepší využití dostupného místa.  
  
 ![Tok obsahu přeformátování dokumentu](../../../../docs/framework/wpf/advanced/media/edocs-flowdocument.png "eDocs_FlowDocument")  
  
 Jak je vidět na předchozím obrázku, tok obsahu může obsahovat mnoho komponent, jako třeba odstavců, seznamy, obrázky a další. Tyto součásti odpovídají elementů v značek a objekty v procedurální kódu. Jsme budou přenášeny po tyto třídy podrobně později v [toku související třídy](#flow_related_classes) části tohoto přehledu. Nyní tady je příklad jednoduchého kódu, který vytvoří toku dokumentu, který obsahuje odstavců s některé tučně a seznam.
  
 [!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]  
  
 Na obrázku níže ukazuje, jak vypadá tento fragment kódu.  
  
 ![Snímek obrazovky: Příklad FlowDocument vykresleného](../../../../docs/framework/wpf/advanced/media/flow-ovw-first-example.png "Flow_Ovw_First_Example")  
  
 V tomto příkladu <xref:System.Windows.Controls.FlowDocumentReader> řízení se používá k hostování toku obsahu. V tématu [typů dokumentů toku](#flow_document_types) Další informace o toku obsahu hostování ovládacích prvků. <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, a <xref:System.Windows.Documents.Bold> elementy jsou používány k ovládání formátování obsahu, na základě jejich pořadí v kódu. Například <xref:System.Windows.Documents.Bold> element zabírá jenom část textu v odstavci; v důsledku toho je jenom ta část text tučně. Pokud jste použili HTML, bude povědomé.  
  
 Jak je znázorněno na obrázku výše existuje několik funkcí, které jsou součástí toku dokumenty:
  
-   Hledání: Umožňuje uživateli provádět fulltextové vyhledávání celého dokumentu.  
  
-   Zobrazení režim: Uživatel můžete vybrat způsob jejich zobrazení, včetně režimu zobrazení jednostránkové (-na stránkách), dva--na stránkách (formát čtení kniha) zobrazení a průběžné posouvání režimu zobrazení (neomezené).  Další informace o těchto režimech zobrazení najdete v tématu <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  
  
-   Stránka ovládací prvky pro navigaci: Pokud režimu zobrazení dokumentu používá stránky, ovládací prvky pro navigaci na stránce zahrnout tlačítko Přejít na další stránku (na šipku dolů) nebo předchozí stránku (na šipku nahoru), stejně jako ukazatele pro aktuální číslo stránky a celkový počet stránek. Překlopení prostřednictvím stránky lze také provést pomocí klávesy se šipkami klávesnice.  
  
-   Přiblížení: Ovládací prvky přiblížení uživateli zvýšit nebo snížit úroveň přiblížení, kliknutím na znaménko plus nebo minus tlačítka, povolte v uvedeném pořadí. Ovládací prvky přiblížení také zahrnovat jezdce pro nastavení úrovně přiblížení. Další informace naleznete v tématu <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.  
  
 Tyto funkce se dá změnit podle ovládací prvek použitý pro hostování daného obsahu toku. Další část popisuje různé ovládací prvky.  
  
<a name="flow_document_types"></a>   
## <a name="flow-document-types"></a>Tok typů dokumentů.  
 Zobrazení obsahu dokumentu toku a jak se zobrazuje je závislá na jaké objekt se používá k hostování toku obsahu. Existují čtyři ovládací prvky, které podporují zobrazení obsah toku: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.RichTextBox>, a <xref:System.Windows.Controls.FlowDocumentScrollViewer>. Tyto ovládací prvky jsou popsány níže.  
  
 **Poznámka:** <xref:System.Windows.Documents.FlowDocument> je potřeba přímo hostitele toku obsahu, tak využívat všechny tyto ovládací prvky zobrazení <xref:System.Windows.Documents.FlowDocument> povolit toku obsahu hostování.  
  
### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> obsahuje funkce, které uživateli umožňuje dynamicky zvolit různé režimy zobrazení, včetně režimu zobrazení jednostránkové (-na stránkách), dva--na stránkách (formát čtení kniha) zobrazení a průběžné posouvání režimu zobrazení (neomezené). Další informace o těchto režimech zobrazení najdete v tématu <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>. Pokud nepotřebujete schopnost dynamicky přepínání mezi režimy jiné zobrazení, <xref:System.Windows.Controls.FlowDocumentPageViewer> a <xref:System.Windows.Controls.FlowDocumentScrollViewer> poskytují světlejšího váhy toku obsahu prohlížeče, opravené v režimu konkrétní zobrazení.  
  
### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer a třídy FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> Zobrazuje obsah stránky na čas režimu zobrazení při <xref:System.Windows.Controls.FlowDocumentScrollViewer> ukazuje obsahu v průběžném režimu posouvání. Obě <xref:System.Windows.Controls.FlowDocumentPageViewer> a <xref:System.Windows.Controls.FlowDocumentScrollViewer> opravě do režimu konkrétní zobrazení. Porovnání <xref:System.Windows.Controls.FlowDocumentReader>, což zahrnuje funkce, které uživateli umožňuje dynamicky zvolit různé režimy zobrazení (jako poskytované <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> – výčet), za cenu probíhá další náročné než <xref:System.Windows.Controls.FlowDocumentPageViewer> nebo <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Ve výchozím nastavení je vždy zobrazen svislý posuvník a vodorovný posuvník se zobrazí v případě potřeby. Výchozí uživatelské rozhraní pro <xref:System.Windows.Controls.FlowDocumentScrollViewer> nezahrnuje panel nástrojů, nicméně <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> vlastnost slouží k povolení integrované panelu nástrojů.  
  
### <a name="richtextbox"></a>RichTextBox  
 Můžete použít <xref:System.Windows.Controls.RichTextBox> když chcete povolit uživatelům upravit obsah toku. Například pokud jste chtěli vytvořit editor, který povolené uživatele k manipulaci s věcí, jako jsou tabulky, kurzíva nebo bold formátování a podobně, byste použili <xref:System.Windows.Controls.RichTextBox>. V tématu [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md) Další informace.  
  
 **Poznámka:** toku obsahu uvnitř <xref:System.Windows.Controls.RichTextBox> není chovat úplně stejně jako obsah toku, které jsou obsažené v jiných ovládacích prvků. Například neexistují žádné sloupce v <xref:System.Windows.Controls.RichTextBox> a proto žádné Automatická změna velikosti chování. Také nejsou k dispozici v rámci obvykle integrovaných funkcí, tok obsahu, jako je hledání, zobrazení, navigaci na stránce a přiblížení <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="creating_flow_content"></a>   
## <a name="creating-flow-content"></a>Vytváření obsah toku  
 Obsah toku může být složité, který se skládá z různých prvků, včetně text, obrázky, tabulky a to i v <xref:System.Windows.UIElement> odvozených tříd jako ovládací prvky. Abyste pochopili, jak vytvořit komplexní tok obsahu, jsou důležité následující body:  
  
-   **Třídy související s toku**: Každá třída používají v toku obsahu má konkrétní účel. Kromě toho hierarchický vztah mezi třídami toku vám pomůže pochopit, jak se používají. Například třídy odvozené od <xref:System.Windows.Documents.Block> třída se používá k obsahovat jiné objekty, zatímco třídy odvozené od <xref:System.Windows.Documents.Inline> obsahují objekty, které jsou zobrazeny.  
  
-   **Obsah schématu**: dokument toku může vyžadovat značné množství vnořených elementů. Schéma obsahu určuje možné nadřazených a podřízených vztahy mezi elementy.  
  
 V následujících částech se projít tyto oblasti podrobněji.  
  
<a name="flow_related_classes"></a>   
## <a name="flow-related-classes"></a>Tok související třídy  
 Následující diagram ukazuje objekty obvykle používané s toku obsahu:  
  
 ![Diagram: Tok obsahu elementu hierarchie tříd](../../../../docs/framework/wpf/advanced/media/flow-class-hierarchy.png "Flow_Class_Hierarchy")  
  
 Pro účely obsah toku existují dvě důležité kategorie:  
  
1.  **Třídy odvozené bloku**: označovaný taky jako "Obsahu prvků bloku" nebo právě "bloku prvků". Elementy, které dědí od <xref:System.Windows.Documents.Block> lze použít k seskupení prvků pod společným nadřazeným prvkem nebo použít běžné atributy pro skupinu.  
  
2.  **Třídy odvozené vložené**: označovaný taky jako "Vloženého obsahu prvků" nebo jen "vložené prvky". Elementy, které dědí od <xref:System.Windows.Documents.Inline> jsou buď obsažené v blokovém elementu nebo jiné vloženého elementu. Vložené elementy jsou často používá jako přímý kontejneru obsahu, který je vykreslen na obrazovku. Například <xref:System.Windows.Documents.Paragraph> (prvek bloku) může obsahovat <xref:System.Windows.Documents.Run> (vloženého elementu) ale <xref:System.Windows.Documents.Run> ve skutečnosti obsahuje text, který je vykreslen na obrazovce.  
  
 Každá třída v těchto dvou kategorií je popsány níže.  
  
### <a name="block-derived-classes"></a>Třídy odvozené bloku  
 **Odstavce**  
  
 <xref:System.Windows.Documents.Paragraph> se obvykle používá k seskupení obsahu do odstavec. Nejjednodušší a nejběžnější použití odstavce je vytvoření odstavec textu.  
  
 [!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]  
  
 Jak vidíte níže však může obsahovat také další odvozené vložené prvky. 
  
 **Část**  
  
 <xref:System.Windows.Documents.Section> slouží jenom k obsahovat jiné <xref:System.Windows.Documents.Block>-odvozené elementy. Nevztahuje se žádné výchozí formátování na elementy, které obsahuje. Ale libovolné vlastnosti hodnoty sady na <xref:System.Windows.Documents.Section> se vztahuje na jeho podřízené elementy. Oddíl můžete také prostřednictvím kódu programu iteraci v rámci jeho podřízené kolekce. <xref:System.Windows.Documents.Section> slouží k podobným způsobem \<DIV > značky v kódu HTML.  
  
 V následujícím příkladu jsou tři odstavce definované v rámci jednoho <xref:System.Windows.Documents.Section>. V části má <xref:System.Windows.Documents.TextElement.Background%2A> hodnota vlastnosti červené, proto barvu pozadí odstavců je také red.  
  
 [!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]  
  
 **BlockUIContainer**  
  
 <xref:System.Windows.Documents.BlockUIContainer> umožňuje <xref:System.Windows.UIElement> elementy (tj. <xref:System.Windows.Controls.Button>) má být vložen v odvozených bloku toku obsahu. <xref:System.Windows.Documents.InlineUIContainer> (viz níže) slouží k vložení <xref:System.Windows.UIElement> elementy v odvozených vloženého toku obsahu. <xref:System.Windows.Documents.BlockUIContainer> a <xref:System.Windows.Documents.InlineUIContainer> jsou důležité, protože neexistuje jiný způsob, jak používat <xref:System.Windows.UIElement> v toku obsahu, pokud je obsažen v jednom z těchto dvou elementů.  
  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Documents.BlockUIContainer> element hostitele <xref:System.Windows.UIElement> objektů v rámci toku obsahu.  
  
 [!code-xaml[SpanSnippets#_BlockUIXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Vložených prvků uživatelského rozhraní v toku obsahu](../../../../docs/framework/wpf/advanced/media/blockuicontainer.png "BlockUIContainer")  
  
 **seznam**  
  
 <xref:System.Windows.Documents.List> slouží k vytvoření seznamu s odrážkami nebo číselný. Nastavte <xref:System.Windows.Documents.List.MarkerStyle%2A> vlastnosti <xref:System.Windows.TextMarkerStyle> hodnotu výčtu, která určí styl seznamu. Následující příklad ukazuje postup vytvoření jednoduchého seznamu.  
  
 [!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]  
  
 **Poznámka:** <xref:System.Windows.Documents.List> je jediným prvkem toku, který používá <xref:System.Windows.Documents.ListItemCollection> ke správě podřízené elementy.  
  
 **Tabulka**  
  
 <xref:System.Windows.Documents.Table> slouží k vytvoření tabulky. <xref:System.Windows.Documents.Table> je podobná <xref:System.Windows.Controls.Grid> elementu, ale k dispozici další možnosti a proto vyžaduje větší režijní náklady na prostředek. Protože <xref:System.Windows.Controls.Grid> je <xref:System.Windows.UIElement>, v toku obsahu jej nelze použít, pokud je součástí <xref:System.Windows.Documents.BlockUIContainer> nebo <xref:System.Windows.Documents.InlineUIContainer>. Další informace o <xref:System.Windows.Documents.Table>, najdete v části [tabulky přehled](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
### <a name="inline-derived-classes"></a>Vložené odvozené třídy  
 **Spustit**  
  
 <xref:System.Windows.Documents.Run> slouží jako neformátovaný text. By se dalo očekávat <xref:System.Windows.Documents.Run> objekty, které se použije hojně v toku obsahu. Však ve značkách <xref:System.Windows.Documents.Run> elementy nejsou potřeba explicitně použít. <xref:System.Windows.Documents.Run> je potřeba použít při vytváření nebo manipulace s toku dokumenty pomocí kódu. Například v kódu níže první <xref:System.Windows.Documents.Paragraph> Určuje <xref:System.Windows.Documents.Run> element explicitně při druhý není. Oba odstavce generovat výstup identické.  
  
 [!code-xaml[FlowOvwSnippets_snip#RunExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]  
  
 **Poznámka:** počínaje [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], <xref:System.Windows.Documents.Run.Text%2A> vlastnost <xref:System.Windows.Documents.Run> objektu je vlastnost závislosti. Můžete vytvořit vazbu <xref:System.Windows.Documents.Run.Text%2A> vlastnost k data zdroje, například <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Documents.Run.Text%2A> Vlastnost plně podporuje jednosměrné vazby. <xref:System.Windows.Documents.Run.Text%2A> Vlastnost také podporuje vazba obousměrná, s výjimkou <xref:System.Windows.Controls.RichTextBox>. Příklad naleznete v tématu <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>.  
  
 **Značka span**  
  
 <xref:System.Windows.Documents.Span> Další prvky vloženého obsahu skupiny společně. Žádné vyplývajících vykreslování se použije k obsahu v rámci <xref:System.Windows.Documents.Span> elementu. Ale elementy, dědí <xref:System.Windows.Documents.Span> včetně <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Italic> a <xref:System.Windows.Documents.Underline> formátování textu.  
  
 Dole je příklad <xref:System.Windows.Documents.Span> používá tak, aby obsahovala vloženého obsahu včetně textu, <xref:System.Windows.Documents.Bold> elementu a <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]  
  
 Následující snímek obrazovky ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Rozpětí Příklad vykresleného](../../../../docs/framework/wpf/advanced/media/flow-spanexample.gif "Flow_SpanExample")  
  
 **InlineUIContainer**  
  
 <xref:System.Windows.Documents.InlineUIContainer> umožňuje <xref:System.Windows.UIElement> elementy (tj. ovládacího prvku jako <xref:System.Windows.Controls.Button>) má být vložen v <xref:System.Windows.Documents.Inline> obsahu elementu. Tento element je ekvivalentní vložený <xref:System.Windows.Documents.BlockUIContainer> popsané výše. Dole je příklad, který používá <xref:System.Windows.Documents.InlineUIContainer> k vložení <xref:System.Windows.Controls.Button> vložený v <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]  
  
 **Poznámka:** <xref:System.Windows.Documents.InlineUIContainer> nemusí být explicitně používány značek. Pokud vynecháte, <xref:System.Windows.Documents.InlineUIContainer> vytvoří přesto při kompilaci kódu.  
  
 **Obrázek a Floater**  
  
 <xref:System.Windows.Documents.Figure> a <xref:System.Windows.Documents.Floater> slouží k vložení obsahu v dokumentech toku pomocí vlastnosti umístění, které se dají přizpůsobit nezávislé na primární tok obsahu. <xref:System.Windows.Documents.Figure> nebo <xref:System.Windows.Documents.Floater> elementy se často používají k zvýrazněte nebo věnované části obsahu hostitele podpora obrázky nebo další obsah v rámci hlavní tok obsahu, nebo se vložit volně související obsah, jako jsou oznámení o inzerovaném programu.  
  
 Následující příklad ukazuje, jak pro vložení <xref:System.Windows.Documents.Figure> do odstavec textu.  
  
 [!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]  
  
 Následující obrázek znázorňuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Obrázek příkladu](../../../../docs/framework/wpf/advanced/media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")  
  
 <xref:System.Windows.Documents.Figure> a <xref:System.Windows.Documents.Floater> lišit v několika způsoby a používají se pro různé scénáře.  
  
 **Obrázek:**  
  
-   Je možné umístit: můžete nastavit vodorovného a svislého ukotvení pro ukotvení relativně ke stránce, obsah, sloupce nebo odstavce. Můžete také jeho <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> a <xref:System.Windows.Documents.Figure.VerticalOffset%2A> vlastnosti k určení libovolné pozici.  
  
-   Je více než jeden sloupec značné množství: můžete nastavit <xref:System.Windows.Documents.Figure> výšky a šířky na násobky stránky, obsah nebo sloupec výšky a šířky. Všimněte si, že se v případě stránky a obsah, větší než 1 násobků, které nejsou povoleny. Například můžete nastavit šířku <xref:System.Windows.Documents.Figure> "0,5 stránka" nebo "0,25 obsah" nebo "2 sloupci". Můžete také nastavit výšky a šířky pixelů absolutní hodnoty.  
  
-   Není stránkování: Pokud obsah uvnitř <xref:System.Windows.Documents.Figure> nevejde uvnitř <xref:System.Windows.Documents.Figure>, se budou vykreslovat ať obsah dostatek místa, a dojde ke ztrátě zbývající obsah  
  
 **Floater:**  
  
-   Nelze umístit a vykreslí bez ohledu na místo, může být k dispozici pro ni. Nelze nastavit offset nebo ukotvení <xref:System.Windows.Documents.Floater>.  
  
-   Nemůže být dimenzovány pro více než jeden sloupec: ve výchozím nastavení, <xref:System.Windows.Documents.Floater> velikosti na jeden sloupec. Má <xref:System.Windows.Documents.Floater.Width%2A> vlastnost, která můžete nastavit na hodnotu absolutní pixelů, ale pokud je tato hodnota větší než jeden sloupec šířka je ignorována a floater je velikost na jeden sloupec. Můžete jeho velikost na méně než jeden sloupec nastavením šířky správné pixelů, ale nastavení velikosti není sloupec relativní, takže "0.5Column" není platný výraz pro <xref:System.Windows.Documents.Floater> šířku. <xref:System.Windows.Documents.Floater> žádná vlastnost výšky a je výška nelze nastavit, jeho výška závisí na obsahu  
  
-   <xref:System.Windows.Documents.Floater> stránkuje: Pokud jeho obsah v jeho nastavená šířka rozšiřuje na více než 1 sloupce výšky, floater dělí a stránkuje k dalším sloupci další stránku, atd.  
  
 <xref:System.Windows.Documents.Figure> je vhodná k umístění obsahu samostatné místo řídit velikost a umístění a si jisti, že se obsah vejde po zadanou velikost. <xref:System.Windows.Documents.Floater> je vhodná pro umístění další přeuspořádat obsah, který toků podobná obsah hlavní stránky, ale je oddělená od jeho.  
  
 **LineBreak**  
  
 <xref:System.Windows.Documents.LineBreak> způsobí, že dochází k výskytu obsah toku konec řádku. Následující příklad ukazuje použití <xref:System.Windows.Documents.LineBreak>.  
  
 [!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]  
  
 Následující snímek obrazovky ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Příklad LineBreak](../../../../docs/framework/wpf/advanced/media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")  
  
### <a name="flow-collection-elements"></a>Elementy v kolekci toku  
 V mnoha výše, příklady <xref:System.Windows.Documents.BlockCollection> a <xref:System.Windows.Documents.InlineCollection> se používají k vytvoření toku obsahu prostřednictvím kódu programu. Například pro elementy pro přidání <xref:System.Windows.Documents.Paragraph>, můžete použít syntaxi:  
  
 `…`  
  
 `myParagraph.Inlines.Add(new Run("Some text"));`  
  
 `…`  
  
 Tím se přidá <xref:System.Windows.Documents.Run> k <xref:System.Windows.Documents.InlineCollection> z <xref:System.Windows.Documents.Paragraph>.  Je to stejné jako implicitní <xref:System.Windows.Documents.Run> nalezena uvnitř <xref:System.Windows.Documents.Paragraph> v kódu:  
  
 `…`  
  
 `<Paragraph>`  
  
 `Some Text`  
  
 `</Paragraph>`  
  
 `…`  
  
 Jako příklad použití <xref:System.Windows.Documents.BlockCollection>, následující příklad vytvoří novou <xref:System.Windows.Documents.Section> a pak používá **přidat** metoda pro přidání nové <xref:System.Windows.Documents.Paragraph> k <xref:System.Windows.Documents.Section> obsah.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
 Kromě přidání položky do kolekce toku, můžete odebrat také položky.  Následující příklad odstraní poslední <xref:System.Windows.Documents.Inline> element v <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Následující příklad odebere všechny obsahu (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
 Při práci s toku obsahu prostřednictvím kódu programu, budete pravděpodobně vytvářet rozsáhlé používání těchto kolekcí.  
  
 Tom, zda element toku používá <xref:System.Windows.Documents.InlineCollection> (Inlines) nebo <xref:System.Windows.Documents.BlockCollection> (bloky) tak, aby obsahovala jeho podřízených elementů závisí na typu podřízených elementů (<xref:System.Windows.Documents.Block> nebo <xref:System.Windows.Documents.Inline>) může být obsažený ve nadřazený. Pravidla členství ve skupině pro toku obsahu elementy jsou shrnuty v obsahu schématu v další části.  
  
 **Poznámka:** je třetí typ kolekce používané s obsah toku, <xref:System.Windows.Documents.ListItemCollection>, ale tato kolekce je použít jenom s <xref:System.Windows.Documents.List>. Kromě toho existuje několik kolekcí použít s <xref:System.Windows.Documents.Table>. V tématu [tabulky přehled](../../../../docs/framework/wpf/advanced/table-overview.md) Další informace.  
  
<a name="content_schema"></a>   
## <a name="content-schema"></a>Obsahu schématu  
 Získá počet elementů jiný tok obsahu, může být čtenáře k udržování přehledu o jaký typ podřízených elementů element může obsahovat. Následující diagram shrnuje pravidla členství ve skupině pro prvky toku. Šipky představují vztahy možné nadřazený podřízený.  
  
 ![Diagram: Toku obsahu omezení schématu](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow_Content_Schema")  
  
 Jak je vidět v diagramu výše, děti povoleny pro element nejsou určen nutně ať už jde <xref:System.Windows.Documents.Block> element nebo <xref:System.Windows.Documents.Inline> element. Například <xref:System.Windows.Documents.Span> ( <xref:System.Windows.Documents.Inline> element) může mít pouze <xref:System.Windows.Documents.Inline> podřízených elementů při <xref:System.Windows.Documents.Figure> (také <xref:System.Windows.Documents.Inline> element) může mít pouze <xref:System.Windows.Documents.Block> podřízené elementy. Proto je užitečné pro určení rychle, jaký element může být obsažený v jiné diagram. Jako příklad použijeme diagram určit, jak vytvořit tok obsahu <xref:System.Windows.Controls.RichTextBox>.  
  
 **1.** A <xref:System.Windows.Controls.RichTextBox> musí obsahovat <xref:System.Windows.Documents.FlowDocument> zase obsahující <xref:System.Windows.Documents.Block>-odvozené objektu. Níže je odpovídající segmentu z diagramu výše.  
  
 ![Diagram: Pravidla členství ve skupině RichTextBox](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
 Doposud to je, jak může vypadat kód.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
 **2.** Podle diagramu je vidět, existuje několik <xref:System.Windows.Documents.Block> elementy lze vybírat včetně <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, a <xref:System.Windows.Documents.BlockUIContainer> (viz bloku odvozené třídy). Řekněme, že chceme <xref:System.Windows.Documents.Table>. Podle diagramu výše <xref:System.Windows.Documents.Table> obsahuje <xref:System.Windows.Documents.TableRowGroup> obsahující <xref:System.Windows.Documents.TableRow> elementy, které obsahují <xref:System.Windows.Documents.TableCell> elementy, které obsahují <xref:System.Windows.Documents.Block>-odvozené objektu. Níže je odpovídající segmentu pro <xref:System.Windows.Documents.Table> provedených od diagramu výše.  
  
 ![Diagram: Nadřazených&#47;podřízené schématu pro tabulku](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
 Níže je odpovídající značky.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
 **3.** Znovu jeden nebo více <xref:System.Windows.Documents.Block> elementy jsou nutné pod <xref:System.Windows.Documents.TableCell>. Chcete-li jednoduchý, umožňuje umístit text do buňky. Jsme můžete to provést pomocí <xref:System.Windows.Documents.Paragraph> s <xref:System.Windows.Documents.Run> elementu. Níže je odpovídající segmenty z diagram zobrazující, že <xref:System.Windows.Documents.Paragraph> může trvat <xref:System.Windows.Documents.Inline> elementu a který <xref:System.Windows.Documents.Run> ( <xref:System.Windows.Documents.Inline> element) může trvat jenom prostý text.  
  
 ![Diagram: Nadřazených&#47;podřízené schéma pro odstavec](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
 ![Diagram: Nadřazených&#47;podřízené schéma pro spuštění](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Níže je celý příklad v kódu.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="customizing_text"></a>   
## <a name="customizing-text"></a>Přizpůsobení textu  
 Text je obvykle současných převažujících typ obsahu v dokumentu toku. Objekty zavedená výše se dá použít k řízení většinu aspektů způsobu vykreslování textu, existují některé metody pro přizpůsobení textu, která je popsaná v této části.  
  
### <a name="text-decorations"></a>Textové dekorace  
 Textové dekorace umožňují použije efekty podtržení, čára nahoře, základní a přeškrtnutí text (viz obrázky níže). Tyto dekorace jsou přidány, pomocí <xref:System.Windows.Documents.Inline.TextDecorations%2A> vlastnosti, který je zveřejněný prostřednictvím počet objektů včetně <xref:System.Windows.Documents.Inline>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.TextBox>.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> vlastnost <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]  
  
 [!code-csharp[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
 [!code-vb[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Text s výchozí přeškrtnutí efekt](../../../../docs/framework/wpf/advanced/media/inline-textdec-strike.png "Inline_TextDec_Strike")  
  
 Následující obrázky zobrazit jak **čára nahoře**, **směrného plánu**, a **Underline** dekorace vykreslení.  
  
 ![Snímek obrazovky: Čára nahoře Objekt TextDecorator jako](../../../../docs/framework/wpf/advanced/media/inline-textdec-over.png "Inline_TextDec_Over")  
  
 ![Snímek obrazovky: Výchozí základní vliv na text](../../../../docs/framework/wpf/advanced/media/inline-textdec-base.png "Inline_TextDec_Base")  
  
 ![Snímek obrazovky: Text s výchozí podtržení efekt](../../../../docs/framework/wpf/advanced/media/inline-textdec-under.png "Inline_TextDec_Under")  
  
### <a name="typography"></a>Typografie  
 <xref:System.Windows.Documents.TextElement.Typography%2A> Vlastnost je zveřejněný prostřednictvím většina související toku obsahu včetně <xref:System.Windows.Documents.TextElement>, <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.TextBox>. Tato vlastnost se používá k řízení typografických charakteristiky/variace textu (tj malý nebo velký písmena, což horní a dolní indexy atd).  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Documents.TextElement.Typography%2A> atribut, pomocí <xref:System.Windows.Documents.Paragraph> jako příklad elementu.  
  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Text s změněna typografii](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")  
  
 Naproti tomu následující obrázek ukazuje, jak vykreslí podobný příklad s typografických výchozí vlastnosti.  
  
 ![Snímek obrazovky: Text s změněna typografii](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.TextBox.Typography%2A> vlastnost prostřednictvím kódu programu.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
 V tématu [typografii v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md) Další informace o typografie.  
  
## <a name="see-also"></a>Viz také  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Typografie v rozhraní WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Témata s postupy](../../../../docs/framework/wpf/advanced/flow-content-elements-how-to-topics.md)  
 [Přehled modelu obsahu TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md)  
 [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Přehled tabulky](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [Přehled poznámek](../../../../docs/framework/wpf/advanced/annotations-overview.md)
