---
title: Přehled modelu obsahu TextElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
ms.openlocfilehash: 990642d288481fff8eeef900a86070d54790f151
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336184"
---
# <a name="textelement-content-model-overview"></a>Přehled modelu obsahu TextElement
Tento přehled modelu obsahu popisuje podporované obsah <xref:System.Windows.Documents.TextElement>. <xref:System.Windows.Documents.Paragraph> Třída je typem <xref:System.Windows.Documents.TextElement>. Model obsahu popisuje objekty/prvky mohou být obsaženy v jiné. Tento přehled obsahuje souhrn modelu obsahu použít u objektů odvozené z <xref:System.Windows.Documents.TextElement>. Další informace najdete v tématu [přehled toku dokumentů](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagram modelu obsahu  
 Následující diagram obsahuje souhrn obsahu modelu pro třídy odvozené z <xref:System.Windows.Documents.TextElement> a také jak ostatní jinou hodnotu než `TextElement` třídy, aby se vešel do tohoto modelu.  
  
 ![Diagram: Tok obsahu členství ve skupině schématu](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Jak je vidět z předchozí diagram, podřízené položky pro element povolená nejsou určeny nutně Určuje, zda je třída odvozena z <xref:System.Windows.Documents.Block> třídy nebo <xref:System.Windows.Documents.Inline> třídy. Například <xref:System.Windows.Documents.Span> ( <xref:System.Windows.Documents.Inline>– odvozené třídy) může mít pouze <xref:System.Windows.Documents.Inline> podřízených elementů, ale <xref:System.Windows.Documents.Figure> (také <xref:System.Windows.Documents.Inline>-odvozené třídy) může mít pouze <xref:System.Windows.Documents.Block> podřízené prvky. Diagram je proto užitečné k rychlému určení toho, který element mohou být obsaženy v jiném. Jako příklad použijeme diagramu a zjistěte, jak vytvořit tok obsahu <xref:System.Windows.Controls.RichTextBox>.  
  
1. A <xref:System.Windows.Controls.RichTextBox> musí obsahovat <xref:System.Windows.Documents.FlowDocument> zase obsahující <xref:System.Windows.Documents.Block>-odvozenému objektu. Tady je odpovídající segmentu z předchozího diagramu.  
  
     ![Diagram: Pravidla členství ve skupině RichTextBox](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Proto pokud je kód může vypadat.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. Podle diagramu, existuje několik <xref:System.Windows.Documents.Block> elementy lze vybírat včetně <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, a <xref:System.Windows.Documents.BlockUIContainer> (viz bloku odvozené třídy na předchozím obrázku). Řekněme, že chceme, aby <xref:System.Windows.Documents.Table>. Podle předchozí diagram <xref:System.Windows.Documents.Table> obsahuje <xref:System.Windows.Documents.TableRowGroup> obsahující <xref:System.Windows.Documents.TableRow> prvky, které obsahují <xref:System.Windows.Documents.TableCell> prvky, které obsahují <xref:System.Windows.Documents.Block>-odvozenému objektu. Tady je odpovídající segmentu pro <xref:System.Windows.Documents.Table> z předchozího diagramu.  
  
     ![Diagram: Nadřazené&#47;podřízené schématu pro tabulku](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Tady je odpovídající značky.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Znovu jeden nebo více <xref:System.Windows.Documents.Block> prvky jsou nutné pod <xref:System.Windows.Documents.TableCell>. Aby byl jednoduchý, Pojďme nějaký text umístíte text do buňky. Můžeme to udělat pomocí <xref:System.Windows.Documents.Paragraph> s <xref:System.Windows.Documents.Run> elementu. Tady je odpovídající segmenty z diagram zobrazující, že <xref:System.Windows.Documents.Paragraph> může trvat <xref:System.Windows.Documents.Inline> elementu a zda <xref:System.Windows.Documents.Run> ( <xref:System.Windows.Documents.Inline> element) jde převzít jenom prostý text.  
  
     ![Diagram: Nadřazené&#47;podřízené schéma pro odstavec](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagram: Nadřazené&#47;podřízené schématu pro spuštění](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Níže je celý příklad v kódu.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Práce s obsahu TextElement prostřednictvím kódu programu  
 Obsah <xref:System.Windows.Documents.TextElement> tvoří kolekce, a proto Programová práce s obsahem <xref:System.Windows.Documents.TextElement> objekty se provádí ve spolupráci s těchto kolekcí. Existují tři různé kolekce používané <xref:System.Windows.Documents.TextElement> -odvozené třídy:  
  
-   <xref:System.Windows.Documents.InlineCollection>: Představuje kolekci <xref:System.Windows.Documents.Inline> elementy. <xref:System.Windows.Documents.InlineCollection> definuje povolené podřízený obsah <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span>, a <xref:System.Windows.Controls.TextBlock> elementy.  
  
-   <xref:System.Windows.Documents.BlockCollection>: Představuje kolekci <xref:System.Windows.Documents.Block> elementy. <xref:System.Windows.Documents.BlockCollection> definuje povolené podřízený obsah <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater>, a <xref:System.Windows.Documents.Figure> elementy.  
  
-   <xref:System.Windows.Documents.ListItemCollection>: Element content tok, který představuje určité obsahu položky v seřazená nebo neseřazené <xref:System.Windows.Documents.List>.  
  
 Můžete pracovat s (Přidat nebo odebrat položky) z těchto kolekcí pomocí odpovídajících vlastností **Inlines**, **bloky**, a **položky ListItems**. Následující příklady ukazují, jak manipulovat s obsahem Span pomocí **Inlines** vlastnost.  
  
> [!NOTE]
>  Tabulka používá několik kolekcí pro práci s obsahem, ale nejsou součástí tohoto. Další informace najdete v tématu [Přehled tabulek](table-overview.md).  
  
 Následující příklad vytvoří nový <xref:System.Windows.Documents.Span> a pak použije `Add` spuštěním metody přidat textu jako obsahu podřízené objekty <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Následující příklad vytvoří nový <xref:System.Windows.Documents.Run> elementu a vloží na začátek <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Následující příklad odstraní poslední <xref:System.Windows.Documents.Inline> prvek <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Následující příklad odebere veškerý obsah (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Typy, které sdílejí tento Model obsahu  
 Následující typy dědí <xref:System.Windows.Documents.TextElement> třídy a slouží k zobrazení obsahu je popsáno v tomto přehledu.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Všimněte si, že tento seznam obsahuje pouze neabstraktní typy distribuovat se [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Může používat jiné typy, které dědí z <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Typy, které může obsahovat objekty TextElement  
 Zobrazit [Model obsahu WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Viz také:

- [Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zpracování elementů obsahu toku prostřednictvím vlastnosti Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zpracování sloupců tabulky prostřednictvím vlastnosti Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
