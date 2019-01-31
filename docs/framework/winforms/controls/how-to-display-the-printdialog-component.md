---
title: Postup zobrazení součásti PrintDialog
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: 198ae75d407bd1837033a1cc186d84ff972fdc2f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285152"
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="855c9-102">Postup zobrazení součásti PrintDialog</span><span class="sxs-lookup"><span data-stu-id="855c9-102">How to display the PrintDialog component</span></span>

<span data-ttu-id="855c9-103"><xref:System.Windows.Forms.PrintDialog> Součástí je standardní Windows dialogového okna Tisk pole, která bude zkušenosti s mnoha uživatelů.</span><span class="sxs-lookup"><span data-stu-id="855c9-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="855c9-104">Vzhledem k tomu, že uživatelé budou okamžitě vyhovuje, bylo by vhodné pro použití <xref:System.Windows.Forms.PrintDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="855c9-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>

## <a name="to-display-the-printdialog-component"></a><span data-ttu-id="855c9-105">K zobrazení součásti PrintDialog</span><span class="sxs-lookup"><span data-stu-id="855c9-105">To display the PrintDialog component</span></span>

- <span data-ttu-id="855c9-106">Volání <xref:System.Windows.Forms.Form.ShowDialog%2A> metodu z kódu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="855c9-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>

     <span data-ttu-id="855c9-107">Jakmile součást se zobrazí, uživatelé se s ní pracovat, nastavení vlastnosti tiskové úlohy.</span><span class="sxs-lookup"><span data-stu-id="855c9-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="855c9-108">Tyto jsou uložené v <xref:System.Drawing.Printing.PrinterSettings> třídu (a <xref:System.Drawing.Printing.PageSettings> třídy, když chce uživatel [PageSetupDialog – komponenta](pagesetupdialog-component-windows-forms.md) prostřednictvím <xref:System.Windows.Forms.PrintDialog> součásti) spojené s danou tiskovou úlohu.</span><span class="sxs-lookup"><span data-stu-id="855c9-108">These are saved in the  <xref:System.Drawing.Printing.PrinterSettings> class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="855c9-109">Potom může provést volání vlastností sady k určení, jaké jsou specifikace tiskové úlohy.</span><span class="sxs-lookup"><span data-stu-id="855c9-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>

## <a name="see-also"></a><span data-ttu-id="855c9-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="855c9-110">See also</span></span>

- [<span data-ttu-id="855c9-111">Postupy: Vytvoření tiskových úloh standardní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="855c9-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [<span data-ttu-id="855c9-112">Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu</span><span class="sxs-lookup"><span data-stu-id="855c9-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)
- [<span data-ttu-id="855c9-113">Ovládací prvek PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="855c9-113">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="855c9-114">Komponenta PrintDialog</span><span class="sxs-lookup"><span data-stu-id="855c9-114">PrintDialog Component</span></span>](printdialog-component-windows-forms.md)
- [<span data-ttu-id="855c9-115">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="855c9-115">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="855c9-116">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="855c9-116">Windows Forms Controls</span></span>](index.md)