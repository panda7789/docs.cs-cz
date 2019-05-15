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
ms.openlocfilehash: cd10e0a43ff37b921dc8e024d7a6a51fafbb0400
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591850"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="18b8d-102">Postupy: Tisk formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="18b8d-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="18b8d-103">Jako součást procesu vývoje obvykle chcete vytisknout kopii formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="18b8d-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="18b8d-104">Následující příklad kódu ukazuje, jak vytisknout kopii aktuálního formuláře pomocí <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="18b8d-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18b8d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="18b8d-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="18b8d-106">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="18b8d-106">Robust Programming</span></span>  
 <span data-ttu-id="18b8d-107">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="18b8d-107">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="18b8d-108">Nemáte oprávnění k přístupu k tiskárně.</span><span class="sxs-lookup"><span data-stu-id="18b8d-108">You do not have permission to access the printer.</span></span>  
  
- <span data-ttu-id="18b8d-109">Není nainstalovaná žádná tiskárna.</span><span class="sxs-lookup"><span data-stu-id="18b8d-109">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="18b8d-110">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="18b8d-110">.NET Framework Security</span></span>  
 <span data-ttu-id="18b8d-111">Chcete-li spustit tento příklad kódu, musíte mít oprávnění k přístupu k tiskárně, které používáte s počítačem.</span><span class="sxs-lookup"><span data-stu-id="18b8d-111">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18b8d-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18b8d-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="18b8d-113">Postupy: Vykreslení obrázků pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="18b8d-113">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="18b8d-114">Postupy: Tisk grafiky ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18b8d-114">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)
