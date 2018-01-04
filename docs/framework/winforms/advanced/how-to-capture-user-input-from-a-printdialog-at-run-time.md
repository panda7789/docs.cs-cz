---
title: "Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu"
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
- cpp
helpviewer_keywords:
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fcc2ccc240752c8c54c28fe2358d3ef49cbf3b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a><span data-ttu-id="f9cf5-102">Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu</span><span class="sxs-lookup"><span data-stu-id="f9cf5-102">How to: Capture User Input from a PrintDialog at Run Time</span></span>
<span data-ttu-id="f9cf5-103">Když nastavíte možnosti týkající se tisku v době návrhu, někdy můžete tyto možnosti změnit za běhu, pravděpodobně z důvodu volby provedené uživatelem.</span><span class="sxs-lookup"><span data-stu-id="f9cf5-103">While you can set options related to printing at design time, you will sometimes want to change these options at run time, most likely because of choices made by the user.</span></span> <span data-ttu-id="f9cf5-104">Můžete zachycení uživatelského vstupu pro tisk dokumentu pomocí <xref:System.Windows.Forms.PrintDialog> a <xref:System.Drawing.Printing.PrintDocument> součásti.</span><span class="sxs-lookup"><span data-stu-id="f9cf5-104">You can capture user input for printing a document using the <xref:System.Windows.Forms.PrintDialog> and the <xref:System.Drawing.Printing.PrintDocument> components.</span></span>  
  
### <a name="to-change-print-options-programmatically"></a><span data-ttu-id="f9cf5-105">Chcete-li změnit možnosti tisku prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="f9cf5-105">To change print options programmatically</span></span>  
  
1.  <span data-ttu-id="f9cf5-106">Přidat <xref:System.Windows.Forms.PrintDialog> a <xref:System.Drawing.Printing.PrintDocument> součásti do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="f9cf5-106">Add a <xref:System.Windows.Forms.PrintDialog> and a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="f9cf5-107">Nastavte <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnost <xref:System.Windows.Forms.PrintDialog> k <xref:System.Drawing.Printing.PrintDocument> přidán do formuláře.</span><span class="sxs-lookup"><span data-stu-id="f9cf5-107">Set the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> to the <xref:System.Drawing.Printing.PrintDocument> added to the form.</span></span>  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  <span data-ttu-id="f9cf5-108">Zobrazení <xref:System.Windows.Forms.PrintDialog> součásti pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f9cf5-108">Display the <xref:System.Windows.Forms.PrintDialog> component by using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  <span data-ttu-id="f9cf5-109">Tisk volby uživatele z tohoto dialogového okna se zkopírují na <xref:System.Drawing.Printing.PrinterSettings> vlastnost <xref:System.Drawing.Printing.PrintDocument> součásti.</span><span class="sxs-lookup"><span data-stu-id="f9cf5-109">The user's printing choices from the dialog will be copied to the <xref:System.Drawing.Printing.PrinterSettings> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9cf5-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9cf5-110">See Also</span></span>  
 [<span data-ttu-id="f9cf5-111">Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9cf5-111">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [<span data-ttu-id="f9cf5-112">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9cf5-112">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
