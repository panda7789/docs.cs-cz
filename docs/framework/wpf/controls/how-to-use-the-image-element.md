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
# <a name="how-to-use-the-image-element"></a><span data-ttu-id="ced02-102">Postupy: Použití elementu obrázku</span><span class="sxs-lookup"><span data-stu-id="ced02-102">How to: Use the Image Element</span></span>
<span data-ttu-id="ced02-103">Tento příklad ukazuje, jak zahrnout obrázky do aplikace pomocí <xref:System.Windows.Controls.Image> elementu.</span><span class="sxs-lookup"><span data-stu-id="ced02-103">This example shows how to include images in an application by using the <xref:System.Windows.Controls.Image> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ced02-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ced02-104">Example</span></span>  
 <span data-ttu-id="ced02-105">Následující příklad ukazuje, jak vykreslit obrázek 200 pixelů na šířku.</span><span class="sxs-lookup"><span data-stu-id="ced02-105">The following example shows how to render an image 200 pixels wide.</span></span> <span data-ttu-id="ced02-106">V tomto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příkladu se k definování obrázku používá syntaxe atributů i syntaxe značek vlastností.</span><span class="sxs-lookup"><span data-stu-id="ced02-106">In this [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example, both attribute syntax and property tag syntax are used to define the image.</span></span> <span data-ttu-id="ced02-107">Další informace o syntaxi atributů a syntaxi vlastností najdete v tématu [Přehled vlastností závislosti](../advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ced02-107">For more information on attribute syntax and property syntax, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span> <span data-ttu-id="ced02-108"><xref:System.Windows.Media.Imaging.BitmapImage> Slouží k definování zdrojových dat obrázku a je explicitně definován pro příklad syntaxe značky Property.</span><span class="sxs-lookup"><span data-stu-id="ced02-108">A <xref:System.Windows.Media.Imaging.BitmapImage> is used to define the image's source data and is explicitly defined for the property tag syntax example.</span></span> <span data-ttu-id="ced02-109"><xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> Kromě toho <xref:System.Windows.Media.Imaging.BitmapImage> je v nastavení nastaveno na stejnou <xref:System.Windows.Controls.Image>šířku jako <xref:System.Windows.FrameworkElement.Width%2A> v.</span><span class="sxs-lookup"><span data-stu-id="ced02-109">In addition, the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> of the <xref:System.Windows.Media.Imaging.BitmapImage> is set to the same width as the <xref:System.Windows.FrameworkElement.Width%2A> of the <xref:System.Windows.Controls.Image>.</span></span> <span data-ttu-id="ced02-110">K tomu je potřeba zajistit, aby se k vykreslování obrázku používalo minimální množství paměti.</span><span class="sxs-lookup"><span data-stu-id="ced02-110">This is done to ensure that the minimum amount of memory is used rendering the image.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ced02-111">Obecně platí, že pokud chcete určit velikost vykresleného obrázku, zadejte pouze <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> nebo, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="ced02-111">In general, if you want to specify the size of a rendered image, specify only the <xref:System.Windows.FrameworkElement.Width%2A> or the <xref:System.Windows.FrameworkElement.Height%2A> but not both.</span></span> <span data-ttu-id="ced02-112">Pokud zadáte pouze jednu hodnotu, zůstane zachován poměr stran obrázku.</span><span class="sxs-lookup"><span data-stu-id="ced02-112">If you only specify one, the image's aspect ratio is preserved.</span></span> <span data-ttu-id="ced02-113">V opačném případě se obrázek neočekávaně zobrazuje roztažené nebo pokřivení.</span><span class="sxs-lookup"><span data-stu-id="ced02-113">Otherwise, the image may unexpectedly appear stretched or warped.</span></span> <span data-ttu-id="ced02-114">Pro řízení chování roztažení obrázku použijte <xref:System.Windows.Controls.Image.Stretch%2A> vlastnosti a. <xref:System.Windows.Controls.Image.StretchDirection%2A></span><span class="sxs-lookup"><span data-stu-id="ced02-114">To control the image's stretching behavior, use the <xref:System.Windows.Controls.Image.Stretch%2A> and <xref:System.Windows.Controls.Image.StretchDirection%2A> properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ced02-115"><xref:System.Windows.FrameworkElement.Width%2A> Když zadáte velikost obrázku buď nebo <xref:System.Windows.FrameworkElement.Height%2A>, měli byste také nastavit buď <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> nebo <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> na stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="ced02-115">When you specify the size of an image with either <xref:System.Windows.FrameworkElement.Width%2A> or <xref:System.Windows.FrameworkElement.Height%2A>, you should also set either <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> or <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> to the same respective size.</span></span>  
  
 <span data-ttu-id="ced02-116"><xref:System.Windows.Controls.Image.Stretch%2A> Vlastnost určuje, jak je zdroj obrázku roztažen tak, aby vyplnil prvek obrázku.</span><span class="sxs-lookup"><span data-stu-id="ced02-116">The <xref:System.Windows.Controls.Image.Stretch%2A> property determines how the image source is stretched to fill the image element.</span></span> <span data-ttu-id="ced02-117">Další informace najdete v tématu <xref:System.Windows.Media.Stretch> výčet.</span><span class="sxs-lookup"><span data-stu-id="ced02-117">For more information, see the <xref:System.Windows.Media.Stretch> enumeration.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="ced02-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="ced02-118">Example</span></span>  
 <span data-ttu-id="ced02-119">Následující příklad ukazuje, jak vykreslit obrázek 200 pixelů v širším formátu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="ced02-119">The following example shows how to render an image 200 pixels wide using code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ced02-120">Vlastnosti <xref:System.Windows.Media.Imaging.BitmapImage> nastavení se musí provádět <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> v rámci bloku <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> a.</span><span class="sxs-lookup"><span data-stu-id="ced02-120">Setting <xref:System.Windows.Media.Imaging.BitmapImage> properties must be done within a <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> and <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> block.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="ced02-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ced02-121">See also</span></span>

- [<span data-ttu-id="ced02-122">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="ced02-122">Imaging Overview</span></span>](../graphics-multimedia/imaging-overview.md)
