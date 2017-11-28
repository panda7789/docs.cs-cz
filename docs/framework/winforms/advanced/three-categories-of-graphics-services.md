---
title: "Tři kategorie grafických služeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53429513426d3b197da4740e5e92d44d8b3a5533
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="three-categories-of-graphics-services"></a><span data-ttu-id="a48e7-102">Tři kategorie grafických služeb</span><span class="sxs-lookup"><span data-stu-id="a48e7-102">Three Categories of Graphics Services</span></span>
<span data-ttu-id="a48e7-103">Nabídky grafiky ve Windows Forms lze rozdělit do těchto tří široký kategorií:</span><span class="sxs-lookup"><span data-stu-id="a48e7-103">The graphics offerings in Windows Forms fall into the following three broad categories:</span></span>  
  
-   <span data-ttu-id="a48e7-104">Dvourozměrná (2-D) vektorová grafika</span><span class="sxs-lookup"><span data-stu-id="a48e7-104">Two-dimensional (2-D) vector graphics</span></span>  
  
-   <span data-ttu-id="a48e7-105">Vytvoření bitové kopie</span><span class="sxs-lookup"><span data-stu-id="a48e7-105">Imaging</span></span>  
  
-   <span data-ttu-id="a48e7-106">Typografie</span><span class="sxs-lookup"><span data-stu-id="a48e7-106">Typography</span></span>  
  
## <a name="2-d-vector-graphics"></a><span data-ttu-id="a48e7-107">2D vektorová grafika</span><span class="sxs-lookup"><span data-stu-id="a48e7-107">2-D Vector Graphics</span></span>  
 <span data-ttu-id="a48e7-108">Dvourozměrná vektorová grafika jsou primitiv; například čar, křivek a obrázky; která jsou určena sady bodů na souřadnicový systém.</span><span class="sxs-lookup"><span data-stu-id="a48e7-108">Two-dimensional vector graphics are primitives; such as lines, curves, and figures; that are specified by sets of points on a coordinate system.</span></span> <span data-ttu-id="a48e7-109">Například přímku je zadána jeho dva koncové body a obdélníku je zadána bod poskytnutí umístění jeho levého horního rohu a pár čísel, která poskytuje svou šířku a výšku.</span><span class="sxs-lookup"><span data-stu-id="a48e7-109">For example, a straight line is specified by its two endpoints, and a rectangle is specified by a point giving the location of its upper-left corner and a pair of numbers giving its width and height.</span></span> <span data-ttu-id="a48e7-110">Jednoduché cesta je určena pole bodů, která jsou připojena linkami přímých.</span><span class="sxs-lookup"><span data-stu-id="a48e7-110">A simple path is specified by an array of points that are connected by straight lines.</span></span> <span data-ttu-id="a48e7-111">Bézierovy křivky je sofistikované křivky určeného čtyři kontrolní body.</span><span class="sxs-lookup"><span data-stu-id="a48e7-111">A Bézier spline is a sophisticated curve specified by four control points.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="a48e7-112">poskytuje třídy a struktury, které obsahují informace o primitiv sami, třídy, které obsahují informace o tom, jak se budou vykreslovat primitivní elementy a třídy, které skutečně provést kreslení.</span><span class="sxs-lookup"><span data-stu-id="a48e7-112"> provides classes and structures that store information about the primitives themselves, classes that store information about how the primitives will be drawn, and classes that actually do the drawing.</span></span> <span data-ttu-id="a48e7-113">Například <xref:System.Drawing.Rectangle> struktura ukládá umístění a velikost obdélníku; <xref:System.Drawing.Pen> třída ukládá informace o řádku barvu, šířku čáry a styl čáry; a <xref:System.Drawing.Graphics> třída obsahuje metody pro kreslení obdélníků řádky, cesty, a Další údaje.</span><span class="sxs-lookup"><span data-stu-id="a48e7-113">For example, the <xref:System.Drawing.Rectangle> structure stores the location and size of a rectangle; the <xref:System.Drawing.Pen> class stores information about line color, line width, and line style; and the <xref:System.Drawing.Graphics> class has methods for drawing lines, rectangles, paths, and other figures.</span></span> <span data-ttu-id="a48e7-114">Existují také některé <xref:System.Drawing.Brush> třídy, které obsahují informace o tom, zavře obrázky a cesty bude vyplněn barvy nebo vzory.</span><span class="sxs-lookup"><span data-stu-id="a48e7-114">There are also several <xref:System.Drawing.Brush> classes that store information about how closed figures and paths will be filled with colors or patterns.</span></span>  
  
 <span data-ttu-id="a48e7-115">Můžete zaznamenat bitovou kopii vektoru, což je posloupnost grafiky příkazy, metasoubory.</span><span class="sxs-lookup"><span data-stu-id="a48e7-115">You can record a vector image, which is a sequence of graphics commands, in a metafile.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="a48e7-116">poskytuje <xref:System.Drawing.Imaging.Metafile> třídu pro zaznamenání, zobrazení a uložení metasoubory.</span><span class="sxs-lookup"><span data-stu-id="a48e7-116"> provides the <xref:System.Drawing.Imaging.Metafile> class for recording, displaying, and saving metafiles.</span></span> <span data-ttu-id="a48e7-117">Pomocí <xref:System.Drawing.Imaging.MetafileHeader> a <xref:System.Drawing.Imaging.MetaHeader> třídy, si můžete prohlédnout data uložená v hlavičce metafile.</span><span class="sxs-lookup"><span data-stu-id="a48e7-117">With the <xref:System.Drawing.Imaging.MetafileHeader> and <xref:System.Drawing.Imaging.MetaHeader> classes, you can inspect the data stored in a metafile header.</span></span>  
  
