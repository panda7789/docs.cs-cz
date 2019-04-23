---
title: 'Postupy: Získání objektu vazby ze vlastnosti cíle vazby'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: 7c7392bc11af57b2e9f27e2302f36efb59d40e9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083103"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Postupy: Získání objektu vazby ze vlastnosti cíle vazby
Tento příklad ukazuje, jak získat objekt binding z vlastnosti cílového vázané na data.  
  
## <a name="example"></a>Příklad  
 Můžete dělat tyto věci zobrazíte <xref:System.Windows.Data.Binding> objektu:  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  Je nutné zadat vlastnost závislosti pro vazbu, kterou chcete, protože je možné, že více než jednu vlastnost cílového objektu je použití datových vazeb.  
  
 Alternativně můžete získat <xref:System.Windows.Data.BindingExpression> a potom získat hodnotu <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> vlastnost.  
  
 Kompletní příklad naleznete v tématu [vazby Ukázka ověřování](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
>  Pokud je vaše vazby <xref:System.Windows.Data.MultiBinding>, použijte <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>. Pokud se jedná <xref:System.Windows.Data.PriorityBinding>, použijte <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>. Pokud si nejste jisti, zda je vlastnost target svázán pomocí <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.MultiBinding>, nebo <xref:System.Windows.Data.PriorityBinding>, můžete použít <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření vazby v kódu](how-to-create-a-binding-in-code.md)
- [Témata s postupy](data-binding-how-to-topics.md)
