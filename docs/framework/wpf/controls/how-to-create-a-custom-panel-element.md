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
ms.openlocfilehash: 31edc75114c5dad613e5b65e7d8b051e2c3713af
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799143"
---
# <a name="how-to-create-a-custom-panel-element"></a>Postupy: Vytvoření vlastního elementu panelu
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak přepsat výchozí chování rozložení prvku <xref:System.Windows.Controls.Panel> a vytvořit vlastní prvky rozložení, které jsou odvozeny z <xref:System.Windows.Controls.Panel>.  
  
 Příklad definuje jednoduchý prvek vlastní <xref:System.Windows.Controls.Panel> s názvem `PlotPanel`, který umístí podřízené prvky podle dvou pevně zakódovaných souřadnic x-a y. V tomto příkladu jsou `x` a `y` obě nastaveny na `50`; Proto jsou všechny podřízené prvky umístěny v tomto umístění na osách x a y.  
  
 K implementaci vlastního chování <xref:System.Windows.Controls.Panel> používá tento příklad metody <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>. Každá metoda vrátí <xref:System.Windows.Size> data, která jsou nutná k umístění a vykreslení podřízených prvků.  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Panel>
- [Přehled panelu](panels-overview.md)
