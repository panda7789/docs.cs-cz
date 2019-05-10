---
title: 'Postupy: Vytvoření vazby vlastností dvou ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 332e8e0dfa30ff7aff27c95652f07446baf6511a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754045"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Postupy: Vytvoření vazby vlastností dvou ovládacích prvků
Tento příklad ukazuje, jak vytvořit vazbu vlastnosti jedné instance ovládacího prvku, který z jiného pomocí <xref:System.Windows.Data.Binding.ElementName%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost <xref:System.Windows.Controls.Canvas> k <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> Vlastnost <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Při vykreslení v tomto příkladu bude vypadat nějak takto:  
  
![Snímek obrazovky zobrazující pole se seznamem zaškrtnutým políčkem hodnotou zelené a zelený čtvereček.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> Vlastnost target vazby (v tomto příkladu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost) musí být vlastnost závislosti. Další informace najdete v tématu [přehled datových vazeb](data-binding-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Určení zdroje vazby](how-to-specify-the-binding-source.md)
- [Témata s postupy](data-binding-how-to-topics.md)
