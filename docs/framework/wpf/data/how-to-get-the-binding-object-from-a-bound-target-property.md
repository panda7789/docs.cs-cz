---
title: 'Postupy: Získání objektu připojení z vlastností cíle připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: 0bc793d4c95f8919517a83e434cf795e971dcd32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556728"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Postupy: Získání objektu připojení z vlastností cíle připojení
Tento příklad ukazuje, jak získat objekt binding z vlastnosti cílového vázané na data.  
  
## <a name="example"></a>Příklad  
 Můžete provést následující získat <xref:System.Windows.Data.Binding> objektu:  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  Musíte zadat vlastnost závislosti pro vazbu, které chcete, protože je možné, že více než jednu vlastnost cílového objektu je použití datových vazeb.  
  
 Alternativně můžete získat <xref:System.Windows.Data.BindingExpression> a potom získat hodnotu <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> vlastnost.  
  
 Úplný příklad najdete v části [vazby Ukázka ověřování](http://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
>  Pokud je vaše vazby <xref:System.Windows.Data.MultiBinding>, použijte <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>. Pokud je <xref:System.Windows.Data.PriorityBinding>, použijte <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>. Pokud si nejste jisti, zda je vlastnost target svázán pomocí <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>, nebo <xref:System.Windows.Data.PriorityBinding>, můžete použít <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby v kódu](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
