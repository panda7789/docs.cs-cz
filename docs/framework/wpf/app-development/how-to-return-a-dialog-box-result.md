---
title: 'Postupy: vrácení výsledku pole dialogové okno'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 8f754577a355a58060238bbbb487c36aea14658c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545584"
---
# <a name="how-to-return-a-dialog-box-result"></a>Postupy: vrácení výsledku pole dialogové okno
Tento příklad ukazuje, jak načíst výsledky dialogové okno pro okno, ve kterém je otevřen voláním <xref:System.Windows.Window.ShowDialog%2A>.  
  
## <a name="example"></a>Příklad  
 Předtím, než se zavře dialogové okno a jeho <xref:System.Windows.Window.DialogResult%2A> musí být vlastnost nastavena <xref:System.Nullable%601> <xref:System.Boolean> určující, jak uživatel zavřel dialogové okno. Tato hodnota je vrácen rutinou <xref:System.Windows.Window.ShowDialog%2A> umožňující kód klienta pro určují, jak bylo ukončeno dialogové okno a v důsledku toho, jak zpracovat výsledek.  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A> můžete nastavit pouze v případě okno byl otevřen voláním <xref:System.Windows.Window.ShowDialog%2A>.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Volání metody <xref:System.Windows.Window.ShowDialog%2A> vyžaduje oprávnění k používání všechna okna a vstupních událostech uživatele bez omezení.
