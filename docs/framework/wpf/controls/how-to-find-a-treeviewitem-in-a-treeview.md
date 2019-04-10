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
ms.openlocfilehash: 034ec2e57fb3b6a9b3a81f66f6888a68e2c113d7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219041"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>Postupy: Hledání TreeViewItem v objektu TreeView
<xref:System.Windows.Controls.TreeView> Řízení poskytuje pohodlný způsob, jak zobrazit hierarchická data. Pokud vaše <xref:System.Windows.Controls.TreeView> je svázán se zdrojem dat <xref:System.Windows.Controls.TreeView.SelectedItem%2A> vlastnost představuje pohodlný způsob pro vám umožní rychle načíst zvoleného datového objektu. Je obvykle nejlepší pro práci s podkladového datového objektu, ale v některých případech je nutné programově manipulovat s dat obsahující <xref:System.Windows.Controls.TreeViewItem>. Budete například muset prostřednictvím kódu programu rozbalte <xref:System.Windows.Controls.TreeViewItem>, nebo vyberte jiné položce v <xref:System.Windows.Controls.TreeView>.  
  
 K vyhledání <xref:System.Windows.Controls.TreeViewItem> , která obsahuje objekt konkrétní data, musí procházet jednotlivé úrovně <xref:System.Windows.Controls.TreeView>. Položky v <xref:System.Windows.Controls.TreeView> se také dají Virtualizovat ke zlepšení výkonu. V případě, kde může virtualizované položky, je nutné si uvědomit <xref:System.Windows.Controls.TreeViewItem> ke kontrole, zda datový objekt obsahuje.  
  
## <a name="example"></a>Příklad  
  
## <a name="description"></a>Popis  
 Následující příklady hledání <xref:System.Windows.Controls.TreeView> pro konkrétní objekt a vrátí objekt obsahující <xref:System.Windows.Controls.TreeViewItem>. V příkladu se každý zajišťuje <xref:System.Windows.Controls.TreeViewItem> je vytvořena instance tak, aby její podřízené položky lze prohledávat. Tento příklad funguje taky Pokud <xref:System.Windows.Controls.TreeView> nepoužívá virtualizované položky.  
  
> [!NOTE]
>  Následující příklad funguje pro všechny <xref:System.Windows.Controls.TreeView>, bez ohledu na základní datový model a prohledávání všech <xref:System.Windows.Controls.TreeViewItem> dokud nebude nalezen objekt. Další technikou, který má lepší výkon je hledání datový model pro zadaný objekt, udržovat přehled o jeho umístění v rámci hierarchie dat a pak vyhledejte odpovídající <xref:System.Windows.Controls.TreeViewItem> v <xref:System.Windows.Controls.TreeView>. Ale techniku, která má lepší výkon vyžaduje znalosti datového modelu a nedá zobecnit pro každá <xref:System.Windows.Controls.TreeView>.  
  
## <a name="code"></a>Kód  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 Předchozí kód závisí na vlastní <xref:System.Windows.Controls.VirtualizingStackPanel> , která zpřístupní metodu s názvem `BringIntoView`. Následující kód definuje vlastní <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 Následující XAML ukazuje, jak vytvořit <xref:System.Windows.Controls.TreeView> , která používá vlastní <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>Viz také:

- [Zvýšení výkonu TreeView](how-to-improve-the-performance-of-a-treeview.md)
