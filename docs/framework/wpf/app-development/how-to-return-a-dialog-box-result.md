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
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="07cd0-102">Postupy: Vrácení výsledku dialogového okna</span><span class="sxs-lookup"><span data-stu-id="07cd0-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="07cd0-103">Tento příklad ukazuje, jak načíst výsledek dialogového okna pro okno, které je otevřeno voláním <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="07cd0-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07cd0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="07cd0-104">Example</span></span>  
 <span data-ttu-id="07cd0-105">Před zavřením <xref:System.Windows.Window.DialogResult%2A> dialogového okna by měla být vlastnost nastavena <xref:System.Nullable%601> <xref:System.Boolean> s parametrem, který označuje způsob, jakým uživatel zavřel dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="07cd0-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="07cd0-106">Tato hodnota je vrácena nástrojem <xref:System.Windows.Window.ShowDialog%2A> , aby umožnila kódu klienta určit, jak se dialogové okno zavřelo, a v důsledku toho zpracovat výsledek.</span><span class="sxs-lookup"><span data-stu-id="07cd0-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07cd0-107"><xref:System.Windows.Window.DialogResult%2A>dá se nastavit jenom v případě, že se okno otevřelo voláním <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="07cd0-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="07cd0-108">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="07cd0-108">.NET Framework Security</span></span>  
 <span data-ttu-id="07cd0-109">Volání <xref:System.Windows.Window.ShowDialog%2A> vyžaduje oprávnění k použití událostí vstupu všech oken a uživatelem bez omezení.</span><span class="sxs-lookup"><span data-stu-id="07cd0-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
