---
title: 'Postupy: Vykreslení oblasti systémovým štětcem'
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: 26511c577bf06b016dfc69cedc7fce2bafb35f32
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645379"
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a><span data-ttu-id="baa3e-102">Postupy: Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="baa3e-102">How to: Paint an Area with a System Brush</span></span>
<span data-ttu-id="baa3e-103"><xref:System.Windows.SystemColors> Třídě poskytuje přístup k systémových štětců a barvy, jako například <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, a <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span><span class="sxs-lookup"><span data-stu-id="baa3e-103">The <xref:System.Windows.SystemColors> class provides access to system brushes and colors, such as <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, and <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span></span> <span data-ttu-id="baa3e-104">Je systém štětce <xref:System.Windows.Media.SolidColorBrush> objekt, který vykreslí oblasti barvou zadaný systém.</span><span class="sxs-lookup"><span data-stu-id="baa3e-104">A system brush is a <xref:System.Windows.Media.SolidColorBrush> object that paints an area with the specified system color.</span></span> <span data-ttu-id="baa3e-105">Systémové štětce vždy vytváří plné barvy; nelze použít k vytvoření přechodu.</span><span class="sxs-lookup"><span data-stu-id="baa3e-105">A system brush always produces a solid fill; it can't be used to create a gradient.</span></span>  
  
 <span data-ttu-id="baa3e-106">Systémových štětců slouží jako statická nebo dynamická prostředek.</span><span class="sxs-lookup"><span data-stu-id="baa3e-106">You can use system brushes as either a static or a dynamic resource.</span></span> <span data-ttu-id="baa3e-107">Použít dynamický prostředek štětce, který se automaticky aktualizovat, pokud uživatel změní štětce systému, jako je aplikace spuštěna; Jinak použijte statických prostředků.</span><span class="sxs-lookup"><span data-stu-id="baa3e-107">Use a dynamic resource if you want the brush to update automatically if the user changes the system brush as the application is running; otherwise, use a static resource.</span></span> <span data-ttu-id="baa3e-108">Třída SystemColors obsahuje širokou škálu statické vlastnosti, které následují přísné zásady vytváření názvů:</span><span class="sxs-lookup"><span data-stu-id="baa3e-108">The SystemColors class contains a variety of static properties that follow a strict naming convention:</span></span>  
  
- <span data-ttu-id="baa3e-109">*\<SystemColor >* štětce</span><span class="sxs-lookup"><span data-stu-id="baa3e-109">*\<SystemColor>* Brush</span></span>  
  
     <span data-ttu-id="baa3e-110">Získá statický odkaz na <xref:System.Windows.Media.SolidColorBrush> zadaný systém barvy.</span><span class="sxs-lookup"><span data-stu-id="baa3e-110">Gets a static reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
- <span data-ttu-id="baa3e-111">*\<SystemColor>* BrushKey</span><span class="sxs-lookup"><span data-stu-id="baa3e-111">*\<SystemColor>* BrushKey</span></span>  
  
     <span data-ttu-id="baa3e-112">Získá odkaz na dynamické <xref:System.Windows.Media.SolidColorBrush> zadaný systém barvy.</span><span class="sxs-lookup"><span data-stu-id="baa3e-112">Gets a dynamic reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
- <span data-ttu-id="baa3e-113">*\<SystemColor>* Color</span><span class="sxs-lookup"><span data-stu-id="baa3e-113">*\<SystemColor>* Color</span></span>  
  
     <span data-ttu-id="baa3e-114">Získá statický odkaz na <xref:System.Windows.Media.Color> struktury zadané systémovou barvou.</span><span class="sxs-lookup"><span data-stu-id="baa3e-114">Gets a static reference to a <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
- <span data-ttu-id="baa3e-115">*\<SystemColor >* ColorKey</span><span class="sxs-lookup"><span data-stu-id="baa3e-115">*\<SystemColor>* ColorKey</span></span>  
  
     <span data-ttu-id="baa3e-116">Získá odkaz na dynamické <xref:System.Windows.Media.Color> struktury zadané systémovou barvou.</span><span class="sxs-lookup"><span data-stu-id="baa3e-116">Gets a dynamic reference to the <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
 <span data-ttu-id="baa3e-117">Systémové barvy je <xref:System.Windows.Media.Color> struktura, která slouží ke konfiguraci štětce.</span><span class="sxs-lookup"><span data-stu-id="baa3e-117">A system color is a <xref:System.Windows.Media.Color> structure that can be used to configure a brush.</span></span> <span data-ttu-id="baa3e-118">Například můžete vytvořit pomocí nastavení systémových barev přechod <xref:System.Windows.Media.GradientStop.Color%2A> vlastnosti <xref:System.Windows.Media.LinearGradientBrush> objektu Přechodové zarážky pomocí systémových barev.</span><span class="sxs-lookup"><span data-stu-id="baa3e-118">For example, you can create a gradient using system colors by setting the <xref:System.Windows.Media.GradientStop.Color%2A> properties of a <xref:System.Windows.Media.LinearGradientBrush> object's gradient stops with system colors.</span></span> <span data-ttu-id="baa3e-119">Příklad najdete v tématu [použití systémových barev v gradientu](how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="baa3e-119">For an example, see [Use System Colors in a Gradient](how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="baa3e-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="baa3e-120">Example</span></span>  
 <span data-ttu-id="baa3e-121">Následující příklad používá odkaz štětce dynamickým nastavit pozadí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="baa3e-121">The following example uses a dynamic system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 <span data-ttu-id="baa3e-122">Následující příklad používá statický systém štětce odkaz nastavení pozadí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="baa3e-122">The next example uses a static system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 <span data-ttu-id="baa3e-123">Příklad ukazující způsob použití systémových barev v gradientu najdete v tématu [použití systémových barev v gradientu](how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="baa3e-123">For an example showing how to use a system color in a gradient, see [Use System Colors in a Gradient](how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa3e-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="baa3e-124">See also</span></span>

- [<span data-ttu-id="baa3e-125">Použití systémových barev v gradientu</span><span class="sxs-lookup"><span data-stu-id="baa3e-125">Use System Colors in a Gradient</span></span>](how-to-use-system-colors-in-a-gradient.md)
- [<span data-ttu-id="baa3e-126">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="baa3e-126">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
