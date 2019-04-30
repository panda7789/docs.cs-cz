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
ms.openlocfilehash: a698b93aac29a0a7f5c959b29a3feb41eb447e8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935405"
---
# <a name="constructing-and-drawing-paths"></a><span data-ttu-id="2baf3-102">Sestavování a kreslení cest</span><span class="sxs-lookup"><span data-stu-id="2baf3-102">Constructing and Drawing Paths</span></span>
<span data-ttu-id="2baf3-103">Cesta je posloupnost primitivy grafiky (řádky, obdélníky, křivek, text a podobně), které mohou zpracovat a vykreslit jako jeden celek.</span><span class="sxs-lookup"><span data-stu-id="2baf3-103">A path is a sequence of graphics primitives (lines, rectangles, curves, text, and the like) that can be manipulated and drawn as a single unit.</span></span> <span data-ttu-id="2baf3-104">Cesta je možné rozdělit do *obrázky* , které jsou otevřeno nebo Uzavřeno.</span><span class="sxs-lookup"><span data-stu-id="2baf3-104">A path can be divided into *figures* that are either open or closed.</span></span> <span data-ttu-id="2baf3-105">Obrázek může obsahovat několik primitiv.</span><span class="sxs-lookup"><span data-stu-id="2baf3-105">A figure can contain several primitives.</span></span>  
  
 <span data-ttu-id="2baf3-106">Cestu můžete nakreslit pomocí volání <xref:System.Drawing.Graphics.DrawPath%2A> metodu <xref:System.Drawing.Graphics> třídy kde můžete zadat cestu voláním <xref:System.Drawing.Graphics.FillPath%2A> metodu <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="2baf3-106">You can draw a path by calling the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class, and you can fill a path by calling the <xref:System.Drawing.Graphics.FillPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2baf3-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2baf3-107">In This Section</span></span>  
 [<span data-ttu-id="2baf3-108">Postupy: Vytváření obrázků z čar, křivek a obrazců</span><span class="sxs-lookup"><span data-stu-id="2baf3-108">How to: Create Figures from Lines, Curves, and Shapes</span></span>](how-to-create-figures-from-lines-curves-and-shapes.md)  
 <span data-ttu-id="2baf3-109">Ukazuje, jak používat <xref:System.Drawing.Drawing2D.GraphicsPath> k vytváření obrázků.</span><span class="sxs-lookup"><span data-stu-id="2baf3-109">Shows how to use a <xref:System.Drawing.Drawing2D.GraphicsPath> to create figures.</span></span>  
  
 [<span data-ttu-id="2baf3-110">Postupy: Vyplňování otevřených obrázků</span><span class="sxs-lookup"><span data-stu-id="2baf3-110">How to: Fill Open Figures</span></span>](how-to-fill-open-figures.md)  
 <span data-ttu-id="2baf3-111">Vysvětluje, jak vyplnit <xref:System.Drawing.Drawing2D.GraphicsPath>.</span><span class="sxs-lookup"><span data-stu-id="2baf3-111">Explains how to fill a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
 [<span data-ttu-id="2baf3-112">Postupy: Narovnání zakřivené cesty na čáru</span><span class="sxs-lookup"><span data-stu-id="2baf3-112">How to: Flatten a Curved Path into a Line</span></span>](how-to-flatten-a-curved-path-into-a-line.md)  
 <span data-ttu-id="2baf3-113">Ukazuje, jak sloučit <xref:System.Drawing.Drawing2D.GraphicsPath>.</span><span class="sxs-lookup"><span data-stu-id="2baf3-113">Shows how to flatten a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2baf3-114">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2baf3-114">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 <span data-ttu-id="2baf3-115">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="2baf3-115">Describes this class and contains links to all of its members.</span></span>
