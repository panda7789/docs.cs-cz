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
ms.openlocfilehash: ad72c7a7fb11dfe605db4119dde831b47dd7c5a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962095"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>Postupy: Hledání TreeViewItem v objektu TreeView
<xref:System.Windows.Controls.TreeView> Ovládací prvek poskytuje pohodlný způsob zobrazení hierarchických dat. Pokud je svázán se zdrojem dat <xref:System.Windows.Controls.TreeView.SelectedItem%2A> , poskytuje vlastnost pohodlný způsob, jak rychle načíst vybraný datový objekt. <xref:System.Windows.Controls.TreeView> Obvykle je nejvhodnější pracovat s podkladovým datovým objektem, ale někdy může být nutné programově manipulovat s daty, která obsahují <xref:System.Windows.Controls.TreeViewItem>. Například může být nutné programově rozbalit <xref:System.Windows.Controls.TreeViewItem>nebo vybrat jinou položku <xref:System.Windows.Controls.TreeView>v.  
  
 Chcete-li <xref:System.Windows.Controls.TreeViewItem> najít, který obsahuje konkrétní datový objekt, je nutné procházet jednotlivé úrovně. <xref:System.Windows.Controls.TreeView> Položky v <xref:System.Windows.Controls.TreeView> může být také virtualizované pro zlepšení výkonu. V případě, že položky mohou být virtualizované, je také nutné si uvědomit a <xref:System.Windows.Controls.TreeViewItem> ověřit, zda obsahuje datový objekt.  
  
## <a name="example"></a>Příklad  
  
## <a name="description"></a>Popis  
 Následující příklad vyhledá <xref:System.Windows.Controls.TreeView> konkrétní objekt a vrátí objekt obsahující <xref:System.Windows.Controls.TreeViewItem>. V příkladu je zajištěna <xref:System.Windows.Controls.TreeViewItem> instance každého z nich, aby bylo možné prohledávat jeho podřízené položky. Tento příklad funguje také v případě <xref:System.Windows.Controls.TreeView> , že nepoužívá virtualizované položky.  
  
> [!NOTE]
> Následující příklad funguje pro všechny <xref:System.Windows.Controls.TreeView>bez ohledu na podkladový datový model a vyhledá každý <xref:System.Windows.Controls.TreeViewItem> , dokud se objekt nenajde. Dalším způsobem, který má lepší výkon, je vyhledat datový model pro zadaný objekt, sledovat jeho umístění v rámci hierarchie dat a potom najít odpovídající <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.TreeView>v. Nicméně technika, která má vyšší výkon, vyžaduje znalost datového modelu a nelze ji zobecnit pro všechny uvedené <xref:System.Windows.Controls.TreeView>.  
  
## <a name="code"></a>Kód  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 Předchozí kód spoléhá na vlastní <xref:System.Windows.Controls.VirtualizingStackPanel> , který zpřístupňuje metodu s názvem. `BringIntoView` Následující kód definuje vlastní <xref:System.Windows.Controls.VirtualizingStackPanel>.  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 Následující kód XAML ukazuje <xref:System.Windows.Controls.TreeView> , jak vytvořit, který používá vlastní. <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>Viz také:

- [Zvýšení výkonu TreeView](how-to-improve-the-performance-of-a-treeview.md)
