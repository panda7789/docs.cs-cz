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
ms.openlocfilehash: f8e5a7475765bffb76e7b07e81db25b4a62ae038
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703833"
---
# <a name="flow-document-overview"></a>Přehled toku dokumentů
Dokumenty toku jsou určená k optimalizaci pro zobrazení a čitelnost. Dokumenty toku místo nastavování jedno předdefinované rozložení dynamicky upravit a přeformátování jejich obsah na základě proměnných za běhu, jako je například velikost okna, rozlišení zařízení a volitelné uživatelských předvoleb. Kromě toho nabízejí dokumenty toku dokumentu pokročilé funkce, jako je stránkování a sloupce. Toto téma obsahuje přehled toku dokumentů a postupy jejich vytvoření.  

<a name="what_is_a_flow_document"></a>   
## <a name="what-is-a-flow-document"></a>Co je dokument Flow  
 Plovoucí dokument je určen k "přeformátování obsah" v závislosti na velikosti okna, rozlišení zařízení i ostatním proměnným prostředí. Kromě toho mají dokumenty toku počet integrované funkce, včetně vyhledávání, zobrazování režimy, které optimalizují čitelnost a umožňuje změnit velikost a vzhled písma. Dokumenty toku se co nejlépe využít v případě snadné čtení je scénář využití primární dokumentu. Naproti tomu pevné dokumenty by mít statické prezentace. Oprava dokumentů jsou užitečné, pokud je základní přesné zdrojový obsah. Zobrazit [dokumenty v platformě WPF](documents-in-wpf.md) Další informace o různých typů dokumentů.  
  
 Následující obrázek znázorňuje tok ukázkový dokument zobrazit v několika oknech různých velikostí. Jako zobrazovanou oblast změní, obsah přeteče co nejlíp využít volného místa.  
  
 ![Tok obsahu dokumentu s přeskupením](./media/edocs-flowdocument.png "eDocs_FlowDocument")  
  
 Jak je vidět na obrázku výše, plovoucího obsahu může obsahovat mnoho komponent včetně odstavce, seznamy, obrázků a dalších. Tyto součásti odpovídají elementy v kódu a objekty v kódu procedury. Můžeme se přenášejí prostřednictvím těchto tříd podrobně později v [tok související třídy](#flow_related_classes) části tohoto přehledu. Teď tady je příklad jednoduchého kódu, který vytvoří dokument tok skládající se z odstavec s nějaký tučný text a seznam.
  
 [!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]  
  
 Na obrázku níže ukazuje, jak vypadá tento fragment kódu.  
  
 ![Snímek obrazovky: Příklad FlowDocument vykresleného](./media/flow-ovw-first-example.png "Flow_Ovw_First_Example")  
  
 V tomto příkladu <xref:System.Windows.Controls.FlowDocumentReader> ovládací prvek slouží jako hostitel plovoucího obsahu. V tématu [typů dokumentů tok](#flow_document_types) Další informace o hostování ovládacích prvků plovoucího obsahu. <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, a <xref:System.Windows.Documents.Bold> elementy se používají k řízení formátování obsahu na základě jejich pořadí v kódu. Například <xref:System.Windows.Documents.Bold> element zabírá pouze část textu v odstavci; v důsledku toho je tučný pouze část textu. Pokud jste použili HTML, bude povědomé.  
  
 Jak je zdůrazněno na výše uvedeném obrázku jsou integrované do toku dokumenty několik funkcí:
  
- Hledání: Umožňuje uživateli provádět fulltextové vyhledávání celého dokumentu.  
  
- Režim zobrazení: Uživatel může vybrat režim své upřednostňované zobrazení včetně zobrazení (stránka na-time) jednostránkové režimu, dvě--na stránkách (formát čtení adresáře) zobrazení režimu a režimu kontinuálního rolování (neomezené) zobrazení.  Další informace o těchto režimech zobrazení najdete v tématu <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  
  
- Ovládací prvky navigace stránky: Pokud je režim zobrazení dokumentu používá stránky, ovládací prvky navigace stránky zahrnují tlačítka pro přechod na další stránce (šipka dolů) nebo předchozí stránku (na šipku nahoru), stejně jako ukazatele pro aktuální číslo stránky a celkový počet stránek. Překlopení prostřednictvím stránek lze dosáhnout také pomocí šipkových kláves klávesnice.  
  
- Přiblížení: Ovládací prvky zvětšení povolení uživatele chcete zvýšit nebo snížit úroveň přiblížení, kliknutím na znaménko plus nebo mínus, v uvedeném pořadí. Ovládací prvky zvětšení také zahrnovat posuvníku pro úpravu úroveň zvětšení. Další informace naleznete v tématu <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.  
  
 Tyto funkce lze upravit na základě ovládací prvek použitý k hostování plovoucího obsahu. Další část popisuje různé ovládací prvky.  
  
<a name="flow_document_types"></a>   
## <a name="flow-document-types"></a>Typy dokumentů toku  
 Zobrazení obsahu dokumentu toku a jak se zobrazuje je závislá na objekt slouží jako hostitel plovoucího obsahu. Existují čtyři ovládací prvky, které podporují prohlížení plovoucího obsahu: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.RichTextBox>, a <xref:System.Windows.Controls.FlowDocumentScrollViewer>. Tyto ovládací prvky jsou popsány níže.  
  
 **Poznámka:** <xref:System.Windows.Documents.FlowDocument> je potřeba přímo hostitele plovoucího obsahu, tak všechny tyto ovládací prvky zobrazení využití <xref:System.Windows.Documents.FlowDocument> povolit tok obsahu hostování.
  
### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> obsahuje funkce, které uživateli umožňuje dynamicky vybrat mezi různých režimů zobrazení, včetně zobrazení (stránka na-time) jednostránkové režimu, dvě--na stránkách (formát čtení adresáře) zobrazení režimu a režimu kontinuálního rolování (neomezené) zobrazení. Další informace o těchto režimech zobrazení najdete v tématu <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>. Pokud nepotřebujete umožňuje dynamicky přepnout mezi režimy různých zobrazení <xref:System.Windows.Controls.FlowDocumentPageViewer> a <xref:System.Windows.Controls.FlowDocumentScrollViewer> poskytují nenáročný tok prohlížeče obsahu, které jsou opravené v režimu konkrétní zobrazení.  
  
### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>Prohlížeč FlowDocumentPageViewer a prohlížeče FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> Zobrazí obsah stránky v čase režimu zobrazení, zatímco <xref:System.Windows.Controls.FlowDocumentScrollViewer> ukazuje obsahu v režimu kontinuálního rolování. Obě <xref:System.Windows.Controls.FlowDocumentPageViewer> a <xref:System.Windows.Controls.FlowDocumentScrollViewer> jsou pevně režimu konkrétní zobrazení. Porovnat s <xref:System.Windows.Controls.FlowDocumentReader>, který obsahuje funkce, které uživateli umožňuje dynamicky vybrat mezi různé režimy zobrazení (podle <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> výčet), za cenu se náročnější než <xref:System.Windows.Controls.FlowDocumentPageViewer> nebo <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Ve výchozím nastavení je vždy zobrazen svislý posuvník a vodorovný posuvník se zobrazí v případě potřeby. Výchozí uživatelské rozhraní pro <xref:System.Windows.Controls.FlowDocumentScrollViewer> nezahrnuje panel nástrojů, nicméně <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> vlastnost slouží k povolení integrovaných nástrojů.  
  
### <a name="richtextbox"></a>RichTextBox  
 Můžete použít <xref:System.Windows.Controls.RichTextBox> Pokud chcete povolit uživatelům upravit obsah toku. Například Kdybyste chtěli vytvořit editor, který povolené uživatele k manipulaci s věci, jako jsou tabulky, kurzíva a bold formátování a další, můžete využít <xref:System.Windows.Controls.RichTextBox>. Zobrazit [RichTextBox – přehled](../controls/richtextbox-overview.md) Další informace.  
  
 **Poznámka:** Obsah uvnitř toku <xref:System.Windows.Controls.RichTextBox> nechová stejně jako plovoucího obsahu obsažené v jiných ovládacích prvků. Například neexistují žádné sloupce v <xref:System.Windows.Controls.RichTextBox> a proto žádná automatická změna velikosti chování. Kromě toho nejsou k dispozici v rámci obvykle integrovaných funkcí plovoucího obsahu, jako je hledání, zobrazení, navigaci na stránce a přiblížení <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="creating_flow_content"></a>   
## <a name="creating-flow-content"></a>Vytvoření toku obsahu  
 Obsah toku může být složité, který se skládá z různých prvků, včetně text, obrázky, tabulky a dokonce i <xref:System.Windows.UIElement> odvozené třídy jako ovládací prvky. Chcete-li pochopit, jak vytvořit komplexní tok obsahu, jsou důležité následující body:  
  
- **Třídy související s tok**: Každá třída používaná v plovoucího obsahu má konkrétní účel. Kromě toho hierarchický vztah mezi třídami tok vám pomůže porozumět způsobu použití. Například třídy odvozené z <xref:System.Windows.Documents.Block> třída se používá k obsahovat další objekty, zatímco třídy odvozené z <xref:System.Windows.Documents.Inline> obsahují objekty, které jsou zobrazeny.  
  
- **Obsah schématu**: Plovoucí dokument může vyžadovat značné množství vnořené elementy. Schéma obsahu určuje možné nadřazené a podřízené vztahy mezi elementy.  
  
 Následující oddíly půjdou přes všechny tyto oblasti podrobněji.  
  
<a name="flow_related_classes"></a>   
## <a name="flow-related-classes"></a>Tok související třídy  
 Následující diagram znázorňuje objekty nejčastěji používané s plovoucího obsahu:  
  
 ![Diagram: Tok obsahu elementu hierarchie tříd](./media/flow-class-hierarchy.png "Flow_Class_Hierarchy")  
  
 Pro účely obsah toku existují dvě důležité kategorie:  
  
1. **Třídy odvozené bloku**: Také označují jako "Bloku obsahu prvky" nebo jen "bloku prvky". Prvky, které dědí <xref:System.Windows.Documents.Block> lze použít k seskupení elementů pod společným nadřazeným prvkem nebo použít běžné atributy do skupiny.  
  
2. **Třídy odvozené vložené**: Také označují jako "Vloženého obsahu prvky" nebo jen "vložené prvky". Prvky, které dědí <xref:System.Windows.Documents.Inline> jsou buď obsažené v blokovém elementu nebo jiné vloženého elementu. Vložené prvky jsou často používá jako přímé kontejneru obsah, který se zobrazí na obrazovce. Například <xref:System.Windows.Documents.Paragraph> (blokovém elementu) může obsahovat <xref:System.Windows.Documents.Run> (vloženého elementu) ale <xref:System.Windows.Documents.Run> ve skutečnosti obsahuje text, který se vykreslí na obrazovce.  
  
 Každá třída v těchto dvou kategorií jsou popsány níže.  
  
### <a name="block-derived-classes"></a>Blok odvozené třídy  
 **Odstavec**  
  
 <xref:System.Windows.Documents.Paragraph> obvykle slouží k seskupení obsahu do odstavce. Nejjednodušším a nejběžnějším užívání odstavec je vytvoření odstavci textu.  
  
 [!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]  
  
 Jak vidíte níže, ale může obsahovat také další elementy odvozené vložené. 
  
 **Oddíl**  
  
 <xref:System.Windows.Documents.Section> slouží jenom k obsahovat jiné <xref:System.Windows.Documents.Block>-odvozené elementy. Se nevztahují žádné výchozí formátování prvků, které obsahuje. Však hodnoty nastavené na žádné vlastnosti <xref:System.Windows.Documents.Section> se vztahuje na jeho podřízené prvky. Oddíl také umožňuje programově iteraci v rámci její podřízená kolekce. <xref:System.Windows.Documents.Section> se používá podobným způsobem jako do \<DIV > značku ve formátu HTML.  
  
 V následujícím příkladu jsou definovány tři odstavce v rámci jednoho <xref:System.Windows.Documents.Section>. Oddíl má <xref:System.Windows.Documents.TextElement.Background%2A> hodnota vlastnosti červené, tedy barvu pozadí odstavců je také červené.  
  
 [!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]  
  
 **BlockUIContainer**  
  
 <xref:System.Windows.Documents.BlockUIContainer> umožňuje <xref:System.Windows.UIElement> prvky (například <xref:System.Windows.Controls.Button>) má být vložen v bloku odvozené plovoucího obsahu. <xref:System.Windows.Documents.InlineUIContainer> (viz níže) slouží k vložení <xref:System.Windows.UIElement> prvků v odvozených vložené plovoucího obsahu. <xref:System.Windows.Documents.BlockUIContainer> a <xref:System.Windows.Documents.InlineUIContainer> jsou důležité, protože neexistuje žádný způsob použití <xref:System.Windows.UIElement> v toku obsahu, pokud je obsažen v jednom z těchto dvou prvků.  
  
 Následující příklad ukazuje způsob použití <xref:System.Windows.Documents.BlockUIContainer> prvek hostitele <xref:System.Windows.UIElement> objektů v rámci plovoucího obsahu.  
  
 [!code-xaml[SpanSnippets#_BlockUIXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tomto příkladu:  
  
 ![Snímek obrazovky zobrazující prvku UIElement součástí plovoucího obsahu.](./media/flow-document-overview/embedded-blockuicontainer.png)  
  
 **Seznam**  
  
 <xref:System.Windows.Documents.List> slouží k vytvoření seznamu s odrážkami nebo číselné. Nastavte <xref:System.Windows.Documents.List.MarkerStyle%2A> vlastnost <xref:System.Windows.TextMarkerStyle> hodnotu výčtu pro určení stylu ze seznamu. Následující příklad ukazuje, jak vytvořit jednoduchý seznam.  
  
 [!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]  
  
 **Poznámka:** <xref:System.Windows.Documents.List> je jediným prvkem tok, který používá <xref:System.Windows.Documents.ListItemCollection> Spravovat podřízené prvky.  
  
 **Tabulka**  
  
 <xref:System.Windows.Documents.Table> slouží k vytvoření tabulky. <xref:System.Windows.Documents.Table> se podobá <xref:System.Windows.Controls.Grid> element, ale je k dispozici další možnosti a proto vyžaduje větší režijní náklady na prostředek. Protože <xref:System.Windows.Controls.Grid> je <xref:System.Windows.UIElement>, tok obsahu jej nelze použít, pokud je obsažen v <xref:System.Windows.Documents.BlockUIContainer> nebo <xref:System.Windows.Documents.InlineUIContainer>. Další informace o <xref:System.Windows.Documents.Table>, naleznete v tématu [Přehled tabulek](table-overview.md).  
  
### <a name="inline-derived-classes"></a>Vložené odvozené třídy  
 **Spuštění**  
  
 <xref:System.Windows.Documents.Run> slouží jako neformátovaný text. Očekáváte <xref:System.Windows.Documents.Run> objekty pro rozsáhlé v toku obsahu. Ale v kódu <xref:System.Windows.Documents.Run> prvky nejsou musí být použito explicitně. <xref:System.Windows.Documents.Run> je potřeba použít při vytváření nebo manipulace s dokumenty toku pomocí kódu. Například v kódu níže, první <xref:System.Windows.Documents.Paragraph> Určuje <xref:System.Windows.Documents.Run> element explicitně při druhém nikoli. Oba odstavce generovat výstup identické.  
  
 [!code-xaml[FlowOvwSnippets_snip#RunExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]  
  
 **Poznámka:**  Počínaje [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], <xref:System.Windows.Documents.Run.Text%2A> vlastnost <xref:System.Windows.Documents.Run> objekt je vlastnost závislosti. Můžete vytvořit vazbu <xref:System.Windows.Documents.Run.Text%2A> vlastnost datového zdroje, jako <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Documents.Run.Text%2A> Vlastnost plně podporuje jednosměrné vazby. <xref:System.Windows.Documents.Run.Text%2A> Vlastnost také podporuje obousměrnou vazbu, s výjimkou <xref:System.Windows.Controls.RichTextBox>. Příklad naleznete v tématu <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>.  
  
 **značka span**  
  
 <xref:System.Windows.Documents.Span> seskupuje další prvky vloženého obsahu. Žádné vlastní vykreslování platí pro obsah v rámci <xref:System.Windows.Documents.Span> elementu. Ale prvky, které dědí <xref:System.Windows.Documents.Span> včetně <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Italic> a <xref:System.Windows.Documents.Underline> formátování textu.  
  
 Níže je příklad <xref:System.Windows.Documents.Span> používá tak, aby obsahovala vložený obsah, včetně textu, <xref:System.Windows.Documents.Bold> elementu a <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]  
  
 Následující snímek obrazovky ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Vykreslí značky Span příklad](./media/flow-spanexample.gif "Flow_SpanExample")  
  
 **InlineUIContainer**  
  
 <xref:System.Windows.Documents.InlineUIContainer> umožňuje <xref:System.Windows.UIElement> prvky (například ovládací prvek jako <xref:System.Windows.Controls.Button>) mají být vloženy <xref:System.Windows.Documents.Inline> obsahu elementu. Tento element je ekvivalentní vložené <xref:System.Windows.Documents.BlockUIContainer> popsané výše. Tady je příklad, který používá <xref:System.Windows.Documents.InlineUIContainer> k vložení <xref:System.Windows.Controls.Button> vložený v <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]  
  
 **Poznámka:** <xref:System.Windows.Documents.InlineUIContainer> není potřeba explicitně použít v kódu. Pokud vynecháte, <xref:System.Windows.Documents.InlineUIContainer> bude vytvořeno při kompilaci kódu.  
  
 **Obrázek a Floater**  
  
 <xref:System.Windows.Documents.Figure> a <xref:System.Windows.Documents.Floater> slouží k vložení obsahu do dokumentů toku s vlastnosti umístění, které je možné přizpůsobit nezávisle na primární tok obsahu. <xref:System.Windows.Documents.Figure> nebo <xref:System.Windows.Documents.Floater> prvky jsou často používány k zvýrazněte nebo věnované části obsahu k hostiteli podporující obrázky nebo další obsah v rámci hlavní tok obsahu, nebo vkládat volně související obsah, jako jsou oznámení o inzerovaných programech.  
  
 Následující příklad ukazuje postup vložení <xref:System.Windows.Documents.Figure> do textu odstavce.  
  
 [!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]  
  
 Následující obrázek znázorňuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Obrázek příkladu](./media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")  
  
 <xref:System.Windows.Documents.Figure> a <xref:System.Windows.Documents.Floater> se liší v několika způsoby a používají se pro různé scénáře.  
  
 **Obrázek:**  
  
- Může být umístěné: Můžete nastavit jeho vodorovného a svislého kotev vztahů k ukotvení vzhledem ke stránce, obsah, sloupce nebo odstavce. Můžete také použít jeho <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> a <xref:System.Windows.Documents.Figure.VerticalOffset%2A> vlastnosti k určení libovolné pozici.  
  
- Je více než jednomu sloupci proměnlivou velikostí: Můžete nastavit <xref:System.Windows.Documents.Figure> výšku a šířku na násobky stránky, obsah nebo sloupec výšky a šířky. Všimněte si, že v případě stránky a obsahu, násobky větší než 1 nejsou povoleny. Například můžete nastavit šířku <xref:System.Windows.Documents.Figure> "0,5 stránka" nebo "0,25 obsah" nebo "2 sloupci". Můžete také nastavit výšku a šířku na pixel absolutní hodnoty.  
  
- Stránkování není: Pokud je obsah uvnitř <xref:System.Windows.Documents.Figure> nevejde dovnitř <xref:System.Windows.Documents.Figure>, zobrazí se pak přizpůsobit libovolný obsah a dojde ke ztrátě zbývající obsah  
  
 **Floater:**  
  
- Nelze umístit a zobrazí se pak bez ohledu na místo, může být k dispozici pro něj. Nelze nastavit posun nebo ukotvení <xref:System.Windows.Documents.Floater>.  
  
- Nelze mít více než jednomu sloupci velikost: Ve výchozím nastavení <xref:System.Windows.Documents.Floater> velikosti na jeden sloupec. Má <xref:System.Windows.Documents.Floater.Width%2A> vlastnost, která můžete nastavit na hodnotu absolutní pixelů, ale pokud tato hodnota je větší než jeden sloupec šířky je ignorována a floater je nastavena na jeden sloupec. Můžete měnit velikost ho na méně než jeden sloupec tak, že nastavíte šířku správné pixelů, ale nastavení velikosti není relativní ke sloupci, takže "0.5Column" není platný výraz pro <xref:System.Windows.Documents.Floater> šířku. <xref:System.Windows.Documents.Floater> nemá žádnou vlastnost výšku a je nelze nastavit výšku, její výška závisí na obsahu  
  
- <xref:System.Windows.Documents.Floater> stránkuje: Pokud svůj obsah na jeho nastavená šířka rozšiřuje na více než 1 sloupec výšky, floater přestane fungovat a stránkuje do dalšího sloupce, další stránku, atd.  
  
 <xref:System.Windows.Documents.Figure> je vhodné místo pro umístění obsahu samostatný ve které chcete určit velikost a umístění a si jisti, že se obsah vejde v zadané velikosti. <xref:System.Windows.Documents.Floater> je vhodné místo pro další obsah přeuspořádat, na kterém tok podobně jako na hlavní stránce obsah, ale je oddělená od něj.  
  
 **LineBreak**  
  
 <xref:System.Windows.Documents.LineBreak> způsobí, že konec řádku vyskytuje v plovoucího obsahu. Následující příklad ukazuje použití <xref:System.Windows.Documents.LineBreak>.  
  
 [!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]  
  
 Následující snímek obrazovky ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Příklad LineBreak](./media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")  
  
### <a name="flow-collection-elements"></a>Kolekce elementů toku  
 V mnoha příkladech <xref:System.Windows.Documents.BlockCollection> a <xref:System.Windows.Documents.InlineCollection> se používají k vytvoření obsahu toku prostřednictvím kódu programu. Například pro přidání prvků do <xref:System.Windows.Documents.Paragraph>, můžete použít syntaxi:  
  
 `…`  
  
 `myParagraph.Inlines.Add(new Run("Some text"));`  
  
 `…`  
  
 Tím se přidá <xref:System.Windows.Documents.Run> k <xref:System.Windows.Documents.InlineCollection> z <xref:System.Windows.Documents.Paragraph>.  To je stejný jako implicitní <xref:System.Windows.Documents.Run> nalezena uvnitř <xref:System.Windows.Documents.Paragraph> v kódu:  
  
 `…`  
  
 `<Paragraph>`  
  
 `Some Text`  
  
 `</Paragraph>`  
  
 `…`  
  
 Jako příklad použití <xref:System.Windows.Documents.BlockCollection>, následující příklad vytvoří nový <xref:System.Windows.Documents.Section> a použije je **přidat** způsob, jak přidat nové <xref:System.Windows.Documents.Paragraph> k <xref:System.Windows.Documents.Section> obsah.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
 Kromě přidání položky do kolekce flow, můžete odebrat také položky.  Následující příklad odstraní poslední <xref:System.Windows.Documents.Inline> prvek <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Následující příklad odebere veškerý obsah (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
 Při práci s plovoucího obsahu prostřednictvím kódu programu, budete pravděpodobně vytvářet rozsáhlé používání těchto kolekcí.  
  
 Určuje, zda prvek flow používá <xref:System.Windows.Documents.InlineCollection> (Inlines) nebo <xref:System.Windows.Documents.BlockCollection> (bloky) tak, aby obsahovala jeho podřízené prvky závisí na typu podřízených elementů (<xref:System.Windows.Documents.Block> nebo <xref:System.Windows.Documents.Inline>) mohou být obsaženy nadřazenou položkou. Pravidla členství ve skupině pro tok obsahu prvky jsou shrnuté v obsahu schématu v další části.  
  
 **Poznámka:** Je třetí typ kolekce použít s plovoucího obsahu <xref:System.Windows.Documents.ListItemCollection>, ale tato kolekce se používá pouze pro <xref:System.Windows.Documents.List>. Kromě toho existuje několik kolekcí použít s <xref:System.Windows.Documents.Table>. Zobrazit [Přehled tabulek](table-overview.md) Další informace.  
  
<a name="content_schema"></a>   
## <a name="content-schema"></a>Schéma obsahu  
 Získá počet elementů obsahu toku jiné, může být náročné udržovat přehled o jaký typ elementu může obsahovat podřízené elementy. Následující diagram obsahuje souhrn pravidla členství ve skupině pro prvky toku. Šipky představují možné nadřazené a podřízené vztahy.  
  
 ![Diagram: Tok obsahu členství ve skupině schématu](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Jak je vidět v diagramu výše, podřízené položky pro element povolená nejsou určeny nutně, jestli se jedná <xref:System.Windows.Documents.Block> element nebo <xref:System.Windows.Documents.Inline> elementu. Například <xref:System.Windows.Documents.Span> ( <xref:System.Windows.Documents.Inline> element) může mít pouze <xref:System.Windows.Documents.Inline> podřízené prvky při <xref:System.Windows.Documents.Figure> (také <xref:System.Windows.Documents.Inline> element) může mít pouze <xref:System.Windows.Documents.Block> podřízené prvky. Diagram je proto užitečné k rychlému určení toho, který element mohou být obsaženy v jiném. Jako příklad použijeme diagramu a zjistěte, jak vytvořit tok obsahu <xref:System.Windows.Controls.RichTextBox>.  
  
 **1.** A <xref:System.Windows.Controls.RichTextBox> musí obsahovat <xref:System.Windows.Documents.FlowDocument> zase obsahující <xref:System.Windows.Documents.Block>-odvozenému objektu. Níže je odpovídající segment z výše uvedeném diagramu.  
  
 ![Diagram: Pravidla členství ve skupině RichTextBox](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
 Proto pokud je kód může vypadat.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
 **2.** Podle diagramu, existuje několik <xref:System.Windows.Documents.Block> elementy lze vybírat včetně <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, a <xref:System.Windows.Documents.BlockUIContainer> (viz bloku odvozené třídy). Řekněme, že chceme, aby <xref:System.Windows.Documents.Table>. Podle diagramu výše <xref:System.Windows.Documents.Table> obsahuje <xref:System.Windows.Documents.TableRowGroup> obsahující <xref:System.Windows.Documents.TableRow> prvky, které obsahují <xref:System.Windows.Documents.TableCell> prvky, které obsahují <xref:System.Windows.Documents.Block>-odvozenému objektu. Níže je odpovídající segmentu pro <xref:System.Windows.Documents.Table> z výše uvedeném diagramu.  
  
 ![Diagram: Nadřazené&#47;podřízené schématu pro tabulku](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
 Níže je odpovídající značky.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
 **3.** Znovu jeden nebo více <xref:System.Windows.Documents.Block> prvky jsou nutné pod <xref:System.Windows.Documents.TableCell>. Aby byl jednoduchý, Pojďme nějaký text umístíte text do buňky. Můžeme to udělat pomocí <xref:System.Windows.Documents.Paragraph> s <xref:System.Windows.Documents.Run> elementu. Níže je odpovídající segmenty z diagram zobrazující, že <xref:System.Windows.Documents.Paragraph> může trvat <xref:System.Windows.Documents.Inline> elementu a zda <xref:System.Windows.Documents.Run> ( <xref:System.Windows.Documents.Inline> element) jde převzít jenom prostý text.  
  
 ![Diagram: Nadřazené&#47;podřízené schéma pro odstavec](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
 ![Diagram: Nadřazené&#47;podřízené schématu pro spuštění](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Níže je celý příklad v kódu.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="customizing_text"></a>   
## <a name="customizing-text"></a>Přizpůsobení textu  
 Text je obvykle nejrozšířenější typu obsahu v dokumentu toku. Ačkoli objekty zavedené výše lze použít k řízení většinu aspektů způsobu vykreslování textu, existují některé metody pro přizpůsobení textu, který je popsaný v této části.  
  
### <a name="text-decorations"></a>Dekorace textu  
 Dekorace textu umožňují efektů podtržení, přeškrtnutí, Směrný plán a přeškrtnutý text (viz obrázky níže). Tyto dekorace jsou přidány pomocí <xref:System.Windows.Documents.Inline.TextDecorations%2A> vlastnost, která je vystavena podle počtu objektů včetně <xref:System.Windows.Documents.Inline>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.TextBox>.  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> vlastnost <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]  
  
 [!code-csharp[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
 [!code-vb[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Text s efektem přeškrtnutí výchozí](./media/inline-textdec-strike.png "Inline_TextDec_Strike")  
  
 Následující obrázky zobrazit jak **přeškrtnutí**, **směrného plánu**, a **podtržení** dekorace vykreslení.  
  
 ![Snímek obrazovky: Čára nahoře TextDecorator](./media/inline-textdec-over.png "Inline_TextDec_Over")  
  
 ![Snímek obrazovky: Výchozí základní vliv na text](./media/inline-textdec-base.png "Inline_TextDec_Base")  
  
 ![Snímek obrazovky: Text s efektem podtržení výchozí](./media/inline-textdec-under.png "Inline_TextDec_Under")  
  
### <a name="typography"></a>Typografie  
 <xref:System.Windows.Documents.TextElement.Typography%2A> Vlastnost je zveřejněný prostřednictvím většina související tok obsahu včetně <xref:System.Windows.Documents.TextElement>, <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.TextBox>. Tato vlastnost se používá k řízení zkrácené typografické vlastnosti/variace textu (tj malé nebo velké písmena, což horních a dolních indexů atd).  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Documents.TextElement.Typography%2A> atribut, pomocí <xref:System.Windows.Documents.Paragraph> jako příklad elementu.  
  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 Následující obrázek ukazuje, jak se vykreslí v tomto příkladu.  
  
 ![Snímek obrazovky: Text se změněnou typografií](./media/textelement-typog.png "TextElement_Typog")  
  
 Naproti tomu následující obrázek ukazuje, jak se vykreslí podobný příklad s výchozí typografické vlastnosti.  
  
 ![Snímek obrazovky: Text se změněnou typografií](./media/textelement-typog-default.png "TextElement_Typog_Default")  
  
 Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.TextBox.Typography%2A> vlastnost prostřednictvím kódu programu.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
 Zobrazit [Typografie v rozhraní WPF](typography-in-wpf.md) Další informace o typografii.  
  
## <a name="see-also"></a>Viz také:

- [Text](optimizing-performance-text.md)
- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Témata s postupy](flow-content-elements-how-to-topics.md)
- [Přehled modelu obsahu TextElement](textelement-content-model-overview.md)
- [RichTextBox – přehled](../controls/richtextbox-overview.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tabulky](table-overview.md)
- [Přehled poznámek](annotations-overview.md)
