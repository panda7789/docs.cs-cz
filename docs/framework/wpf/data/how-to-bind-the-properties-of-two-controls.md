---
title: 'Postupy: Svázání vlastností dvou ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: f3355969d0f12f0f3ed9b49bdb7efa6913c5e4c4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372097"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Postupy: Svázání vlastností dvou ovládacích prvků
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
