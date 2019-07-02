---
title: Sestavování a kreslení křivek
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
ms.openlocfilehash: 4c1b0cc6c6f878569fcf0c392f1b6f9683ec8afc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506098"
---
# <a name="constructing-and-drawing-curves"></a><span data-ttu-id="c1898-102">Sestavování a kreslení křivek</span><span class="sxs-lookup"><span data-stu-id="c1898-102">Constructing and Drawing Curves</span></span>
<span data-ttu-id="c1898-103">Rozhraní GDI + podporuje několik typů křivek: symbol tří teček, elipsy, základní křivky vyhlazení a Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="c1898-103">GDI+ supports several types of curves: ellipses, arcs, cardinal splines, and Bézier splines.</span></span> <span data-ttu-id="c1898-104">Elipsa je definován ve své ohraničující obdélník; oblouku je část určené počáteční úhel a úhel oblouku elipsy.</span><span class="sxs-lookup"><span data-stu-id="c1898-104">An ellipse is defined by its bounding rectangle; an arc is a portion of an ellipse defined by a starting angle and a sweep angle.</span></span> <span data-ttu-id="c1898-105">Pole bodů a parametr napětí je definován křivky mohutnosti – křivka plynule prochází každý bod v poli, a parametr napětí ovlivňuje způsob, jakým zatáčkách křivky.</span><span class="sxs-lookup"><span data-stu-id="c1898-105">A cardinal spline is defined by an array of points and a tension parameter — the curve passes smoothly through each point in the array, and the tension parameter influences the way the curve bends.</span></span> <span data-ttu-id="c1898-106">Bézierovy křivky je definován tak, že dva koncové body a dva ovládací prvek body, které neprochází přes kontrolních bodů křivky, ale kontrolní body ovlivnit směru a ohybem jako křivku přechází z jednoho koncového bodu na druhý.</span><span class="sxs-lookup"><span data-stu-id="c1898-106">A Bézier spline is defined by two endpoints and two control points  the curve does not pass through the control points, but the control points influence the direction and bend as the curve goes from one endpoint to the other.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1898-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c1898-107">In This Section</span></span>  
 [<span data-ttu-id="c1898-108">Postupy: Kreslení základních křivek</span><span class="sxs-lookup"><span data-stu-id="c1898-108">How to: Draw Cardinal Splines</span></span>](how-to-draw-cardinal-splines.md)  
 <span data-ttu-id="c1898-109">Popisuje základní křivky vyhlazení a jejich vykreslení.</span><span class="sxs-lookup"><span data-stu-id="c1898-109">Describes cardinal splines and how to draw them.</span></span>  
  
 [<span data-ttu-id="c1898-110">Postupy: Kreslení jedné Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="c1898-110">How to: Draw a Single Bézier Spline</span></span>](how-to-draw-a-single-bezier-spline.md)  
 <span data-ttu-id="c1898-111">Popisuje Bézierovy křivky a kreslit.</span><span class="sxs-lookup"><span data-stu-id="c1898-111">Describes a Bézier spline and how to draw one.</span></span>  
  
 [<span data-ttu-id="c1898-112">Postupy: Kreslení sekvence Bézierových křivek</span><span class="sxs-lookup"><span data-stu-id="c1898-112">How to: Draw a Sequence of Bézier Splines</span></span>](how-to-draw-a-sequence-of-bezier-splines.md)  
 <span data-ttu-id="c1898-113">Vysvětluje, jak nakreslit několik Bézierovy křivky v pořadí.</span><span class="sxs-lookup"><span data-stu-id="c1898-113">Explains how to draw several Bézier splines in sequence.</span></span>
