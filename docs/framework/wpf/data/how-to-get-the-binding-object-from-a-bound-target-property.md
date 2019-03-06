---
title: 'Postupy: Získání objektu připojení z vlastností cíle připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], getting binding objects from bound target properties
- properties [WPF], getting binding objects from
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
ms.openlocfilehash: af18cf3fc155148816690bdd16baa3a2a5515eee
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368516"
---
# <a name="how-to-get-the-binding-object-from-a-bound-target-property"></a>Postupy: Získání objektu připojení z vlastností cíle připojení
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
