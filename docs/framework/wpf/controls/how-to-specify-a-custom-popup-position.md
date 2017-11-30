---
title: "Postupy: Určení vlastního překryvného umístění"
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
helpviewer_keywords: Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ab9baca1103adf8de96204bdb1b3353a5456b94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-a-custom-popup-position"></a>Postupy: Určení vlastního překryvného umístění
Tento příklad ukazuje, jak chcete určit vlastní umístění pro <xref:System.Windows.Controls.Primitives.Popup> řídit, kdy <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>.  
  
## <a name="example"></a>Příklad  
 Když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>, <xref:System.Windows.Controls.Primitives.Popup> volání definované instanci <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegovat. Tento delegát vrací sadu možné body, které jsou relativní vzhledem k levém horním rohu cílovou oblast a v levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>. <xref:System.Windows.Controls.Primitives.Popup> v místě, které poskytuje nejlepší viditelnost dojde k umístění.  
  
 Následující příklad ukazuje, jak definovat pozice <xref:System.Windows.Controls.Primitives.Popup> nastavením <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnost <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Také ukazuje, jak vytvořit a přiřadit <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegáta, aby bylo možné umístit <xref:System.Windows.Controls.Primitives.Popup>.  Vrátí delegáta zpětného volání, dva <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> objekty.  Pokud <xref:System.Windows.Controls.Primitives.Popup> je skrytý na základě okraji obrazovky na první pozici, <xref:System.Windows.Controls.Primitives.Popup> je umístěn na druhé pozici.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Kompletní příklad, najdete v části [místní umístění ukázka](http://go.microsoft.com/fwlink/?LinkID=160032).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [Přehled místní nabídka](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
