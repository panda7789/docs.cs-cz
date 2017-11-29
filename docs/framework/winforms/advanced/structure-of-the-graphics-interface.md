---
title: "Struktura rozhraní grafiky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd1da930df151869ea3e891da7057f44ed0a4603
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="structure-of-the-graphics-interface"></a><span data-ttu-id="d1cf4-102">Struktura rozhraní grafiky</span><span class="sxs-lookup"><span data-stu-id="d1cf4-102">Structure of the Graphics Interface</span></span>
<span data-ttu-id="d1cf4-103">Spravované třídy rozhraní pro [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] obsahuje o 60 třídy, 50 výčty a struktury 8.</span><span class="sxs-lookup"><span data-stu-id="d1cf4-103">The managed class interface to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] contains about 60 classes, 50 enumerations, and 8 structures.</span></span> <span data-ttu-id="d1cf4-104"><xref:System.Drawing.Graphics> Třída je základem [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkce; je třída, která ve skutečnosti nevykresluje čar, křivek, obrázky, bitové kopie a text.</span><span class="sxs-lookup"><span data-stu-id="d1cf4-104">The <xref:System.Drawing.Graphics> class is at the core of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] functionality; it is the class that actually draws lines, curves, figures, images, and text.</span></span>  
  
## <a name="important-classes"></a><span data-ttu-id="d1cf4-105">Důležité třídy</span><span class="sxs-lookup"><span data-stu-id="d1cf4-105">Important Classes</span></span>  
 <span data-ttu-id="d1cf4-106">Mnoho tříd pracovat společně <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="d1cf4-106">Many classes work together with the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="d1cf4-107">Například <xref:System.Drawing.Graphics.DrawLine%2A> metoda obdrží <xref:System.Drawing.Pen> objekt, který obsahuje atributy (barvu, šířku, přerušovaná čára a podobně) na řádku, které se mají vykreslovat.</span><span class="sxs-lookup"><span data-stu-id="d1cf4-107">For example, the <xref:System.Drawing.Graphics.DrawLine%2A> method receives a <xref:System.Drawing.Pen> object, which holds attributes (color, width, dash style, and the like) of the line to be drawn.</span></span> <span data-ttu-id="d1cf4-108"><xref:System.Drawing.Graphics.FillRectangle%2A> Metoda může přijímat ukazatel na <xref:System.Drawing.Drawing2D.LinearGradientBrush> objekt, který pracuje <xref:System.Drawing.Graphics> objekt vyplníte obdélníku postupně Změna barev.</span><span class="sxs-lookup"><span data-stu-id="d1cf4-108">The <xref:System.Drawing.Graphics.FillRectangle%2A> method can receive a pointer to a <xref:System.Drawing.Drawing2D.LinearGradientBrush> object, which works with the <xref:System.Drawing.Graphics> object to fill a rectangle with a gradually changing color.</span></span> <span data-ttu-id="d1cf4-109"><xref:System.Drawing.Font>a <xref:System.Drawing.StringFormat> objekty ovlivnit způsob <xref:System.Drawing.Graphics> objekt nevykresluje text.</span><span class="sxs-lookup"><span data-stu-id="d1cf4-109"><xref:System.Drawing.Font> and <xref:System.Drawing.StringFormat> objects influence the way a <xref:System.Drawing.Graphics> object draws text.</span></span> <span data-ttu-id="d1cf4-110">A <xref:System.Drawing.Drawing2D.Matrix> objekt ukládá a zpracovává Světové transformace <xref:System.Drawing.Graphics> objekt, který se používá k otočit, škálovat a překlopit bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="d1cf4-110">A <xref:System.Drawing.Drawing2D.Matrix> object stores and manipulates the world transformation of a <xref:System.Drawing.Graphics> object, which is used to rotate, scale, and flip images.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="d1cf4-111">poskytuje několik struktury (například <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, a <xref:System.Drawing.Size>) pro uspořádání dat grafiky.</span><span class="sxs-lookup"><span data-stu-id="d1cf4-111"> provides several structures (for example, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, and <xref:System.Drawing.Size>) for organizing graphics data.</span></span> <span data-ttu-id="d1cf4-112">Navíc určité třídy slouží především strukturované datové typy.</span><span class="sxs-lookup"><span data-stu-id="d1cf4-112">Also, certain classes serve primarily as structured data types.</span></span> <span data-ttu-id="d1cf4-113">Například <xref:System.Drawing.Imaging.BitmapData> třída je Pomocník pro <xref:System.Drawing.Bitmap> třída a <xref:System.Drawing.Drawing2D.PathData> třída je Pomocník pro <xref:System.Drawing.Drawing2D.GraphicsPath> třídy.</span><span class="sxs-lookup"><span data-stu-id="d1cf4-113">For example, the <xref:System.Drawing.Imaging.BitmapData> class is a helper for the <xref:System.Drawing.Bitmap> class, and the <xref:System.Drawing.Drawing2D.PathData> class is a helper for the <xref:System.Drawing.Drawing2D.GraphicsPath> class.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="d1cf4-114">definuje několik výčty, které jsou kolekce související konstanty.</span><span class="sxs-lookup"><span data-stu-id="d1cf4-114"> defines several enumerations, which are collections of related constants.</span></span> <span data-ttu-id="d1cf4-115">Například <xref:System.Drawing.Drawing2D.LineJoin> výčet obsahuje prvky <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, a <xref:System.Drawing.Drawing2D.LineJoin.Round>, který zadejte stylů, které umožňuje připojit dva řádky.</span><span class="sxs-lookup"><span data-stu-id="d1cf4-115">For example, the <xref:System.Drawing.Drawing2D.LineJoin> enumeration contains the elements <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, and <xref:System.Drawing.Drawing2D.LineJoin.Round>, which specify styles that can be used to join two lines.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1cf4-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1cf4-116">See Also</span></span>  
 [<span data-ttu-id="d1cf4-117">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="d1cf4-117">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [<span data-ttu-id="d1cf4-118">O GDI + spravovaný kód</span><span class="sxs-lookup"><span data-stu-id="d1cf4-118">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [<span data-ttu-id="d1cf4-119">Použití spravovaných grafických tříd</span><span class="sxs-lookup"><span data-stu-id="d1cf4-119">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
