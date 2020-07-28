---
title: Přehled toku dokumentů
description: Přečtěte si o službě Flow Documents in Windows Presentation Foundation, které dynamicky upravují obsah v závislosti na velikosti okna, rozlišení zařízení a uživatelských preferencích.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], flow documents [WPF], , '
- ', '
- flow documents [WPF]
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
ms.openlocfilehash: dac0cb91175a1398a0124020c048e14d7bcd1f76
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165237"
---
# <a name="flow-document-overview"></a>Přehled toku dokumentů

Dokumenty Flow jsou navržené k optimalizaci zobrazení a čitelnosti. Místo toho, aby se nastavily na jedno předdefinované rozložení, dokumenty Flow dynamicky upravují a přenášejí svůj obsah na základě proměnných run-time, jako je velikost okna, rozlišení zařízení a volitelné předvolby uživatele. Kromě toho dokumenty Flow nabízí pokročilé funkce dokumentů, jako jsou stránkování a sloupce. V tomto tématu najdete přehled dokumentů Flow a jejich vytváření.

<a name="what_is_a_flow_document"></a>

## <a name="what-is-a-flow-document"></a>Co je Flowový dokument

Dokument flow je navržený tak, aby "přetekl obsah" v závislosti na velikosti okna, rozlišení zařízení a dalších proměnných prostředí. Kromě toho mají dokumenty Flow řadu integrovaných funkcí, včetně vyhledávání, zobrazení režimů, které optimalizují čitelnost, a možnosti měnit velikost a vzhled písem. Dokumenty Flow se nejlépe využívají v případě, že je snadné přečíst scénář použití primárního dokumentu. Na rozdíl od jsou pevné dokumenty navržené tak, aby měly statickou prezentaci. Pevné dokumenty jsou užitečné v případě, že je důležitá přesnost zdrojového obsahu. Další informace o různých typech dokumentů naleznete [v tématu dokumenty v WPF](documents-in-wpf.md) .

Následující obrázek znázorňuje vzorový dokument s ukázkovým tokem zobrazený v několika oknech různých velikostí. Po změně oblasti zobrazení se obsah přesměruje, aby se zajistilo optimální využití dostupného místa.

![Přetékání obsahu dokumentu toku](./media/edocs-flowdocument.png "eDocs_FlowDocument")

