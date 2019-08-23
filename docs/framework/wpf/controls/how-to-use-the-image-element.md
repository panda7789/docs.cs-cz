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
ms.openlocfilehash: 164eee7c10d9e388c6e6ee695af479ca2d6974b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958316"
---
# <a name="how-to-use-the-image-element"></a>Postupy: Použití elementu obrázku
Tento příklad ukazuje, jak zahrnout obrázky do aplikace pomocí <xref:System.Windows.Controls.Image> elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vykreslit obrázek 200 pixelů na šířku. V tomto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příkladu se k definování obrázku používá syntaxe atributů i syntaxe značek vlastností. Další informace o syntaxi atributů a syntaxi vlastností najdete v tématu [Přehled vlastností závislosti](../advanced/dependency-properties-overview.md). <xref:System.Windows.Media.Imaging.BitmapImage> Slouží k definování zdrojových dat obrázku a je explicitně definován pro příklad syntaxe značky Property. <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> Kromě toho <xref:System.Windows.Media.Imaging.BitmapImage> je v nastavení nastaveno na stejnou <xref:System.Windows.Controls.Image>šířku jako <xref:System.Windows.FrameworkElement.Width%2A> v. K tomu je potřeba zajistit, aby se k vykreslování obrázku používalo minimální množství paměti.  
  
> [!NOTE]
> Obecně platí, že pokud chcete určit velikost vykresleného obrázku, zadejte pouze <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> nebo, ale ne obojí. Pokud zadáte pouze jednu hodnotu, zůstane zachován poměr stran obrázku. V opačném případě se obrázek neočekávaně zobrazuje roztažené nebo pokřivení. Pro řízení chování roztažení obrázku použijte <xref:System.Windows.Controls.Image.Stretch%2A> vlastnosti a. <xref:System.Windows.Controls.Image.StretchDirection%2A>  
  
> [!NOTE]
> <xref:System.Windows.FrameworkElement.Width%2A> Když zadáte velikost obrázku buď nebo <xref:System.Windows.FrameworkElement.Height%2A>, měli byste také nastavit buď <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> nebo <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> na stejnou velikost.  
  
 <xref:System.Windows.Controls.Image.Stretch%2A> Vlastnost určuje, jak je zdroj obrázku roztažen tak, aby vyplnil prvek obrázku. Další informace najdete v tématu <xref:System.Windows.Media.Stretch> výčet.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vykreslit obrázek 200 pixelů v širším formátu pomocí kódu.  
  
> [!NOTE]
> Vlastnosti <xref:System.Windows.Media.Imaging.BitmapImage> nastavení se musí provádět <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> v rámci bloku <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> a.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled obrázků](../graphics-multimedia/imaging-overview.md)
