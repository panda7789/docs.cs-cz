---
title: "Přehled modelu obsahu TextElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81f95ea4582230fe66c59655ab9b98a405c1e173
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="textelement-content-model-overview"></a>Přehled modelu obsahu TextElement
Tento model obsahu přehled popisuje podporované obsah <xref:System.Windows.Documents.TextElement>. <xref:System.Windows.Documents.Paragraph> Třída je typ <xref:System.Windows.Documents.TextElement>. Model obsahu popisuje, jaké objekty elementy může být obsažený v jiné. Tento přehled obsahuje souhrn modelu obsahu použít pro objekty, které jsou odvozené z <xref:System.Windows.Documents.TextElement>. Další informace najdete v tématu [toku dokumentu přehled](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
  
<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagram modelu obsahu  
 Následující diagram shrnuje modelu obsahu pro třídy odvozené od <xref:System.Windows.Documents.TextElement> a také jak jiných jinou hodnotu než `TextElement` třídy nevejde se do tohoto modelu.  
  
 ![Diagram: Toku obsahu omezení schématu](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow_Content_Schema")  
  
 Vyplývá z na předchozím obrázku, děti povoleny pro element nejsou určen nutně jestli je třída odvozená z <xref:System.Windows.Documents.Block> třídy nebo <xref:System.Windows.Documents.Inline> třídy. Například <xref:System.Windows.Documents.Span> ( <xref:System.Windows.Documents.Inline>-odvozené třídy) může mít pouze <xref:System.Windows.Documents.Inline> podřízených elementů, ale <xref:System.Windows.Documents.Figure> (také <xref:System.Windows.Documents.Inline>-odvozené třídy) může mít pouze <xref:System.Windows.Documents.Block> podřízené elementy. Proto je užitečné pro určení rychle, jaký element může být obsažený v jiné diagram. Jako příklad použijeme diagram určit, jak vytvořit tok obsahu <xref:System.Windows.Controls.RichTextBox>.  
  
1.  A <xref:System.Windows.Controls.RichTextBox> musí obsahovat <xref:System.Windows.Documents.FlowDocument> zase obsahující <xref:System.Windows.Documents.Block>-odvozené objektu. Následuje odpovídající segmentu z na předchozím obrázku.  
  
     ![Diagram: Pravidla členství ve skupině RichTextBox](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Doposud to je, jak může vypadat kód.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2.  Podle diagramu je vidět, existuje několik <xref:System.Windows.Documents.Block> elementy lze vybírat včetně <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, a <xref:System.Windows.Documents.BlockUIContainer> (viz třídy odvozené bloku na předchozím obrázku). Řekněme, že chceme <xref:System.Windows.Documents.Table>. Podle na předchozím obrázku <xref:System.Windows.Documents.Table> obsahuje <xref:System.Windows.Documents.TableRowGroup> obsahující <xref:System.Windows.Documents.TableRow> elementy, které obsahují <xref:System.Windows.Documents.TableCell> elementy, které obsahují <xref:System.Windows.Documents.Block>-odvozené objektu. Následuje odpovídající segmentu pro <xref:System.Windows.Documents.Table> převzaty z na předchozím obrázku.  
  
     ![Diagram: Nadřazené &#47; podřízené schématu pro tabulku](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Následuje odpovídající značky.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3.  Znovu jeden nebo více <xref:System.Windows.Documents.Block> elementy jsou nutné pod <xref:System.Windows.Documents.TableCell>. Chcete-li jednoduchý, umožňuje umístit text do buňky. Jsme můžete to provést pomocí <xref:System.Windows.Documents.Paragraph> s <xref:System.Windows.Documents.Run> elementu. Následuje odpovídající segmenty z diagram zobrazující, že <xref:System.Windows.Documents.Paragraph> může trvat <xref:System.Windows.Documents.Inline> elementu a že <xref:System.Windows.Documents.Run> ( <xref:System.Windows.Documents.Inline> element) může trvat jenom prostý text.  
  
     ![Diagram: Nadřazené &#47; podřízené schéma pro odstavec](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagram: Nadřazené &#47; Podřízené schéma pro spuštění](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Níže je celý příklad v kódu.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Práce s obsahem TextElement prostřednictvím kódu programu  
 Obsah <xref:System.Windows.Documents.TextElement> je tvořený kolekcí a tak prostřednictvím kódu programu manipulace s obsah <xref:System.Windows.Documents.TextElement> objekty se provádí ve spolupráci s těchto kolekcí. Existují tři různé kolekce používá <xref:System.Windows.Documents.TextElement> -odvozených tříd:  
  
-   <xref:System.Windows.Documents.InlineCollection>: Představuje kolekci <xref:System.Windows.Documents.Inline> elementy. <xref:System.Windows.Documents.InlineCollection>definuje povolené podřízené obsah <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span>, a <xref:System.Windows.Controls.TextBlock> elementy.  
  
-   <xref:System.Windows.Documents.BlockCollection>: Představuje kolekci <xref:System.Windows.Documents.Block> elementy. <xref:System.Windows.Documents.BlockCollection>definuje povolené podřízené obsah <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater>, a <xref:System.Windows.Documents.Figure> elementy.  
  
-   <xref:System.Windows.Documents.ListItemCollection>: Tok obsahu elementu, který představuje konkrétní položku obsahu v seřazená nebo je neuspořádaného <xref:System.Windows.Documents.List>.  
  
 Můžete upravit (Přidat nebo odebrat položky) z těchto kolekcí pomocí příslušné vlastnosti **Inlines**, **bloky**, a **položky ListItems**. Následující příklady ukazují, jak pracovat s obsah rozpětí pomocí **Inlines** vlastnost.  
  
> [!NOTE]
>  Tabulka používá několik kolekcí pro práci s obsahem, ale nejsou popsané v tomto poli. Další informace najdete v tématu [tabulky přehled](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
 Následující příklad vytvoří novou <xref:System.Windows.Documents.Span> objekt a používá `Add` metoda pro přidání textu se spouští jako obsahu podřízené objekty <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Následující příklad vytvoří novou <xref:System.Windows.Documents.Run> elementu a vloží ho od začátku <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Následující příklad odstraní poslední <xref:System.Windows.Documents.Inline> element v <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Následující příklad odebere všechny obsahu (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Typy, které sdílejí tento Model obsahu  
 Následující typy dědí <xref:System.Windows.Documents.TextElement> třídy a může se použít k zobrazení obsahu popsané v tomto přehledu.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Všimněte si, že tento seznam obsahuje pouze neabstraktní typy distribuované s [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Může používat jiné typy, které dědí od <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Typy, které může obsahovat objekty TextElement  
 V tématu [modelu obsahu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Viz také  
 [Manipulace s FlowDocument prostřednictvím vlastnosti bloky](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Manipulace s toku obsahu prvků prostřednictvím vlastnost bloky](../../../../docs/framework/wpf/advanced/how-to-manipulate-flow-content-elements-through-the-blocks-property.md)  
 [Manipulace s FlowDocument prostřednictvím vlastnosti bloky](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [Manipulace se sloupci tabulky pomocí vlastnosti sloupce](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)  
 [Manipulaci se skupinami řádek tabulky pomocí vlastnosti RowGroups](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
