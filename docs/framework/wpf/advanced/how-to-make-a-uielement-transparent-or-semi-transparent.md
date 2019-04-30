---
title: 'Postupy: Vytvoření průhledného nebo poloprůhledného elementu UIElement'
ms.date: 03/30/2017
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
ms.openlocfilehash: 1de9a7e11fee241ecb71242e9808e77b7e5e63b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942867"
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a>Postupy: Vytvoření průhledného nebo poloprůhledného elementu UIElement
Tento příklad ukazuje, jak vytvořit <xref:System.Windows.UIElement> průhledného nebo poloprůhledného. Chcete-li prvek průhledného nebo poloprůhledného, nastavíte jeho <xref:System.Windows.UIElement.Opacity%2A> vlastnost. Hodnota `0.0` nastaví prvek zcela transparentní, při hodnotu `1.0` nastaví prvek stane zcela neprůhledný. Hodnota `0.5` nastaví prvek 50 % neprůhledných a tak dále. Elementu <xref:System.Windows.UIElement.Opacity%2A> je nastavena na `1.0` ve výchozím nastavení.  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví <xref:System.Windows.UIElement.Opacity%2A> tlačítka na `0.25`, provádění a její obsah (v tomto případě text tlačítka) 25 % neprůhledné.  
  
 [!code-xaml[brushsamples_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 Pokud obsah elementu má svoje vlastní <xref:System.Windows.UIElement.Opacity%2A> nastavení tyto hodnoty jsou vynásobené proti obsahující prvky <xref:System.Windows.UIElement.Opacity%2A>.  
  
 Následující příklad nastaví tlačítka <xref:System.Windows.UIElement.Opacity%2A> k `0.25`a <xref:System.Windows.UIElement.Opacity%2A> ze <xref:System.Windows.Controls.Image> ovládací prvek obsažený v tlačítka s `0.5`. Obrázek v důsledku toho se zobrazí 12,5 % neprůhledné: 0.25 * 0.5 = 0.125.  
  
 [!code-xaml[brushsamples_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 Dalším způsobem, jak řídit krytí elementu je nastavit neprůhlednost <xref:System.Windows.Media.Brush> , který vykreslí element. Tento přístup umožňuje selektivně alter krytí částí elementu a poskytuje výkonnostních výhod oproti použití prvku <xref:System.Windows.UIElement.Opacity%2A> vlastnost. Následující příklad nastaví <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush> používá k malování tlačítka <xref:System.Windows.Controls.Control.Background%2A> je nastavena na `0.25`. V důsledku toho štětec pozadí je neprůhledný 25 %, ale jeho obsah (text tlačítka) zůstávají neprůhledné 100 %.  
  
 [!code-xaml[brushsamples_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 Můžete také řídit krytí jednotlivé barvy v rámci štětce. Další informace o barvy a štětce naleznete v tématu [Malování plnými barvami a přechody přehled](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Příklad ukazuje, jak animace krytí elementu, naleznete v tématu [animace krytí elementu nebo štětce](../graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).
