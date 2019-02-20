---
title: Grafika a kreslení v rozhraní Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e6d3c395a2d5b8ae885114a53b230d7265102bc8
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441161"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="3d58b-102">Grafika a kreslení v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d58b-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="3d58b-103">Modul common language runtime používá pokročilé provádění Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) volá [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d58b-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) called [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="3d58b-104">S [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete vytvořit grafiky, kreslení textu a manipulaci s grafické obrázky jako objekty.</span><span class="sxs-lookup"><span data-stu-id="3d58b-104">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can create graphics, draw text, and manipulate graphical images as objects.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="3d58b-105">je určená k výkonu a snadnost použití.</span><span class="sxs-lookup"><span data-stu-id="3d58b-105">is designed to offer performance and ease of use.</span></span> <span data-ttu-id="3d58b-106">Můžete použít [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] k vykreslení grafické obrázky ve Windows Forms a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="3d58b-106">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="3d58b-107">I když [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] přímo na webové formuláře, můžete zobrazit grafické obrázky prostřednictvím ovládacího prvku obrázek Webový Server.</span><span class="sxs-lookup"><span data-stu-id="3d58b-107">Although you cannot use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="3d58b-108">V této části najdete témata, která představují základní informace o [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programování.</span><span class="sxs-lookup"><span data-stu-id="3d58b-108">In this section, you will find topics that introduce the fundamentals of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programming.</span></span> <span data-ttu-id="3d58b-109">I když nemají být komplexní referenční informace, tato část obsahuje informace o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, a <xref:System.Drawing.Color> objekty a vysvětluje, jak provádět úkoly, jako je kreslení tvarů, textu, kreslení nebo zobrazení obrázků.</span><span class="sxs-lookup"><span data-stu-id="3d58b-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="3d58b-110">Další informace najdete v tématu [referenční dokumentace rozhraní GDI +](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="3d58b-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="3d58b-111">Pokud byste chtěli přidejte se k nám a rovnou začít, najdete v článku [Začínáme s programováním grafiky](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="3d58b-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="3d58b-112">Obsahuje témata o tom, jak použít kód kreslení čar, tvary, text a informace o Windows forms.</span><span class="sxs-lookup"><span data-stu-id="3d58b-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3d58b-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3d58b-113">In This Section</span></span>  
 [<span data-ttu-id="3d58b-114">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="3d58b-114">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 <span data-ttu-id="3d58b-115">Poskytuje úvod ke spravovaným třídám související grafiky.</span><span class="sxs-lookup"><span data-stu-id="3d58b-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="3d58b-116">Informace o spravovaném kódu GDI+</span><span class="sxs-lookup"><span data-stu-id="3d58b-116">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 <span data-ttu-id="3d58b-117">Poskytuje informace o managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] třídy.</span><span class="sxs-lookup"><span data-stu-id="3d58b-117">Provides information about the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span>  
  
 [<span data-ttu-id="3d58b-118">Použití spravovaných grafických tříd</span><span class="sxs-lookup"><span data-stu-id="3d58b-118">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 <span data-ttu-id="3d58b-119">Ukazuje, jak k provádění různých úloh s použitím [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] spravovaných tříd.</span><span class="sxs-lookup"><span data-stu-id="3d58b-119">Demonstrates how to complete a variety of tasks using the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3d58b-120">Odkaz</span><span class="sxs-lookup"><span data-stu-id="3d58b-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="3d58b-121">Poskytuje přístup k [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] základní grafické funkce.</span><span class="sxs-lookup"><span data-stu-id="3d58b-121">Provides access to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="3d58b-122">Poskytuje vyspělé 2D a vektorové grafické funkce.</span><span class="sxs-lookup"><span data-stu-id="3d58b-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="3d58b-123">Poskytuje pokročilé [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkce pro zpracování obrázků.</span><span class="sxs-lookup"><span data-stu-id="3d58b-123">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="3d58b-124">Poskytuje pokročilé [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Typografie funkce.</span><span class="sxs-lookup"><span data-stu-id="3d58b-124">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typography functionality.</span></span> <span data-ttu-id="3d58b-125">Třídy v tomto oboru názvů lze použít k vytvoření a použití kolekce písem.</span><span class="sxs-lookup"><span data-stu-id="3d58b-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="3d58b-126">Poskytuje funkce tisku.</span><span class="sxs-lookup"><span data-stu-id="3d58b-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3d58b-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3d58b-127">Related Sections</span></span>  
 [<span data-ttu-id="3d58b-128">Malování a vykreslování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="3d58b-128">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="3d58b-129">Podrobně popisuje, jak poskytnout kód pro vykreslování ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="3d58b-129">Details how to provide code for painting controls.</span></span>
