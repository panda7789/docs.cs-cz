---
title: 'Postupy: Přizpůsobení dílků na posuvníku'
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: 3b32bbedb5f654ce75e90a827eb0c4dba1d4d345
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910686"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a>Postupy: Přizpůsobení dílků na posuvníku
Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Slider> ovládací prvek, který má osové značky.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.Primitives.TickBar> Zobrazí, když jste nastavili <xref:System.Windows.Controls.Slider.TickPlacement%2A> vlastnost na hodnotu jinou než <xref:System.Windows.Controls.Primitives.TickPlacement.None>, což je výchozí hodnota.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Slider> s <xref:System.Windows.Controls.Primitives.TickBar> , zobrazí osové značky. <xref:System.Windows.Controls.Slider.TickPlacement%2A> a <xref:System.Windows.Controls.Slider.TickFrequency%2A> vlastnosti definujte umístění značek a intervalu mezi nimi. Při přesunu <xref:System.Windows.Controls.Primitives.Thumb>, popisy zobrazit hodnotu <xref:System.Windows.Controls.Slider>. <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> Vlastnost definuje, kde dojde k popisky. <xref:System.Windows.Controls.Primitives.Thumb> Pohybů plb typu odpovídá místo značek, protože <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> je nastavena na `true`.  
  
 Následující příklad ukazuje způsob použití <xref:System.Windows.Controls.Slider.Ticks%2A> vlastnost vytvořit osové značky společně <xref:System.Windows.Controls.Slider> v nepravidelných intervalech.  
  
 [!code-xaml[Slider#4](~/samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Slider>
- <xref:System.Windows.Controls.Primitives.TickBar>
- <xref:System.Windows.Controls.Slider.TickPlacement%2A>
- [Postupy: Svázání posuvníku hodnotu vlastnosti](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms788716(v=vs.90))
