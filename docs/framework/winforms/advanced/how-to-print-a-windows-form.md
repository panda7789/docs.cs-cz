---
title: 'Postupy: Tisk formuláře Windows Form'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: 42940654a0754ac3616ca7983af07d20607f480f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522266"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="cad03-102">Postupy: Tisk formuláře Windows Form</span><span class="sxs-lookup"><span data-stu-id="cad03-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="cad03-103">Jako součást procesu vývoje obvykle můžete vytisknout kopii svého formuláře systému Windows.</span><span class="sxs-lookup"><span data-stu-id="cad03-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="cad03-104">Následující příklad kódu ukazuje, jak chcete vytisknout kopii aktuálního formuláře pomocí <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="cad03-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cad03-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="cad03-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cad03-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cad03-106">Compiling the Code</span></span>  
 <span data-ttu-id="cad03-107">Toto je příklad dokončení kódu, který obsahuje `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="cad03-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cad03-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="cad03-108">Robust Programming</span></span>  
 <span data-ttu-id="cad03-109">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="cad03-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="cad03-110">Nemáte oprávnění k přístupu k tiskárně.</span><span class="sxs-lookup"><span data-stu-id="cad03-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="cad03-111">Neexistuje žádné nainstalovanou tiskárnu.</span><span class="sxs-lookup"><span data-stu-id="cad03-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cad03-112">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cad03-112">.NET Framework Security</span></span>  
 <span data-ttu-id="cad03-113">Chcete-li spustit tento příklad kódu, musí mít oprávnění k přístupu k tiskárně, které používáte pro váš počítač.</span><span class="sxs-lookup"><span data-stu-id="cad03-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cad03-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="cad03-114">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="cad03-115">Postupy: Vykreslení obrázků pomocí GDI+</span><span class="sxs-lookup"><span data-stu-id="cad03-115">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [<span data-ttu-id="cad03-116">Postupy: Tisk grafiky v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cad03-116">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
