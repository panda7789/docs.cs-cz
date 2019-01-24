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
ms.openlocfilehash: b85bbaed13d9406f85c62a9a5bc5ca220d90b0b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607943"
---
# <a name="how-to-create-a-text-decoration"></a>Postupy: Vytvoření dekorace textu
A <xref:System.Windows.TextDecoration> objekt je vizuální dekoru můžete přidat do textu. Existují čtyři druhy dekorace textu: podtržení, Směrný plán, přeškrtnutí a přeškrtnutí. Následující příklad ukazuje umístění dekorace textu vzhledem k textu.  
  
 ![Diagram umístění textové dekorace](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")  
Příklad typů dekorace textu  
  
 Pro přidání do textové dekorace textu, vytvořte <xref:System.Windows.TextDecoration> objekt a upravit její vlastnosti. Použití <xref:System.Windows.TextDecoration.Location%2A> vlastnosti a určit, kde dekorace textu se zobrazí, jako je například podtržení. Použití <xref:System.Windows.TextDecoration.Pen%2A> vlastnosti k určení vzhledu textové dekorace, jako je například plné barvy nebo barevný přechod. Pokud nezadáte hodnotu <xref:System.Windows.TextDecoration.Pen%2A> vlastnost dekorace výchozí hodnoty na stejnou barvu jako text. Po definování <xref:System.Windows.TextDecoration> objektu, přidejte ji tak <xref:System.Windows.TextDecorations> kolekce objektu požadovaný text.  
  
 Následující příklad ukazuje dekorace textu, který byl navržen štětec lineárního přechodu a přerušované pera.  
  
 ![Dekorace textu pomocí lineárního přechodu podtržení](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")  
Příklad podtržení stylem lineárního přechodu štětce a přerušované pera  
  
 <xref:System.Windows.Documents.Hyperlink> Je objekt, který vám umožní hostitele hypertextové odkazy do plovoucího obsahu toku na úrovni vložení obsahu elementu. Ve výchozím nastavení <xref:System.Windows.Documents.Hyperlink> používá <xref:System.Windows.TextDecoration> zobrazíte podtržení. <xref:System.Windows.TextDecoration> objekty lze vytvořit instanci, náročné na výkon, zejména v případě, že budete mít mnoho <xref:System.Windows.Documents.Hyperlink> objekty. Pokud provedete převážně <xref:System.Windows.Documents.Hyperlink> prvky, možná budete chtít zvážit zobrazující podtržení jenom v případě, že se aktivuje událost, například <xref:System.Windows.ContentElement.MouseEnter> událostí.  
  
 V následujícím příkladu je dynamický podtržení pro odkaz "My MSN" – zobrazí se jenom v případě <xref:System.Windows.ContentElement.MouseEnter> událost se aktivuje.  
  
 ![Hypertextové odkazy zobrazení TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Hypertextové odkazy definované pomocí TextDecorations  
  
 Další informace najdete v tématu [podtržený zadejte hypertextového odkazu](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kódu používá textové dekorace podtržení výchozí písmo hodnotu.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 V následujícím příkladu kódu je vytvořen textové dekorace podtržení s štětec jednotné barvy pro pero.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 V následujícím příkladu kódu je vytvořen textové dekorace podtržení s přerušované pera štětec lineárního přechodu.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Určení podtržení hypertextového odkazu](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
