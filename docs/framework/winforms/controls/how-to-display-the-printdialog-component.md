---
title: "Postupy: Zobrazení součásti PrintDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e1162a4e926d5be35f8f7bb7cdeb92264f293aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="18575-102">Postupy: Zobrazení součásti PrintDialog</span><span class="sxs-lookup"><span data-stu-id="18575-102">How to: Display the PrintDialog Component</span></span>
<span data-ttu-id="18575-103"><xref:System.Windows.Forms.PrintDialog> Součást je standardní tiskové dialogové okno, mnoho uživatelů bude znát.</span><span class="sxs-lookup"><span data-stu-id="18575-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="18575-104">Protože uživatelé budou okamžitě vyhovuje, je výhodné pro použití <xref:System.Windows.Forms.PrintDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="18575-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
### <a name="to-display-the-printdialog-component"></a><span data-ttu-id="18575-105">K zobrazení součásti PrintDialog</span><span class="sxs-lookup"><span data-stu-id="18575-105">To display the PrintDialog component</span></span>  
  
-   <span data-ttu-id="18575-106">Volání <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda z kódu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="18575-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>  
  
     <span data-ttu-id="18575-107">Jakmile se zobrazí komponentu, uživatelé budou komunikovat s, nastavení vlastností tiskové úlohy.</span><span class="sxs-lookup"><span data-stu-id="18575-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="18575-108">Tyto jsou uloženy ve <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` – třída (a <xref:System.Drawing.Printing.PageSettings> třídy, pokud uživatel přistoupí k [PageSetupDialog – komponenta](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) prostřednictvím <xref:System.Windows.Forms.PrintDialog> součásti) spojené s danou tiskovou úlohu.</span><span class="sxs-lookup"><span data-stu-id="18575-108">These are saved in the <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="18575-109">Potom můžete provést volání do vlastností že nastavují k určení specifika tiskové úlohy.</span><span class="sxs-lookup"><span data-stu-id="18575-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18575-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="18575-110">See Also</span></span>  
 [<span data-ttu-id="18575-111">Postupy: Vytvoření tiskových úloh standardní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18575-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [<span data-ttu-id="18575-112">Postupy: zachycení uživatelského vstupu z komponenty PrintDialog za běhu</span><span class="sxs-lookup"><span data-stu-id="18575-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [<span data-ttu-id="18575-113">Printpreviewdialog – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="18575-113">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="18575-114">PrintDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="18575-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [<span data-ttu-id="18575-115">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18575-115">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="18575-116">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18575-116">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
