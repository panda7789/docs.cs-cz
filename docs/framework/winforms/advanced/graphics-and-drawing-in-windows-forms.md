---
title: Grafika a kreslení v rozhraní Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e110203605c31f90f71c949f81c18ebf464d52eb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505541"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="36dea-102">Grafika a kreslení v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="36dea-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="36dea-103">Modul common language runtime používá pokročilé implementace systému Windows rozhraní GDI (Graphics Device) volá rozhraní GDI +.</span><span class="sxs-lookup"><span data-stu-id="36dea-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="36dea-104">Pomocí GDI + můžete vytvořit grafiky, kreslení textu a manipulaci s grafické obrázky jako objekty.</span><span class="sxs-lookup"><span data-stu-id="36dea-104">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="36dea-105">Rozhraní GDI + je určená k výkonu a snadnost použití.</span><span class="sxs-lookup"><span data-stu-id="36dea-105">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="36dea-106">Můžete použijete GDI + k vykreslení grafické obrázky ve Windows Forms a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="36dea-106">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="36dea-107">I když nelze použijete GDI + přímo na webové formuláře, můžete zobrazit grafické obrázky prostřednictvím ovládacího prvku obrázek Webový Server.</span><span class="sxs-lookup"><span data-stu-id="36dea-107">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="36dea-108">V této části najdete témata, která představí základy programování v rozhraní GDI +.</span><span class="sxs-lookup"><span data-stu-id="36dea-108">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="36dea-109">I když nemají být komplexní referenční informace, tato část obsahuje informace o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, a <xref:System.Drawing.Color> objekty a vysvětluje, jak provádět úkoly, jako je kreslení tvarů, textu, kreslení nebo zobrazení obrázků.</span><span class="sxs-lookup"><span data-stu-id="36dea-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="36dea-110">Další informace najdete v tématu [referenční dokumentace rozhraní GDI +](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="36dea-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="36dea-111">Pokud byste chtěli přidejte se k nám a rovnou začít, najdete v článku [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="36dea-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="36dea-112">Obsahuje témata o tom, jak použít kód kreslení čar, tvary, text a informace o Windows forms.</span><span class="sxs-lookup"><span data-stu-id="36dea-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36dea-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="36dea-113">In This Section</span></span>  
 [<span data-ttu-id="36dea-114">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="36dea-114">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="36dea-115">Poskytuje úvod ke spravovaným třídám související grafiky.</span><span class="sxs-lookup"><span data-stu-id="36dea-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="36dea-116">Informace o spravovaném kódu GDI+</span><span class="sxs-lookup"><span data-stu-id="36dea-116">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="36dea-117">Poskytuje informace o spravovaných třídách rozhraní GDI +.</span><span class="sxs-lookup"><span data-stu-id="36dea-117">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="36dea-118">Použití spravovaných grafických tříd</span><span class="sxs-lookup"><span data-stu-id="36dea-118">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="36dea-119">Ukazuje, jak na kompletní širokou škálu úloh s použitím rozhraní GDI + spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="36dea-119">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="36dea-120">Odkaz</span><span class="sxs-lookup"><span data-stu-id="36dea-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="36dea-121">Poskytuje přístup k základní grafické funkce rozhraní GDI +.</span><span class="sxs-lookup"><span data-stu-id="36dea-121">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="36dea-122">Poskytuje vyspělé 2D a vektorové grafické funkce.</span><span class="sxs-lookup"><span data-stu-id="36dea-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="36dea-123">Poskytuje pokročilé rozhraní GDI + funkce pro zpracování obrázků.</span><span class="sxs-lookup"><span data-stu-id="36dea-123">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="36dea-124">Poskytuje pokročilé funkce Typografie rozhraní GDI +.</span><span class="sxs-lookup"><span data-stu-id="36dea-124">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="36dea-125">Třídy v tomto oboru názvů lze použít k vytvoření a použití kolekce písem.</span><span class="sxs-lookup"><span data-stu-id="36dea-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="36dea-126">Poskytuje funkce tisku.</span><span class="sxs-lookup"><span data-stu-id="36dea-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="36dea-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="36dea-127">Related Sections</span></span>  
 [<span data-ttu-id="36dea-128">Malování a vykreslování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="36dea-128">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="36dea-129">Podrobně popisuje, jak poskytnout kód pro vykreslování ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="36dea-129">Details how to provide code for painting controls.</span></span>
