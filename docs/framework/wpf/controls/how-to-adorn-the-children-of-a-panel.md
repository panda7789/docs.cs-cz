---
title: "Postupy: Doplnění podřízených položek panelu"
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
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 70a2c1e7735a6df31a44fce7eb9bb2371acc208b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>Postupy: Doplnění podřízených položek panelu
Tento příklad ukazuje, jak programově vytvořit vazbu adorner podřízené objekty daného zadané <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Příklad  
 Při vytváření vazby adorner podřízených objektů daného <xref:System.Windows.Controls.Panel>, postupujte takto:  
  
1.  Deklarovat nové <xref:System.Windows.Documents.AdornerLayer> objekt a volání `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> metody k vyhledání vrstvu adorner pro element, jehož podřízené objekty mají být ozdobené.  
  
2.  Zobrazení výčtu prostřednictvím podřízené objekty daného nadřazeného elementu a volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metoda pro vazbu adorner každý podřízený element.  
  
 Následující příklad vytvoří vazbu SimpleCircleAdorner (viz výše) u podřízených objektů daného <xref:System.Windows.Controls.StackPanel> s názvem *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  Pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] vytvořit vazbu adorner jiný element se aktuálně nepodporuje.  
  
## <a name="see-also"></a>Viz také  
 [Přehled doplňků pro úpravy](../../../../docs/framework/wpf/controls/adorners-overview.md)
