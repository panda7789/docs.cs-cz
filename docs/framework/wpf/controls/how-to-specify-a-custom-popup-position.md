---
title: 'Postupy: Určení vlastního překryvného umístění'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: 8714cfa4f7e5bb0ca157ee9d551392571303f60e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551736"
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
 [Přehled prvku Popup](../../../../docs/framework/wpf/controls/popup-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)
