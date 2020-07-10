---
title: 'Postupy: Tisk formuláře Windows Form'
description: Naučte se programově tisknout kopii aktuálního formuláře Windows pomocí metody CopyFromScreen.
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
ms.openlocfilehash: b59ea4b5347903b36a166c4f8ac0d8d7db18635e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174689"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="6bbbc-103">Postupy: Tisk formuláře Windows Form</span><span class="sxs-lookup"><span data-stu-id="6bbbc-103">How to: Print a Windows Form</span></span>
<span data-ttu-id="6bbbc-104">V rámci procesu vývoje obvykle budete chtít vytisknout kopii formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="6bbbc-104">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="6bbbc-105">Následující příklad kódu ukazuje, jak vytisknout kopii aktuálního formuláře pomocí <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6bbbc-105">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bbbc-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6bbbc-106">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6bbbc-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="6bbbc-107">Robust Programming</span></span>  
 <span data-ttu-id="6bbbc-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="6bbbc-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="6bbbc-109">Nemáte oprávnění pro přístup k tiskárně.</span><span class="sxs-lookup"><span data-stu-id="6bbbc-109">You do not have permission to access the printer.</span></span>  
  
- <span data-ttu-id="6bbbc-110">Není nainstalovaná žádná tiskárna.</span><span class="sxs-lookup"><span data-stu-id="6bbbc-110">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6bbbc-111">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6bbbc-111">.NET Framework Security</span></span>  
 <span data-ttu-id="6bbbc-112">Aby bylo možné spustit tento příklad kódu, musíte mít oprávnění pro přístup k tiskárně, kterou používáte s vaším počítačem.</span><span class="sxs-lookup"><span data-stu-id="6bbbc-112">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bbbc-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bbbc-113">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="6bbbc-114">Postupy: Vykreslení obrázků pomocí GDI+</span><span class="sxs-lookup"><span data-stu-id="6bbbc-114">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="6bbbc-115">Postupy: Tisk grafiky v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6bbbc-115">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)
