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
ms.locfileid: "33555909"
---
# <a name="how-to-use-the-image-element"></a><span data-ttu-id="68974-102">Postupy: Použití elementu obrázku</span><span class="sxs-lookup"><span data-stu-id="68974-102">How to: Use the Image Element</span></span>
<span data-ttu-id="68974-103">Tento příklad ukazuje, jak mají být zahrnuty bitové kopie aplikace pomocí <xref:System.Windows.Controls.Image> elementu.</span><span class="sxs-lookup"><span data-stu-id="68974-103">This example shows how to include images in an application by using the <xref:System.Windows.Controls.Image> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68974-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="68974-104">Example</span></span>  
 <span data-ttu-id="68974-105">Následující příklad ukazuje, jak Vykreslit obrázek 200 pixelů.</span><span class="sxs-lookup"><span data-stu-id="68974-105">The following example shows how to render an image 200 pixels wide.</span></span> <span data-ttu-id="68974-106">V tomto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příkladu atribut syntaxe a syntaxe značek vlastnost slouží k určení bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="68974-106">In this [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example, both attribute syntax and property tag syntax are used to define the image.</span></span> <span data-ttu-id="68974-107">Další informace o syntaxi atributů a vlastnost syntaxi najdete v části [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="68974-107">For more information on attribute syntax and property syntax, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span> <span data-ttu-id="68974-108">A <xref:System.Windows.Media.Imaging.BitmapImage> se používá k definování obrázku zdrojová data a byl explicitně definován pro příklad syntaxe vlastnost značky.</span><span class="sxs-lookup"><span data-stu-id="68974-108">A <xref:System.Windows.Media.Imaging.BitmapImage> is used to define the image's source data and is explicitly defined for the property tag syntax example.</span></span> <span data-ttu-id="68974-109">Kromě toho <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> z <xref:System.Windows.Media.Imaging.BitmapImage> je nastaven na šířku stejné jako <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Controls.Image>.</span><span class="sxs-lookup"><span data-stu-id="68974-109">In addition, the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> of the <xref:System.Windows.Media.Imaging.BitmapImage> is set to the same width as the <xref:System.Windows.FrameworkElement.Width%2A> of the <xref:System.Windows.Controls.Image>.</span></span> <span data-ttu-id="68974-110">Tomu je potřeba zajistit, že minimální množství paměti se používá vykreslování obrázku.</span><span class="sxs-lookup"><span data-stu-id="68974-110">This is done to ensure that the minimum amount of memory is used rendering the image.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68974-111">Obecně platí, pokud chcete určit velikost vykreslené bitové kopie, zadejte pouze <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A> , ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="68974-111">In general, if you want to specify the size of a rendered image, specify only the <xref:System.Windows.FrameworkElement.Width%2A> or the <xref:System.Windows.FrameworkElement.Height%2A> but not both.</span></span> <span data-ttu-id="68974-112">Pokud zadáte jenom jeden, se zachová poměr stran obrázku.</span><span class="sxs-lookup"><span data-stu-id="68974-112">If you only specify one, the image's aspect ratio is preserved.</span></span> <span data-ttu-id="68974-113">Bitovou kopii, jinak hodnota neočekávaně může být roztažený nebo pokřivený.</span><span class="sxs-lookup"><span data-stu-id="68974-113">Otherwise, the image may unexpectedly appear stretched or warped.</span></span> <span data-ttu-id="68974-114">K řízení bitovou kopii je roztažení chování, použijte <xref:System.Windows.Controls.Image.Stretch%2A> a <xref:System.Windows.Controls.Image.StretchDirection%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="68974-114">To control the image's stretching behavior, use the <xref:System.Windows.Controls.Image.Stretch%2A> and <xref:System.Windows.Controls.Image.StretchDirection%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68974-115">Pokud zadáte velikost bitové kopie s buď <xref:System.Windows.FrameworkElement.Width%2A> nebo <xref:System.Windows.FrameworkElement.Height%2A>, také byste měli nastavit buď <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> nebo <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> na stejné odpovídající velikost.</span><span class="sxs-lookup"><span data-stu-id="68974-115">When you specify the size of an image with either <xref:System.Windows.FrameworkElement.Width%2A> or <xref:System.Windows.FrameworkElement.Height%2A>, you should also set either <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> or <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> to the same respective size.</span></span>  
  
 <span data-ttu-id="68974-116"><xref:System.Windows.Controls.Image.Stretch%2A> Vlastnost určuje, jak zdroj bitové kopie je roztažen tak, aby vyplnění element obrázku.</span><span class="sxs-lookup"><span data-stu-id="68974-116">The <xref:System.Windows.Controls.Image.Stretch%2A> property determines how the image source is stretched to fill the image element.</span></span> <span data-ttu-id="68974-117">Další informace najdete v tématu <xref:System.Windows.Media.Stretch> výčtu.</span><span class="sxs-lookup"><span data-stu-id="68974-117">For more information, see the <xref:System.Windows.Media.Stretch> enumeration.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="68974-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="68974-118">Example</span></span>  
 <span data-ttu-id="68974-119">Následující příklad ukazuje, jak Vykreslit obrázek 200 pixelů pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="68974-119">The following example shows how to render an image 200 pixels wide using code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68974-120">Nastavení <xref:System.Windows.Media.Imaging.BitmapImage> vlastnosti je třeba provést v rámci <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> a <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> bloku.</span><span class="sxs-lookup"><span data-stu-id="68974-120">Setting <xref:System.Windows.Media.Imaging.BitmapImage> properties must be done within a <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> and <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> block.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="68974-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="68974-121">See Also</span></span>  
 [<span data-ttu-id="68974-122">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="68974-122">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
