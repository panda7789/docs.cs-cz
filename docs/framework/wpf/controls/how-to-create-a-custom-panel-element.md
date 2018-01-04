---
title: "Postupy: Vytvoření vlastního elementu panelu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eacc5435e259c20c25b64d6e82c33d07338602a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-panel-element"></a>Postupy: Vytvoření vlastního elementu panelu
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak lze přepsat výchozí chování rozložení <xref:System.Windows.Controls.Panel> elementu a vytvořit vlastní rozložení elementy, které jsou odvozeny od <xref:System.Windows.Controls.Panel>.  
  
 V příkladu definuje jednoduché vlastní <xref:System.Windows.Controls.Panel> prvek s názvem `PlotPanel`, který umisťuje podřízených elementů podle dvě pevně souřadnic x a y-. V tomto příkladu `x` a `y` jsou nastaveny na `50`; proto jsou všechny podřízené prvky umístěny v tomto umístění na x a y osy.  
  
 K implementaci vlastních <xref:System.Windows.Controls.Panel> chování, v příkladu se používá <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody. Každá metoda vrátí <xref:System.Windows.Size> data, která je nutné umístit a vykreslit podřízené elementy.  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Panel>  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Vytvořit vlastní vzorek panely obsah zabalení](http://go.microsoft.com/fwlink/?LinkID=159979)
