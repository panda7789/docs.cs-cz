---
title: 'Postupy: Převod připojených dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 5069b6d6b7ded52011ec4c65ca2c47e41bba2ece
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705716"
---
# <a name="how-to-convert-bound-data"></a>Postupy: Převod připojených dat
Tento příklad ukazuje, jak použít převod na data, která se používá ve vazbách.  
  
 K převodu dat při vytváření vazby, musíte vytvořit třídu, která implementuje <xref:System.Windows.Data.IValueConverter> rozhraní, která zahrnuje <xref:System.Windows.Data.IValueConverter.Convert%2A> a <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci konvertor data, která převede datum hodnoty předané v tak, aby se zobrazí pouze roku, měsíce a dne. Při implementaci <xref:System.Windows.Data.IValueConverter> rozhraní, je vhodné k vyplnění implementaci <xref:System.Windows.Data.ValueConversionAttribute> atribut skutečnost vývoj nástrojů typy dat zapojených do převodu, jako v následujícím příkladu:  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Jakmile vytvoříte konvertor, můžete ji přidat jako prostředek v vaše [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru. V následujícím příkladu *src* mapuje na obor názvů, ve kterém *DateConverter* je definována.  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Nakonec můžete použít převaděč ve vaší vazbě pomocí následující syntaxe. V následujícím příkladu, obsah textu <xref:System.Windows.Controls.TextBlock> je vázán na *StartDate*, což je vlastnost z externího zdroje dat.  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Prostředků stylu odkazuje v předchozím příkladu jsou definovány v oddílu prostředků není zobrazené v tomto tématu.  
  
## <a name="see-also"></a>Viz také:
- [Implementace ověření vazby](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
