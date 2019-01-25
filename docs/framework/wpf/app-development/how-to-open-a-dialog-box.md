---
title: 'Postupy: Otevřete dialogové okno'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
ms.openlocfilehash: 0ed41d212eee74d0c3eed1d3341d64a6abc876a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638142"
---
# <a name="how-to-open-a-dialog-box"></a><span data-ttu-id="8c40b-102">Postupy: Otevřete dialogové okno</span><span class="sxs-lookup"><span data-stu-id="8c40b-102">How to: Open a Dialog Box</span></span>
<span data-ttu-id="8c40b-103">Tento příklad ukazuje, jak otevřít dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="8c40b-103">This example shows how to open a dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c40b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c40b-104">Example</span></span>  
 <span data-ttu-id="8c40b-105">Dialogové okno je okno, které se otevře po vytvoření instance <xref:System.Windows.Window> a volání <xref:System.Windows.Window.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8c40b-105">A dialog box is a window that is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span> <span data-ttu-id="8c40b-106"><xref:System.Windows.Window.ShowDialog%2A> Otevře se okno a nevrací, dokud se nové dialogové okno se zavřelo.</span><span class="sxs-lookup"><span data-stu-id="8c40b-106"><xref:System.Windows.Window.ShowDialog%2A> opens a window and doesn't return until the new dialog box has been closed.</span></span> <span data-ttu-id="8c40b-107">Tento typ okno se také označuje jako *modální* okna a omezí vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="8c40b-107">This type of window is also known as a *modal* window, and restricts user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="8c40b-108">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8c40b-108">.NET Framework Security</span></span>  
 <span data-ttu-id="8c40b-109">Volání <xref:System.Windows.Window.ShowDialog%2A> vyžaduje souhlas s používáním všechna okna a události uživatelského vstupu bez omezení.</span><span class="sxs-lookup"><span data-stu-id="8c40b-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c40b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c40b-110">See also</span></span>
- [<span data-ttu-id="8c40b-111">Vrácení výsledku dialogového okna</span><span class="sxs-lookup"><span data-stu-id="8c40b-111">Return a Dialog Box Result</span></span>](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)
