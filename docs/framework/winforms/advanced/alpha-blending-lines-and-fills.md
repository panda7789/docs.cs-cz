---
title: "Alfa míchání čar a výplní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5b3c0ee3ec82d4d8447c43b7dc9b275591ebe890
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="alpha-blending-lines-and-fills"></a><span data-ttu-id="fc84f-102">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="fc84f-102">Alpha Blending Lines and Fills</span></span>
<span data-ttu-id="fc84f-103">V [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], barvu, která je hodnotu 32-bit s 8 bitů každý pro platformu alpha, červená, zelená a modrá.</span><span class="sxs-lookup"><span data-stu-id="fc84f-103">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a color is a 32-bit value with 8 bits each for alpha, red, green, and blue.</span></span> <span data-ttu-id="fc84f-104">Určuje hodnotu alfa průhlednost barvy – v rozsahu, ke kterému je barvu smíšení barvou pozadí.</span><span class="sxs-lookup"><span data-stu-id="fc84f-104">The alpha value indicates the transparency of the color — the extent to which the color is blended with the background color.</span></span> <span data-ttu-id="fc84f-105">Hodnoty alfa rozsahu od 0 do 255, kde 0 představuje plně průhlednou barvu, a 255 představuje plně neprůhledné barvy.</span><span class="sxs-lookup"><span data-stu-id="fc84f-105">Alpha values range from 0 through 255, where 0 represents a fully transparent color, and 255 represents a fully opaque color.</span></span>  
  
 <span data-ttu-id="fc84f-106">Prolnutí alfa je x pixelů míchání dat barva zdroje a pozadí.</span><span class="sxs-lookup"><span data-stu-id="fc84f-106">Alpha blending is a pixel-by-pixel blending of source and background color data.</span></span> <span data-ttu-id="fc84f-107">Všechny tři komponenty (červená, zelená, modrá) zadaná zdrojová barvu, která je smíšený s odpovídající součást barvu pozadí podle následujícího vzorce:</span><span class="sxs-lookup"><span data-stu-id="fc84f-107">Each of the three components (red, green, blue) of a given source color is blended with the corresponding component of the background color according to the following formula:</span></span>  
  
 <span data-ttu-id="fc84f-108">displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alfa) / 255</span><span class="sxs-lookup"><span data-stu-id="fc84f-108">displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255</span></span>  
  
 <span data-ttu-id="fc84f-109">Předpokládejme například, red součástí zdrojové barvy je 150 a červenou barvu pozadí komponenta je 100.</span><span class="sxs-lookup"><span data-stu-id="fc84f-109">For example, suppose the red component of the source color is 150 and the red component of the background color is 100.</span></span> <span data-ttu-id="fc84f-110">Pokud je alfa hodnota 200, komponentu červenou barvu výsledné se vypočítává takto:</span><span class="sxs-lookup"><span data-stu-id="fc84f-110">If the alpha value is 200, the red component of the resultant color is calculated as follows:</span></span>  
  
 <span data-ttu-id="fc84f-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span><span class="sxs-lookup"><span data-stu-id="fc84f-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc84f-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fc84f-112">In This Section</span></span>  
 [<span data-ttu-id="fc84f-113">Postupy: kreslení neprůhledných a poloprůhledných čar</span><span class="sxs-lookup"><span data-stu-id="fc84f-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 <span data-ttu-id="fc84f-114">Ukazuje, jak kreslení smíšení alfa čar.</span><span class="sxs-lookup"><span data-stu-id="fc84f-114">Shows how to draw alpha-blended lines.</span></span>  
  
 [<span data-ttu-id="fc84f-115">Postupy: kreslení pomocí neprůhledných a poloprůhledných štětců</span><span class="sxs-lookup"><span data-stu-id="fc84f-115">How to: Draw with Opaque and Semitransparent Brushes</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 <span data-ttu-id="fc84f-116">Vysvětluje, jak alpha blend s štětce.</span><span class="sxs-lookup"><span data-stu-id="fc84f-116">Explains how to alpha-blend with brushes.</span></span>  
  
 [<span data-ttu-id="fc84f-117">Postupy: použití řízení alfa míchání pomocí režimu skládání</span><span class="sxs-lookup"><span data-stu-id="fc84f-117">How to: Use Compositing Mode to Control Alpha Blending</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 <span data-ttu-id="fc84f-118">Popisuje, jak k řízení alfa míchání pomocí <xref:System.Drawing.Drawing2D.CompositingMode>.</span><span class="sxs-lookup"><span data-stu-id="fc84f-118">Describes how to control alpha blending using <xref:System.Drawing.Drawing2D.CompositingMode>.</span></span>  
  
 [<span data-ttu-id="fc84f-119">Postupy: použití matice barev k nastavení alfa hodnot v obrázcích</span><span class="sxs-lookup"><span data-stu-id="fc84f-119">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 <span data-ttu-id="fc84f-120">Vysvětluje, jak používat <xref:System.Drawing.Imaging.ColorMatrix> objektu k řízení alfa míchání.</span><span class="sxs-lookup"><span data-stu-id="fc84f-120">Explains how to use a <xref:System.Drawing.Imaging.ColorMatrix> object to control alpha blending.</span></span>
