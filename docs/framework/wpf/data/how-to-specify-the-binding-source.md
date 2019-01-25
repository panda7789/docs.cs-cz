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
ms.openlocfilehash: f2e3fa3352da85c7da394a582cfcd058fe3fadf4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577123"
---
# <a name="how-to-specify-the-binding-source"></a>Postupy: Určení zdroje připojení
V datové vazbě objekt zdroj vazby odkazuje na objekt, který je získat data z. Toto téma popisuje různé způsoby určení zdroje připojení.  
  
## <a name="example"></a>Příklad  
 Pokud vytváříte několik vlastností vazbu na společný zdroj, kterou chcete použít `DataContext` vlastnost, která poskytuje pohodlný způsob, jak vytvořit obor, ve kterém zdědí všechny vlastnosti vázané na data společný zdroj.  
  
 V následujícím příkladu se naváže kontext dat v kořenovém elementu aplikace. To umožňuje všechny podřízené prvky dědit daného datového kontextu. Data pro vazbu pocházejí z vlastní datové třídy `NetIncome`, odkazuje přímo prostřednictvím mapování a daný klíč prostředku `incomeDataSource`.  
  
 [!code-xaml[DirectionalBinding#DataContext1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 Následující příklad ukazuje definici `NetIncome` třídy.  
  
 [!code-csharp[DirectionalBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  Výše uvedený příklad vytvoří instanci objektu ve značkách a použije ho jako prostředek. Pokud chcete vytvořit vazbu na objekt, který se už vytvářejí instance v kódu, je nutné nastavit `DataContext` vlastnost prostřednictvím kódu programu. Příklad najdete v tématu [zkontrolujte Data k dispozici pro vazbu v XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).  
  
 Případně pokud chcete zadat zdroj na jednotlivé vazby explicitně, máte následující možnosti. Tyto přednost zděděné datového kontextu.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Pomocí této vlastnosti se nastavit zdroj na instanci objektu. Pokud nepotřebujete funkce pro vytváření oboru v několika vlastnosti, které dědí stejný datový kontext, můžete použít <xref:System.Windows.Data.Binding.Source%2A> vlastnost místo `DataContext` vlastnost. Další informace naleznete v tématu <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|To je užitečné, pokud chcete zadat zdroj relativně vzhledem k, ve kterém je váš cíl vazby. Některé běžné scénáře, ve kterém může pomocí této vlastnosti je, když chcete svázat vlastnost jednoho prvku na jinou vlastnost stejného elementu nebo pokud definujete vazby ve stylu nebo šablony. Další informace naleznete v tématu <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Při zadání řetězce, který reprezentuje element, který chcete svázat. To je užitečné, pokud chcete vytvořit vazbu na vlastnost jiný element ve vaší aplikaci. Například, pokud chcete použít <xref:System.Windows.Controls.Slider> řídit výšku jiný ovládací prvek ve vaší aplikaci, nebo pokud chcete vytvořit vazbu <xref:System.Windows.Controls.ContentControl.Content%2A> ovládacího prvku na <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> vlastnost vaše <xref:System.Windows.Controls.ListBox> ovládacího prvku. Další informace naleznete v tématu <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [Dědičnost hodnoty vlastnosti](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Přehled deklarací vazeb](../../../../docs/framework/wpf/data/binding-declarations-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
