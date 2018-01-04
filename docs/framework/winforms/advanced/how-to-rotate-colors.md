---
title: "Postupy: Otáčení barev"
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
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81b022011bd5613b8e956aa83482d2836508a4f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="ae622-102">Postupy: Otáčení barev</span><span class="sxs-lookup"><span data-stu-id="ae622-102">How to: Rotate Colors</span></span>
<span data-ttu-id="ae622-103">Otočení v four-dimensional barevný prostor je obtížné vizualizace.</span><span class="sxs-lookup"><span data-stu-id="ae622-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="ae622-104">Jsme můžete usnadňují vizualizaci otočení souhlasit a jedna z komponent Barva pevné zachovat.</span><span class="sxs-lookup"><span data-stu-id="ae622-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="ae622-105">Předpokládejme, že jsme souhlas s zachovat komponentu alfa pevné na 1 (plně neprůhledný).</span><span class="sxs-lookup"><span data-stu-id="ae622-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="ae622-106">Potom jsme vizualizovat trojrozměrné barevný prostor s červenou, zelené a modré osy, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="ae622-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="ae622-107">![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")</span><span class="sxs-lookup"><span data-stu-id="ae622-107">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")</span></span>  
  
 <span data-ttu-id="ae622-108">Barvu, která lze považovat za bod v 3D prostoru.</span><span class="sxs-lookup"><span data-stu-id="ae622-108">A color can be thought of as a point in 3-D space.</span></span> <span data-ttu-id="ae622-109">Například bodu (1, 0, 0) v prostoru představuje červenou barvu a bodem (0, 1, 0) v prostoru představuje zelenou barvu.</span><span class="sxs-lookup"><span data-stu-id="ae622-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="ae622-110">Následující obrázek znázorňuje, co znamená otočit barvu (1, 0, 0) prostřednictvím úhel 60 stupňů v rovině Red zeleně.</span><span class="sxs-lookup"><span data-stu-id="ae622-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="ae622-111">Otočení paralelně roviny rovinou Red zelená lze považovat za otočení blue osy.</span><span class="sxs-lookup"><span data-stu-id="ae622-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 <span data-ttu-id="ae622-112">![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")</span><span class="sxs-lookup"><span data-stu-id="ae622-112">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")</span></span>  
  
 <span data-ttu-id="ae622-113">Následující obrázek ukazuje, jak k chybě při inicializaci matice barev k provedení otočení o jednotlivých tři souřadnice osy (červená, zelená, modrá).</span><span class="sxs-lookup"><span data-stu-id="ae622-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue).</span></span>  
  
 <span data-ttu-id="ae622-114">![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")</span><span class="sxs-lookup"><span data-stu-id="ae622-114">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae622-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae622-115">Example</span></span>  
 <span data-ttu-id="ae622-116">V následujícím příkladu má obrázek, který je všechny jedné barvy (1, 0, 0,6) a použije rotaci 60 stupeň blue osy.</span><span class="sxs-lookup"><span data-stu-id="ae622-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="ae622-117">Úhel otočení je, jež se v rovině rovnoběžné roviny red zeleně.</span><span class="sxs-lookup"><span data-stu-id="ae622-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="ae622-118">Následující obrázek znázorňuje původní bitové kopie na levé straně a obrázek otočen barva na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="ae622-118">The following illustration shows the original image on the left and the color-rotated image on the right.</span></span>  
  
 <span data-ttu-id="ae622-119">![Otáčení barev](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")</span><span class="sxs-lookup"><span data-stu-id="ae622-119">![Rotate Colors](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")</span></span>  
  
 <span data-ttu-id="ae622-120">Následující obrázek znázorňuje vizualizaci otočení barev provést v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ae622-120">The following illustration shows a visualization of the color rotation performed in the following code.</span></span>  
  
 <span data-ttu-id="ae622-121">![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")</span><span class="sxs-lookup"><span data-stu-id="ae622-121">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")</span></span>  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae622-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ae622-122">Compiling the Code</span></span>  
 <span data-ttu-id="ae622-123">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ae622-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="ae622-124">Nahraďte `RotationInput.bmp` s název souboru obrázku a cesta platné ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="ae622-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae622-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae622-125">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="ae622-126">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ae622-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="ae622-127">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="ae622-127">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
