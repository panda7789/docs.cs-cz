---
title: "Postupy: Přizpůsobení dílků na posuvníku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d21d2950ed228bf588a202419c222ee86dde5b0d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="04b57-102">Postupy: Přizpůsobení dílků na posuvníku</span><span class="sxs-lookup"><span data-stu-id="04b57-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="04b57-103">Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Slider> ovládací prvek, který má osové značky.</span><span class="sxs-lookup"><span data-stu-id="04b57-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04b57-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="04b57-104">Example</span></span>  
 <span data-ttu-id="04b57-105"><xref:System.Windows.Controls.Primitives.TickBar> Zobrazí, když nastavíte <xref:System.Windows.Controls.Slider.TickPlacement%2A> vlastnost na hodnotu jinou než <xref:System.Windows.Controls.Primitives.TickPlacement.None>, což je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="04b57-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="04b57-106">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Slider> s <xref:System.Windows.Controls.Primitives.TickBar> , zobrazí osové značky.</span><span class="sxs-lookup"><span data-stu-id="04b57-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="04b57-107"><xref:System.Windows.Controls.Slider.TickPlacement%2A> a <xref:System.Windows.Controls.Slider.TickFrequency%2A> vlastnosti definovat umístění značek a interval mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="04b57-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="04b57-108">Když přesunete <xref:System.Windows.Controls.Primitives.Thumb>, popisy tlačítek Zobrazit hodnotu <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="04b57-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="04b57-109"><xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> Vlastnost definuje, kde se popisky tlačítek probíhat.</span><span class="sxs-lookup"><span data-stu-id="04b57-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="04b57-110"><xref:System.Windows.Controls.Primitives.Thumb> Pohybů odpovídají umístění značek, protože <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> je nastaven na `true`.</span><span class="sxs-lookup"><span data-stu-id="04b57-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="04b57-111">Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.Slider.Ticks%2A> vlastnost vytvořit osové značky společně <xref:System.Windows.Controls.Slider> nepravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="04b57-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="04b57-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="04b57-112">See Also</span></span>  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [<span data-ttu-id="04b57-113">Postupy: témata posuvníku</span><span class="sxs-lookup"><span data-stu-id="04b57-113">Slider How-to Topics</span></span>](http://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
