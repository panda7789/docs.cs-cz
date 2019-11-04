---
title: 'Postupy: Vygenerování hodnoty na základě seznamu připojených položek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: da183a34eb85de54b1e3f54f8d14c09e25640165
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459690"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>Postupy: Vygenerování hodnoty na základě seznamu připojených položek
<xref:System.Windows.Data.MultiBinding> umožňuje svázat vlastnost target vazby se seznamem vlastností zdroje a potom použít logiku pro vytvoření hodnoty s danými vstupy. Tento příklad ukazuje, jak použít <xref:System.Windows.Data.MultiBinding>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `NameListData` odkazuje na kolekci objektů `PersonName`, což jsou objekty, které obsahují dvě vlastnosti, `firstName` a `lastName`. Následující příklad vytvoří <xref:System.Windows.Controls.TextBlock>, který zobrazuje jméno a příjmení osoby s posledním názvem.  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 Aby bylo možné pochopit, jak se vytvoří formát křestního jména, Podívejme se na implementaci `NameConverter`:  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` implementuje rozhraní <xref:System.Windows.Data.IMultiValueConverter>. `NameConverter` přebírá hodnoty z jednotlivých vazeb a ukládá je do pole objektů hodnot. Pořadí, ve kterém se <xref:System.Windows.Data.Binding> prvky zobrazí pod prvkem <xref:System.Windows.Data.MultiBinding>, je pořadí, ve kterém jsou tyto hodnoty uloženy v poli. Hodnota atributu <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> je odkazována argumentem parametru metody <xref:System.Windows.Data.MultiBinding.Converter%2A>, která provádí přepínač na parametru pro určení způsobu formátování názvu.  
  
## <a name="see-also"></a>Viz také:

- [Převod vázaných dat](how-to-convert-bound-data.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
