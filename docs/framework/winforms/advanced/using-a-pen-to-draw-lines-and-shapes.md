---
title: "Kreslení čar a obrazců pomocí pera"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0913dc2745e1b244e4b03c0e6b946441a401c5b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="6d7c8-102">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="6d7c8-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="6d7c8-103">Použití [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objekty k vykreslení segmenty čáry, křivky a jsou podrobněji popsány dále tvarů.</span><span class="sxs-lookup"><span data-stu-id="6d7c8-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="6d7c8-104">V této části *řádku* odkazuje na některý z těchto, není-li zadán rozumí pouze úsek čáry.</span><span class="sxs-lookup"><span data-stu-id="6d7c8-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="6d7c8-105">Nastavte vlastnosti pera k řízení barvu, šířku, zarovnání a styl čar vykreslovány pomocí pera.</span><span class="sxs-lookup"><span data-stu-id="6d7c8-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d7c8-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6d7c8-106">In This Section</span></span>  
 [<span data-ttu-id="6d7c8-107">Postupy: kreslení čar pomocí pera</span><span class="sxs-lookup"><span data-stu-id="6d7c8-107">How to: Use a Pen to Draw Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="6d7c8-108">Vysvětluje, jak kreslení čar.</span><span class="sxs-lookup"><span data-stu-id="6d7c8-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="6d7c8-109">Postupy: kreslení obdélníků pomocí pera</span><span class="sxs-lookup"><span data-stu-id="6d7c8-109">How to: Use a Pen to Draw Rectangles</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="6d7c8-110">Popisuje, jak kreslení obdélníků.</span><span class="sxs-lookup"><span data-stu-id="6d7c8-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="6d7c8-111">Postupy: nastavení šířky a pera a zarovnání</span><span class="sxs-lookup"><span data-stu-id="6d7c8-111">How to: Set Pen Width and Alignment</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="6d7c8-112">Vysvětluje, jak změnit šířku a zarovnání `Pen` objektu.</span><span class="sxs-lookup"><span data-stu-id="6d7c8-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="6d7c8-113">Postupy: kreslení čáry s ukončením</span><span class="sxs-lookup"><span data-stu-id="6d7c8-113">How to: Draw a Line with Line Caps</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="6d7c8-114">Popisuje postup přidání zakončení při kreslení čáry.</span><span class="sxs-lookup"><span data-stu-id="6d7c8-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="6d7c8-115">Postupy: spojení čar</span><span class="sxs-lookup"><span data-stu-id="6d7c8-115">How to: Join Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-join-lines.md)  
 <span data-ttu-id="6d7c8-116">Ukazuje, jak připojit dva řádky.</span><span class="sxs-lookup"><span data-stu-id="6d7c8-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="6d7c8-117">Postupy: kreslení vlastní přerušované čáry</span><span class="sxs-lookup"><span data-stu-id="6d7c8-117">How to: Draw a Custom Dashed Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="6d7c8-118">Popisuje, jak k vykreslení na přerušovanou čáru.</span><span class="sxs-lookup"><span data-stu-id="6d7c8-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="6d7c8-119">Postupy: kreslení čáry vyplněné texturou</span><span class="sxs-lookup"><span data-stu-id="6d7c8-119">How to: Draw a Line Filled with a Texture</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="6d7c8-120">Vysvětluje, jak kreslení čáry vyplněné texturou.</span><span class="sxs-lookup"><span data-stu-id="6d7c8-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6d7c8-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="6d7c8-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="6d7c8-122">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="6d7c8-122">Describes this class and has links to all its members.</span></span>
