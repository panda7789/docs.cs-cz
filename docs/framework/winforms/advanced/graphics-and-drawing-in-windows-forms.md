---
title: Grafika a kreslení
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 10ad18d38c84f6e447601ab6c8bf1a953dabb7cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746400"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="70b82-102">Grafika a kreslení v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="70b82-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="70b82-103">Modul CLR (Common Language Runtime) používá pokročilou implementaci Windows GDI (GDI) s názvem GDI+.</span><span class="sxs-lookup"><span data-stu-id="70b82-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="70b82-104">Pomocí nástroje GDI+ můžete vytvářet grafiky, kreslit text a manipulovat s grafickými obrázky jako objekty.</span><span class="sxs-lookup"><span data-stu-id="70b82-104">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="70b82-105">GDI+ je navržený tak, aby poskytoval výkon a snadné použití.</span><span class="sxs-lookup"><span data-stu-id="70b82-105">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="70b82-106">Pomocí rozhraní GDI+ můžete vykreslit grafické obrázky na model Windows Forms a ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="70b82-106">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="70b82-107">I když nemůžete použít rozhraní GDI+ přímo na webových formulářích, můžete zobrazit grafické obrázky pomocí ovládacího prvku webového serveru imagí.</span><span class="sxs-lookup"><span data-stu-id="70b82-107">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="70b82-108">V této části najdete témata, která zavádějí základy programování v rozhraní GDI+.</span><span class="sxs-lookup"><span data-stu-id="70b82-108">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="70b82-109">I když se nejedná o ucelený odkaz, obsahuje tato část informace o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>a <xref:System.Drawing.Color>ch objektech a vysvětluje, jak provádět takové úkoly jako kreslení tvarů, kreslení textu nebo zobrazování obrázků.</span><span class="sxs-lookup"><span data-stu-id="70b82-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="70b82-110">Další informace najdete v tématu [Reference k rozhraní GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="70b82-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="70b82-111">Pokud byste chtěli přejít na začátek a hned začít, přečtěte si téma [Začínáme with Graphics Programming](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="70b82-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="70b82-112">Obsahuje témata týkající se použití kódu k vykreslování čar, tvarů, textu a dalších v modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="70b82-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70b82-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="70b82-113">In This Section</span></span>  
 [<span data-ttu-id="70b82-114">Přehled grafiky</span><span class="sxs-lookup"><span data-stu-id="70b82-114">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="70b82-115">Poskytuje Úvod do spravovaných tříd souvisejících s grafikou.</span><span class="sxs-lookup"><span data-stu-id="70b82-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="70b82-116">Informace o spravovaném kódu GDI+</span><span class="sxs-lookup"><span data-stu-id="70b82-116">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="70b82-117">Poskytuje informace o spravovaných třídách rozhraní GDI+.</span><span class="sxs-lookup"><span data-stu-id="70b82-117">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="70b82-118">Použití spravovaných grafických tříd</span><span class="sxs-lookup"><span data-stu-id="70b82-118">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="70b82-119">Ukazuje, jak provést různé úlohy pomocí spravovaných tříd rozhraní GDI+.</span><span class="sxs-lookup"><span data-stu-id="70b82-119">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="70b82-120">Odkaz</span><span class="sxs-lookup"><span data-stu-id="70b82-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="70b82-121">Poskytuje přístup k funkci GDI+ Basic Graphics.</span><span class="sxs-lookup"><span data-stu-id="70b82-121">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="70b82-122">Poskytuje pokročilé funkce dvourozměrné a vektorové grafiky.</span><span class="sxs-lookup"><span data-stu-id="70b82-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="70b82-123">Poskytuje pokročilé funkce pro vytváření bitových kopií rozhraní GDI+.</span><span class="sxs-lookup"><span data-stu-id="70b82-123">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="70b82-124">Poskytuje pokročilé funkce typografie rozhraní GDI+.</span><span class="sxs-lookup"><span data-stu-id="70b82-124">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="70b82-125">Třídy v tomto oboru názvů lze použít k vytvoření a použití kolekcí písem.</span><span class="sxs-lookup"><span data-stu-id="70b82-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="70b82-126">Poskytuje funkce tisku.</span><span class="sxs-lookup"><span data-stu-id="70b82-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="70b82-127">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="70b82-127">Related Sections</span></span>  
 [<span data-ttu-id="70b82-128">Malování a vykreslování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="70b82-128">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="70b82-129">Obsahuje podrobnosti o tom, jak poskytnout kód pro vykreslování ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="70b82-129">Details how to provide code for painting controls.</span></span>
