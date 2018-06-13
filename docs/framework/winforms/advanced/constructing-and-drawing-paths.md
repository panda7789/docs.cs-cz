---
title: Sestavování a kreslení cest
ms.date: 03/30/2017
helpviewer_keywords:
- paths [Windows Forms], drawing
- drawing paths [Windows Forms]
- graphics paths [Windows Forms], creating
- graphics paths [Windows Forms], drawing
- examples [Windows Forms], drawing paths
ms.assetid: f16ec921-56cf-46d1-9741-d7316ad06b23
ms.openlocfilehash: 120bb3edcf8e35feca37f02dda5148ba4eebd0ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520653"
---
# <a name="constructing-and-drawing-paths"></a><span data-ttu-id="a6e82-102">Sestavování a kreslení cest</span><span class="sxs-lookup"><span data-stu-id="a6e82-102">Constructing and Drawing Paths</span></span>
<span data-ttu-id="a6e82-103">Cestu je posloupnost primitiv grafiky (řádky, obdélníky, křivek, text a podobně), které je možné s nimi manipulovat a vykreslovat jako na jednu jednotku.</span><span class="sxs-lookup"><span data-stu-id="a6e82-103">A path is a sequence of graphics primitives (lines, rectangles, curves, text, and the like) that can be manipulated and drawn as a single unit.</span></span> <span data-ttu-id="a6e82-104">Cestu je možné rozdělit do *obrázky* které jsou otevřené nebo uzavřený.</span><span class="sxs-lookup"><span data-stu-id="a6e82-104">A path can be divided into *figures* that are either open or closed.</span></span> <span data-ttu-id="a6e82-105">Obrázku může obsahovat několik primitiv.</span><span class="sxs-lookup"><span data-stu-id="a6e82-105">A figure can contain several primitives.</span></span>  
  
 <span data-ttu-id="a6e82-106">Cestu můžete nakreslit voláním <xref:System.Drawing.Graphics.DrawPath%2A> metodu <xref:System.Drawing.Graphics> třídy a zadejte cestu k voláním <xref:System.Drawing.Graphics.FillPath%2A> metodu <xref:System.Drawing.Graphics> – třída.</span><span class="sxs-lookup"><span data-stu-id="a6e82-106">You can draw a path by calling the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class, and you can fill a path by calling the <xref:System.Drawing.Graphics.FillPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6e82-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a6e82-107">In This Section</span></span>  
 [<span data-ttu-id="a6e82-108">Postupy: Vytváření obrázků z čar, křivek a obrazců</span><span class="sxs-lookup"><span data-stu-id="a6e82-108">How to: Create Figures from Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-figures-from-lines-curves-and-shapes.md)  
 <span data-ttu-id="a6e82-109">Ukazuje, jak používat <xref:System.Drawing.Drawing2D.GraphicsPath> k vytváření obrázků.</span><span class="sxs-lookup"><span data-stu-id="a6e82-109">Shows how to use a <xref:System.Drawing.Drawing2D.GraphicsPath> to create figures.</span></span>  
  
 [<span data-ttu-id="a6e82-110">Postupy: Vyplňování otevřených obrázků</span><span class="sxs-lookup"><span data-stu-id="a6e82-110">How to: Fill Open Figures</span></span>](../../../../docs/framework/winforms/advanced/how-to-fill-open-figures.md)  
 <span data-ttu-id="a6e82-111">Vysvětluje, jak k vyplnění <xref:System.Drawing.Drawing2D.GraphicsPath>.</span><span class="sxs-lookup"><span data-stu-id="a6e82-111">Explains how to fill a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
 [<span data-ttu-id="a6e82-112">Postupy: Narovnání zakřivené cesty na čáru</span><span class="sxs-lookup"><span data-stu-id="a6e82-112">How to: Flatten a Curved Path into a Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-flatten-a-curved-path-into-a-line.md)  
 <span data-ttu-id="a6e82-113">Ukazuje, jak k vyrovnání <xref:System.Drawing.Drawing2D.GraphicsPath>.</span><span class="sxs-lookup"><span data-stu-id="a6e82-113">Shows how to flatten a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a6e82-114">Odkaz</span><span class="sxs-lookup"><span data-stu-id="a6e82-114">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 <span data-ttu-id="a6e82-115">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="a6e82-115">Describes this class and contains links to all of its members.</span></span>
