---
title: "Postupy: Tučné zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar"
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
- calendars [Windows Forms], displaying dates in bold
- examples [Windows Forms], calendar controls
- GetDayBold event
- MonthCalendar control [Windows Forms], dates displayed in bold
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 141d943c4f4dfc3976e66e13e7c0975aba3f1687
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="75673-102">Postupy: Tučné zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="75673-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="75673-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek může zobrazit dnů tučným písmem jako singulární kalendářní data nebo na základě opakovaných.</span><span class="sxs-lookup"><span data-stu-id="75673-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="75673-104">Můžete takto například k upozornění speciální datum, jako je například svátků a víkendech.</span><span class="sxs-lookup"><span data-stu-id="75673-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="75673-105">Tři vlastnosti řízení této funkce.</span><span class="sxs-lookup"><span data-stu-id="75673-105">Three properties control this feature.</span></span> <span data-ttu-id="75673-106"><xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> Vlastnost obsahuje jeden kalendářní data.</span><span class="sxs-lookup"><span data-stu-id="75673-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="75673-107"><xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> Vlastnost obsahuje data, která se zobrazují tučným písmem každý rok.</span><span class="sxs-lookup"><span data-stu-id="75673-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="75673-108"><xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> Vlastnost obsahuje data, která se zobrazují tučným písmem každý měsíc.</span><span class="sxs-lookup"><span data-stu-id="75673-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="75673-109">Každý z těchto vlastností obsahuje pole <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="75673-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="75673-110">Chcete-li přidat nebo odebrat data z jednoho z těchto seznamů, musíte přidat nebo odebrat <xref:System.DateTime> objektu.</span><span class="sxs-lookup"><span data-stu-id="75673-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="75673-111">K tomu jsou zobrazeny tučným písmem</span><span class="sxs-lookup"><span data-stu-id="75673-111">To make a date appear in bold type</span></span>  
  
1.  <span data-ttu-id="75673-112">Vytvořte <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="75673-112">Create the <xref:System.DateTime> objects.</span></span>  
  
    ```vb  
    Dim myVacation1 As Date = New DateTime(2001, 6, 10)  
    Dim myVacation2 As Date = New DateTime(2001, 6, 17)  
    ```  
  
    ```csharp  
    DateTime myVacation1 = new DateTime(2001, 6, 10);  
    DateTime myVacation2 = new DateTime(2001, 6, 17);  
    ```  
  
    ```cpp  
    DateTime myVacation1 = DateTime(2001, 6, 10);  
    DateTime myVacation2 = DateTime(2001, 6, 17);  
    ```  
  
2.  <span data-ttu-id="75673-113">Tučně souběžného voláním <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> metodu <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="75673-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
    ```vb  
    MonthCalendar1.AddBoldedDate(myVacation1)  
    MonthCalendar1.AddBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.AddBoldedDate(myVacation1);  
    monthCalendar1.AddBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->AddBoldedDate(myVacation1);  
    monthCalendar1->AddBoldedDate(myVacation2);  
    ```  
  
     <span data-ttu-id="75673-114">– nebo –</span><span class="sxs-lookup"><span data-stu-id="75673-114">–or–</span></span>  
  
     <span data-ttu-id="75673-115">Tučně sadu kalendářních dat všechny najednou tak, že vytvoříte pole <xref:System.DateTime> objektů a jeho přiřazení k jedné z vlastností.</span><span class="sxs-lookup"><span data-stu-id="75673-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
    ```vb  
    Dim VacationDates As DateTime() = {myVacation1, myVacation2}  
    MonthCalendar1.BoldedDates = VacationDates  
    ```  
  
    ```csharp  
    DateTime[] VacationDates = {myVacation1, myVacation2};  
    monthCalendar1.BoldedDates = VacationDates;  
    ```  
  
    ```cpp  
    Array<DateTime>^ VacationDates = {myVacation1, myVacation2};  
    monthCalendar1->BoldedDates = VacationDates;  
    ```  
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="75673-116">Aby se data zobrazí v pravidelných písma</span><span class="sxs-lookup"><span data-stu-id="75673-116">To make a date appear in the regular font</span></span>  
  
1.  <span data-ttu-id="75673-117">Zkontrolujte datum jeden uveden tučně objeví v pravidelných písmo voláním <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="75673-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveBoldedDate(myVacation1)  
    MonthCalendar1.RemoveBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveBoldedDate(myVacation1);  
    monthCalendar1.RemoveBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveBoldedDate(myVacation1);  
    monthCalendar1->RemoveBoldedDate(myVacation2);  
    ```  
  
     <span data-ttu-id="75673-118">– nebo –</span><span class="sxs-lookup"><span data-stu-id="75673-118">–or–</span></span>  
  
     <span data-ttu-id="75673-119">Odeberte všechny tučné datum z jedné z těchto tří seznamů voláním <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="75673-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  <span data-ttu-id="75673-120">Aktualizujte vzhled písma tak, že volání <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="75673-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="75673-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="75673-121">See Also</span></span>  
 [<span data-ttu-id="75673-122">Ovládací prvek MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="75673-122">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="75673-123">Postupy: Výběr rozsahu kalendářních dat v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="75673-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="75673-124">Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="75673-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [<span data-ttu-id="75673-125">Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="75673-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
