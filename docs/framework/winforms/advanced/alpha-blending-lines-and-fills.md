---
title: Alfa míchání čar a výplní
ms.date: 03/30/2017
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
ms.openlocfilehash: 66061341ee6539e2172c537a0b2a6ec9ff87565c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506120"
---
# <a name="alpha-blending-lines-and-fills"></a><span data-ttu-id="949d9-102">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="949d9-102">Alpha Blending Lines and Fills</span></span>
<span data-ttu-id="949d9-103">V rozhraní GDI + je barva hodnotu 32 bitů s 8 bity pro platformu alpha, červené, zelené a modré.</span><span class="sxs-lookup"><span data-stu-id="949d9-103">In GDI+, a color is a 32-bit value with 8 bits each for alpha, red, green, and blue.</span></span> <span data-ttu-id="949d9-104">Určuje hodnotu alfa průhlednost barvy – v rozsahu, do které jsou prolnuty barva barvou pozadí.</span><span class="sxs-lookup"><span data-stu-id="949d9-104">The alpha value indicates the transparency of the color — the extent to which the color is blended with the background color.</span></span> <span data-ttu-id="949d9-105">Hodnoty alfa v rozmezí 0 až 255, kde 0 představuje plně průhlednou barvu, a 255 představuje barvu úplně neprůhledné.</span><span class="sxs-lookup"><span data-stu-id="949d9-105">Alpha values range from 0 through 255, where 0 represents a fully transparent color, and 255 represents a fully opaque color.</span></span>  
  
 <span data-ttu-id="949d9-106">Alfa míchání je – obrazový prolnutí data o barvách zdroj a na pozadí.</span><span class="sxs-lookup"><span data-stu-id="949d9-106">Alpha blending is a pixel-by-pixel blending of source and background color data.</span></span> <span data-ttu-id="949d9-107">Všechny tři komponenty (červená, zelená, modrá) barvu daného zdroje jsou prolnuty pomocí odpovídající komponenty barvu pozadí podle následující vzorec:</span><span class="sxs-lookup"><span data-stu-id="949d9-107">Each of the three components (red, green, blue) of a given source color is blended with the corresponding component of the background color according to the following formula:</span></span>  
  
 <span data-ttu-id="949d9-108">displayColor = sourceColor × alfa / 255 + x backgroundColor (255 – alfa) / 255</span><span class="sxs-lookup"><span data-stu-id="949d9-108">displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255</span></span>  
  
 <span data-ttu-id="949d9-109">Předpokládejme například, hodnota červené ze zdrojové barvy je 150 a červené barvu pozadí je 100.</span><span class="sxs-lookup"><span data-stu-id="949d9-109">For example, suppose the red component of the source color is 150 and the red component of the background color is 100.</span></span> <span data-ttu-id="949d9-110">Pokud je hodnota alpha 200, červené výsledné barvy se vypočítává takto:</span><span class="sxs-lookup"><span data-stu-id="949d9-110">If the alpha value is 200, the red component of the resultant color is calculated as follows:</span></span>  
  
 <span data-ttu-id="949d9-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span><span class="sxs-lookup"><span data-stu-id="949d9-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="949d9-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="949d9-112">In This Section</span></span>  
 [<span data-ttu-id="949d9-113">Postupy: Kreslení neprůhledných a poloprůhledných čar</span><span class="sxs-lookup"><span data-stu-id="949d9-113">How to: Draw Opaque and Semitransparent Lines</span></span>](how-to-draw-opaque-and-semitransparent-lines.md)  
 <span data-ttu-id="949d9-114">Ukazuje, jak kreslení čar prolnutí alfa.</span><span class="sxs-lookup"><span data-stu-id="949d9-114">Shows how to draw alpha-blended lines.</span></span>  
  
 [<span data-ttu-id="949d9-115">Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců</span><span class="sxs-lookup"><span data-stu-id="949d9-115">How to: Draw with Opaque and Semitransparent Brushes</span></span>](how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 <span data-ttu-id="949d9-116">Vysvětluje, jak pomocí štětců prolnutí alfa.</span><span class="sxs-lookup"><span data-stu-id="949d9-116">Explains how to alpha-blend with brushes.</span></span>  
  
 [<span data-ttu-id="949d9-117">Postupy: Pomocí řízení funkce alfa Blending pomocí režimu skládání</span><span class="sxs-lookup"><span data-stu-id="949d9-117">How to: Use Compositing Mode to Control Alpha Blending</span></span>](how-to-use-compositing-mode-to-control-alpha-blending.md)  
 <span data-ttu-id="949d9-118">Popisuje, jak řízení alfa míchání pomocí <xref:System.Drawing.Drawing2D.CompositingMode>.</span><span class="sxs-lookup"><span data-stu-id="949d9-118">Describes how to control alpha blending using <xref:System.Drawing.Drawing2D.CompositingMode>.</span></span>  
  
 [<span data-ttu-id="949d9-119">Postupy: Použití matice barev k nastavení alfa hodnot v obrázcích</span><span class="sxs-lookup"><span data-stu-id="949d9-119">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>](how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 <span data-ttu-id="949d9-120">Vysvětluje způsob používání <xref:System.Drawing.Imaging.ColorMatrix> objekt pro řízení alfa míchání.</span><span class="sxs-lookup"><span data-stu-id="949d9-120">Explains how to use a <xref:System.Drawing.Imaging.ColorMatrix> object to control alpha blending.</span></span>
