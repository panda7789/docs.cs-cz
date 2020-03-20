---
title: 'Postupy: Vytvoření dekorace textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: cf3b3c3bcb75153a0be4f7ced03b38134b79a930
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185926"
---
# <a name="how-to-create-a-text-decoration"></a>Postupy: Vytvoření dekorace textu
Objekt <xref:System.Windows.TextDecoration> je vizuální ozdoba, kterou můžete přidat k textu. Existují čtyři typy textových dekorací: podtržení, účaří, přeškrtávací a nadčár. Následující příklad ukazuje umístění textových dekorací vzhledem k textu.  
  
 ![Diagram typů textových dekorací](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 Chcete-li k textu přidat <xref:System.Windows.TextDecoration> textovou ozdobu, vytvořte objekt a upravte jeho vlastnosti. Pomocí <xref:System.Windows.TextDecoration.Location%2A> vlastnosti určete, kde se zobrazí dekorace textu, například podtržení. <xref:System.Windows.TextDecoration.Pen%2A> Vlastnost í slouží k určení vzhledu dekorace textu, například plné výplně nebo barvy přechodu. Pokud nezadáte hodnotu vlastnosti, <xref:System.Windows.TextDecoration.Pen%2A> dekorace budou mít výchozí hodnotu stejné barvy jako text. Po definování objektu <xref:System.Windows.TextDecoration> jej přidejte <xref:System.Windows.TextDecorations> do kolekce požadovaného textového objektu.  
  
 Následující příklad ukazuje textovou výzdobu, která byla stylizována s lineárním přechodem stopy a přerušované pero.  
  
 ![Dekorace textu s lineárním přechodem podtržení](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 Objekt <xref:System.Windows.Documents.Hyperlink> je prvek obsahu toku na úrovni vložky, který umožňuje hostovat hypertextové odkazy v rámci obsahu toku. Ve výchozím <xref:System.Windows.Documents.Hyperlink> nastavení <xref:System.Windows.TextDecoration> používá objekt k zobrazení podtržení. <xref:System.Windows.TextDecoration>objekty mohou být náročné na výkon k vytvoření <xref:System.Windows.Documents.Hyperlink> instance, zejména pokud máte mnoho objektů. Pokud provedete rozsáhlé <xref:System.Windows.Documents.Hyperlink> použití prvků, můžete zvážit zobrazení podtržení pouze při <xref:System.Windows.ContentElement.MouseEnter> aktivaci události, jako je například událost.  
  
 V následujícím příkladu je podtržení pro odkaz "Moje MSN" <xref:System.Windows.ContentElement.MouseEnter> dynamické – zobrazí se pouze při aktivaci události.  
  
 ![Hypertextové odkazy zobrazující textdekorace](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  

 Další informace naleznete [v tématu Určení, zda je hypertextový odkaz podtržený](how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kódu používá dekorace podtržení textu výchozí hodnotu písma.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 V následujícím příkladu kódu je dekorace podtržení textu vytvořena s plnou barevnou stopou pro pero.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 V následujícím příkladu kódu je vytvořena dekorace podtržení textu s lineárním přechodem pro přerušované pero.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Určení podtržení hypertextového odkazu](how-to-specify-whether-a-hyperlink-is-underlined.md)
