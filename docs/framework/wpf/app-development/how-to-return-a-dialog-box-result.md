---
title: 'Postupy: Vrácení výsledku dialogového okna'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: b574a5bbc08d947371837116915c2fc8c13ec81d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357765"
---
# <a name="how-to-return-a-dialog-box-result"></a>Postupy: Vrácení výsledku dialogového okna
Tento příklad ukazuje, jak načíst výsledek dialogového okna pro okno, které se otevře voláním <xref:System.Windows.Window.ShowDialog%2A>.  
  
## <a name="example"></a>Příklad  
 Předtím, než dialogové okno se zavře a jeho <xref:System.Windows.Window.DialogResult%2A> vlastnost musí být nastavena s <xref:System.Nullable%601> <xref:System.Boolean> , která indikuje, jak uživatel zavření dialogových oken. Tato hodnota je vrácený <xref:System.Windows.Window.ShowDialog%2A> povolit klientský kód určíte, jak bylo ukončeno dialogových oken a, v důsledku toho, jak zpracovat výsledek.  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A> lze nastavit pouze v případě, že okno byl otevřen voláním <xref:System.Windows.Window.ShowDialog%2A>.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Volání <xref:System.Windows.Window.ShowDialog%2A> vyžaduje souhlas s používáním všechna okna a události uživatelského vstupu bez omezení.
