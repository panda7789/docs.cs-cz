---
title: 'Postupy: Použití elementu obrázku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Image
- Image control [WPF]
- rendering images [WPF]
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
ms.openlocfilehash: 11481533af7b3ad75b571f9f97251c123e0af1b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-image-element"></a>Postupy: Použití elementu obrázku
Tento příklad ukazuje, jak mají být zahrnuty bitové kopie aplikace pomocí <xref:System.Windows.Controls.Image> elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak Vykreslit obrázek 200 pixelů. V tomto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příkladu atribut syntaxe a syntaxe značek vlastnost slouží k určení bitovou kopii. Další informace o syntaxi atributů a vlastnost syntaxi najdete v části [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). A <xref:System.Windows.Media.Imaging.BitmapImage> se používá k definování obrázku zdrojová data a byl explicitně definován pro příklad syntaxe vlastnost značky. Kromě toho <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> z <xref:System.Windows.Media.Imaging.BitmapImage> je nastaven na šířku stejné jako <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Controls.Image>. Tomu je potřeba zajistit, že minimální množství paměti se používá vykreslování obrázku.  
  
> [!NOTE]
>  Obecně platí, pokud chcete určit velikost vykreslené bitové kopie, zadejte pouze <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A> , ale ne obojí. Pokud zadáte jenom jeden, se zachová poměr stran obrázku. Bitovou kopii, jinak hodnota neočekávaně může být roztažený nebo pokřivený. K řízení bitovou kopii je roztažení chování, použijte <xref:System.Windows.Controls.Image.Stretch%2A> a <xref:System.Windows.Controls.Image.StretchDirection%2A> vlastnosti.  
  
> [!NOTE]
>  Pokud zadáte velikost bitové kopie s buď <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A>, také byste měli nastavit buď <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> nebo <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> na stejné odpovídající velikost.  
  
 <xref:System.Windows.Controls.Image.Stretch%2A> Vlastnost určuje, jak zdroj bitové kopie je roztažen tak, aby vyplnění element obrázku. Další informace najdete v tématu <xref:System.Windows.Media.Stretch> výčtu.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak Vykreslit obrázek 200 pixelů pomocí kódu.  
  
> [!NOTE]
>  Nastavení <xref:System.Windows.Media.Imaging.BitmapImage> vlastnosti je třeba provést v rámci <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> a <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> bloku.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled obrázků](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
