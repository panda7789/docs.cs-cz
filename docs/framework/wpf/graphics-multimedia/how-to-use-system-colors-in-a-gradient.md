---
title: 'Postupy: Použití systémových barev v přechodu'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 55c99640907a0c372f8c7bbc50b9b45c9f15ef3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769236"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a><span data-ttu-id="0b112-102">Postupy: Použití systémových barev v přechodu</span><span class="sxs-lookup"><span data-stu-id="0b112-102">How to: Use System Colors in a Gradient</span></span>
<span data-ttu-id="0b112-103">Pokud chcete použít systémové barvy v přechodu, je použít  *\<SystemColor >* barvu a  *\<SystemColor >* ColorKey statické vlastnosti <xref:System.Windows.SystemColors> třídy získat odkaz na barvu, kde  *\<SystemColor >* je název požadované systémovou barvou.</span><span class="sxs-lookup"><span data-stu-id="0b112-103">To use a system color in a gradient, you use the *\<SystemColor>* Color and *\<SystemColor>* ColorKey static properties of the <xref:System.Windows.SystemColors> class to obtain a reference to the color, where *\<SystemColor>* is the name of the desired system color.</span></span> <span data-ttu-id="0b112-104">Použití  *\<SystemColor >* ColorKey vlastnosti, pokud chcete vytvořit dynamické odkaz, který se aktualizuje automaticky při změně motiv systému.</span><span class="sxs-lookup"><span data-stu-id="0b112-104">Use the *\<SystemColor>* ColorKey properties when you want to create a dynamic reference that updates automatically as the system theme changes.</span></span> <span data-ttu-id="0b112-105">Jinak použijte  *\<SystemColor >* barva vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0b112-105">Otherwise, use the *\<SystemColor>* Color properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b112-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b112-106">Example</span></span>  
 <span data-ttu-id="0b112-107">Následující příklad používá dynamické systémových barev prostředků k vytvoření přechodu.</span><span class="sxs-lookup"><span data-stu-id="0b112-107">The following example uses dynamic system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 <span data-ttu-id="0b112-108">Následující příklad používá statickou systémových barev prostředků k vytvoření přechodu.</span><span class="sxs-lookup"><span data-stu-id="0b112-108">The next example uses static system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="0b112-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b112-109">See also</span></span>

- <xref:System.Windows.SystemColors>
- [<span data-ttu-id="0b112-110">Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="0b112-110">Paint an Area with a System Brush</span></span>](how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="0b112-111">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="0b112-111">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
