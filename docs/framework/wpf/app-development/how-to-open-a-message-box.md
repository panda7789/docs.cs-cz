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
ms.openlocfilehash: f05190030ed6324917348fa1926abd5385e30f7e
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46507775"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="859ea-102">Postupy: otevření okna se zprávou</span><span class="sxs-lookup"><span data-stu-id="859ea-102">How to: Open a Message Box</span></span>
<span data-ttu-id="859ea-103">Tento příklad ukazuje, jak otevřít okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="859ea-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="859ea-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="859ea-104">Example</span></span>  
 <span data-ttu-id="859ea-105">Okno se zprávou je prefabrikované modální dialogové okno pro zobrazení informací o uživateli.</span><span class="sxs-lookup"><span data-stu-id="859ea-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="859ea-106">Zavoláním statické se otevře okno se zprávou <xref:System.Windows.MessageBox.Show%2A> metodu <xref:System.Windows.MessageBox> třídy.</span><span class="sxs-lookup"><span data-stu-id="859ea-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="859ea-107">Když <xref:System.Windows.MessageBox.Show%2A> je volána, předávání zpráv pomocí parametru řetězce.</span><span class="sxs-lookup"><span data-stu-id="859ea-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="859ea-108">Několik přetížení <xref:System.Windows.MessageBox.Show%2A> umožňují konfigurovat, jak se zobrazí okno se zprávou (viz <xref:System.Windows.MessageBox>).</span><span class="sxs-lookup"><span data-stu-id="859ea-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="859ea-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="859ea-109">See Also</span></span>  
 [<span data-ttu-id="859ea-110">Ukázka MessageBox</span><span class="sxs-lookup"><span data-stu-id="859ea-110">MessageBox Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160023)
