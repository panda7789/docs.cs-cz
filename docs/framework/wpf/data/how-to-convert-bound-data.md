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
ms.openlocfilehash: f9ad390626092d481bf47f017f643a29302c1b29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458867"
---
# <a name="how-to-convert-bound-data"></a>Postupy: Převod připojených dat
Tento příklad ukazuje, jak použít převod na data, která se používají ve vazbách.  
  
 Chcete-li převést data během vytváření vazby, je nutné vytvořit třídu, která implementuje rozhraní <xref:System.Windows.Data.IValueConverter>, které zahrnuje metody <xref:System.Windows.Data.IValueConverter.Convert%2A> a <xref:System.Windows.Data.IValueConverter.ConvertBack%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci převaděče data, který převede hodnotu data předaného, aby zobrazila pouze rok, měsíc a den. Při implementaci rozhraní <xref:System.Windows.Data.IValueConverter> je vhodné sezpůsobovat implementaci pomocí atributu <xref:System.Windows.Data.ValueConversionAttribute>, aby označoval vývojové nástroje jako datové typy, které jsou součástí převodu, jako v následujícím příkladu:  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Po vytvoření převaděče ho můžete přidat jako prostředek do souboru [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. V následujícím příkladu *Src* mapuje na obor názvů, ve kterém je definována *DateConverter* .  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Nakonec můžete použít převodník ve vazbě pomocí následující syntaxe. V následujícím příkladu je textový obsah <xref:System.Windows.Controls.TextBlock> svázán s *StartDate*, což je vlastnost externího zdroje dat.  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Prostředky stylu, na které je odkazováno v předchozím příkladu, jsou definovány v oddílu prostředků, který není zobrazen v tomto tématu.  
  
## <a name="see-also"></a>Viz také:

- [Implementace ověření vazby](how-to-implement-binding-validation.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