Jak je vidět na obrázku výše, může obsah toku zahrnovat mnoho součástí, včetně odstavců, seznamů, obrázků a dalších. Tyto komponenty odpovídají prvkům ve značkách a objektech v procedurálním kódu. Podrobněji na těchto třídách se dozvíte později v části [související třídy toku](#flow_related_classes) tohoto přehledu. Prozatím je zde příklad jednoduchého příkladu kódu, který vytvoří flowový dokument skládající se z odstavce s nějakým tučným textem a seznamem.

[!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]

Následující obrázek ukazuje, jak tento fragment kódu vypadá.

![Snímek obrazovky: příklad vykresleného FlowDocumentu](./media/flow-ovw-first-example.png "Flow_Ovw_First_Example")

V tomto příkladu se <xref:System.Windows.Controls.FlowDocumentReader> ovládací prvek používá pro hostování obsahu toku. Další informace o ovládacích prvcích hostování obsahu toku naleznete v tématu [typy dokumentů Flow](#flow_document_types) . <xref:System.Windows.Documents.Paragraph>prvky,, <xref:System.Windows.Documents.List> <xref:System.Windows.Documents.ListItem> a <xref:System.Windows.Documents.Bold> se používají k řízení formátování obsahu na základě jejich pořadí v označení. Například <xref:System.Windows.Documents.Bold> element pokrývá pouze část textu v odstavci. v důsledku toho je pouze tato část textu tučně. Pokud jste používali HTML, bude pro vás tato aplikace znát.

Jak je zvýrazněno na ilustraci výše, je k dispozici několik funkcí, které jsou integrované do dokumentů Flow:

- Hledání: umožňuje uživateli provádět fulltextové vyhledávání celého dokumentu.

- Režim zobrazení: uživatel může vybrat upřednostňovaný režim zobrazení, včetně jedné stránky (při zobrazení stránky v čase), režimu zobrazení na dvě stránky (formát pro čtení knih) a režimu průběžného posouvání (bez dolního okraje).  Další informace o těchto režimech zobrazení naleznete v tématu <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> .

- Ovládací prvky navigace stránky: Pokud režim zobrazení dokumentu používá stránky, ovládací prvky pro navigaci na stránce obsahují tlačítko pro přechod na další stránku (šipku dolů) nebo na předchozí stránku (šipka nahoru) a také indikátory pro aktuální číslo stránky a celkový počet stránek. Převrácení stránek lze provést také pomocí kláves se šipkami na klávesnici.

- Zoom: ovládací prvky přiblížení umožňují uživateli zvětšit nebo zmenšit úroveň přiblížení kliknutím na tlačítko plus nebo mínus v uvedeném pořadí. Ovládací prvky přiblížení také obsahují posuvník pro úpravu úrovně přiblížení. Další informace naleznete v tématu <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.

Tyto funkce lze upravit na základě ovládacího prvku používaného pro hostování obsahu toku. V další části jsou popsány různé ovládací prvky.

<a name="flow_document_types"></a>

## <a name="flow-document-types"></a>Typy dokumentů toku

Zobrazení obsahu dokumentu toku a jeho zobrazení závisí na tom, k čemu je objekt použit k hostování obsahu toku. Existují čtyři ovládací prvky, které podporují zobrazení obsahu toku: <xref:System.Windows.Controls.FlowDocumentReader> , <xref:System.Windows.Controls.FlowDocumentPageViewer> , <xref:System.Windows.Controls.RichTextBox> a <xref:System.Windows.Controls.FlowDocumentScrollViewer> . Tyto ovládací prvky jsou stručně popsány níže.

> [!NOTE]
> <xref:System.Windows.Documents.FlowDocument>je vyžadován pro přímé hostování obsahu toku, takže všechny tyto ovládací prvky pro zobrazení využívají <xref:System.Windows.Documents.FlowDocument> k povolení hostování obsahu toku.

### <a name="flowdocumentreader"></a>FlowDocumentReader

<xref:System.Windows.Controls.FlowDocumentReader>obsahuje funkce, které umožňují uživateli dynamicky volit mezi různými režimy zobrazení, včetně jednostránkového režimu zobrazení stránky v čase (Page-on-time), režimu zobrazení na dvě stránky (formát pro čtení knih) a nepřetržitého režimu posouvání (bez dolního okraje). Další informace o těchto režimech zobrazení naleznete v tématu <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> . Pokud nepotřebujete, aby bylo možné dynamicky přepínat mezi různými režimy zobrazení, <xref:System.Windows.Controls.FlowDocumentPageViewer> a <xref:System.Windows.Controls.FlowDocumentScrollViewer> zajistit, aby mohli uživatelé s neproporcionálním tokem obsahu v určitém režimu zobrazení.

### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>Prohlížeč FlowDocumentPageViewer a FlowDocumentScrollViewer

<xref:System.Windows.Controls.FlowDocumentPageViewer>zobrazuje obsah v režimu zobrazení stránky v čase, zatímco <xref:System.Windows.Controls.FlowDocumentScrollViewer> zobrazuje obsah v režimu nepřetržitého posouvání. <xref:System.Windows.Controls.FlowDocumentPageViewer>A <xref:System.Windows.Controls.FlowDocumentScrollViewer> jsou vyřešeny v určitém režimu zobrazení. Porovnejte s <xref:System.Windows.Controls.FlowDocumentReader> , což zahrnuje funkce, které umožňují uživateli dynamicky volit mezi různými režimy zobrazení (poskytované <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> výčtem), a to za cenu většího množství prostředků než <xref:System.Windows.Controls.FlowDocumentPageViewer> nebo <xref:System.Windows.Controls.FlowDocumentScrollViewer> .

Ve výchozím nastavení je vždy zobrazen svislý posuvník a v případě potřeby bude vodorovný posuvník viditelný. Výchozí uživatelské rozhraní pro <xref:System.Windows.Controls.FlowDocumentScrollViewer> neobsahuje panel nástrojů. <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> vlastnost však lze použít k povolení integrovaného panelu nástrojů.

### <a name="richtextbox"></a>RichTextBox

Použijete, <xref:System.Windows.Controls.RichTextBox> Pokud chcete, aby uživatel mohl upravovat obsah toku. Pokud byste například chtěli vytvořit editor, který uživateli povolil manipulaci s například tabulkami, kurzívou a formátováním tučného textu atd., použijete <xref:System.Windows.Controls.RichTextBox> . Další informace najdete v tématu [RichTextBox Overview](../controls/richtextbox-overview.md) .

> [!NOTE]
> Obsah toku uvnitř a <xref:System.Windows.Controls.RichTextBox> se chová stejně jako obsah toku obsažený v jiných ovládacích prvcích. Například neexistují žádné sloupce v typu <xref:System.Windows.Controls.RichTextBox> , a proto žádné chování při automatické změně velikosti. V nástroji nejsou k dispozici také obvykle integrované funkce obsahu toku, jako je hledání, režim zobrazení, navigace na stránce a přiblížení <xref:System.Windows.Controls.RichTextBox> .

<a name="creating_flow_content"></a>

## <a name="creating-flow-content"></a>Vytváření obsahu toku

Obsah toku může být složitý, tvořený různými prvky, včetně textu, obrázků, tabulek a dokonce i <xref:System.Windows.UIElement> odvozených tříd, jako jsou ovládací prvky. Pro pochopení, jak vytvořit složitý obsah toku, jsou důležité následující body:

- **Třídy související s tokem**: Každá třída použitá v obsahu toku má konkrétní účel. Kromě toho hierarchické vztahy mezi třídami Flow pomáhají pochopit, jak se používají. Například třídy, které jsou odvozeny z <xref:System.Windows.Documents.Block> třídy, se používají k zahrnutí jiných objektů, zatímco třídy odvozené z <xref:System.Windows.Documents.Inline> obsahují objekty, které jsou zobrazeny.

- **Schéma obsahu**: dokument toku může vyžadovat podstatný počet vnořených prvků. Schéma obsahu určuje možné vztahy nadřazený-podřízený mezi prvky.

V následujících částech se podrobněji přecházejí na každou z těchto oblastí.

<a name="flow_related_classes"></a>

## <a name="flow-related-classes"></a>Třídy související s tokem

Následující obrázek znázorňuje objekty, které se obvykle používají s obsahem toku:

![Diagram: hierarchie tříd prvků obsahu toku](./media/flow-class-hierarchy.png "Flow_Class_Hierarchy")

Pro účely toku obsahu jsou k dispozici dvě důležité kategorie:

1. **Třídy odvozené od bloku**: označuje se také jako "blok obsahu prvky" nebo pouze "blokové elementy". Prvky, které dědí z <xref:System.Windows.Documents.Block> , lze použít k seskupení prvků v rámci společného nadřazeného objektu nebo pro použití běžných atributů pro skupinu.

2. **Vložené – odvozené třídy**: označují se také jako vložené prvky obsahu nebo pouze vložené prvky. Prvky, které dědí z <xref:System.Windows.Documents.Inline> , jsou buď obsaženy v rámci elementu bloku nebo jiného vloženého prvku. Vložené prvky jsou často používány jako přímý kontejner obsahu, který je vykreslen na obrazovku. Například <xref:System.Windows.Documents.Paragraph> element (Block element) může obsahovat <xref:System.Windows.Documents.Run> (vložený element) <xref:System.Windows.Documents.Run> , ale ve skutečnosti obsahuje text, který je vykreslen na obrazovce.

Každá třída v těchto dvou kategoriích je stručně popsána níže.

### <a name="block-derived-classes"></a>Třídy odvozené od bloku

**Odstavec**

<xref:System.Windows.Documents.Paragraph>se obvykle používá k seskupení obsahu do odstavce. Nejjednodušší a nejběžnější použití odstavce je vytvoření odstavce textu.

[!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]

Můžete však také obsahovat další prvky odvozené od sebe, které jsou uvedeny níže.

**Sekce**

<xref:System.Windows.Documents.Section>slouží pouze k zahrnutí jiných <xref:System.Windows.Documents.Block> odvozených elementů. Neaplikuje žádné výchozí formátování na prvky, které obsahuje. Nicméně jakékoli hodnoty vlastností nastavené u <xref:System.Windows.Documents.Section> objektu se vztahují na jeho podřízené prvky. Oddíl také umožňuje programově iterovat prostřednictvím své podřízené kolekce. <xref:System.Windows.Documents.Section>se používá podobným způsobem jako \<DIV> značka v HTML.

V následujícím příkladu jsou definovány tři odstavce v jednom z nich <xref:System.Windows.Documents.Section> . Oddíl má <xref:System.Windows.Documents.TextElement.Background%2A> hodnotu vlastnosti Red, takže barva pozadí odstavců je také červená.

[!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]

**BlockUIContainer**

<xref:System.Windows.Documents.BlockUIContainer>povoluje <xref:System.Windows.UIElement> vložení prvků (tj. a <xref:System.Windows.Controls.Button> ) do obsahu toku odvozeného z bloku. <xref:System.Windows.Documents.InlineUIContainer>(viz níže) slouží k vložení <xref:System.Windows.UIElement> prvků do vloženého obsahu toku odvozeného. <xref:System.Windows.Documents.BlockUIContainer>a <xref:System.Windows.Documents.InlineUIContainer> jsou důležité, protože neexistuje žádný jiný způsob, jak použít <xref:System.Windows.UIElement> obsah v toku, pokud není obsažený v jednom z těchto dvou prvků.

Následující příklad ukazuje, jak použít <xref:System.Windows.Documents.BlockUIContainer> element k hostování <xref:System.Windows.UIElement> objektů v rámci obsahu toku.

[!code-xaml[SpanSnippets#_BlockUIXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]

Následující obrázek ukazuje, jak tento příklad vykresluje:

![Snímek obrazovky, který zobrazuje prvek UIElement vložený v obsahu toku.](./media/flow-document-overview/embedded-blockuicontainer.png)

**Seznam**

<xref:System.Windows.Documents.List>slouží k vytvoření seznamu s odrážkami nebo číselného seznamu. Nastavte <xref:System.Windows.Documents.List.MarkerStyle%2A> vlastnost na <xref:System.Windows.TextMarkerStyle> hodnotu výčtu pro určení stylu seznamu. Následující příklad ukazuje, jak vytvořit jednoduchý seznam.

[!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.List>je jediným prvkem toku, který používá <xref:System.Windows.Documents.ListItemCollection> ke správě podřízených elementů.

**Tabulka**

<xref:System.Windows.Documents.Table>slouží k vytvoření tabulky. <xref:System.Windows.Documents.Table>je podobný elementu, <xref:System.Windows.Controls.Grid> ale má více možností, a proto vyžaduje větší nároky na prostředky. Protože <xref:System.Windows.Controls.Grid> je <xref:System.Windows.UIElement> , nelze jej použít v obsahu toku, pokud není obsažen v <xref:System.Windows.Documents.BlockUIContainer> nebo <xref:System.Windows.Documents.InlineUIContainer> . Další informace o <xref:System.Windows.Documents.Table> najdete v tématu [Přehled tabulek](table-overview.md).

### <a name="inline-derived-classes"></a>Vložené – odvozené třídy

**Spouštěl**

<xref:System.Windows.Documents.Run>slouží k zahrnutí neformátovaného textu. Můžete očekávat, že se <xref:System.Windows.Documents.Run> objekty budou v obsahu toku používat rozsáhle. Nicméně v označení, <xref:System.Windows.Documents.Run> prvky není nutné použít explicitně. <xref:System.Windows.Documents.Run>je nutné použít při vytváření nebo manipulaci s dokumenty toku pomocí kódu. Například v následujícím kódu <xref:System.Windows.Documents.Paragraph> Určuje první <xref:System.Windows.Documents.Run> prvek explicitně, zatímco druhý nikoli. Oba odstavce generují identický výstup.

[!code-xaml[FlowOvwSnippets_snip#RunExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]

> [!NOTE]
> Počínaje .NET Framework 4 <xref:System.Windows.Documents.Run.Text%2A> <xref:System.Windows.Documents.Run> je vlastnost objektu závislá. Vlastnost můžete navazovat <xref:System.Windows.Documents.Run.Text%2A> na zdroj dat, jako je například <xref:System.Windows.Controls.TextBlock> . <xref:System.Windows.Documents.Run.Text%2A>Vlastnost plně podporuje jednosměrnou vazbu. <xref:System.Windows.Documents.Run.Text%2A>Vlastnost také podporuje obousměrnou vazbu s výjimkou <xref:System.Windows.Controls.RichTextBox> . Příklad naleznete v tématu <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>.

**Kontextové**

<xref:System.Windows.Documents.Span>Seskupí ostatní vložené prvky obsahu dohromady. Pro obsah v rámci elementu není použito žádné podstatné vykreslování <xref:System.Windows.Documents.Span> . Nicméně prvky, které dědí z <xref:System.Windows.Documents.Span> zahrnutí <xref:System.Windows.Documents.Hyperlink> , <xref:System.Windows.Documents.Bold> <xref:System.Windows.Documents.Italic> a <xref:System.Windows.Documents.Underline> aplikují formátování na text.

Níže je uveden příklad, který se <xref:System.Windows.Documents.Span> používá k zahrnutí vloženého obsahu, včetně textu, <xref:System.Windows.Documents.Bold> prvku a <xref:System.Windows.Controls.Button> .

[!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]

Následující snímek obrazovky ukazuje, jak tento příklad vykresluje.

![Snímek obrazovky: příklad vykresleného rozsahu](./media/flow-spanexample.gif "Flow_SpanExample")

**InlineUIContainer**

<xref:System.Windows.Documents.InlineUIContainer>povoluje <xref:System.Windows.UIElement> vložení prvků (například ovládacího prvku jako <xref:System.Windows.Controls.Button> ) do <xref:System.Windows.Documents.Inline> elementu obsahu. Tento prvek je vložený ekvivalent, který je <xref:System.Windows.Documents.BlockUIContainer> popsaný výše. Níže je příklad, který používá <xref:System.Windows.Documents.InlineUIContainer> k vložení <xref:System.Windows.Controls.Button> vloženého do <xref:System.Windows.Documents.Paragraph> .

[!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.InlineUIContainer>není nutné použít explicitně v kódu. Pokud tento parametr vynecháte, <xref:System.Windows.Documents.InlineUIContainer> bude vytvořen i v případě, že je kód zkompilován.

**Obrázek a float**

<xref:System.Windows.Documents.Figure>a <xref:System.Windows.Documents.Floater> slouží k vložení obsahu do dokumentů Flow s vlastnostmi umístění, které je možné přizpůsobit nezávisle na primárním toku obsahu. <xref:System.Windows.Documents.Figure><xref:System.Windows.Documents.Floater>prvky nebo se často používají k zdůraznění nebo zvýraznění částí obsahu, k hostování podpůrných imagí nebo jiného obsahu v rámci hlavního toku obsahu nebo k vložení volně propojeného obsahu, jako je například inzerce.

Následující příklad ukazuje, jak vložit <xref:System.Windows.Documents.Figure> do odstavce textu.

[!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]

Následující obrázek ukazuje, jak tento příklad vykresluje.

![Snímek obrazovky: příklad obrázku](./media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")

<xref:System.Windows.Documents.Figure>a <xref:System.Windows.Documents.Floater> liší se různými způsoby a používají se pro různé scénáře.

**Obrázek**

- Lze umístit: můžete nastavit vodorovné a svislé kotvy, které mají být ukotveny relativně ke stránce, obsahu, sloupci nebo odstavci. Můžete také použít jeho <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> vlastnosti a a <xref:System.Windows.Documents.Figure.VerticalOffset%2A> zadat libovolné posuny.

- Je proměnlivá na více než jeden sloupec: <xref:System.Windows.Documents.Figure> Výška a šířka můžete nastavit na násobky stránky, obsahu nebo výšky sloupce nebo šířky. Všimněte si, že v případě stránky a obsahu nejsou násobky větší než 1 povoleny. Můžete například nastavit šířku a <xref:System.Windows.Documents.Figure> na "0,5 stránku" nebo "0,25 obsahu" nebo "2 sloupec". Můžete také nastavit možnost Výška a šířka na absolutní hodnoty v pixelech.

- Nestránkuje: Pokud se obsah uvnitř prvku <xref:System.Windows.Documents.Figure> nevejde do <xref:System.Windows.Documents.Figure> , vykreslí se veškerý obsah, který se přizpůsobí, a zbývající obsah se ztratí.

**Float:**

- Nedá se umístit a vykreslí se tam, kde se dá pro něj použít místo. Nelze nastavit posunutí nebo ukotvení a <xref:System.Windows.Documents.Floater> .

- Velikost nelze měnit na více než jeden sloupec: ve výchozím nastavení <xref:System.Windows.Documents.Floater> velikosti v jednom sloupci. Má <xref:System.Windows.Documents.Floater.Width%2A> vlastnost, kterou lze nastavit na absolutní hodnotu v pixelech, ale pokud je tato hodnota větší než jedna šířka sloupce, bude ignorována a velikost objektu float je v jednom sloupci. Velikost můžete změnit na méně než jeden sloupec nastavením správné šířky pixelů, ale velikost není relativní vzhledem k sloupci, takže "0.5 sloupec" není platným výrazem pro <xref:System.Windows.Documents.Floater> šířku. <xref:System.Windows.Documents.Floater>nemá žádnou vlastnost Height a nelze ji nastavit, její výška závisí na obsahu

- <xref:System.Windows.Documents.Floater>stránkování: v případě, že se její obsah v zadané šířce rozšiřuje na více než 1 výšku sloupce, zalomení floatů a stránkování do dalšího sloupce, další stránka atd.

 <xref:System.Windows.Documents.Figure>je vhodným místem pro umístění samostatného obsahu, u kterého chcete řídit velikost a umístění, a máte jistotu, že se obsah vejde do zadané velikosti. <xref:System.Windows.Documents.Floater>je vhodným místem pro vložení dalšího obsahu pro volné toky, který se podobá obsahu hlavní stránky, ale je od něj oddělený.

**LineBreak**

<xref:System.Windows.Documents.LineBreak>způsobí, že dojde k přerušení řádku v obsahu toku. Následující příklad ukazuje použití <xref:System.Windows.Documents.LineBreak> .

[!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]

Následující snímek obrazovky ukazuje, jak tento příklad vykresluje.

![Snímek obrazovky: příklad LineBreak](./media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")

### <a name="flow-collection-elements"></a>Prvky shromažďování toků

V mnoha příkladech uvedených výše <xref:System.Windows.Documents.BlockCollection> <xref:System.Windows.Documents.InlineCollection> jsou a použity k programovému vytváření obsahu toku. Chcete-li například přidat prvky do <xref:System.Windows.Documents.Paragraph> , můžete použít syntaxi:

```csharp
myParagraph.Inlines.Add(new Run("Some text"));
```

Tím se přidá <xref:System.Windows.Documents.Run> k <xref:System.Windows.Documents.InlineCollection> z <xref:System.Windows.Documents.Paragraph> .  To je stejné jako implicitní <xref:System.Windows.Documents.Run> nalezené uvnitř <xref:System.Windows.Documents.Paragraph> v kódu:

```xml
<Paragraph>
Some Text
</Paragraph>
```

Jako příklad použití <xref:System.Windows.Documents.BlockCollection> , následující příklad vytvoří nový <xref:System.Windows.Documents.Section> a poté použije metodu **Add** k přidání nového <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Section> obsahu.

[!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
[!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]

Kromě přidávání položek do kolekce toků můžete také odebrat položky.  Následující příklad odstraní poslední <xref:System.Windows.Documents.Inline> prvek v <xref:System.Windows.Documents.Span> .

[!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
[!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]

Následující příklad vymaže veškerý obsah ( <xref:System.Windows.Documents.Inline> prvky) z <xref:System.Windows.Documents.Span> .

[!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
[!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]

Když pracujete s obsahem toku programově, pravděpodobně budete mít rozsáhlé používání těchto kolekcí.

Určuje, zda prvek Flow používá <xref:System.Windows.Documents.InlineCollection> (vložené) nebo <xref:System.Windows.Documents.BlockCollection> (bloky) k zahrnutí jeho podřízených prvků závisí na typu podřízených prvků ( <xref:System.Windows.Documents.Block> nebo <xref:System.Windows.Documents.Inline> ) může být obsaženo v nadřazeném prvku. Pravidla zahrnutí pro prvky obsahu toku jsou shrnuta ve schématu obsahu v následující části.

> [!NOTE]
> K dispozici je třetí typ kolekce, který je použit s obsahem toku, <xref:System.Windows.Documents.ListItemCollection> ale tato kolekce je použita pouze s <xref:System.Windows.Documents.List> . Kromě toho je k dispozici několik kolekcí pro <xref:System.Windows.Documents.Table> . Další informace najdete v tématu [Přehled tabulek](table-overview.md) .

<a name="content_schema"></a>

## <a name="content-schema"></a>Schéma obsahu

Vzhledem k počtu různých prvků obsahu toku může být zahlcení, aby bylo možné sledovat typ podřízených prvků, které může element obsahovat. Diagram níže shrnuje pravidla omezení pro prvky toku. Šipky označují možné vztahy mezi nadřazenými a podřízenými objekty.

![Diagram: schéma zahrnutí obsahu toku](./media/flow-content-schema.png "Flow_Content_Schema")

Jak je možné vidět z diagramu výše, podřízené položky, které jsou povoleny pro element, nejsou nutně určeny podle toho, zda se jedná o <xref:System.Windows.Documents.Block> prvek nebo <xref:System.Windows.Documents.Inline> prvek. Například <xref:System.Windows.Documents.Span> ( <xref:System.Windows.Documents.Inline> element) může mít <xref:System.Windows.Documents.Inline> podřízené prvky pouze v době, kdy a <xref:System.Windows.Documents.Figure> (také <xref:System.Windows.Documents.Inline> element) může mít pouze <xref:System.Windows.Documents.Block> podřízené prvky. Diagram je proto vhodný pro rychlé určení toho, který prvek může být obsažen v jiném. Pomocí tohoto diagramu můžete například určit, jak vytvořit obsah toku <xref:System.Windows.Controls.RichTextBox> .

**1.** a <xref:System.Windows.Controls.RichTextBox> musí obsahovat <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Documents.Block> objekt odvozený od. Níže je odpovídající segment z diagramu výše.

![Diagram: RichTextBox pravidla zahrnutí](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")

Proto je to tak, jak může vypadat označení jako.

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]

**2.** v závislosti na diagramu existuje několik prvků, <xref:System.Windows.Documents.Block> které je třeba vybrat z příkazu zahrnout <xref:System.Windows.Documents.Paragraph> , <xref:System.Windows.Documents.Section> ,, <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.List> a <xref:System.Windows.Documents.BlockUIContainer> (viz třídy odvozené od bloku výše). Řekněme, že chceme <xref:System.Windows.Documents.Table> . Podle diagramu výše <xref:System.Windows.Documents.Table> obsahuje <xref:System.Windows.Documents.TableRowGroup> obsahující <xref:System.Windows.Documents.TableRow> prvky, které obsahují <xref:System.Windows.Documents.TableCell> prvky, které obsahují <xref:System.Windows.Documents.Block> objekt odvozený od. Níže je odpovídající segment pro <xref:System.Windows.Documents.Table> pořízení z diagramu výše.

![Diagram: nadřazený&#47;podřízených schématu pro tabulku](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")

Níže je uveden odpovídající kód.

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]

**3.** znovu se vyžaduje jeden nebo více <xref:System.Windows.Documents.Block> elementů pod <xref:System.Windows.Documents.TableCell> . Chcete-li to jednoduché, umístěte text do buňky. To lze provést pomocí <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> elementu s elementem. Níže jsou odpovídající segmenty z diagramu ukazující, že <xref:System.Windows.Documents.Paragraph> může převzít <xref:System.Windows.Documents.Inline> prvek a který <xref:System.Windows.Documents.Run> ( <xref:System.Windows.Documents.Inline> element) může převzít pouze prostý text.

![Diagram: nadřazený&#47;podřízených schématu pro odstavec](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")

![Diagram: nadřazený&#47;podřízených schématu pro běh](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")

Níže je uveden celý příklad v kódu.

[!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]

<a name="customizing_text"></a>

## <a name="customizing-text"></a>Přizpůsobení textu

Obvykle se jedná o nejaktuálnější typ obsahu v dokumentu toku. I když se výše uvedené objekty dají použít k řízení většiny aspektů toho, jak se text vykresluje, existují jiné metody přizpůsobení textu, který je popsaný v této části.

### <a name="text-decorations"></a>Dekorace textu

Dekorace textu umožňují aplikovat efekty podtržení, nadtržítko, účaří a přeškrtnutí na text (viz obrázky níže). Tyto dekorace jsou přidány pomocí <xref:System.Windows.Documents.Inline.TextDecorations%2A> vlastnosti, která je vystavena několika objekty <xref:System.Windows.Documents.Inline> , včetně, <xref:System.Windows.Documents.Paragraph> , <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.TextBox> .

Následující příklad ukazuje, jak nastavit <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> vlastnost <xref:System.Windows.Documents.Paragraph> .

[!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]

[!code-csharp[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
[!code-vb[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]

Následující obrázek ukazuje, jak tento příklad vykresluje.

![Snímek obrazovky: text s výchozím efektem přeškrtnutí](./media/inline-textdec-strike.png "Inline_TextDec_Strike")

Následující obrázky znázorňují, jak vykreslování Obkreslí **nadtržítko**, **účaří**a **podtržení** .

![Snímek obrazovky: nadtržítko TextDecorator](./media/inline-textdec-over.png "Inline_TextDec_Over")

![Snímek obrazovky: výchozí efekt účaří textu](./media/inline-textdec-base.png "Inline_TextDec_Base")

![Snímek obrazovky: text s výchozím efektem podtržení](./media/inline-textdec-under.png "Inline_TextDec_Under")

### <a name="typography"></a>Typografie

<xref:System.Windows.Documents.TextElement.Typography%2A>Vlastnost je zveřejněna většinou obsahu souvisejícího s tokem, včetně <xref:System.Windows.Documents.TextElement> , <xref:System.Windows.Documents.FlowDocument> , <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.TextBox> . Tato vlastnost slouží k řízení typografických vlastností/variací textu (tj. malých nebo velkých písmen, vytváření horních indexů a dolních indexů atd.).

Následující příklad ukazuje, jak nastavit <xref:System.Windows.Documents.TextElement.Typography%2A> atribut pomocí <xref:System.Windows.Documents.Paragraph> jako ukázkového prvku.

[!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]

Následující obrázek ukazuje, jak tento příklad vykresluje.

![Snímek obrazovky: text se změněnou typografickou sadou](./media/textelement-typog.png "TextElement_Typog")

Naproti tomu následující obrázek ukazuje, jak se vykresluje podobný příklad s výchozími typografických vlastností.

![Snímek obrazovky: text se změněnou typografickou sadou](./media/textelement-typog-default.png "TextElement_Typog_Default")

Následující příklad ukazuje, jak nastavit <xref:System.Windows.Controls.TextBox.Typography%2A> vlastnost programově.

[!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
[!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]

Další informace o typografii najdete [v části typografie v](typography-in-wpf.md) subsystému WPF.

## <a name="see-also"></a>Viz také

- [Text](optimizing-performance-text.md)
- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [– postupy](flow-content-elements-how-to-topics.md)
- [Přehled modelu obsahu TextElement](textelement-content-model-overview.md)
- [RichTextBox – přehled](../controls/richtextbox-overview.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tabulky](table-overview.md)
- [Přehled poznámek](annotations-overview.md)
