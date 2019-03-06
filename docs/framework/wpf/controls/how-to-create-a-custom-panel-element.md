---
title: 'Postupy: Vytvoření vlastního elementu panelu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 2e778adfb79a64c8f248992aee92de9471906129
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368698"
---
# <a name="how-to-create-a-custom-panel-element"></a>Postupy: Vytvoření vlastního elementu panelu
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak přepsat výchozí chování rozložení <xref:System.Windows.Controls.Panel> elementu a vytvářet vlastní rozložení prvků, které jsou odvozeny z <xref:System.Windows.Controls.Panel>.  
  
 V příkladu je definována jednoduchý vlastní <xref:System.Windows.Controls.Panel> prvek s názvem `PlotPanel`, které se umístí podřízené prvky podle dvě pevně zakódované souřadnic x a y-. V tomto příkladu `x` a `y` jsou nastaveny na `50`; proto všechny podřízené prvky jsou umístěny na tomto místě na x a y osy.  
  
 K implementaci vlastní <xref:System.Windows.Controls.Panel> chování, v příkladu se používá <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody. Každá metoda vrátí <xref:System.Windows.Size> data, která je potřeba umístit a vykreslování podřízených elementů.  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.Panel>
- [Přehled panelu](panels-overview.md)
- [Vytvoření vlastního panelu ukázky zabalení obsahu](https://go.microsoft.com/fwlink/?LinkID=159979)
