---
title: 'Postupy: Určení zdroje připojení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 4fde66b22bac6b4a2cfeb4eceb50027daadee387
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454364"
---
# <a name="how-to-specify-the-binding-source"></a>Postupy: Určení zdroje připojení
V datové vazbě odkazuje zdrojový objekt vazby na objekt, ze kterého získáváte data. Toto téma popisuje různé způsoby určení zdroje vazby.  
  
## <a name="example"></a>Příklad  
 Pokud vytváříte vazbu několika vlastností na společný zdroj, budete chtít použít vlastnost `DataContext`, která poskytuje pohodlný způsob, jak vytvořit obor, ve kterém všechny vlastnosti vázané na data dědí společný zdroj.  
  
 V následujícím příkladu je datový kontext vytvořen v kořenovém elementu aplikace. To umožňuje všem podřízeným elementům dědit tento datový kontext. Data pro vazbu pocházejí z vlastní třídy dat, `NetIncome`, na kterou odkazuje přímo prostřednictvím mapování a s použitím klíče prostředku `incomeDataSource`.  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 Následující příklad ukazuje definici třídy `NetIncome`.  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> Výše uvedený příklad vytvoří instanci objektu v kódu a použije ho jako prostředek. Pokud chcete vytvořit propojení s objektem, který již byl vytvořen v kódu, je nutné nastavit vlastnost `DataContext` programově. Příklad naleznete [v tématu zpřístupnění dat pro vazbu v jazyce XAML](how-to-make-data-available-for-binding-in-xaml.md).  
  
 Případně, pokud chcete zadat zdroj pro jednotlivé vazby explicitně, máte následující možnosti. Mají přednost před zděděným kontextem dat.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Tato vlastnost slouží k nastavení zdroje na instanci objektu. Pokud nepotřebujete, aby bylo možné vytvořit obor, ve kterém několik vlastností dědí stejný kontext dat, můžete místo vlastnosti `DataContext` použít vlastnost <xref:System.Windows.Data.Binding.Source%2A>. Další informace najdete v tématu <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|To je užitečné, pokud chcete určit zdroj relativní k umístění vazby na cíl. Některé běžné scénáře, kdy můžete použít tuto vlastnost, je, když chcete svázat jednu vlastnost elementu s jinou vlastností stejného prvku nebo pokud definujete vazbu ve stylu nebo šabloně. Další informace najdete v tématu <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Zadejte řetězec, který představuje prvek, ke kterému se má vytvořit vazba. To je užitečné, pokud chcete vytvořit vazby na vlastnost jiného prvku v aplikaci. Například pokud chcete použít <xref:System.Windows.Controls.Slider> k řízení výšky jiného ovládacího prvku v aplikaci, nebo pokud chcete navazovat <xref:System.Windows.Controls.ContentControl.Content%2A> ovládacího prvku na vlastnost <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> ovládacího prvku <xref:System.Windows.Controls.ListBox>. Další informace najdete v tématu <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [Dědičnost hodnoty vlastnosti](../advanced/property-value-inheritance.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled deklarací vazeb](binding-declarations-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
