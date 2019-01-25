---
title: 'Postupy: Tisk formuláře Windows'
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
ms.openlocfilehash: 5e672f40797a90111daefed0be74c941d4cc37b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628133"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="1b614-102">Postupy: Tisk formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="1b614-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="1b614-103">Jako součást procesu vývoje obvykle chcete vytisknout kopii formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="1b614-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="1b614-104">Následující příklad kódu ukazuje, jak vytisknout kopii aktuálního formuláře pomocí <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1b614-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b614-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b614-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1b614-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1b614-106">Compiling the Code</span></span>  
 <span data-ttu-id="1b614-107">Toto je příklad úplného kódu, který obsahuje `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="1b614-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1b614-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1b614-108">Robust Programming</span></span>  
 <span data-ttu-id="1b614-109">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="1b614-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="1b614-110">Nemáte oprávnění k přístupu k tiskárně.</span><span class="sxs-lookup"><span data-stu-id="1b614-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="1b614-111">Není nainstalovaná žádná tiskárna.</span><span class="sxs-lookup"><span data-stu-id="1b614-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1b614-112">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1b614-112">.NET Framework Security</span></span>  
 <span data-ttu-id="1b614-113">Chcete-li spustit tento příklad kódu, musíte mít oprávnění k přístupu k tiskárně, které používáte s počítačem.</span><span class="sxs-lookup"><span data-stu-id="1b614-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b614-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b614-114">See also</span></span>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="1b614-115">Postupy: Vykreslení obrázků pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="1b614-115">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)
- [<span data-ttu-id="1b614-116">Postupy: Tisk grafiky ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1b614-116">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
