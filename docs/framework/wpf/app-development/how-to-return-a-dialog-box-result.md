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
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="ef6c0-102">Postupy: Vrácení výsledku dialogového okna</span><span class="sxs-lookup"><span data-stu-id="ef6c0-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="ef6c0-103">Tento příklad ukazuje, jak načíst výsledek dialogového okna pro okno, které se otevře voláním <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef6c0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef6c0-104">Example</span></span>  
 <span data-ttu-id="ef6c0-105">Předtím, než dialogové okno se zavře a jeho <xref:System.Windows.Window.DialogResult%2A> vlastnost musí být nastavena s <xref:System.Nullable%601> <xref:System.Boolean> , která indikuje, jak uživatel zavření dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="ef6c0-106">Tato hodnota je vrácený <xref:System.Windows.Window.ShowDialog%2A> povolit klientský kód určíte, jak bylo ukončeno dialogových oken a, v důsledku toho, jak zpracovat výsledek.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef6c0-107"><xref:System.Windows.Window.DialogResult%2A> lze nastavit pouze v případě, že okno byl otevřen voláním <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="ef6c0-108">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ef6c0-108">.NET Framework Security</span></span>  
 <span data-ttu-id="ef6c0-109">Volání <xref:System.Windows.Window.ShowDialog%2A> vyžaduje souhlas s používáním všechna okna a události uživatelského vstupu bez omezení.</span><span class="sxs-lookup"><span data-stu-id="ef6c0-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
