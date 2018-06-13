---
title: 'Postupy: Hledání TreeViewItem v objektu TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: cff931312e6bc6db5ae5f26c0db80ad2f43825f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554752"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>Postupy: Hledání TreeViewItem v objektu TreeView
<xref:System.Windows.Controls.TreeView> Řízení nabízí pohodlný způsob, jak zobrazit hierarchické data. Pokud vaše <xref:System.Windows.Controls.TreeView> je vázán na zdroj dat <xref:System.Windows.Controls.TreeView.SelectedItem%2A> vlastnost představuje pohodlný způsob pro vás lze snadno obnovit vybraná data objektu. Je obvykle nejvhodnější pro práci s základní datový objekt, ale někdy budete muset programově měnit data na obsahující <xref:System.Windows.Controls.TreeViewItem>. Například budete muset prostřednictvím kódu programu rozbalte <xref:System.Windows.Controls.TreeViewItem>, nebo vyberte jinou položku v <xref:System.Windows.Controls.TreeView>.  
  
 Najít <xref:System.Windows.Controls.TreeViewItem> , který obsahuje objekt konkrétní data, musí procházet jednotlivých úrovních <xref:System.Windows.Controls.TreeView>. Položky v <xref:System.Windows.Controls.TreeView> se také dají Virtualizovat ke zlepšení výkonu. V případě, kde může být položky Virtualizovat, je nutné si uvědomit, <xref:System.Windows.Controls.TreeViewItem> zkontrolujte, zda obsahuje datový objekt.  
  
## <a name="example"></a>Příklad  
  
## <a name="description"></a>Popis  
 Následující příklady hledání <xref:System.Windows.Controls.TreeView> pro konkrétní objekt a vrátí objekt obsahující <xref:System.Windows.Controls.TreeViewItem>. V příkladu zajišťuje, aby se každý <xref:System.Windows.Controls.TreeViewItem> je vytvořena instance tak, aby její podřízené položky lze vyhledat. Tento příklad funguje taky Pokud <xref:System.Windows.Controls.TreeView> nepoužívá virtualizované položky.  
  
> [!NOTE]
>  V následujícím příkladu se dá použít pro žádné <xref:System.Windows.Controls.TreeView>, bez ohledu na základní datový model a hledání každých <xref:System.Windows.Controls.TreeViewItem> dokud nebude nalezen objekt. Další postup, který má lepší výkon je vyhledávání datový model pro zadaný objekt, sledovat její umístění v rámci hierarchie dat a pak vyhledejte odpovídající <xref:System.Windows.Controls.TreeViewItem> v <xref:System.Windows.Controls.TreeView>. Ale technika, který má lepší výkon vyžaduje znalost datový model a nemůže být zobecněn pro všechny zadané <xref:System.Windows.Controls.TreeView>.  
  
## <a name="code"></a>Kód  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 Předchozí kód spoléhá na vlastní <xref:System.Windows.Controls.VirtualizingStackPanel> který zpřístupní metodu s názvem `BringIntoView`. Následující kód definuje vlastní <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 Následující XAML ukazuje, jak vytvořit <xref:System.Windows.Controls.TreeView> používající vlastní <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-xaml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>Viz také  
 [Zvýšení výkonu TreeView](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)
