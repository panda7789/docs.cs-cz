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
ms.openlocfilehash: acd67dd870c6912eddc368bf674804d98dba2db8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740753"
---
# <a name="textelement-content-model-overview"></a>Přehled modelu obsahu TextElement
Přehled tohoto modelu obsahu popisuje podporovaný obsah pro <xref:System.Windows.Documents.TextElement>. Třída <xref:System.Windows.Documents.Paragraph> je typ <xref:System.Windows.Documents.TextElement>. Model obsahu popisuje prvky, které mohou být obsaženy v jiných objektech. Tento přehled shrnuje obsahový model používaný pro objekty odvozené od <xref:System.Windows.Documents.TextElement>. Další informace najdete v tématu [Přehled dokumentů Flow](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagram modelu obsahu  
 Následující diagram shrnuje model obsahu pro třídy odvozené od <xref:System.Windows.Documents.TextElement> a také způsob, jakým se do tohoto modelu vejdou jiné třídy, které nejsou `TextElement`.  
  
 ![Diagram: schéma zahrnutí obsahu toku](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Jak je vidět z předchozího diagramu, podřízené položky, které jsou povoleny pro element, nejsou nutně určeny podle toho, zda je třída odvozena od <xref:System.Windows.Documents.Block> třídy nebo <xref:System.Windows.Documents.Inline> třídy. Například <xref:System.Windows.Documents.Span> (třída odvozená <xref:System.Windows.Documents.Inline>) může mít pouze <xref:System.Windows.Documents.Inline> podřízené prvky, ale <xref:System.Windows.Documents.Figure> (také <xref:System.Windows.Documents.Inline>odvozená třída) může mít pouze <xref:System.Windows.Documents.Block> podřízené prvky. Diagram je proto vhodný pro rychlé určení toho, který prvek může být obsažen v jiném. Pomocí tohoto diagramu můžete například určit, jak vytvořit obsah toku <xref:System.Windows.Controls.RichTextBox>.  
  
1. <xref:System.Windows.Controls.RichTextBox> musí obsahovat <xref:System.Windows.Documents.FlowDocument>, který zase musí obsahovat objekt odvozený <xref:System.Windows.Documents.Block>. Následuje odpovídající segment z předchozího diagramu.  
  
     ![Diagram: RichTextBox pravidla zahrnutí](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Proto je to tak, jak může vypadat označení jako.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. Podle diagramu je k dispozici několik <xref:System.Windows.Documents.Block> prvků, které zahrnují <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>a <xref:System.Windows.Documents.BlockUIContainer> (viz třídy odvozené od bloku v předchozím diagramu). Řekněme, že chceme <xref:System.Windows.Documents.Table>. Podle předchozího diagramu <xref:System.Windows.Documents.Table> obsahuje <xref:System.Windows.Documents.TableRowGroup> obsahující <xref:System.Windows.Documents.TableRow> prvky, které obsahují <xref:System.Windows.Documents.TableCell> prvky, které obsahují objekt odvozený <xref:System.Windows.Documents.Block>. Níže je uveden odpovídající segment <xref:System.Windows.Documents.Table> z předchozího diagramu.  
  
     ![Diagram: nadřazené&#47;podřízené schéma pro tabulku](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Následuje odpovídající kód.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Jeden nebo více elementů <xref:System.Windows.Documents.Block> je v rámci <xref:System.Windows.Documents.TableCell>vyžadováno. Chcete-li to jednoduché, umístěte text do buňky. To lze provést pomocí <xref:System.Windows.Documents.Paragraph> s <xref:System.Windows.Documents.Run> prvkem. Níže jsou uvedené odpovídající segmenty z diagramu ukazující, že <xref:System.Windows.Documents.Paragraph> může převzít <xref:System.Windows.Documents.Inline> prvek a že <xref:System.Windows.Documents.Run> (element <xref:System.Windows.Documents.Inline>) může přebírat pouze prostý text.  
  
     ![Diagram: nadřazený&#47;podřízený schéma pro odstavec](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagram: nadřazený&#47;podřízený schéma pro běh](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Následuje celý příklad v kódu.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Práce s obsahem TextElement prostřednictvím kódu programu  
 Obsah <xref:System.Windows.Documents.TextElement> se skládá ze kolekcí a tím, že programově manipuluje s obsahem <xref:System.Windows.Documents.TextElement> objektů, pracuje s těmito kolekcemi. Třídy odvozené od <xref:System.Windows.Documents.TextElement> používají tři různé kolekce:  
  
- <xref:System.Windows.Documents.InlineCollection>: představuje kolekci <xref:System.Windows.Documents.Inline> prvků. <xref:System.Windows.Documents.InlineCollection> definuje povolený podřízený obsah prvků <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span>a <xref:System.Windows.Controls.TextBlock>.  
  
- <xref:System.Windows.Documents.BlockCollection>: představuje kolekci <xref:System.Windows.Documents.Block> prvků. <xref:System.Windows.Documents.BlockCollection> definuje povolený podřízený obsah pro prvky <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater>a <xref:System.Windows.Documents.Figure>.  
  
- <xref:System.Windows.Documents.ListItemCollection>: prvek obsahu toku, který představuje konkrétní položku obsahu v seřazené nebo neuspořádaném <xref:System.Windows.Documents.List>.  
  
 Můžete manipulovat (Přidat nebo odebrat položky) z těchto kolekcí pomocí příslušných vlastností **řádků**, **bloků**a **ListItems**. Následující příklady ukazují, jak manipulovat s obsahem rozsahu pomocí vlastnosti **Inlines** .  
  
> [!NOTE]
> Tabulka používá k manipulaci s obsahem několik kolekcí, které zde nejsou pokryté. Další informace najdete v tématu [Přehled tabulek](table-overview.md).  
  
 Následující příklad vytvoří nový objekt <xref:System.Windows.Documents.Span> a poté pomocí metody `Add` přidá dvě textová spuštění jako podřízené objekty obsahu <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Následující příklad vytvoří nový prvek <xref:System.Windows.Documents.Run> a vloží jej na začátek <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Následující příklad odstraní poslední <xref:System.Windows.Documents.Inline> prvek v <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Následující příklad vymaže veškerý obsah (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Typy, které sdílejí tento model obsahu  
 Následující typy dědí z třídy <xref:System.Windows.Documents.TextElement> a lze je použít k zobrazení obsahu, který je popsán v tomto přehledu.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Všimněte si, že tento seznam obsahuje pouze neabstraktní typy distribuované s Windows SDK. Můžete použít jiné typy, které dědí z <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Typy, které mohou obsahovat objekty TextElement  
 Viz [model obsahu WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Viz také:

- [Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zpracování elementů obsahu toku prostřednictvím vlastnosti Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zpracování sloupců tabulky prostřednictvím vlastnosti Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Zpracování skupin řádků tabulky pomocí vlastnosti RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
