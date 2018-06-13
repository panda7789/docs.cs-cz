---
title: Grafika a kreslení v rozhraní Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 3dbb5d36ce2e550c0420a23b40247771e10d60ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521599"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="2c3f6-102">Grafika a kreslení v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c3f6-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="2c3f6-103">Pokročilé implementace rozhraní Windows grafiky zařízení používá modul common language runtime ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) názvem [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2c3f6-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) called [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="2c3f6-104">S [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete vytvořit grafiky, kreslení textu a manipulaci s grafickým rozhraním obrázky jako objekty.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-104">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can create graphics, draw text, and manipulate graphical images as objects.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="2c3f6-105"> je určená k poskytování výkonu a snadného použití.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-105"> is designed to offer performance and ease of use.</span></span> <span data-ttu-id="2c3f6-106">Můžete použít [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] k vykreslení grafické Image na Windows Forms a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-106">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="2c3f6-107">I když nelze použít [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] přímo na webových formulářů, můžete zobrazit grafické obrázky prostřednictvím ovládacího prvku Obrázek webového serveru.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-107">Although you cannot use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="2c3f6-108">V této části najdete témata, která zavést Základy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programování.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-108">In this section, you will find topics that introduce the fundamentals of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programming.</span></span> <span data-ttu-id="2c3f6-109">I když nemají být komplexní odkaz, tato část obsahuje informace o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, a <xref:System.Drawing.Color> objektů a vysvětluje, jak provádět úlohy, jako jsou kreslení tvarů, kreslení textu, nebo zobrazení obrázků.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="2c3f6-110">Další informace najdete v tématu [GDI + odkaz](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).</span><span class="sxs-lookup"><span data-stu-id="2c3f6-110">For more information, see [GDI+ Reference](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).</span></span>  
  
 <span data-ttu-id="2c3f6-111">Pokud chcete v přeskočit a rovnou začít, najdete v článku [Začínáme s programováním grafiky](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="2c3f6-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="2c3f6-112">Obsahuje témata týkající se používání kódu kreslení čar, tvarů, text a informace v rozhraní Windows forms.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c3f6-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2c3f6-113">In This Section</span></span>  
 [<span data-ttu-id="2c3f6-114">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="2c3f6-114">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 <span data-ttu-id="2c3f6-115">Poskytuje úvod do související grafika spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="2c3f6-116">Informace o spravovaném kódu GDI+</span><span class="sxs-lookup"><span data-stu-id="2c3f6-116">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 <span data-ttu-id="2c3f6-117">Poskytuje informace o spravovaný [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] třídy.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-117">Provides information about the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span>  
  
 [<span data-ttu-id="2c3f6-118">Použití spravovaných grafických tříd</span><span class="sxs-lookup"><span data-stu-id="2c3f6-118">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 <span data-ttu-id="2c3f6-119">Ukazuje, jak dokončit různé úkoly pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-119">Demonstrates how to complete a variety of tasks using the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2c3f6-120">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2c3f6-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="2c3f6-121">Poskytuje přístup k [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] základní grafické funkce.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-121">Provides access to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="2c3f6-122">Poskytuje pokročilé dvourozměrná a vektorové grafiky funkce.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="2c3f6-123">Poskytuje pokročilé [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkce pro zpracování obrázků.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-123">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="2c3f6-124">Poskytuje pokročilé [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typografii funkce.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-124">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typography functionality.</span></span> <span data-ttu-id="2c3f6-125">Vytvoření a použití písem, lze použít třídy v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="2c3f6-126">Poskytuje funkce, tisku.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2c3f6-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2c3f6-127">Related Sections</span></span>  
 [<span data-ttu-id="2c3f6-128">Malování a vykreslování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="2c3f6-128">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="2c3f6-129">Podrobnosti, jak poskytnout kód pro vykreslování ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="2c3f6-129">Details how to provide code for painting controls.</span></span>
