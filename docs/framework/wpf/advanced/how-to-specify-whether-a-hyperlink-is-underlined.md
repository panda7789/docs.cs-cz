---
title: "Postupy: Určení podtržení hypertextového odkazu"
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
helpviewer_keywords: Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7914b3b3332b7ea0abe05b3048b5016888e2d93e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a>Postupy: Určení podtržení hypertextového odkazu
<xref:System.Windows.Documents.Hyperlink> Je objekt na úrovni toku obsahu element, který umožňuje hostitele hypertextové odkazy v rámci toku obsahu. Ve výchozím nastavení <xref:System.Windows.Documents.Hyperlink> používá <xref:System.Windows.TextDecoration> objekt, který chcete zobrazit podtržení. <xref:System.Windows.TextDecoration>objekty lze náročné vytvořit instanci, výkonu, zejména pokud máte mnoho <xref:System.Windows.Documents.Hyperlink> objekty. Pokud provedete rozsáhlé používání šířky <xref:System.Windows.Documents.Hyperlink> elementy, možná budete chtít zvážit zobrazující podtržení jenom v případě, že aktivuje událost, například <xref:System.Windows.ContentElement.MouseEnter> událostí.  
  
 V následujícím příkladu je, že podtržení odkazu "Moje MSN" dynamické – zobrazí se pouze když <xref:System.Windows.ContentElement.MouseEnter> je aktivována událost.  
  
 ![Hypertextové odkazy zobrazující objekty TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Hypertextové odkazy definované s objekty TextDecorations  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje ukázka <xref:System.Windows.Documents.Hyperlink> definované s i bez podtržení, které:  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 Následující příklad kódu ukazuje, jak vytvořit podtržení pro <xref:System.Windows.Documents.Hyperlink> na <xref:System.Windows.ContentElement.MouseEnter> události a odeberte na <xref:System.Windows.ContentElement.MouseLeave> událostí.  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [Optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Vytvoření textové dekorace](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
