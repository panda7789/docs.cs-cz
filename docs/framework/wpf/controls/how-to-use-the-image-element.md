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
ms.openlocfilehash: ec3ca16915038ebbb68df24bfd071168c346663d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372461"
---
# <a name="how-to-use-the-image-element"></a>Postupy: Použití elementu obrázku
Tento příklad ukazuje, jak zahrnout i obrázky v aplikaci s použitím <xref:System.Windows.Controls.Image> elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak Vykreslit obrázek 200 pixelů na šířku. V tomto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] například syntaxe atributu a vlastnost syntaxe značek se používají k definování image. Další informace o syntaxi atributů a vlastnost syntaxe, naleznete v tématu [přehled vlastností závislosti](../advanced/dependency-properties-overview.md). A <xref:System.Windows.Media.Imaging.BitmapImage> se používá k definování zdroje dat na obrázku a není výslovně uveden syntaxe například vlastnost tag. Kromě toho <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> z <xref:System.Windows.Media.Imaging.BitmapImage> je nastavena na šířku stejné jako <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Controls.Image>. To slouží k zajištění, že minimální velikost paměti se používá vykreslování na obrázku.  
  
> [!NOTE]
>  Obecně platí, pokud chcete určit velikost vykresleného obrázku, zadejte pouze <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A> , ale ne obojí. Pokud zadáte pouze jeden, poměr stran obrázku je zachován. Na obrázku v opačném případě může být neočekávaně v roztažený nebo pokřivený. K řízení na obrázku je roztažení chování, použijte <xref:System.Windows.Controls.Image.Stretch%2A> a <xref:System.Windows.Controls.Image.StretchDirection%2A> vlastnosti.  
  
> [!NOTE]
>  Pokud zadáte velikost obrázku s oběma <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A>, také byste měli nastavit buď <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> nebo <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> do příslušných stejnou velikost.  
  
 <xref:System.Windows.Controls.Image.Stretch%2A> Vlastnost určuje, jak je zdroj obrázku roztažený tak, aby vyplnil elementu obrázku. Další informace najdete v tématu <xref:System.Windows.Media.Stretch> výčtu.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak Vykreslit obrázek 200 pixelů pomocí kódu.  
  
> [!NOTE]
>  Nastavení <xref:System.Windows.Media.Imaging.BitmapImage> vlastností je třeba provést v rámci <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> a <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> bloku.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled obrázků](../graphics-multimedia/imaging-overview.md)
