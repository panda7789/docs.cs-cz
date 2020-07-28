---
title: 'Postupy: Vytvoření připojení v kódu'
description: Naučte se vytvořit vazbu v kódu v Windows Presentation Foundation aplikaci voláním metody použijte SetBinding přímo.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: aa2a29f4c1262d8ac54641b856c297b284b23a38
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165814"
---
# <a name="how-to-create-a-binding-in-code"></a>Postupy: Vytvoření připojení v kódu
Tento příklad ukazuje, jak vytvořit a nastavit <xref:System.Windows.Data.Binding> v kódu.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.FrameworkElement>Třída a <xref:System.Windows.FrameworkContentElement> Třída zpřístupňují `SetBinding` metodu. Pokud vytváříte vazbu na prvek, který dědí jednu z těchto tříd, můžete zavolat <xref:System.Windows.FrameworkElement.SetBinding%2A> metodu přímo.  
  
 Následující příklad vytvoří třídu s názvem, `MyData` , která obsahuje vlastnost s názvem `MyDataProperty` .  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 Následující příklad ukazuje, jak vytvořit objekt vazby pro nastavení zdroje vazby.  Příklad používá <xref:System.Windows.FrameworkElement.SetBinding%2A> pro svázání <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnosti `myText` prvku, což je <xref:System.Windows.Controls.TextBlock> ovládací prvek, do `MyDataProperty` .  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Kompletní ukázku kódu naleznete v tématu [Ukázka vazby výhradně pro kód](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).  
  
 Namísto volání <xref:System.Windows.FrameworkElement.SetBinding%2A> můžete použít <xref:System.Windows.Data.BindingOperations.SetBinding%2A> statickou metodu <xref:System.Windows.Data.BindingOperations> třídy. Následující příklad volá <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> místo <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> pro vytvoření vazby `myText` na `myDataProperty` .  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>Viz také

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [– postupy](data-binding-how-to-topics.md)
