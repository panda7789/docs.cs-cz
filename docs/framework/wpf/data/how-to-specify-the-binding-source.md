---
title: 'Postupy: Určení zdroje připojení'
description: Naučte se, jak určit zdroj vazby v tomto příkladu v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 02f27da007ebe8c5985f91b83adfba7d3d00219a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621662"
---
# <a name="how-to-specify-the-binding-source"></a>Postupy: Určení zdroje připojení
V datové vazbě odkazuje zdrojový objekt vazby na objekt, ze kterého získáváte data. Toto téma popisuje různé způsoby určení zdroje vazby.  
  
## <a name="example"></a>Příklad  
 Pokud vytváříte vazbu několika vlastností na společný zdroj, budete chtít použít `DataContext` vlastnost, která poskytuje pohodlný způsob, jak vytvořit obor, ve kterém všechny vlastnosti vázané na data dědí společný zdroj.  
  
 V následujícím příkladu je datový kontext vytvořen v kořenovém elementu aplikace. To umožňuje všem podřízeným elementům dědit tento datový kontext. Data pro vazbu pocházejí z vlastní třídy dat, `NetIncome` na kterou odkazuje přímo prostřednictvím mapování a podle klíče prostředku `incomeDataSource` .  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 Následující příklad ukazuje definici `NetIncome` třídy.  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> Výše uvedený příklad vytvoří instanci objektu v kódu a použije ho jako prostředek. Pokud chcete vytvořit propojení s objektem, který již byl vytvořen v kódu, je nutné nastavit `DataContext` vlastnost programově. Příklad naleznete [v tématu zpřístupnění dat pro vazbu v jazyce XAML](how-to-make-data-available-for-binding-in-xaml.md).  
  
 Případně, pokud chcete zadat zdroj pro jednotlivé vazby explicitně, máte následující možnosti. Mají přednost před zděděným kontextem dat.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Tato vlastnost slouží k nastavení zdroje na instanci objektu. Pokud nepotřebujete, aby bylo možné vytvořit obor, ve kterém několik vlastností dědí stejný kontext dat, můžete <xref:System.Windows.Data.Binding.Source%2A> místo vlastnosti použít vlastnost `DataContext` . Další informace naleznete v tématu <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|To je užitečné, pokud chcete určit zdroj relativní k umístění vazby na cíl. Některé běžné scénáře, kdy můžete použít tuto vlastnost, je, když chcete svázat jednu vlastnost elementu s jinou vlastností stejného prvku nebo pokud definujete vazbu ve stylu nebo šabloně. Další informace naleznete v tématu <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Zadejte řetězec, který představuje prvek, ke kterému se má vytvořit vazba. To je užitečné, pokud chcete vytvořit vazby na vlastnost jiného prvku v aplikaci. Například pokud chcete použít <xref:System.Windows.Controls.Slider> k řízení výšky jiného ovládacího prvku v aplikaci, nebo pokud chcete vytvořit svázání <xref:System.Windows.Controls.ContentControl.Content%2A> ovládacího prvku s <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> vlastností <xref:System.Windows.Controls.ListBox> ovládacího prvku. Další informace naleznete v tématu <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [Dědičnost hodnoty vlastnosti](../advanced/property-value-inheritance.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled deklarací připojení](binding-declarations-overview.md)
- [– postupy](data-binding-how-to-topics.md)
