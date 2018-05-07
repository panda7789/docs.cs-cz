---
title: 'Postupy: Vytvoření připojení v kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 62c5610bf5590594f34a3401b9397bb17d23f5ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-binding-in-code"></a>Postupy: Vytvoření připojení v kódu
Tento příklad ukazuje postup vytvoření a nastavení <xref:System.Windows.Data.Binding> v kódu.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.FrameworkElement> – Třída a <xref:System.Windows.FrameworkContentElement> třída obě vystavit `SetBinding` metoda. Pokud vytváříte vazbu element, který dědí některý z těchto tříd, můžete zavolat <xref:System.Windows.FrameworkElement.SetBinding%2A> metoda přímo.  
  
 Následující příklad vytvoří třídu s názvem, `MyData`, který obsahuje vlastnost s názvem `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 Následující příklad ukazuje, jak vytvořit objekt vazby nastavit zdroj vazby.  V příkladu je <xref:System.Windows.FrameworkElement.SetBinding%2A> k vytvoření vazby <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost `myText`, který je <xref:System.Windows.Controls.TextBlock> řídit, na `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Úplný příklad najdete v části [jen kód vazby ukázka](http://msdn.microsoft.com/library/764aaf0b-2216-4941-9548-9c98da18d1a6).  
  
 Místo volání <xref:System.Windows.FrameworkElement.SetBinding%2A>, můžete použít <xref:System.Windows.Data.BindingOperations.SetBinding%2A> statickou metodu <xref:System.Windows.Data.BindingOperations> třídy. Následující příklad, volání <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> místo <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> pro vazbu `myText` k `myDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
