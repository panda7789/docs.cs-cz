---
title: Kreslení čar a obrazců pomocí pera
ms.date: 03/30/2017
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
ms.openlocfilehash: d20b4e47c9f8a5dd7a144e6ebb3151d3ab65a800
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505137"
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="7d22a-102">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="7d22a-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="7d22a-103">Použijete GDI + `Pen` objektů pro kreslení segmenty čáry, křivky a obrysových obrazců.</span><span class="sxs-lookup"><span data-stu-id="7d22a-103">Use GDI+ `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="7d22a-104">V této části *řádku* odkazuje na některé z těchto, pokud není uvedeno rozumí čárového segmentu.</span><span class="sxs-lookup"><span data-stu-id="7d22a-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="7d22a-105">Nastavte vlastnosti pera řízení barvu, šířku, zarovnání a styl čáry dekorace pomocí pera.</span><span class="sxs-lookup"><span data-stu-id="7d22a-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d22a-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7d22a-106">In This Section</span></span>  
 [<span data-ttu-id="7d22a-107">Postupy: Kreslení čar pomocí pera</span><span class="sxs-lookup"><span data-stu-id="7d22a-107">How to: Use a Pen to Draw Lines</span></span>](how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="7d22a-108">Vysvětluje, jak kreslit čáry.</span><span class="sxs-lookup"><span data-stu-id="7d22a-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="7d22a-109">Postupy: Kreslení obdélníků pomocí pera</span><span class="sxs-lookup"><span data-stu-id="7d22a-109">How to: Use a Pen to Draw Rectangles</span></span>](how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="7d22a-110">Popisuje, jak kreslení obdélníků.</span><span class="sxs-lookup"><span data-stu-id="7d22a-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="7d22a-111">Postupy: Nastavení šířky a pera a zarovnání</span><span class="sxs-lookup"><span data-stu-id="7d22a-111">How to: Set Pen Width and Alignment</span></span>](how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="7d22a-112">Vysvětluje, jak změnit šířku a zarovnání `Pen` objektu.</span><span class="sxs-lookup"><span data-stu-id="7d22a-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="7d22a-113">Postupy: Kreslení čáry s ukončením</span><span class="sxs-lookup"><span data-stu-id="7d22a-113">How to: Draw a Line with Line Caps</span></span>](how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="7d22a-114">Popisuje postup přidání zakončení při kreslení čáry.</span><span class="sxs-lookup"><span data-stu-id="7d22a-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="7d22a-115">Postupy: Spojení čar</span><span class="sxs-lookup"><span data-stu-id="7d22a-115">How to: Join Lines</span></span>](how-to-join-lines.md)  
 <span data-ttu-id="7d22a-116">Ukazuje, jak propojit nejběžnější dva řádky.</span><span class="sxs-lookup"><span data-stu-id="7d22a-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="7d22a-117">Postupy: Kreslení vlastní přerušované čáry</span><span class="sxs-lookup"><span data-stu-id="7d22a-117">How to: Draw a Custom Dashed Line</span></span>](how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="7d22a-118">Popisuje, jak nakreslit na přerušovanou čáru.</span><span class="sxs-lookup"><span data-stu-id="7d22a-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="7d22a-119">Postupy: Kreslení čáry vyplněné texturou</span><span class="sxs-lookup"><span data-stu-id="7d22a-119">How to: Draw a Line Filled with a Texture</span></span>](how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="7d22a-120">Vysvětluje, jak kreslení čáry vyplněné texturou.</span><span class="sxs-lookup"><span data-stu-id="7d22a-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7d22a-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="7d22a-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="7d22a-122">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="7d22a-122">Describes this class and has links to all its members.</span></span>
