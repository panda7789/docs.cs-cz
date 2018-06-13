---
title: 'Postupy: Zobrazení součásti PrintDialog'
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: d8765187522f8becf24b519434b7c170c1c755b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532184"
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="dac35-102">Postupy: Zobrazení součásti PrintDialog</span><span class="sxs-lookup"><span data-stu-id="dac35-102">How to: Display the PrintDialog Component</span></span>
<span data-ttu-id="dac35-103"><xref:System.Windows.Forms.PrintDialog> Součást je standardní tiskové dialogové okno, mnoho uživatelů bude znát.</span><span class="sxs-lookup"><span data-stu-id="dac35-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="dac35-104">Protože uživatelé budou okamžitě vyhovuje, je výhodné pro použití <xref:System.Windows.Forms.PrintDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="dac35-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
### <a name="to-display-the-printdialog-component"></a><span data-ttu-id="dac35-105">K zobrazení součásti PrintDialog</span><span class="sxs-lookup"><span data-stu-id="dac35-105">To display the PrintDialog component</span></span>  
  
-   <span data-ttu-id="dac35-106">Volání <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda z kódu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="dac35-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>  
  
     <span data-ttu-id="dac35-107">Jakmile se zobrazí komponentu, uživatelé budou komunikovat s, nastavení vlastností tiskové úlohy.</span><span class="sxs-lookup"><span data-stu-id="dac35-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="dac35-108">Tyto jsou uloženy ve <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` – třída (a <xref:System.Drawing.Printing.PageSettings> třídy, pokud uživatel přistoupí k [PageSetupDialog – komponenta](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) prostřednictvím <xref:System.Windows.Forms.PrintDialog> součásti) spojené s danou tiskovou úlohu.</span><span class="sxs-lookup"><span data-stu-id="dac35-108">These are saved in the <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="dac35-109">Potom můžete provést volání do vlastností že nastavují k určení specifika tiskové úlohy.</span><span class="sxs-lookup"><span data-stu-id="dac35-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac35-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="dac35-110">See Also</span></span>  
 [<span data-ttu-id="dac35-111">Postupy: Vytváření standardních tiskových úloh modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dac35-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [<span data-ttu-id="dac35-112">Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu</span><span class="sxs-lookup"><span data-stu-id="dac35-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [<span data-ttu-id="dac35-113">Ovládací prvek PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="dac35-113">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="dac35-114">Komponenta PrintDialog</span><span class="sxs-lookup"><span data-stu-id="dac35-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [<span data-ttu-id="dac35-115">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dac35-115">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="dac35-116">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="dac35-116">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
