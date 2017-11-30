---
title: "Postupy: Tisk formuláře Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9149b90317036c7c62c5fca3056bb697df56e543
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="b1ecc-102">Postupy: Tisk formuláře Windows Form</span><span class="sxs-lookup"><span data-stu-id="b1ecc-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="b1ecc-103">Jako součást procesu vývoje obvykle můžete vytisknout kopii svého formuláře systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b1ecc-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="b1ecc-104">Následující příklad kódu ukazuje, jak chcete vytisknout kopii aktuálního formuláře pomocí <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="b1ecc-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1ecc-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1ecc-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b1ecc-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b1ecc-106">Compiling the Code</span></span>  
 <span data-ttu-id="b1ecc-107">Toto je příklad dokončení kódu, který obsahuje `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="b1ecc-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b1ecc-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="b1ecc-108">Robust Programming</span></span>  
 <span data-ttu-id="b1ecc-109">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="b1ecc-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b1ecc-110">Nemáte oprávnění k přístupu k tiskárně.</span><span class="sxs-lookup"><span data-stu-id="b1ecc-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="b1ecc-111">Neexistuje žádné nainstalovanou tiskárnu.</span><span class="sxs-lookup"><span data-stu-id="b1ecc-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b1ecc-112">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b1ecc-112">.NET Framework Security</span></span>  
 <span data-ttu-id="b1ecc-113">Chcete-li spustit tento příklad kódu, musí mít oprávnění k přístupu k tiskárně, které používáte pro váš počítač.</span><span class="sxs-lookup"><span data-stu-id="b1ecc-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ecc-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1ecc-114">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="b1ecc-115">Postupy: vykreslení obrázků pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="b1ecc-115">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [<span data-ttu-id="b1ecc-116">Postupy: tisk grafiky ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1ecc-116">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
