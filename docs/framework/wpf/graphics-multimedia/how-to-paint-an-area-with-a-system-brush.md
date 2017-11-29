---
title: "Postupy: Vykreslení oblasti systémovým štětcem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 355df3718d90768cdfa8bc9780c44c19eb4bf9bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a><span data-ttu-id="3a55b-102">Postupy: Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="3a55b-102">How to: Paint an Area with a System Brush</span></span>
<span data-ttu-id="3a55b-103"><xref:System.Windows.SystemColors> Třída poskytuje přístup k systému štětce a barvy, například <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, a <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span><span class="sxs-lookup"><span data-stu-id="3a55b-103">The <xref:System.Windows.SystemColors> class provides access to system brushes and colors, such as <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, and <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span></span> <span data-ttu-id="3a55b-104">Je systém štětce <xref:System.Windows.Media.SolidColorBrush> objekt, který vybarví oblast s barvu zadaný systém.</span><span class="sxs-lookup"><span data-stu-id="3a55b-104">A system brush is a <xref:System.Windows.Media.SolidColorBrush> object that paints an area with the specified system color.</span></span> <span data-ttu-id="3a55b-105">Štětce systému vždy vytvoří plnou výplň; nelze použít k vytvoření přechodu.</span><span class="sxs-lookup"><span data-stu-id="3a55b-105">A system brush always produces a solid fill; it can't be used to create a gradient.</span></span>  
  
 <span data-ttu-id="3a55b-106">Štětce systému můžete použít jako statické nebo dynamické prostředků.</span><span class="sxs-lookup"><span data-stu-id="3a55b-106">You can use system brushes as either a static or a dynamic resource.</span></span> <span data-ttu-id="3a55b-107">Pomocí dynamického prostředku, pokud chcete, aby štětce k aktualizaci automaticky, pokud uživatel změní štětce systému, jako je aplikace spuštěna; Jinak použijte statické prostředků.</span><span class="sxs-lookup"><span data-stu-id="3a55b-107">Use a dynamic resource if you want the brush to update automatically if the user changes the system brush as the application is running; otherwise, use a static resource.</span></span> <span data-ttu-id="3a55b-108">Třída SystemColors obsahuje celou řadu statické vlastnosti, které následují striktní zásady vytváření názvů:</span><span class="sxs-lookup"><span data-stu-id="3a55b-108">The SystemColors class contains a variety of static properties that follow a strict naming convention:</span></span>  
  
-   <span data-ttu-id="3a55b-109">*\<SystemColor >*štětce</span><span class="sxs-lookup"><span data-stu-id="3a55b-109">*\<SystemColor>*Brush</span></span>  
  
     <span data-ttu-id="3a55b-110">Získá statický odkaz na <xref:System.Windows.Media.SolidColorBrush> barvy zadaný systému.</span><span class="sxs-lookup"><span data-stu-id="3a55b-110">Gets a static reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="3a55b-111">*\<SystemColor >*BrushKey</span><span class="sxs-lookup"><span data-stu-id="3a55b-111">*\<SystemColor>*BrushKey</span></span>  
  
     <span data-ttu-id="3a55b-112">Získá odkaz na dynamické <xref:System.Windows.Media.SolidColorBrush> barvy zadaný systému.</span><span class="sxs-lookup"><span data-stu-id="3a55b-112">Gets a dynamic reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="3a55b-113">*\<SystemColor >*barev</span><span class="sxs-lookup"><span data-stu-id="3a55b-113">*\<SystemColor>*Color</span></span>  
  
     <span data-ttu-id="3a55b-114">Získá statický odkaz na <xref:System.Windows.Media.Color> struktura barvu zadaný systém.</span><span class="sxs-lookup"><span data-stu-id="3a55b-114">Gets a static reference to a <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
-   <span data-ttu-id="3a55b-115">*\<SystemColor >*ColorKey</span><span class="sxs-lookup"><span data-stu-id="3a55b-115">*\<SystemColor>*ColorKey</span></span>  
  
     <span data-ttu-id="3a55b-116">Získá dynamické odkaz na <xref:System.Windows.Media.Color> struktura barvu zadaný systém.</span><span class="sxs-lookup"><span data-stu-id="3a55b-116">Gets a dynamic reference to the <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
 <span data-ttu-id="3a55b-117">Barva systému je <xref:System.Windows.Media.Color> struktura, která můžete použít ke konfiguraci štětce.</span><span class="sxs-lookup"><span data-stu-id="3a55b-117">A system color is a <xref:System.Windows.Media.Color> structure that can be used to configure a brush.</span></span> <span data-ttu-id="3a55b-118">Například můžete vytvořit pomocí nastavení barvy systému přechod <xref:System.Windows.Media.GradientStop.Color%2A> vlastnosti <xref:System.Windows.Media.LinearGradientBrush> objektu Přechodové zarážky pomocí systému barev.</span><span class="sxs-lookup"><span data-stu-id="3a55b-118">For example, you can create a gradient using system colors by setting the <xref:System.Windows.Media.GradientStop.Color%2A> properties of a <xref:System.Windows.Media.LinearGradientBrush> object's gradient stops with system colors.</span></span> <span data-ttu-id="3a55b-119">Příklad, naleznete v části [použití systému barev v přechodu](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="3a55b-119">For an example, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a55b-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a55b-120">Example</span></span>  
 <span data-ttu-id="3a55b-121">Následující příklad používá dynamický systém štětce odkaz nastavit na pozadí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="3a55b-121">The following example uses a dynamic system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 <span data-ttu-id="3a55b-122">Další příklad používá k nastavení pozadí tlačítko odkaz štětce statický systém.</span><span class="sxs-lookup"><span data-stu-id="3a55b-122">The next example uses a static system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 <span data-ttu-id="3a55b-123">Příkladem zobrazujícím postup používání systémové barvy v přechodu, najdete v části [používat barvy systému v přechodu](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="3a55b-123">For an example showing how to use a system color in a gradient, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a55b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a55b-124">See Also</span></span>  
 [<span data-ttu-id="3a55b-125">Použití systému barvy v přechodu</span><span class="sxs-lookup"><span data-stu-id="3a55b-125">Use System Colors in a Gradient</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)  
 [<span data-ttu-id="3a55b-126">Malování s plnou barvy a přechody – přehled</span><span class="sxs-lookup"><span data-stu-id="3a55b-126">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
