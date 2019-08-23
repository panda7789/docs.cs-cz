---
title: 'Postupy: Získání objektu vazby ze vlastnosti cíle vazby'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: c7aacc2145ffe98ec7b58afb3b2e3dca151ef0ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965438"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Postupy: Získání objektu vazby ze vlastnosti cíle vazby
Tento příklad ukazuje, jak získat objekt vazby z vlastnosti target vázaného na data.  
  
## <a name="example"></a>Příklad  
 K získání <xref:System.Windows.Data.Binding> objektu můžete provést následující akce:  
  
 [!code-csharp[BindValidation#GetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
> Je nutné zadat vlastnost závislosti požadované vazby, protože je možné, že více než jedna vlastnost cílového objektu používá datovou vazbu.  
  
 Alternativně můžete získat <xref:System.Windows.Data.BindingExpression> a získat hodnotu <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> vlastnosti.  
  
 Kompletní příklad naleznete v tématu [Ukázka ověřování vazby](https://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
> Pokud je <xref:System.Windows.Data.MultiBinding>vaše vazba, použijte <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>. Pokud je <xref:System.Windows.Data.PriorityBinding>, použijte <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>. Pokud si nejste jistí, jestli je cílová vlastnost svázaná pomocí <xref:System.Windows.Data.Binding>, a <xref:System.Windows.Data.MultiBinding>, nebo <xref:System.Windows.Data.PriorityBinding>, můžete použít <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření vazby v kódu](how-to-create-a-binding-in-code.md)
- [Témata s postupy](data-binding-how-to-topics.md)
