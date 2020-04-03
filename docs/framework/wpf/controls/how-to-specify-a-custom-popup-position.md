---
title: 'Postupy: Určení vlastního překryvného umístění'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Popup control [WPF], specifying custom position
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
ms.openlocfilehash: b48dedc044b418062642af5c5bb40afab78a3c97
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635754"
---
# <a name="how-to-specify-a-custom-popup-position"></a>Postupy: Určení vlastního překryvného umístění
Tento příklad ukazuje, jak určit <xref:System.Windows.Controls.Primitives.Popup> vlastní pozici <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> ovládacího <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>prvku, když je vlastnost nastavena na .  
  
## <a name="example"></a>Příklad  
 Pokud <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je vlastnost <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>nastavena <xref:System.Windows.Controls.Primitives.Popup> na , volá <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> definovanou instanci delegáta. Tento delegát vrátí sadu možných bodů, které jsou relativní k levému hornímu rohu <xref:System.Windows.Controls.Primitives.Popup>cílové oblasti a levému hornímu rohu . Umístění <xref:System.Windows.Controls.Primitives.Popup> dochází v bodě, který poskytuje nejlepší viditelnost.  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.Primitives.Popup> pozici a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> nastavením vlastnosti na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Také ukazuje, jak vytvořit <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> a přiřadit delegáta, aby bylo možné umístit <xref:System.Windows.Controls.Primitives.Popup>.  Delegát zpětného volání <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> vrátí dva objekty.  Pokud <xref:System.Windows.Controls.Primitives.Popup> je skryt okrajem obrazovky v <xref:System.Windows.Controls.Primitives.Popup> první poloze, je umístěn na druhé pozici.  
  
 [!code-xaml[PopupCustomPlacement#CustomPlacement](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 Kompletní ukázku naleznete v tématu [Ukázka umístění automaticky otevíraném zobrazení](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.Primitives.Popup>
- [Místní okno – přehled](popup-overview.md)
- [Články s postupy](popup-how-to-topics.md)
