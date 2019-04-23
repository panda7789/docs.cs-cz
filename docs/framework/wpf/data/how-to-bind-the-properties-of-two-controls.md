---
title: 'Postupy: Vytvoření vazby vlastností dvou ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 0dd7b817b632758cfca8b5c45d88e333510485f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222058"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Postupy: Vytvoření vazby vlastností dvou ovládacích prvků
Tento příklad ukazuje, jak vytvořit vazbu vlastnosti jedné instance ovládacího prvku, který z jiného pomocí <xref:System.Windows.Data.Binding.ElementName%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost <xref:System.Windows.Controls.Canvas> k <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> Vlastnost <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Při vykreslení v tomto příkladu bude vypadat nějak takto:  
  
 ![Na plátně se zeleným pozadím](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")  
  
 **Poznámka:** cílovou vlastnost vazby (v tomto příkladu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost) musí být vlastnost závislosti. Další informace najdete v tématu [přehled datových vazeb](data-binding-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Určení zdroje vazby](how-to-specify-the-binding-source.md)
- [Témata s postupy](data-binding-how-to-topics.md)
