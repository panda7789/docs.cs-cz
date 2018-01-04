---
title: "Postupy: Vygenerování hodnoty na základě seznamu připojených položek"
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
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3987690a1acb180ee22fa02e399accd9c5d481d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>Postupy: Vygenerování hodnoty na základě seznamu připojených položek
<xref:System.Windows.Data.MultiBinding>Umožňuje vytvořit vazbu cílovou vlastnost vazby na seznamu vlastností zdroje a pak použít logiku k vytvoření hodnoty s danou vstupy. Tento příklad ukazuje, jak používat <xref:System.Windows.Data.MultiBinding>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `NameListData` odkazuje na kolekci `PersonName` objekty, které jsou objekty, které obsahují dvě vlastnosti, `firstName` a `lastName`. Následující příklad vytvoří <xref:System.Windows.Controls.TextBlock> který ukazuje první a poslední jméno osoby s příjmení první.  
  
 [!code-xaml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 Abyste pochopili, jak se vytvářejí ve formátu poslední název první, Podívejme se na provádění `NameConverter`:  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter`implementuje <xref:System.Windows.Data.IMultiValueConverter> rozhraní. `NameConverter`přijímá hodnoty z jednotlivých vazby a ukládá je v poli hodnoty objektu. V jakém pořadí <xref:System.Windows.Data.Binding> prvky se zobrazí v části <xref:System.Windows.Data.MultiBinding> elementu je v tom pořadí, ve kterém jsou tyto hodnoty uloženy v poli. Hodnota <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> atribut se odkazuje parametr argument <xref:System.Windows.Data.MultiBinding.Converter%2A> metodu, která provádí přepínač parametr k určení postupu pro název formátu.  
  
## <a name="see-also"></a>Viz také  
 [Převod vázaných dat](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
