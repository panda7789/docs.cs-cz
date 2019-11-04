---
title: 'Postupy: Připojení k vyčíslení'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 93f33e497fd7acb81c55f86bf38737d4e7d79bf2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454437"
---
# <a name="how-to-bind-to-an-enumeration"></a>Postupy: Připojení k vyčíslení
Tento příklad ukazuje, jak vytvořit vazbu na výčet pomocí vazby na metodu GetValues výčtu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Controls.ListBox> zobrazuje seznam <xref:System.Windows.HorizontalAlignment> hodnot výčtu prostřednictvím datové vazby. <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Button> jsou vázány tak, že můžete změnit hodnotu vlastnosti <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.Controls.Button> tím, že vyberete hodnotu v <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření vazby k metodě](how-to-bind-to-a-method.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
