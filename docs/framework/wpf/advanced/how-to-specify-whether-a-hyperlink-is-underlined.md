---
title: 'Postupy: Určení podtržení hypertextového odkazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 5718912e24a0697f209669b0ab4e7f4df1765ed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943946"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a>Postupy: Určení podtržení hypertextového odkazu
<xref:System.Windows.Documents.Hyperlink> Je objekt, který vám umožní hostitele hypertextové odkazy do plovoucího obsahu toku na úrovni vložení obsahu elementu. Ve výchozím nastavení <xref:System.Windows.Documents.Hyperlink> používá <xref:System.Windows.TextDecoration> zobrazíte podtržení. <xref:System.Windows.TextDecoration> objekty lze vytvořit instanci, náročné na výkon, zejména v případě, že budete mít mnoho <xref:System.Windows.Documents.Hyperlink> objekty. Pokud provedete převážně <xref:System.Windows.Documents.Hyperlink> prvky, možná budete chtít zvážit zobrazující podtržení jenom v případě, že se aktivuje událost, například <xref:System.Windows.ContentElement.MouseEnter> událostí.  
  
 V následujícím příkladu je dynamický podtržení pro odkaz "My MSN", to znamená, zobrazí se jenom v případě <xref:System.Windows.ContentElement.MouseEnter> událost se aktivuje.  
  
  ![Zobrazení TextDecorations hypertextových odkazů](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)  

## <a name="example"></a>Příklad  
 Následující ukázkový kód <xref:System.Windows.Documents.Hyperlink> definována a nemusíte podtržení:  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 Následující příklad kódu ukazuje, jak vytvořit podtržení pro <xref:System.Windows.Documents.Hyperlink> na <xref:System.Windows.ContentElement.MouseEnter> události a odeberte na <xref:System.Windows.ContentElement.MouseLeave> událostí.  
  
 [!code-csharp[Performance#PerformanceSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Vytvoření dekorace textu](how-to-create-a-text-decoration.md)
