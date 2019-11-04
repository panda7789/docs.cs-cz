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
ms.openlocfilehash: 616487a16ebbe6e23fe067fb7ce72644aa3f919f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458846"
---
# <a name="how-to-create-a-binding-in-code"></a>Postupy: Vytvoření připojení v kódu
Tento příklad ukazuje, jak vytvořit a nastavit <xref:System.Windows.Data.Binding> v kódu.  
  
## <a name="example"></a>Příklad  
 Třída <xref:System.Windows.FrameworkElement> a třída <xref:System.Windows.FrameworkContentElement> vystavuje metodu `SetBinding`. Pokud vytváříte vazbu prvku, který dědí jednu z těchto tříd, můžete volat metodu <xref:System.Windows.FrameworkElement.SetBinding%2A> přímo.  
  
 Následující příklad vytvoří třídu s názvem, `MyData`, která obsahuje vlastnost s názvem `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 Následující příklad ukazuje, jak vytvořit objekt vazby pro nastavení zdroje vazby.  V příkladu se používá <xref:System.Windows.FrameworkElement.SetBinding%2A> k navázání vlastnosti <xref:System.Windows.Controls.TextBlock.Text%2A> `myText`, což je ovládací prvek <xref:System.Windows.Controls.TextBlock>, na `MyDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Kompletní ukázku kódu naleznete v tématu [Ukázka vazby výhradně pro kód](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).  
  
 Namísto volání <xref:System.Windows.FrameworkElement.SetBinding%2A>lze použít statickou metodu <xref:System.Windows.Data.BindingOperations.SetBinding%2A> třídy <xref:System.Windows.Data.BindingOperations>. Následující příklad volá <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> namísto <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> k navázání `myText` na `myDataProperty`.  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
