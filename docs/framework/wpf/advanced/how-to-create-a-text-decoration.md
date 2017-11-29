---
title: "Postupy: Vytvoření dekorace textu"
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9229ce86dbe640c4eb960c455dd049ff40b38d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-text-decoration"></a>Postupy: Vytvoření dekorace textu
A <xref:System.Windows.TextDecoration> objekt je visual dekoru můžete přidat do textu. Existují čtyři typy textové dekorace: podtržení, standardních hodnot, přeškrtnutí a čáry nahoře. Následující příklad ukazuje umístění textové dekorace textu.  
  
 ![Diagram umístění textové dekorace](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")  
Příklad textové dekorace typů  
  
 Chcete-li přidat textové dekorace na text, vytvořte <xref:System.Windows.TextDecoration> objektu a upravit její vlastnosti. Použití <xref:System.Windows.TextDecoration.Location%2A> vlastnosti k určení, kde textová dekorace se zobrazí, jako je například podtržení. Použití <xref:System.Windows.TextDecoration.Pen%2A> vlastnosti a určit vzhled textová dekorace, jako je plné výplně nebo barva barevného přechodu. Pokud nezadáte hodnotu <xref:System.Windows.TextDecoration.Pen%2A> vlastnost dekorace výchozí hodnoty pro stejnou barvu jako text. Jakmile definujete <xref:System.Windows.TextDecoration> objektu, přidejte ho do <xref:System.Windows.TextDecorations> kolekce objekt požadovaná textu.  
  
 Následující příklad ukazuje textové dekorace něhož má byly použity lineární štětce přechodu a pera přerušovanou.  
  
 ![Textové dekorace s lineárního přechodu podtržení](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")  
Příklad podtržení navržen s lineárního přechodu štětce a přerušovanou pera  
  
 <xref:System.Windows.Documents.Hyperlink> Je objekt na úrovni toku obsahu element, který umožňuje hostitele hypertextové odkazy v rámci toku obsahu. Ve výchozím nastavení <xref:System.Windows.Documents.Hyperlink> používá <xref:System.Windows.TextDecoration> objekt, který chcete zobrazit podtržení. <xref:System.Windows.TextDecoration>objekty lze náročné vytvořit instanci, výkonu, zejména pokud máte mnoho <xref:System.Windows.Documents.Hyperlink> objekty. Pokud provedete rozsáhlé používání šířky <xref:System.Windows.Documents.Hyperlink> elementy, možná budete chtít zvážit zobrazující podtržení jenom v případě, že aktivuje událost, například <xref:System.Windows.ContentElement.MouseEnter> událostí.  
  
 V následujícím příkladu je, že podtržení odkazu "Moje MSN" dynamické – zobrazí se pouze když <xref:System.Windows.ContentElement.MouseEnter> je aktivována událost.  
  
 ![Hypertextové odkazy zobrazující objekty TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Hypertextové odkazy definované s objekty TextDecorations  
  
 Další informace najdete v tématu [určit, zda hypertextový odkaz je podtržený](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kódu textové dekorace podtržení, které používá výchozí hodnota písma.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 V následujícím příkladu kódu textové dekorace podtržení, které se vytvoří s plnobarevné štětce pro pero.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 V následujícím příkladu kódu textové dekorace podtržení, které se vytvoří s lineární štětce přechodu pro přerušovanou pera.  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [Zadejte, že zda hypertextový odkaz jsou podtržené.](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
