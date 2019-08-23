---
title: 'Postupy: Vrácení výsledku dialogového okna'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 5e3670006762bcd09634b29314ecf2d05b1a44da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968235"
---
# <a name="how-to-return-a-dialog-box-result"></a>Postupy: Vrácení výsledku dialogového okna
Tento příklad ukazuje, jak načíst výsledek dialogového okna pro okno, které je otevřeno voláním <xref:System.Windows.Window.ShowDialog%2A>.  
  
## <a name="example"></a>Příklad  
 Před zavřením <xref:System.Windows.Window.DialogResult%2A> dialogového okna by měla být vlastnost nastavena <xref:System.Nullable%601> <xref:System.Boolean> s parametrem, který označuje způsob, jakým uživatel zavřel dialogové okno. Tato hodnota je vrácena nástrojem <xref:System.Windows.Window.ShowDialog%2A> , aby umožnila kódu klienta určit, jak se dialogové okno zavřelo, a v důsledku toho zpracovat výsledek.  
  
> [!NOTE]
> <xref:System.Windows.Window.DialogResult%2A>dá se nastavit jenom v případě, že se okno otevřelo voláním <xref:System.Windows.Window.ShowDialog%2A>.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Volání <xref:System.Windows.Window.ShowDialog%2A> vyžaduje oprávnění k použití událostí vstupu všech oken a uživatelem bez omezení.
