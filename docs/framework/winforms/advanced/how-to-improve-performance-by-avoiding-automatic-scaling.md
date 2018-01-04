---
title: "Postupy: Zvýšení výkonu zabráněním automatické změně měřítka"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f49fc4b1e59879b9ecc67295610187fa2e5e80d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a><span data-ttu-id="a870b-102">Postupy: Zvýšení výkonu zabráněním automatické změně měřítka</span><span class="sxs-lookup"><span data-stu-id="a870b-102">How to: Improve Performance by Avoiding Automatic Scaling</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="a870b-103">může automaticky škálovat bitovou kopii, při kreslení, které by snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="a870b-103"> may automatically scale an image as you draw it, which would decrease performance.</span></span> <span data-ttu-id="a870b-104">Alternativně můžete řídit škálování bitovou kopii pomocí předání dimenze cílové obdélníku, které <xref:System.Drawing.Graphics.DrawImage%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a870b-104">Alternatively, you can control the scaling of the image by passing the dimensions of the destination rectangle to the <xref:System.Drawing.Graphics.DrawImage%2A> method.</span></span>  
  
 <span data-ttu-id="a870b-105">Například následující volání do <xref:System.Drawing.Graphics.DrawImage%2A> metoda určuje levého horního rohu (50, 30), ale neurčuje obdélníku cílový.</span><span class="sxs-lookup"><span data-stu-id="a870b-105">For example, the following call to the <xref:System.Drawing.Graphics.DrawImage%2A> method specifies an upper-left corner of (50, 30) but does not specify a destination rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 <span data-ttu-id="a870b-106">I když je to nejjednodušší verze <xref:System.Drawing.Graphics.DrawImage%2A> metoda z hlediska počtu povinnými argumenty, není nutně nejúčinnější.</span><span class="sxs-lookup"><span data-stu-id="a870b-106">Although this is the easiest version of the <xref:System.Drawing.Graphics.DrawImage%2A> method in terms of the number of required arguments, it is not necessarily the most efficient.</span></span> <span data-ttu-id="a870b-107">Pokud řešení používá [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (obvykle 96 bodů na palec) se liší od řešení uložené v <xref:System.Drawing.Image> objekt, pak se <xref:System.Drawing.Graphics.DrawImage%2A> metoda bude změna měřítka obrázku.</span><span class="sxs-lookup"><span data-stu-id="a870b-107">If the resolution used by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (usually 96 dots per inch) is different from the resolution stored in the <xref:System.Drawing.Image> object, then the <xref:System.Drawing.Graphics.DrawImage%2A> method will scale the image.</span></span> <span data-ttu-id="a870b-108">Předpokládejme například, že <xref:System.Drawing.Image> objekt má šířka 216 pixelů a hodnota uložené horizontální rozlišení 72 bodů na palec.</span><span class="sxs-lookup"><span data-stu-id="a870b-108">For example, suppose an <xref:System.Drawing.Image> object has a width of 216 pixels and a stored horizontal resolution value of 72 dots per inch.</span></span> <span data-ttu-id="a870b-109">Protože 216/72 je 3, <xref:System.Drawing.Graphics.DrawImage%2A> bude změna měřítka obrázku tak, aby měl šířku 3 palce s rozlišením 96 dpi.</span><span class="sxs-lookup"><span data-stu-id="a870b-109">Because 216/72 is 3, <xref:System.Drawing.Graphics.DrawImage%2A> will scale the image so that it has a width of 3 inches at a resolution of 96 dots per inch.</span></span> <span data-ttu-id="a870b-110">To znamená <xref:System.Drawing.Graphics.DrawImage%2A> zobrazí obrázek, který obsahuje šířku 96 x 3 = 288 pixelů.</span><span class="sxs-lookup"><span data-stu-id="a870b-110">That is, <xref:System.Drawing.Graphics.DrawImage%2A> will display an image that has a width of 96x3 = 288 pixels.</span></span>  
  
 <span data-ttu-id="a870b-111">I když se liší od 96 bodů na palec, rozlišení obrazovky [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bude pravděpodobně škálování bitovou kopii jako kdyby k rozlišení 96 dpi.</span><span class="sxs-lookup"><span data-stu-id="a870b-111">Even if your screen resolution is different from 96 dots per inch, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] will probably scale the image as if the screen resolution were 96 dots per inch.</span></span> <span data-ttu-id="a870b-112">Je to způsobeno [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> objekt je přidružený ke kontextu zařízení a kdy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dotazy kontext zařízení pro rozlišení obrazovky, výsledek je obvykle 96, bez ohledu na skutečné rozlišení.</span><span class="sxs-lookup"><span data-stu-id="a870b-112">That is because a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> object is associated with a device context, and when [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] queries the device context for the screen resolution, the result is usually 96, regardless of the actual screen resolution.</span></span> <span data-ttu-id="a870b-113">Automatické škálování zadáním cílového obdélníku v se můžete vyhnout <xref:System.Drawing.Graphics.DrawImage%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a870b-113">You can avoid automatic scaling by specifying the destination rectangle in the <xref:System.Drawing.Graphics.DrawImage%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a870b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a870b-114">Example</span></span>  
 <span data-ttu-id="a870b-115">Následující příklad nevykresluje stejnou bitovou kopii dvakrát.</span><span class="sxs-lookup"><span data-stu-id="a870b-115">The following example draws the same image twice.</span></span> <span data-ttu-id="a870b-116">V prvním případě nejsou zadané šířky a výšky obdélníku cílové a bitovou kopii je automaticky škálovat.</span><span class="sxs-lookup"><span data-stu-id="a870b-116">In the first case, the width and height of the destination rectangle are not specified, and the image is automatically scaled.</span></span> <span data-ttu-id="a870b-117">V druhém případě šířka a výška (měřeno v pixelech) rámeček cílové zadat být stejné jako šířka a výška původní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="a870b-117">In the second case, the width and height (measured in pixels) of the destination rectangle are specified to be the same as the width and height of the original image.</span></span> <span data-ttu-id="a870b-118">Následující obrázek znázorňuje obrázek se vykresluje dvakrát.</span><span class="sxs-lookup"><span data-stu-id="a870b-118">The following illustration shows the image rendered twice.</span></span>  
  
 <span data-ttu-id="a870b-119">![Škálovat Texture](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")</span><span class="sxs-lookup"><span data-stu-id="a870b-119">![Scaled Texture](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a870b-120">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a870b-120">Compiling the Code</span></span>  
 <span data-ttu-id="a870b-121">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="a870b-121">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="a870b-122">Nahraďte Texture.jpg s název bitové kopie a cestu, která jsou platné ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="a870b-122">Replace Texture.jpg with an image name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a870b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="a870b-123">See Also</span></span>  
 [<span data-ttu-id="a870b-124">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="a870b-124">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="a870b-125">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="a870b-125">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
