---
title: 'Postupy: Vykreslení oblasti systémovým štětcem'
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: f8a66ffc283016d65a17b33e98ce28fe4cd1c242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561144"
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a><span data-ttu-id="5d11d-102">Postupy: Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="5d11d-102">How to: Paint an Area with a System Brush</span></span>
<span data-ttu-id="5d11d-103"><xref:System.Windows.SystemColors> Třída poskytuje přístup k systému štětce a barvy, například <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, a <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span><span class="sxs-lookup"><span data-stu-id="5d11d-103">The <xref:System.Windows.SystemColors> class provides access to system brushes and colors, such as <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, and <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span></span> <span data-ttu-id="5d11d-104">Je systém štětce <xref:System.Windows.Media.SolidColorBrush> objekt, který vybarví oblast s barvu zadaný systém.</span><span class="sxs-lookup"><span data-stu-id="5d11d-104">A system brush is a <xref:System.Windows.Media.SolidColorBrush> object that paints an area with the specified system color.</span></span> <span data-ttu-id="5d11d-105">Štětce systému vždy vytvoří plnou výplň; nelze použít k vytvoření přechodu.</span><span class="sxs-lookup"><span data-stu-id="5d11d-105">A system brush always produces a solid fill; it can't be used to create a gradient.</span></span>  
  
 <span data-ttu-id="5d11d-106">Štětce systému můžete použít jako statické nebo dynamické prostředků.</span><span class="sxs-lookup"><span data-stu-id="5d11d-106">You can use system brushes as either a static or a dynamic resource.</span></span> <span data-ttu-id="5d11d-107">Pomocí dynamického prostředku, pokud chcete, aby štětce k aktualizaci automaticky, pokud uživatel změní štětce systému, jako je aplikace spuštěna; Jinak použijte statické prostředků.</span><span class="sxs-lookup"><span data-stu-id="5d11d-107">Use a dynamic resource if you want the brush to update automatically if the user changes the system brush as the application is running; otherwise, use a static resource.</span></span> <span data-ttu-id="5d11d-108">Třída SystemColors obsahuje celou řadu statické vlastnosti, které následují striktní zásady vytváření názvů:</span><span class="sxs-lookup"><span data-stu-id="5d11d-108">The SystemColors class contains a variety of static properties that follow a strict naming convention:</span></span>  
  
-   <span data-ttu-id="5d11d-109">*\<SystemColor >* štětce</span><span class="sxs-lookup"><span data-stu-id="5d11d-109">*\<SystemColor>* Brush</span></span>  
  
     <span data-ttu-id="5d11d-110">Získá statický odkaz na <xref:System.Windows.Media.SolidColorBrush> barvy zadaný systému.</span><span class="sxs-lookup"><span data-stu-id="5d11d-110">Gets a static reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="5d11d-111">*\<SystemColor >* BrushKey</span><span class="sxs-lookup"><span data-stu-id="5d11d-111">*\<SystemColor>* BrushKey</span></span>  
  
     <span data-ttu-id="5d11d-112">Získá odkaz na dynamické <xref:System.Windows.Media.SolidColorBrush> barvy zadaný systému.</span><span class="sxs-lookup"><span data-stu-id="5d11d-112">Gets a dynamic reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="5d11d-113">*\<SystemColor >* barev</span><span class="sxs-lookup"><span data-stu-id="5d11d-113">*\<SystemColor>* Color</span></span>  
  
     <span data-ttu-id="5d11d-114">Získá statický odkaz na <xref:System.Windows.Media.Color> struktura barvu zadaný systém.</span><span class="sxs-lookup"><span data-stu-id="5d11d-114">Gets a static reference to a <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
-   <span data-ttu-id="5d11d-115">*\<SystemColor >* ColorKey</span><span class="sxs-lookup"><span data-stu-id="5d11d-115">*\<SystemColor>* ColorKey</span></span>  
  
     <span data-ttu-id="5d11d-116">Získá dynamické odkaz na <xref:System.Windows.Media.Color> struktura barvu zadaný systém.</span><span class="sxs-lookup"><span data-stu-id="5d11d-116">Gets a dynamic reference to the <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
 <span data-ttu-id="5d11d-117">Barva systému je <xref:System.Windows.Media.Color> struktura, která můžete použít ke konfiguraci štětce.</span><span class="sxs-lookup"><span data-stu-id="5d11d-117">A system color is a <xref:System.Windows.Media.Color> structure that can be used to configure a brush.</span></span> <span data-ttu-id="5d11d-118">Například můžete vytvořit pomocí nastavení barvy systému přechod <xref:System.Windows.Media.GradientStop.Color%2A> vlastnosti <xref:System.Windows.Media.LinearGradientBrush> objektu Přechodové zarážky pomocí systému barev.</span><span class="sxs-lookup"><span data-stu-id="5d11d-118">For example, you can create a gradient using system colors by setting the <xref:System.Windows.Media.GradientStop.Color%2A> properties of a <xref:System.Windows.Media.LinearGradientBrush> object's gradient stops with system colors.</span></span> <span data-ttu-id="5d11d-119">Příklad, naleznete v části [použití systému barev v přechodu](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="5d11d-119">For an example, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d11d-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d11d-120">Example</span></span>  
 <span data-ttu-id="5d11d-121">Následující příklad používá dynamický systém štětce odkaz nastavit na pozadí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="5d11d-121">The following example uses a dynamic system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 <span data-ttu-id="5d11d-122">Další příklad používá k nastavení pozadí tlačítko odkaz štětce statický systém.</span><span class="sxs-lookup"><span data-stu-id="5d11d-122">The next example uses a static system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 <span data-ttu-id="5d11d-123">Příkladem zobrazujícím postup používání systémové barvy v přechodu, najdete v části [používat barvy systému v přechodu](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="5d11d-123">For an example showing how to use a system color in a gradient, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d11d-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d11d-124">See Also</span></span>  
 [<span data-ttu-id="5d11d-125">Použití systémových barev v gradientu</span><span class="sxs-lookup"><span data-stu-id="5d11d-125">Use System Colors in a Gradient</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)  
 [<span data-ttu-id="5d11d-126">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="5d11d-126">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
