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
ms.openlocfilehash: 21df7228f8dca884c5f36be23ae1aced7b31cc9a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942219"
---
# <a name="textelement-content-model-overview"></a>Přehled modelu obsahu TextElement
Přehled tohoto modelu obsahu popisuje podporovaný obsah pro <xref:System.Windows.Documents.TextElement>. <xref:System.Windows.Documents.Paragraph> Třída je <xref:System.Windows.Documents.TextElement>typem. Model obsahu popisuje prvky, které mohou být obsaženy v jiných objektech. Tento přehled shrnuje obsahový model používaný pro objekty odvozené z <xref:System.Windows.Documents.TextElement>. Další informace najdete v tématu [Přehled dokumentů Flow](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagram modelu obsahu  
 Následující diagram shrnuje obsahový model pro třídy odvozené od <xref:System.Windows.Documents.TextElement> a také způsob, jakým jsou do tohoto modelu přizpůsobeny jiné `TextElement` třídy, které nejsou.  
  
 ![Znázorňuje ](./media/flow-content-schema.png "Flow_Content_Schema") schématu zahrnutí obsahu toku  
  
 Jak je vidět z předchozího diagramu, podřízené položky, které jsou povoleny pro element, nejsou nutně určeny podle toho, zda je třída odvozena <xref:System.Windows.Documents.Block> od třídy <xref:System.Windows.Documents.Inline> nebo třídy. <xref:System.Windows.Documents.Span> Například třída <xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Block> <xref:System.Windows.Documents.Figure> (odvozená od třídy) může mít <xref:System.Windows.Documents.Inline> pouze podřízené prvky, ale třída (také odvozená třída) může mít pouze podřízené prvky. <xref:System.Windows.Documents.Inline> Diagram je proto vhodný pro rychlé určení toho, který prvek může být obsažen v jiném. Pomocí tohoto diagramu můžete například určit, jak vytvořit obsah <xref:System.Windows.Controls.RichTextBox>toku.  
  
1. <xref:System.Windows.Controls.RichTextBox> Musí obsahovat<xref:System.Windows.Documents.Block>objektodvozenýod. <xref:System.Windows.Documents.FlowDocument> Následuje odpovídající segment z předchozího diagramu.  
  
     ![Znázorňuje RichTextBox pravidla]zahrnutí(./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Proto je to tak, jak může vypadat označení jako.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. Podle diagramu je k dispozici několik <xref:System.Windows.Documents.Block> prvků, které lze vybrat z příkazu zahrnutí <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.List> <xref:System.Windows.Documents.Section>,, <xref:System.Windows.Documents.BlockUIContainer> a (viz třídy odvozené od bloku v předchozím diagramu). Řekněme, že <xref:System.Windows.Documents.Table>chceme. Podle <xref:System.Windows.Documents.Table> předchozího diagramu <xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.TableRowGroup> obsahuje prvky<xref:System.Windows.Documents.TableCell>obsahující prvky, kteréobsahujíobjektodvozenýod.<xref:System.Windows.Documents.Block> Níže je uveden odpovídající segment pro <xref:System.Windows.Documents.Table> pořízení z předchozího diagramu.  
  
     ![Znázorňuje Nadřazené&#47;podřízené schéma pro](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2") tabulky  
  
     Následuje odpovídající kód.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Jeden nebo více <xref:System.Windows.Documents.Block> prvků je opět vyžadováno <xref:System.Windows.Documents.TableCell>pod. Chcete-li to jednoduché, umístěte text do buňky. To lze provést pomocí <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> elementu s elementem. Níže jsou odpovídající segmenty z diagramu ukazující <xref:System.Windows.Documents.Paragraph> , že může <xref:System.Windows.Documents.Inline> převzít prvek <xref:System.Windows.Documents.Inline> a že <xref:System.Windows.Documents.Run> (element) může převzít pouze prostý text.  
  
     ![Znázorňuje Nadřazené&#47;podřízené schéma pro](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3") odstavce  
  
     ![Znázorňuje Nadřazené&#47;nadřazené schéma pro běh](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Následuje celý příklad v kódu.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Práce s obsahem TextElement prostřednictvím kódu programu  
 Obsah a <xref:System.Windows.Documents.TextElement> se skládá ze kolekcí, takže programové manipulaci s <xref:System.Windows.Documents.TextElement> obsahem objektů se provádí pomocí těchto kolekcí. Existují tři různé kolekce používané <xref:System.Windows.Documents.TextElement> odvozenými třídami:  
  
- <xref:System.Windows.Documents.InlineCollection>: Představuje kolekci <xref:System.Windows.Documents.Inline> elementů. <xref:System.Windows.Documents.InlineCollection>definuje povolený podřízený obsah <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Controls.TextBlock> prvků, <xref:System.Windows.Documents.Span>a.  
  
- <xref:System.Windows.Documents.BlockCollection>: Představuje kolekci <xref:System.Windows.Documents.Block> elementů. <xref:System.Windows.Documents.BlockCollection><xref:System.Windows.Documents.FlowDocument>definuje povolený podřízený obsah prvků, <xref:System.Windows.Documents.ListItem> <xref:System.Windows.Documents.TableCell> <xref:System.Windows.Documents.Section>,,, <xref:System.Windows.Documents.Floater>a <xref:System.Windows.Documents.Figure> .  
  
- <xref:System.Windows.Documents.ListItemCollection>: Prvek obsahu toku, který představuje konkrétní položku obsahu v seřazeném nebo neuspořádaném pořadí <xref:System.Windows.Documents.List>.  
  
 Můžete manipulovat (Přidat nebo odebrat položky) z těchto kolekcí pomocí příslušných vlastností **řádků**, **bloků**a **ListItems**. Následující příklady ukazují, jak manipulovat s obsahem rozsahu pomocí vlastnosti Inlines.  
  
> [!NOTE]
> Tabulka používá k manipulaci s obsahem několik kolekcí, které zde nejsou pokryté. Další informace najdete v tématu [Přehled tabulek](table-overview.md).  
  
 Následující příklad vytvoří nový <xref:System.Windows.Documents.Span> objekt a poté `Add` použije metodu pro přidání dvou textových běhů <xref:System.Windows.Documents.Span>jako podřízených objektů obsahu.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Následující příklad vytvoří nový <xref:System.Windows.Documents.Run> prvek a vloží jej na začátek. <xref:System.Windows.Documents.Span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Následující příklad odstraní poslední <xref:System.Windows.Documents.Inline> prvek <xref:System.Windows.Documents.Span>v.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Následující příklad vymaže veškerý obsah (<xref:System.Windows.Documents.Inline> prvky) <xref:System.Windows.Documents.Span>z.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Typy, které sdílejí tento model obsahu  
 Následující typy dědí z <xref:System.Windows.Documents.TextElement> třídy a lze je použít k zobrazení obsahu popsaného v tomto přehledu.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Všimněte si, že tento seznam obsahuje pouze neabstraktní typy distribuované [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]s. Můžete použít jiné typy, které dědí z <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Typy, které mohou obsahovat objekty TextElement  
 Viz [model obsahu WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Viz také:

- [Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zpracování elementů obsahu toku prostřednictvím vlastnosti Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zpracování sloupců tabulky prostřednictvím vlastnosti Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
