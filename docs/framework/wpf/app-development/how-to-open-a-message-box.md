---
title: 'Postupy: otevření okna se zprávou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: bd2c4dce78e46163eb4628cb3aab829fc0173edf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123724"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="90b3c-102">Postupy: otevření okna se zprávou</span><span class="sxs-lookup"><span data-stu-id="90b3c-102">How to: Open a Message Box</span></span>
<span data-ttu-id="90b3c-103">Tento příklad ukazuje, jak otevřít okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="90b3c-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90b3c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="90b3c-104">Example</span></span>  
 <span data-ttu-id="90b3c-105">Okno se zprávou je přednastavené modální dialogové okno pro zobrazení informací uživatelům.</span><span class="sxs-lookup"><span data-stu-id="90b3c-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="90b3c-106">Okno se zprávou je otevřeno voláním metody static <xref:System.Windows.MessageBox.Show%2A> třídy <xref:System.Windows.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="90b3c-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="90b3c-107">Při volání <xref:System.Windows.MessageBox.Show%2A> je zpráva předána pomocí řetězcového parametru.</span><span class="sxs-lookup"><span data-stu-id="90b3c-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="90b3c-108">Několik přetížení <xref:System.Windows.MessageBox.Show%2A> umožňuje nakonfigurovat, jak se zobrazí okno se zprávou (viz <xref:System.Windows.MessageBox>).</span><span class="sxs-lookup"><span data-stu-id="90b3c-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="90b3c-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="90b3c-109">See also</span></span>

- [<span data-ttu-id="90b3c-110">MessageBox – ukázka</span><span class="sxs-lookup"><span data-stu-id="90b3c-110">MessageBox Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)
