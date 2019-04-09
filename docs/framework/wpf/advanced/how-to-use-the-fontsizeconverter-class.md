---
title: 'Postupy: Použití třídy FontSizeConverter'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: f33a297ae07d5509d2b4d9a98636086ac433a57f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088181"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>Postupy: Použití třídy FontSizeConverter
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak vytvořit instanci <xref:System.Windows.FontSizeConverter> a použít ho ke změně velikosti písma.  
  
 Příklad definuje vlastní metodu nazvanou `changeSize` , která převede obsah <xref:System.Windows.Controls.ListBoxItem>, jak jsou definovány v samostatném [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru, do instance <xref:System.Double>nebo novější do <xref:System.String>. Tato metoda předává <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.FontSizeConverter> objekt, který převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do instance <xref:System.Double>. Tato hodnota je pak předán zpět jako hodnotu <xref:System.Windows.Controls.TextBlock.FontSize%2A> vlastnost <xref:System.Windows.Controls.TextBlock> elementu.  
  
 Tento příklad také definuje druhý vlastní metodu, která je volána `changeFamily`. Tato metoda převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> k <xref:System.String>a poté předá tuto hodnotu <xref:System.Windows.Controls.TextBlock.FontFamily%2A> vlastnost <xref:System.Windows.Controls.TextBlock> elementu.  
  
 V tomto příkladu se nespustí.  
  
 [!code-csharp[FontSizeConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FontSizeConverter>
