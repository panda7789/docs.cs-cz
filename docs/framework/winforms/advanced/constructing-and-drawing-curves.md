---
title: "Sestavování a kreslení křivek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62e9b9e0e1aa432578b7173cd58f88dd44957f84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="constructing-and-drawing-curves"></a><span data-ttu-id="4a2c8-102">Sestavování a kreslení křivek</span><span class="sxs-lookup"><span data-stu-id="4a2c8-102">Constructing and Drawing Curves</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4a2c8-103">podporuje několik typů křivek: symbol tří teček, oblouky, základní křivky vyhlazení a Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="4a2c8-103"> supports several types of curves: ellipses, arcs, cardinal splines, and Bézier splines.</span></span> <span data-ttu-id="4a2c8-104">Elipsy je definována jeho ohraničující obdélník; oblouk je část elipsy definované počáteční úhel a úhel oblouku.</span><span class="sxs-lookup"><span data-stu-id="4a2c8-104">An ellipse is defined by its bounding rectangle; an arc is a portion of an ellipse defined by a starting angle and a sweep angle.</span></span> <span data-ttu-id="4a2c8-105">Pole bodů a pnutí parametru je definováno křivky mohutnosti – křivku plynule projdou každý bod v poli a parametr pnutí ovlivňuje způsob zatáčkách křivku.</span><span class="sxs-lookup"><span data-stu-id="4a2c8-105">A cardinal spline is defined by an array of points and a tension parameter — the curve passes smoothly through each point in the array, and the tension parameter influences the way the curve bends.</span></span> <span data-ttu-id="4a2c8-106">Bézierovy křivky definované dva koncové body a dva kontrolních bodů, které křivku nepředává prostřednictvím kontrolní body, ale kontrolní body ovlivnit směr a ohybem jako křivku přejde z jeden koncový bod na druhý.</span><span class="sxs-lookup"><span data-stu-id="4a2c8-106">A Bézier spline is defined by two endpoints and two control points  the curve does not pass through the control points, but the control points influence the direction and bend as the curve goes from one endpoint to the other.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4a2c8-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4a2c8-107">In This Section</span></span>  
 [<span data-ttu-id="4a2c8-108">Postupy: Kreslení základních křivek</span><span class="sxs-lookup"><span data-stu-id="4a2c8-108">How to: Draw Cardinal Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-cardinal-splines.md)  
 <span data-ttu-id="4a2c8-109">Popisuje základní křivky vyhlazení a k jejich vykreslení.</span><span class="sxs-lookup"><span data-stu-id="4a2c8-109">Describes cardinal splines and how to draw them.</span></span>  
  
 [<span data-ttu-id="4a2c8-110">Postupy: Kreslení jedné bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="4a2c8-110">How to: Draw a Single Bézier Spline</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-single-bezier-spline.md)  
 <span data-ttu-id="4a2c8-111">Popisuje Bézierovy křivky a kreslení jeden.</span><span class="sxs-lookup"><span data-stu-id="4a2c8-111">Describes a Bézier spline and how to draw one.</span></span>  
  
 [<span data-ttu-id="4a2c8-112">Postupy: Kreslení sekvence Bézierových křivek</span><span class="sxs-lookup"><span data-stu-id="4a2c8-112">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)  
 <span data-ttu-id="4a2c8-113">Vysvětluje, jak k vykreslení několik Bézierovy křivky v pořadí.</span><span class="sxs-lookup"><span data-stu-id="4a2c8-113">Explains how to draw several Bézier splines in sequence.</span></span>
