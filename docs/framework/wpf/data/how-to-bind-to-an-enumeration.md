---
title: 'Postupy: Vytvoření vazby k výčtu'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 5026261366d6abde82790f05780d8ba2c29c4a49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62021008"
---
# <a name="how-to-bind-to-an-enumeration"></a>Postupy: Vytvoření vazby k výčtu
Tento příklad ukazuje, jak připojení k vyčíslení navázáním metoda GetValues výčtu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Controls.ListBox> zobrazí seznam <xref:System.Windows.HorizontalAlignment> hodnot výčtu prostřednictvím datové vazby. <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Button> vázány tak, že můžete změnit <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnotu vlastnosti <xref:System.Windows.Controls.Button> tak, že vyberete hodnotu v <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření vazby k metodě](how-to-bind-to-a-method.md)
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
