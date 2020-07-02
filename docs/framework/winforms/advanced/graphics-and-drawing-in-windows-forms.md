---
title: Grafika a kreslení
description: Přečtěte si o objektech grafiky, pera, štětce a barvě a o tom, jak provádět takové úkoly jako kreslení tvarů, kreslení textu nebo zobrazování obrázků v model Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 58d8cde6aa102225cf9e3c342efe37218c818307
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618399"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="88c91-103">Grafika a kreslení v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88c91-103">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="88c91-104">Modul CLR (Common Language Runtime) používá pokročilou implementaci Windows GDI (GDI) s názvem GDI+.</span><span class="sxs-lookup"><span data-stu-id="88c91-104">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="88c91-105">Pomocí nástroje GDI+ můžete vytvářet grafiky, kreslit text a manipulovat s grafickými obrázky jako objekty.</span><span class="sxs-lookup"><span data-stu-id="88c91-105">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="88c91-106">GDI+ je navržený tak, aby poskytoval výkon a snadné použití.</span><span class="sxs-lookup"><span data-stu-id="88c91-106">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="88c91-107">Pomocí rozhraní GDI+ můžete vykreslit grafické obrázky na model Windows Forms a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="88c91-107">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="88c91-108">I když nemůžete použít rozhraní GDI+ přímo na webových formulářích, můžete zobrazit grafické obrázky pomocí ovládacího prvku webového serveru imagí.</span><span class="sxs-lookup"><span data-stu-id="88c91-108">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="88c91-109">V této části najdete témata, která zavádějí základy programování v rozhraní GDI+.</span><span class="sxs-lookup"><span data-stu-id="88c91-109">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="88c91-110">I když není zamýšlen jako vyčerpávající odkaz, Tato část obsahuje informace o <xref:System.Drawing.Graphics> <xref:System.Drawing.Pen> objektech,, <xref:System.Drawing.Brush> a a <xref:System.Drawing.Color> vysvětluje, jak provádět takové úkoly jako vykreslování tvarů, kreslení textu nebo zobrazování obrázků.</span><span class="sxs-lookup"><span data-stu-id="88c91-110">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="88c91-111">Další informace najdete v tématu [Reference k rozhraní GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="88c91-111">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="88c91-112">Pokud byste chtěli přejít na začátek a hned začít, přečtěte si téma [Začínáme with Graphics Programming](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="88c91-112">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="88c91-113">Obsahuje témata týkající se použití kódu k vykreslování čar, tvarů, textu a dalších v modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="88c91-113">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="88c91-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="88c91-114">In This Section</span></span>  
 [<span data-ttu-id="88c91-115">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="88c91-115">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="88c91-116">Poskytuje Úvod do spravovaných tříd souvisejících s grafikou.</span><span class="sxs-lookup"><span data-stu-id="88c91-116">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="88c91-117">Informace o spravovaném kódu GDI+</span><span class="sxs-lookup"><span data-stu-id="88c91-117">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="88c91-118">Poskytuje informace o spravovaných třídách rozhraní GDI+.</span><span class="sxs-lookup"><span data-stu-id="88c91-118">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="88c91-119">Použití spravovaných grafických tříd</span><span class="sxs-lookup"><span data-stu-id="88c91-119">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="88c91-120">Ukazuje, jak provést různé úlohy pomocí spravovaných tříd rozhraní GDI+.</span><span class="sxs-lookup"><span data-stu-id="88c91-120">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="88c91-121">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="88c91-121">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="88c91-122">Poskytuje přístup k funkci GDI+ Basic Graphics.</span><span class="sxs-lookup"><span data-stu-id="88c91-122">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="88c91-123">Poskytuje pokročilé funkce dvourozměrné a vektorové grafiky.</span><span class="sxs-lookup"><span data-stu-id="88c91-123">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="88c91-124">Poskytuje pokročilé funkce pro vytváření bitových kopií rozhraní GDI+.</span><span class="sxs-lookup"><span data-stu-id="88c91-124">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="88c91-125">Poskytuje pokročilé funkce typografie rozhraní GDI+.</span><span class="sxs-lookup"><span data-stu-id="88c91-125">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="88c91-126">Třídy v tomto oboru názvů lze použít k vytvoření a použití kolekcí písem.</span><span class="sxs-lookup"><span data-stu-id="88c91-126">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="88c91-127">Poskytuje funkce tisku.</span><span class="sxs-lookup"><span data-stu-id="88c91-127">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="88c91-128">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="88c91-128">Related Sections</span></span>  
 [<span data-ttu-id="88c91-129">Malování a vykreslování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="88c91-129">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="88c91-130">Obsahuje podrobnosti o tom, jak poskytnout kód pro vykreslování ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="88c91-130">Details how to provide code for painting controls.</span></span>
