---
title: 'Postupy: Animace velikosti FrameworkElement'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17882494e48c5d692c8a774e6d77408557976c71
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a><span data-ttu-id="65bad-102">Postupy: Animace velikosti FrameworkElement</span><span class="sxs-lookup"><span data-stu-id="65bad-102">How to: Animate the Size of a FrameworkElement</span></span>
<span data-ttu-id="65bad-103">Pro animaci velikost <xref:System.Windows.FrameworkElement>, můžete buď animace jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti nebo použijte animovaný <xref:System.Windows.Media.ScaleTransform>.</span><span class="sxs-lookup"><span data-stu-id="65bad-103">To animate the size of a <xref:System.Windows.FrameworkElement>, you can either animate its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties or use an animated <xref:System.Windows.Media.ScaleTransform>.</span></span>  
  
 <span data-ttu-id="65bad-104">V následujícím příkladu animuje velikost dvě tlačítka, pomocí těchto dvou přístupů.</span><span class="sxs-lookup"><span data-stu-id="65bad-104">In the following example animates the size of two buttons using these two approaches.</span></span> <span data-ttu-id="65bad-105">Jedno tlačítko změní velikost animace jeho <xref:System.Windows.FrameworkElement.Width%2A> vlastností a druhou změní velikost animace <xref:System.Windows.Media.ScaleTransform> u jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="65bad-105">One button is resized by animating its <xref:System.Windows.FrameworkElement.Width%2A> property and another is resized by animating a <xref:System.Windows.Media.ScaleTransform> applied to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span> <span data-ttu-id="65bad-106">Každé tlačítko obsahuje část textu.</span><span class="sxs-lookup"><span data-stu-id="65bad-106">Each button contains some text.</span></span> <span data-ttu-id="65bad-107">Na začátku hledaný text zobrazuje stejné v obou tlačítek, ale jako tlačítka se změní velikost, je poškozený, text v druhé tlačítko.</span><span class="sxs-lookup"><span data-stu-id="65bad-107">Initially, the text appears the same in both buttons, but as the buttons are resized, the text in the second button becomes distorted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65bad-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="65bad-108">Example</span></span>  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 <span data-ttu-id="65bad-109">Když prvku transformujete, jsou transformovány celý elementu a jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="65bad-109">When you transform an element, the entire element and its contents are transformed.</span></span> <span data-ttu-id="65bad-110">Při přímo změnit velikost elementu, stejně jako na první tlačítko nejsou v obsahu elementu změnit, pokud jejich velikost a umístění závisí na velikosti jeho nadřazený element.</span><span class="sxs-lookup"><span data-stu-id="65bad-110">When you directly alter the size of an element, as in the case of the first button, the element's contents are not resized unless their size and position depend on the size of their parent element.</span></span>  
  
 <span data-ttu-id="65bad-111">Animace velikost elementu s použitím animovaný transformaci, která jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost poskytuje lepší výkon než animovaný jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> přímo, protože <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost neaktivuje průchodu rozložení.</span><span class="sxs-lookup"><span data-stu-id="65bad-111">Animating the size of an element by applying an animated transform to its <xref:System.Windows.UIElement.RenderTransform%2A> property provides better performance than animated its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> directly, because the <xref:System.Windows.UIElement.RenderTransform%2A> property does not trigger a layout pass.</span></span>  
  
 <span data-ttu-id="65bad-112">Další informace o animaci vlastnosti najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65bad-112">For more information about animating properties, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="65bad-113">Další informace o transformací, najdete v článku [transformuje přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65bad-113">For more information about transforms, see the [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>
