---
title: "Postupy: Určení zdroje připojení"
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
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23a4c180eb62dd152f1ed24c01b8103ccf1ec562
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-binding-source"></a>Postupy: Určení zdroje připojení
V datové vazbě zdrojového objektu vazby odkazuje na objekt, který je získat data z. Toto téma popisuje různé způsoby zadávání zdroji vazby.  
  
## <a name="example"></a>Příklad  
 Pokud vytváříte několik vlastností vazbu na běžné zdroj, kterou chcete použít `DataContext` vlastnosti, která nabízí pohodlný způsob, jak vytvořit obor, ve kterém všechny vlastnosti vázané na data dědit společný zdroj.  
  
 V následujícím příkladu je vytvořeno kontextu dat v kořenovém elementu aplikace. To umožňuje všechny podřízené elementy pro tento kontext dat dědění. Data pro vazbu pochází od třídy vlastních dat `NetIncome`, odkazuje přímo prostřednictvím mapování a zadané prostředků klíč `incomeDataSource`.  
  
 [!code-xaml[DirectionalBinding#DataContext1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 Následující příklad zobrazuje definici `NetIncome` třídy.  
  
 [!code-csharp[DirectionalBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  Výše uvedený příklad inicializuje objekt v značek a používá jako prostředek. Pokud chcete vytvořit vazbu na objekt, který má již byly vytvořeny v kódu, je nutné nastavit `DataContext` vlastnost prostřednictvím kódu programu. Příklad, naleznete v části [zkontrolujte Data k dispozici pro vazbu v jazyce XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).  
  
 Případně pokud chcete určit zdroj na jednotlivé vazby explicitně, máte následující možnosti. Tyto mají přednost před zděděné data kontextu.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Pomocí této vlastnosti lze nastavit zdroj instance objektu. Pokud nepotřebujete funkce vytvoření oboru ve vlastnosti, které několik dědění stejné kontextu dat, můžete použít <xref:System.Windows.Data.Binding.Source%2A> vlastnost místo `DataContext` vlastnost. Další informace naleznete v tématu <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|To je užitečné, pokud chcete určit zdroj relativně k, kde je váš cíl vazby. Některé běžné scénáře, kde může používat tato vlastnost je, když chcete vytvořit vazbu jednu vlastnost vaší elementu na jinou vlastnost stejného elementu nebo pokud definování vazbu v styl nebo šabloně. Další informace naleznete v tématu <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Zadáte řetězec, který reprezentuje element, který chcete vytvořit vazbu na. To je užitečné, pokud chcete vytvořit vazbu na vlastnost jiný element ve vaší aplikaci. Například, pokud chcete použít <xref:System.Windows.Controls.Slider> řídit výšku jiného ovládacího prvku ve vaší aplikaci, nebo pokud chcete vytvořit vazbu <xref:System.Windows.Controls.ContentControl.Content%2A> ovládacího prvku na <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> vlastnost vaší <xref:System.Windows.Controls.ListBox> ovládacího prvku. Další informace naleznete v tématu <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>  
 [Dědičnost hodnoty vlastnosti](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Přehled deklarací vazeb](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
