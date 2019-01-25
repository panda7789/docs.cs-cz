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
ms.openlocfilehash: 8f4e5b7767e475128b61080ca87e38ee311f4a3a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706427"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>Postupy: Vygenerování hodnoty na základě seznamu připojených položek
<xref:System.Windows.Data.MultiBinding> Umožňuje vytvoření vazby vlastnosti cílové vazby na seznam vlastností zdroje a pak použít logiku k vytvoření hodnoty se dané vstupy. Tento příklad ukazuje, jak používat <xref:System.Windows.Data.MultiBinding>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `NameListData` odkazuje na kolekci `PersonName` objekty, které jsou objekty, které obsahují dvě vlastnosti, `firstName` a `lastName`. Následující příklad vytvoří <xref:System.Windows.Controls.TextBlock> , která zobrazuje jména a příjmení osoby s příjmení první.  
  
 [!code-xaml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 Informace o tom vytváření formátu poslední název first, Pojďme se podívat na provádění `NameConverter`:  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` implementuje <xref:System.Windows.Data.IMultiValueConverter> rozhraní. `NameConverter` přijímá hodnoty od jednotlivých vazeb a ukládá je v objektu pole hodnot. Pořadí, ve kterém <xref:System.Windows.Data.Binding> prvky se zobrazí pod <xref:System.Windows.Data.MultiBinding> elementu je v tom pořadí, ve kterém jsou tyto hodnoty uloženy v poli. Hodnota <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> atribut odkazuje argument parametru <xref:System.Windows.Data.MultiBinding.Converter%2A> metodu, která provádí přepínač parametru lze určit, jak se formát názvu.  
  
## <a name="see-also"></a>Viz také:
- [Převod vázaných dat](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
