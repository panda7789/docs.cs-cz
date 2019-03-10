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
ms.openlocfilehash: 80bf88ad048e55a381d034d2a796de6f77f8691c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714148"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="1d26c-102">Postupy: Tisk formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="1d26c-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="1d26c-103">Jako součást procesu vývoje obvykle chcete vytisknout kopii formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="1d26c-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="1d26c-104">Následující příklad kódu ukazuje, jak vytisknout kopii aktuálního formuláře pomocí <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1d26c-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d26c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d26c-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d26c-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1d26c-106">Compiling the Code</span></span>  
 <span data-ttu-id="1d26c-107">Toto je příklad úplného kódu, který obsahuje `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="1d26c-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1d26c-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1d26c-108">Robust Programming</span></span>  
 <span data-ttu-id="1d26c-109">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="1d26c-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="1d26c-110">Nemáte oprávnění k přístupu k tiskárně.</span><span class="sxs-lookup"><span data-stu-id="1d26c-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="1d26c-111">Není nainstalovaná žádná tiskárna.</span><span class="sxs-lookup"><span data-stu-id="1d26c-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1d26c-112">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d26c-112">.NET Framework Security</span></span>  
 <span data-ttu-id="1d26c-113">Chcete-li spustit tento příklad kódu, musíte mít oprávnění k přístupu k tiskárně, které používáte s počítačem.</span><span class="sxs-lookup"><span data-stu-id="1d26c-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d26c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d26c-114">See also</span></span>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="1d26c-115">Postupy: Vykreslení obrázků pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="1d26c-115">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="1d26c-116">Postupy: Tisk grafiky ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1d26c-116">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)