## <a name="imaging"></a><span data-ttu-id="a48e7-118">Vytvoření bitové kopie</span><span class="sxs-lookup"><span data-stu-id="a48e7-118">Imaging</span></span>  
 <span data-ttu-id="a48e7-119">Některé typy obrázků se obtížně nebo dokonce znemožňují zobrazíte pomocí technik vektorová grafika.</span><span class="sxs-lookup"><span data-stu-id="a48e7-119">Certain kinds of pictures are difficult or impossible to display with the techniques of vector graphics.</span></span> <span data-ttu-id="a48e7-120">Obrázky na tlačítka panelu nástrojů a obrázky, které se zobrazují jako ikony jsou například obtížné určit jako kolekce čar a křivek.</span><span class="sxs-lookup"><span data-stu-id="a48e7-120">For example, the pictures on toolbar buttons and the pictures that appear as icons are difficult to specify as collections of lines and curves.</span></span> <span data-ttu-id="a48e7-121">S vysokým rozlišením digitální fotografie frekventované baseballové stadium je ještě obtížnější vytvoření pomocí vektoru techniky.</span><span class="sxs-lookup"><span data-stu-id="a48e7-121">A high-resolution digital photograph of a crowded baseball stadium is even more difficult to create with vector techniques.</span></span> <span data-ttu-id="a48e7-122">Bitové kopie tohoto typu jsou uloženy jako rastrové obrázky, které jsou pole čísla, která představují barvy jednotlivých tečky na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="a48e7-122">Images of this type are stored as bitmaps, which are arrays of numbers that represent the colors of individual dots on the screen.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="a48e7-123">poskytuje <xref:System.Drawing.Bitmap> třídu pro zobrazení, manipulace a ukládání bitmap.</span><span class="sxs-lookup"><span data-stu-id="a48e7-123"> provides the <xref:System.Drawing.Bitmap> class for displaying, manipulating, and saving bitmaps.</span></span>  
  
## <a name="typography"></a><span data-ttu-id="a48e7-124">Typografie</span><span class="sxs-lookup"><span data-stu-id="a48e7-124">Typography</span></span>  
 <span data-ttu-id="a48e7-125">Typografie je zobrazení textu v různých písma, velikosti a stylů.</span><span class="sxs-lookup"><span data-stu-id="a48e7-125">Typography is the display of text in a variety of fonts, sizes, and styles.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="a48e7-126">poskytuje rozsáhlou podporu pro tento složitý úkol.</span><span class="sxs-lookup"><span data-stu-id="a48e7-126"> provides extensive support for this complex task.</span></span> <span data-ttu-id="a48e7-127">Jeden z nových funkcí v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] subpixel vyhlazení, která umožňuje text vykreslení v displeje hladší vzhled.</span><span class="sxs-lookup"><span data-stu-id="a48e7-127">One of the new features in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is subpixel antialiasing, which gives text rendered on an LCD screen a smoother appearance.</span></span>  
  
 <span data-ttu-id="a48e7-128">Kromě toho Windows Forms nabízí možnost kreslení textu pomocí [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] možnosti v jeho <xref:System.Windows.Forms.TextRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="a48e7-128">In addition, Windows Forms offers the option to draw text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] capabilities in its <xref:System.Windows.Forms.TextRenderer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a48e7-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="a48e7-129">See Also</span></span>  
 [<span data-ttu-id="a48e7-130">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="a48e7-130">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [<span data-ttu-id="a48e7-131">O GDI + spravovaný kód</span><span class="sxs-lookup"><span data-stu-id="a48e7-131">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [<span data-ttu-id="a48e7-132">Použití spravovaných grafických tříd</span><span class="sxs-lookup"><span data-stu-id="a48e7-132">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
