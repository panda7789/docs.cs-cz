---
title: "Postupy: Vytvoření průhledného nebo poloprůhledného elementu UIElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25245319c02ae376410d71afb7a1e56eda259e99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a>Postupy: Vytvoření průhledného nebo poloprůhledného elementu UIElement
Tento příklad ukazuje, jak provádět <xref:System.Windows.UIElement> průhledných nebo poloprůhlednost. K nastavení vzhledu elementu průhledných nebo poloprůhledné, nastavte jeho <xref:System.Windows.UIElement.Opacity%2A> vlastnost. Hodnota `0.0` nastaví prvek zcela transparentní, při hodnotu `1.0` bude zcela neprůhledná elementu. Hodnota `0.5` nastaví prvek 50 % neprůhledných a tak dále. Elementu <xref:System.Windows.UIElement.Opacity%2A> je nastaven na `1.0` ve výchozím nastavení.  
  
## <a name="example"></a>Příklad  
 Následující příklad nastavuje <xref:System.Windows.UIElement.Opacity%2A> tlačítka na `0.25`, nastavení jako ho a její obsah (v tomto případě na tlačítko text) 25 % neprůhledné.  
  
 [!code-xaml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 Pokud obsah elementu mají svůj vlastní <xref:System.Windows.UIElement.Opacity%2A> nastavení, tyto hodnoty se násobí proti obsahující elementy <xref:System.Windows.UIElement.Opacity%2A>.  
  
 Následující příklad ilustruje tlačítko <xref:System.Windows.UIElement.Opacity%2A> k `0.25`a <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Image> řízení, které jsou součástí na tlačítko s `0.5`. V důsledku toho obrázek vypadá jako neprůhledností 12,5 %: 0,25 * 0,5 = 0,125.  
  
 [!code-xaml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 Jiný způsob, jak řídit krytí elementu je nastavit krytí <xref:System.Windows.Media.Brush> který vybarví elementu. Tento přístup umožňuje selektivně alter krytí části elementu a poskytuje výkonnostních výhod oproti použití elementu <xref:System.Windows.UIElement.Opacity%2A> vlastnost. Následující příklad nastavuje <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush> použita k vyplnění na tlačítko <xref:System.Windows.Controls.Control.Background%2A> je nastaven na `0.25`. V důsledku toho je nástroj štětec pozadí 25 % neprůhledné, ale její obsah (text tlačítka) zůstanou neprůhledností 100 %.  
  
 [!code-xaml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 Může také řídit krytí jednotlivé barvy v rámci štětce. Další informace o barvy a štětce najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Příkladem zobrazujícím postup animace elementu krytí, najdete v části [animace krytí Element nebo štětce](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).
