---
title: 'Postupy: Získání objektu připojení z vlastností cíle připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c528515124898c7deb6114e620ce21766123ab3c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453049"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Postupy: Získání objektu připojení z vlastností cíle připojení
Tento příklad ukazuje, jak získat objekt vazby z vlastnosti target vázaného na data.

## <a name="example"></a>Příklad
 K získání <xref:System.Windows.Data.Binding> objektu můžete provést následující:

 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]

> [!NOTE]
> Je nutné zadat vlastnost závislosti požadované vazby, protože je možné, že více než jedna vlastnost cílového objektu používá datovou vazbu.

 Případně můžete získat <xref:System.Windows.Data.BindingExpression> a potom získat hodnotu vlastnosti <xref:System.Windows.Data.BindingExpression.ParentBinding%2A>.

 Kompletní příklad naleznete v tématu [Ukázka ověřování vazby](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation).

> [!NOTE]
> Pokud je vaše vazba <xref:System.Windows.Data.MultiBinding>, použijte <xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A?displayProperty=nameWithType>. Pokud se jedná o <xref:System.Windows.Data.PriorityBinding>, použijte <xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A?displayProperty=nameWithType>. Pokud si nejste jistí, jestli je cílová vlastnost svázaná pomocí <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>nebo <xref:System.Windows.Data.PriorityBinding>, můžete použít <xref:System.Windows.Data.BindingOperations.GetBindingBase%2A?displayProperty=nameWithType>.

## <a name="see-also"></a>Viz také

- [Vytvoření vazby v kódu](how-to-create-a-binding-in-code.md)
- [Témata s postupy](data-binding-how-to-topics.md)
