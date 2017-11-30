---
title: "Postupy: Řízení alfa míchání pomocí režimu skládání"
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
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 564d46cb2d72ac63962657b39146489aaafd6a5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a><span data-ttu-id="d8f6e-102">Postupy: Řízení alfa míchání pomocí režimu skládání</span><span class="sxs-lookup"><span data-stu-id="d8f6e-102">How to: Use Compositing Mode to Control Alpha Blending</span></span>
<span data-ttu-id="d8f6e-103">Mohou nastat situace, kdy budete chtít vytvořit mimo obrazovku rastrový obrázek, který má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d8f6e-103">There may be times when you want to create an off-screen bitmap that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="d8f6e-104">Barvy mají alfanumerické hodnoty, které jsou menší než 255.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-104">Colors have alpha values that are less than 255.</span></span>  
  
-   <span data-ttu-id="d8f6e-105">Barvy nejsou alfa smíšení mezi sebou, jako je vytváření bitové mapy.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-105">Colors are not alpha blended with each other as you create the bitmap.</span></span>  
  
-   <span data-ttu-id="d8f6e-106">Při zobrazení dokončení rastrového obrázku jsou barvy v souboru bitové mapy s barvy pozadí v zobrazení zařízení smíšení alfa.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-106">When you display the finished bitmap, colors in the bitmap are alpha blended with the background colors on the display device.</span></span>  
  
 <span data-ttu-id="d8f6e-107">K vytvoření takové rastrového obrázku, vytvořit prázdnou <xref:System.Drawing.Bitmap> objektu a pak vytvořit <xref:System.Drawing.Graphics> objektu podle této bitové mapy.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-107">To create such a bitmap, construct a blank <xref:System.Drawing.Bitmap> object, and then construct a <xref:System.Drawing.Graphics> object based on that bitmap.</span></span> <span data-ttu-id="d8f6e-108">Nastavení režimu skládání <xref:System.Drawing.Graphics> do objektu <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-108">Set the compositing mode of the <xref:System.Drawing.Graphics> object to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8f6e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d8f6e-109">Example</span></span>  
 <span data-ttu-id="d8f6e-110">Následující příklad vytvoří <xref:System.Drawing.Graphics> na základě objektu <xref:System.Drawing.Bitmap> objektu.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-110">The following example creates a <xref:System.Drawing.Graphics> object based on a <xref:System.Drawing.Bitmap> object.</span></span> <span data-ttu-id="d8f6e-111">Kód používá <xref:System.Drawing.Graphics> objekt spolu se dvěma poloprůhledných štětců (alpha = 160) pro malování bitové mapy.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-111">The code uses the <xref:System.Drawing.Graphics> object along with two semitransparent brushes (alpha = 160) to paint on the bitmap.</span></span> <span data-ttu-id="d8f6e-112">Kód doplní red elipsy a zelené elipsy pomocí poloprůhledných štětců.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-112">The code fills a red ellipse and a green ellipse using the semitransparent brushes.</span></span> <span data-ttu-id="d8f6e-113">Zelené elipsy překrývá red elipsy, ale není zeleným smíšení s červeným, protože režimu skládání <xref:System.Drawing.Graphics> objektu na hodnotu <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-113">The green ellipse overlaps the red ellipse, but the green is not blended with the red because the compositing mode of the <xref:System.Drawing.Graphics> object is set to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span></span>  
  
 <span data-ttu-id="d8f6e-114">Kód nevykresluje bitmapy na obrazovce dvakrát: jednou na bílé pozadí a jednou na barevné pozadí.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-114">The code draws the bitmap on the screen twice: once on a white background and once on a multicolored background.</span></span> <span data-ttu-id="d8f6e-115">Pixelů v souboru bitové mapy, které jsou součástí na dva výpustky mají alfa součást 160, takže na symbol tří teček jsou smíšené s barvy pozadí na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-115">The pixels in the bitmap that are part of the two ellipses have an alpha component of 160, so the ellipses are blended with the background colors on the screen.</span></span>  
  
 <span data-ttu-id="d8f6e-116">Následující obrázek znázorňuje příklad kódu výstup.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-116">The following illustration shows the output of the code example.</span></span> <span data-ttu-id="d8f6e-117">Všimněte si, že jsou na symbol tří teček smíšený s na pozadí, ale nejsou smíšení mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-117">Note that the ellipses are blended with the background, but they are not blended with each other.</span></span>  
  
 <span data-ttu-id="d8f6e-118">![Zdroj kopírování](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")</span><span class="sxs-lookup"><span data-stu-id="d8f6e-118">![Source Copy](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")</span></span>  
  
 <span data-ttu-id="d8f6e-119">Příklad kódu obsahuje tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="d8f6e-119">The code example contains this statement:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 <span data-ttu-id="d8f6e-120">Pokud chcete na symbol tří teček, chcete-li být smíšení mezi sebou můžou mít na pozadí, změňte na následující tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="d8f6e-120">If you want the ellipses to be blended with each other as well as with the background, change that statement to the following:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 <span data-ttu-id="d8f6e-121">Následující obrázek znázorňuje výstup revidovaný kód.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-121">The following illustration shows the output of the revised code.</span></span>  
  
 <span data-ttu-id="d8f6e-122">![Zdroj přes](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")</span><span class="sxs-lookup"><span data-stu-id="d8f6e-122">![Source Over](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d8f6e-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d8f6e-123">Compiling the Code</span></span>  
 <span data-ttu-id="d8f6e-124">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="d8f6e-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f6e-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8f6e-125">See Also</span></span>  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [<span data-ttu-id="d8f6e-126">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="d8f6e-126">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
