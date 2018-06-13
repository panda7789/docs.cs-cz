---
title: Kreslení čar a obrazců pomocí pera
ms.date: 03/30/2017
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
ms.openlocfilehash: 667a5b13c5e8cb5d9a693d6f8512b254f130d606
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524339"
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="2d7cc-102">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="2d7cc-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="2d7cc-103">Použití [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objekty k vykreslení segmenty čáry, křivky a jsou podrobněji popsány dále tvarů.</span><span class="sxs-lookup"><span data-stu-id="2d7cc-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="2d7cc-104">V této části *řádku* odkazuje na některý z těchto, není-li zadán rozumí pouze úsek čáry.</span><span class="sxs-lookup"><span data-stu-id="2d7cc-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="2d7cc-105">Nastavte vlastnosti pera k řízení barvu, šířku, zarovnání a styl čar vykreslovány pomocí pera.</span><span class="sxs-lookup"><span data-stu-id="2d7cc-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d7cc-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2d7cc-106">In This Section</span></span>  
 [<span data-ttu-id="2d7cc-107">Postupy: Kreslení čar pomocí pera</span><span class="sxs-lookup"><span data-stu-id="2d7cc-107">How to: Use a Pen to Draw Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="2d7cc-108">Vysvětluje, jak kreslení čar.</span><span class="sxs-lookup"><span data-stu-id="2d7cc-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="2d7cc-109">Postupy: Kreslení obdélníků pomocí pera</span><span class="sxs-lookup"><span data-stu-id="2d7cc-109">How to: Use a Pen to Draw Rectangles</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="2d7cc-110">Popisuje, jak kreslení obdélníků.</span><span class="sxs-lookup"><span data-stu-id="2d7cc-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="2d7cc-111">Postupy: Nastavení šířky a pera a zarovnání</span><span class="sxs-lookup"><span data-stu-id="2d7cc-111">How to: Set Pen Width and Alignment</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="2d7cc-112">Vysvětluje, jak změnit šířku a zarovnání `Pen` objektu.</span><span class="sxs-lookup"><span data-stu-id="2d7cc-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="2d7cc-113">Postupy: Kreslení čáry s ukončením</span><span class="sxs-lookup"><span data-stu-id="2d7cc-113">How to: Draw a Line with Line Caps</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="2d7cc-114">Popisuje postup přidání zakončení při kreslení čáry.</span><span class="sxs-lookup"><span data-stu-id="2d7cc-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="2d7cc-115">Postupy: Spojení čar</span><span class="sxs-lookup"><span data-stu-id="2d7cc-115">How to: Join Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-join-lines.md)  
 <span data-ttu-id="2d7cc-116">Ukazuje, jak připojit dva řádky.</span><span class="sxs-lookup"><span data-stu-id="2d7cc-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="2d7cc-117">Postupy: Kreslení vlastní přerušované čáry</span><span class="sxs-lookup"><span data-stu-id="2d7cc-117">How to: Draw a Custom Dashed Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="2d7cc-118">Popisuje, jak k vykreslení na přerušovanou čáru.</span><span class="sxs-lookup"><span data-stu-id="2d7cc-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="2d7cc-119">Postupy: Kreslení čáry vyplněné texturou</span><span class="sxs-lookup"><span data-stu-id="2d7cc-119">How to: Draw a Line Filled with a Texture</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="2d7cc-120">Vysvětluje, jak kreslení čáry vyplněné texturou.</span><span class="sxs-lookup"><span data-stu-id="2d7cc-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2d7cc-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2d7cc-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="2d7cc-122">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="2d7cc-122">Describes this class and has links to all its members.</span></span>
