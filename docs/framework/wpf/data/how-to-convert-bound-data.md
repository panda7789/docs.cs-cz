---
title: "Postupy: Převod připojených dat"
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
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f4bcde15940e76e1d022658e32ff6ef8676e45e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-convert-bound-data"></a>Postupy: Převod připojených dat
Tento příklad ukazuje, jak se má použít převod na data, která se používá v vazby.  
  
 Převést data během vazby, je nutné vytvořit třídu, která implementuje <xref:System.Windows.Data.IValueConverter> rozhraní, což zahrnuje <xref:System.Windows.Data.IValueConverter.Convert%2A> a <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci převaděč datum, který převádí hodnoty date předaná tak, aby se zobrazí pouze rok, měsíc a den. Při implementaci <xref:System.Windows.Data.IValueConverter> rozhraní, je vhodné pro uspořádání implementace s <xref:System.Windows.Data.ValueConversionAttribute> atribut a informuje vývoj nástrojů pro datové typy zahrnutých v převodu, jako v následujícím příkladu:  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Po vytvoření převaděč, můžete jej přidat jako prostředek v vaší [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru. V následujícím příkladu *src* se mapuje na obor názvů, ve kterém *DateConverter* je definována.  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Nakonec můžete převaděč ve vašem vazbu pomocí následující syntaxe. V následujícím příkladu, obsah textu <xref:System.Windows.Controls.TextBlock> je vázán k *počátečním*, což je vlastnost externího zdroje dat.  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Styl prostředky, kterou se odkazuje v předchozím příkladu jsou definovány v oddílu prostředků není znázorněné v tomto tématu.  
  
## <a name="see-also"></a>Viz také  
 [Implementace ověření vazby](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
