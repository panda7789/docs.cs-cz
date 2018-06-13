---
title: 'Postupy: Použití systémových barev v gradientu'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 4c3fca1db031b0dc397e9db58195b9714ff8aa9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562177"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a><span data-ttu-id="1f780-102">Postupy: Použití systémových barev v gradientu</span><span class="sxs-lookup"><span data-stu-id="1f780-102">How to: Use System Colors in a Gradient</span></span>
<span data-ttu-id="1f780-103">Chcete-li používat barvy systému v přechodu, použijte  *\<SystemColor >* barev a  *\<SystemColor >* ColorKey statické vlastnosti <xref:System.Windows.SystemColors> třída získat odkaz na barvu, kde  *\<SystemColor >* je název barvy požadované systému.</span><span class="sxs-lookup"><span data-stu-id="1f780-103">To use a system color in a gradient, you use the *\<SystemColor>* Color and *\<SystemColor>* ColorKey static properties of the <xref:System.Windows.SystemColors> class to obtain a reference to the color, where *\<SystemColor>* is the name of the desired system color.</span></span> <span data-ttu-id="1f780-104">Použití  *\<SystemColor >* ColorKey vlastnosti, když chcete vytvořit dynamické odkaz, který aktualizuje automaticky jako změny motiv systému.</span><span class="sxs-lookup"><span data-stu-id="1f780-104">Use the *\<SystemColor>* ColorKey properties when you want to create a dynamic reference that updates automatically as the system theme changes.</span></span> <span data-ttu-id="1f780-105">Jinak použijte  *\<SystemColor >* barvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1f780-105">Otherwise, use the *\<SystemColor>* Color properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f780-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f780-106">Example</span></span>  
 <span data-ttu-id="1f780-107">Následující příklad používá dynamický systém barva prostředky pro vytvoření přechodu.</span><span class="sxs-lookup"><span data-stu-id="1f780-107">The following example uses dynamic system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 <span data-ttu-id="1f780-108">Další příklad používá statický systém barva prostředků k vytvoření přechodu.</span><span class="sxs-lookup"><span data-stu-id="1f780-108">The next example uses static system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="1f780-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f780-109">See Also</span></span>  
 <xref:System.Windows.SystemColors>  
 [<span data-ttu-id="1f780-110">Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="1f780-110">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="1f780-111">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="1f780-111">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
