---
title: "Postupy: Svázání vlastností dvou ovládacích prvků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff3da19d33e747ec514de9cd24fa08ccd6ab13bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Postupy: Svázání vlastností dvou ovládacích prvků
Tento příklad ukazuje, jak pro vazbu s jinou pomocí vlastnost jeden vytvořenou instanci ovládacího prvku <xref:System.Windows.Data.Binding.ElementName%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost <xref:System.Windows.Controls.Canvas> k <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost <xref:System.Windows.Controls.ComboBox>:  
  
 [!code-xaml[BindDptoDp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 Při tomto příkladu vypadá takto:  
  
 ![Na plátno se zeleným pozadím](../../../../docs/framework/wpf/data/media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")  
  
 **Poznámka:** vlastnost target vazba (v tomto příkladu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost) musí být vlastnost závislosti. Další informace najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Zadejte zdroj vazby](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)  
 [Postupy: témata](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
