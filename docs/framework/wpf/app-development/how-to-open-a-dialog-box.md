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
ms.openlocfilehash: 29fe8b0d516f20fcc742b91099a30e368dfe4548
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546358"
---
# <a name="how-to-open-a-dialog-box"></a><span data-ttu-id="ce47e-102">Postupy: Otevřete dialogové okno</span><span class="sxs-lookup"><span data-stu-id="ce47e-102">How to: Open a Dialog Box</span></span>
<span data-ttu-id="ce47e-103">Tento příklad ukazuje, jak otevřít dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="ce47e-103">This example shows how to open a dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce47e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce47e-104">Example</span></span>  
 <span data-ttu-id="ce47e-105">Je dialogové okno, ve kterém je otevřen po vytvoření instance <xref:System.Windows.Window> a volání <xref:System.Windows.Window.ShowDialog%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ce47e-105">A dialog box is a window that is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span> <span data-ttu-id="ce47e-106"><xref:System.Windows.Window.ShowDialog%2A> Otevře se okno a nevrací dokud dialogové okno Nový bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="ce47e-106"><xref:System.Windows.Window.ShowDialog%2A> opens a window and doesn't return until the new dialog box has been closed.</span></span> <span data-ttu-id="ce47e-107">Tento typ okna je také označován jako *modální* okně a omezuje vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="ce47e-107">This type of window is also known as a *modal* window, and restricts user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="ce47e-108">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ce47e-108">.NET Framework Security</span></span>  
 <span data-ttu-id="ce47e-109">Volání metody <xref:System.Windows.Window.ShowDialog%2A> vyžaduje oprávnění k používání všechna okna a vstupních událostech uživatele bez omezení.</span><span class="sxs-lookup"><span data-stu-id="ce47e-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce47e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce47e-110">See Also</span></span>  
 [<span data-ttu-id="ce47e-111">Vrácení výsledku dialogového okna</span><span class="sxs-lookup"><span data-stu-id="ce47e-111">Return a Dialog Box Result</span></span>](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)
