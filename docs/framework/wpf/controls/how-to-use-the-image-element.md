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
ms.openlocfilehash: d7aa2e0e9bd33dfcd68bd19b5084fa1666232a5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530798"
---
# <a name="how-to-use-the-image-element"></a><span data-ttu-id="618ff-102">Postupy: Použití elementu obrázku</span><span class="sxs-lookup"><span data-stu-id="618ff-102">How to: Use the Image Element</span></span>
<span data-ttu-id="618ff-103">Tento příklad ukazuje, jak zahrnout i obrázky v aplikaci s použitím <xref:System.Windows.Controls.Image> elementu.</span><span class="sxs-lookup"><span data-stu-id="618ff-103">This example shows how to include images in an application by using the <xref:System.Windows.Controls.Image> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="618ff-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="618ff-104">Example</span></span>  
 <span data-ttu-id="618ff-105">Následující příklad ukazuje, jak Vykreslit obrázek 200 pixelů na šířku.</span><span class="sxs-lookup"><span data-stu-id="618ff-105">The following example shows how to render an image 200 pixels wide.</span></span> <span data-ttu-id="618ff-106">V tomto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] například syntaxe atributu a vlastnost syntaxe značek se používají k definování image.</span><span class="sxs-lookup"><span data-stu-id="618ff-106">In this [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example, both attribute syntax and property tag syntax are used to define the image.</span></span> <span data-ttu-id="618ff-107">Další informace o syntaxi atributů a vlastnost syntaxe, naleznete v tématu [přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="618ff-107">For more information on attribute syntax and property syntax, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span> <span data-ttu-id="618ff-108">A <xref:System.Windows.Media.Imaging.BitmapImage> se používá k definování zdroje dat na obrázku a není výslovně uveden syntaxe například vlastnost tag.</span><span class="sxs-lookup"><span data-stu-id="618ff-108">A <xref:System.Windows.Media.Imaging.BitmapImage> is used to define the image's source data and is explicitly defined for the property tag syntax example.</span></span> <span data-ttu-id="618ff-109">Kromě toho <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> z <xref:System.Windows.Media.Imaging.BitmapImage> je nastavena na šířku stejné jako <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Controls.Image>.</span><span class="sxs-lookup"><span data-stu-id="618ff-109">In addition, the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> of the <xref:System.Windows.Media.Imaging.BitmapImage> is set to the same width as the <xref:System.Windows.FrameworkElement.Width%2A> of the <xref:System.Windows.Controls.Image>.</span></span> <span data-ttu-id="618ff-110">To slouží k zajištění, že minimální velikost paměti se používá vykreslování na obrázku.</span><span class="sxs-lookup"><span data-stu-id="618ff-110">This is done to ensure that the minimum amount of memory is used rendering the image.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="618ff-111">Obecně platí, pokud chcete určit velikost vykresleného obrázku, zadejte pouze <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A> , ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="618ff-111">In general, if you want to specify the size of a rendered image, specify only the <xref:System.Windows.FrameworkElement.Width%2A> or the <xref:System.Windows.FrameworkElement.Height%2A> but not both.</span></span> <span data-ttu-id="618ff-112">Pokud zadáte pouze jeden, poměr stran obrázku je zachován.</span><span class="sxs-lookup"><span data-stu-id="618ff-112">If you only specify one, the image's aspect ratio is preserved.</span></span> <span data-ttu-id="618ff-113">Na obrázku v opačném případě může být neočekávaně v roztažený nebo pokřivený.</span><span class="sxs-lookup"><span data-stu-id="618ff-113">Otherwise, the image may unexpectedly appear stretched or warped.</span></span> <span data-ttu-id="618ff-114">K řízení na obrázku je roztažení chování, použijte <xref:System.Windows.Controls.Image.Stretch%2A> a <xref:System.Windows.Controls.Image.StretchDirection%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="618ff-114">To control the image's stretching behavior, use the <xref:System.Windows.Controls.Image.Stretch%2A> and <xref:System.Windows.Controls.Image.StretchDirection%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="618ff-115">Pokud zadáte velikost obrázku s oběma <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A>, také byste měli nastavit buď <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> nebo <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> do příslušných stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="618ff-115">When you specify the size of an image with either <xref:System.Windows.FrameworkElement.Width%2A> or <xref:System.Windows.FrameworkElement.Height%2A>, you should also set either <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> or <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> to the same respective size.</span></span>  
  
 <span data-ttu-id="618ff-116"><xref:System.Windows.Controls.Image.Stretch%2A> Vlastnost určuje, jak je zdroj obrázku roztažený tak, aby vyplnil elementu obrázku.</span><span class="sxs-lookup"><span data-stu-id="618ff-116">The <xref:System.Windows.Controls.Image.Stretch%2A> property determines how the image source is stretched to fill the image element.</span></span> <span data-ttu-id="618ff-117">Další informace najdete v tématu <xref:System.Windows.Media.Stretch> výčtu.</span><span class="sxs-lookup"><span data-stu-id="618ff-117">For more information, see the <xref:System.Windows.Media.Stretch> enumeration.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="618ff-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="618ff-118">Example</span></span>  
 <span data-ttu-id="618ff-119">Následující příklad ukazuje, jak Vykreslit obrázek 200 pixelů pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="618ff-119">The following example shows how to render an image 200 pixels wide using code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="618ff-120">Nastavení <xref:System.Windows.Media.Imaging.BitmapImage> vlastností je třeba provést v rámci <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> a <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> bloku.</span><span class="sxs-lookup"><span data-stu-id="618ff-120">Setting <xref:System.Windows.Media.Imaging.BitmapImage> properties must be done within a <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> and <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> block.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="618ff-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="618ff-121">See also</span></span>
- [<span data-ttu-id="618ff-122">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="618ff-122">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
