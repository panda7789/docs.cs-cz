---
title: 'Postupy: Přizpůsobení dílků na posuvníku'
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: 3b32bbedb5f654ce75e90a827eb0c4dba1d4d345
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164239"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="76672-102">Postupy: Přizpůsobení dílků na posuvníku</span><span class="sxs-lookup"><span data-stu-id="76672-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="76672-103">Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Slider> ovládací prvek, který má osové značky.</span><span class="sxs-lookup"><span data-stu-id="76672-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76672-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="76672-104">Example</span></span>  
 <span data-ttu-id="76672-105"><xref:System.Windows.Controls.Primitives.TickBar> Zobrazí, když jste nastavili <xref:System.Windows.Controls.Slider.TickPlacement%2A> vlastnost na hodnotu jinou než <xref:System.Windows.Controls.Primitives.TickPlacement.None>, což je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="76672-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="76672-106">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Slider> s <xref:System.Windows.Controls.Primitives.TickBar> , zobrazí osové značky.</span><span class="sxs-lookup"><span data-stu-id="76672-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="76672-107"><xref:System.Windows.Controls.Slider.TickPlacement%2A> a <xref:System.Windows.Controls.Slider.TickFrequency%2A> vlastnosti definujte umístění značek a intervalu mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="76672-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="76672-108">Při přesunu <xref:System.Windows.Controls.Primitives.Thumb>, popisy zobrazit hodnotu <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="76672-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="76672-109"><xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> Vlastnost definuje, kde dojde k popisky.</span><span class="sxs-lookup"><span data-stu-id="76672-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="76672-110"><xref:System.Windows.Controls.Primitives.Thumb> Pohybů plb typu odpovídá místo značek, protože <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="76672-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="76672-111">Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.Slider.Ticks%2A> vlastnost vytvořit osové značky společně <xref:System.Windows.Controls.Slider> v nepravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="76672-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](~/samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="76672-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76672-112">See also</span></span>

- <xref:System.Windows.Controls.Slider>
- <xref:System.Windows.Controls.Primitives.TickBar>
- <xref:System.Windows.Controls.Slider.TickPlacement%2A>
- [<span data-ttu-id="76672-113">Postupy: Svázání posuvníku hodnotu vlastnosti</span><span class="sxs-lookup"><span data-stu-id="76672-113">How to: Bind a Slider to a Property Value</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms788716(v=vs.90))
