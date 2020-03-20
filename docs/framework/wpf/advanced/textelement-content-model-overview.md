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
ms.openlocfilehash: ddb2613dc924424b5f4b9d90f06d44b45b7b5e77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186895"
---
# <a name="textelement-content-model-overview"></a>Přehled modelu obsahu TextElement
Tento přehled modelu obsahu popisuje podporovaný <xref:System.Windows.Documents.TextElement>obsah pro . Třída <xref:System.Windows.Documents.Paragraph> je typ <xref:System.Windows.Documents.TextElement>. Model obsahu popisuje, jaké objekty nebo prvky mohou být obsaženy v jiných. Tento přehled shrnuje model obsahu používaný <xref:System.Windows.Documents.TextElement>pro objekty odvozené z . Další informace naleznete v [tématu Přehled dokumentu toku](flow-document-overview.md).  

<a name="text_element_classes"></a>
## <a name="content-model-diagram"></a>Diagram modelu obsahu  
 Následující diagram shrnuje model obsahu pro <xref:System.Windows.Documents.TextElement> třídy odvozené `TextElement` z a jak ostatní jiné třídy zapadají do tohoto modelu.  
  
 ![Diagram: Schéma omezení obsahu toku](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Jak je vidět z předchozího diagramu, podřízené povolené pro prvek nejsou nutně určeny tím, zda je třída odvozena z <xref:System.Windows.Documents.Block> třídy nebo <xref:System.Windows.Documents.Inline> třídy. Například <xref:System.Windows.Documents.Span> (odvozené <xref:System.Windows.Documents.Inline>třídy) může mít <xref:System.Windows.Documents.Inline> pouze podřízené <xref:System.Windows.Documents.Figure> prvky, ale (také <xref:System.Windows.Documents.Inline>odvozené třídy) může mít <xref:System.Windows.Documents.Block> pouze podřízené prvky. Diagram je proto užitečné pro rychlé určení, jaký prvek může být obsažen v jiném. Jako příklad použijeme diagram k určení, jak vytvořit obsah <xref:System.Windows.Controls.RichTextBox>toku .  
  
1. A <xref:System.Windows.Controls.RichTextBox> musí <xref:System.Windows.Documents.FlowDocument> obsahovat, který <xref:System.Windows.Documents.Block>zase musí obsahovat -odvozený objekt. Následuje odpovídající segment z předchozího diagramu.  
  
     ![Diagram: Pravidla uzavření pole RichTextBox](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Zatím to je to, co značky by mohly vypadat.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. Podle diagramu existuje několik <xref:System.Windows.Documents.Block> prvků, ze <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Section>kterých můžete vybírat včetně , , <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>a <xref:System.Windows.Documents.BlockUIContainer> (viz Třídy odvozené od bloku v předchozím diagramu). Řekněme, že chceme <xref:System.Windows.Documents.Table>. Podle předchozího diagramu <xref:System.Windows.Documents.Table> obsahuje <xref:System.Windows.Documents.TableRowGroup> obsahující <xref:System.Windows.Documents.TableRow> prvky, <xref:System.Windows.Documents.TableCell> které obsahují <xref:System.Windows.Documents.Block>prvky, které obsahují -odvozený objekt. Následuje odpovídající segment pro <xref:System.Windows.Documents.Table> převzaté z předchozího diagramu.  
  
     ![Diagram: Nadřazené&#47;podřízené schéma pro tabulka](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Následuje odpovídající značky.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Opět platí, <xref:System.Windows.Documents.Block> že jeden nebo <xref:System.Windows.Documents.TableCell>více prvků jsou požadovány pod . Aby to bylo jednoduché, umístěte nějaký text do buňky. Můžeme to udělat <xref:System.Windows.Documents.Paragraph> pomocí <xref:System.Windows.Documents.Run> prvku. Následuje odpovídající segmenty z diagramu, <xref:System.Windows.Documents.Paragraph> které ukazují, že a může mít <xref:System.Windows.Documents.Inline> prvek a že <xref:System.Windows.Documents.Run> <xref:System.Windows.Documents.Inline> (prvek) může trvat pouze prostý text.  
  
     ![Diagram: Nadřazené&#47;podřízené schéma pro odstavec](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagram: Nadřazené&#47;podřízené schéma pro spuštění](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Následuje celý příklad v značek.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>
## <a name="working-with-textelement-content-programmatically"></a>Programově pracovat s obsahem TextElement  
 Obsah a <xref:System.Windows.Documents.TextElement> je tvořen kolekcemi a tak programově manipulace <xref:System.Windows.Documents.TextElement> s obsahem objektů se provádí prací s těmito kolekcemi. Existují tři různé kolekce <xref:System.Windows.Documents.TextElement> používané odvozenými třídami:  
  
- <xref:System.Windows.Documents.InlineCollection>: Představuje kolekci <xref:System.Windows.Documents.Inline> prvků. <xref:System.Windows.Documents.InlineCollection>definuje povolený podřízený obsah <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span>a <xref:System.Windows.Controls.TextBlock> prvky.  
  
- <xref:System.Windows.Documents.BlockCollection>: Představuje kolekci <xref:System.Windows.Documents.Block> prvků. <xref:System.Windows.Documents.BlockCollection>definuje povolený podřízený obsah <xref:System.Windows.Documents.FlowDocument>prvků <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell> <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Figure> , , a.  
  
- <xref:System.Windows.Documents.ListItemCollection>: Prvek obsahu toku, který představuje určitou <xref:System.Windows.Documents.List>položku obsahu v uspořádané nebo neuspořádané .  
  
 Můžete manipulovat (přidat nebo odebrat položky) z těchto kolekcí pomocí příslušných vlastností **Inlines**, **Blocks**a **ListItems**. Následující příklady ukazují, jak manipulovat s obsahem Span pomocí **Inlines** vlastnost.  
  
> [!NOTE]
> Tabulka používá několik kolekcí k manipulaci s jeho obsahem, ale nejsou zde zahrnuty. Další informace naleznete v [tématu Přehled tabulky](table-overview.md).  
  
 Následující příklad vytvoří <xref:System.Windows.Documents.Span> nový objekt a `Add` potom použije metodu k přidání <xref:System.Windows.Documents.Span>dvou textběží jako podřízený obsah .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Následující příklad vytvoří <xref:System.Windows.Documents.Run> nový prvek a vloží jej <xref:System.Windows.Documents.Span>na začátek .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Následující příklad odstraní poslední <xref:System.Windows.Documents.Inline> prvek <xref:System.Windows.Documents.Span>v .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Následující příklad vymaže<xref:System.Windows.Documents.Inline> veškerý obsah <xref:System.Windows.Documents.Span>( prvky) z .  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>
## <a name="types-that-share-this-content-model"></a>Typy, které sdílejí tento model obsahu  
 Následující typy dědí <xref:System.Windows.Documents.TextElement> z třídy a mohou být použity k zobrazení obsahu popsaného v tomto přehledu.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Všimněte si, že tento seznam obsahuje pouze neabstraktní typy distribuované se sadou Windows SDK. Můžete použít jiné typy, <xref:System.Windows.Documents.TextElement>které dědí od .  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>
## <a name="types-that-can-contain-textelement-objects"></a>Typy, které mohou obsahovat objekty TextElement  
 Viz [Model obsahu WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Viz také

- [Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zpracování elementů obsahu toku prostřednictvím vlastnosti Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Zpracování objektu FlowDocument prostřednictvím vlastnosti Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zpracování sloupců tabulky prostřednictvím vlastnosti Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Zpracování skupin řádků tabulky prostřednictvím vlastnosti RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
