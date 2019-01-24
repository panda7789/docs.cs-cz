---
title: 'Postupy: Zobrazení konkrétních dnů Bold s Windows Forms MonthCalendar – ovládací prvek'
ms.date: 03/30/2017
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
ms.openlocfilehash: f310d5e30acffdd358bc5108f39102387289562e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547784"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="38382-102">Postupy: Zobrazení konkrétních dnů Bold s Windows Forms MonthCalendar – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="38382-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="38382-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek mohl zobrazit dnů tučně, jako jednotný data nebo na základě s opakováním.</span><span class="sxs-lookup"><span data-stu-id="38382-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="38382-104">Můžete tak učinit k přitažení pozornosti ke speciální kalendářních dat, jako je například svátků a o víkendech.</span><span class="sxs-lookup"><span data-stu-id="38382-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="38382-105">Tři vlastnosti řízení této funkce.</span><span class="sxs-lookup"><span data-stu-id="38382-105">Three properties control this feature.</span></span> <span data-ttu-id="38382-106"><xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> Vlastnost obsahuje jeden kalendářní data.</span><span class="sxs-lookup"><span data-stu-id="38382-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="38382-107"><xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> Vlastnost obsahuje kalendářní data zobrazená tučným písmem každý rok.</span><span class="sxs-lookup"><span data-stu-id="38382-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="38382-108"><xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> Vlastnost obsahuje kalendářní data zobrazená tučným písmem každý měsíc.</span><span class="sxs-lookup"><span data-stu-id="38382-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="38382-109">Každá z těchto vlastností obsahuje celou řadu <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="38382-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="38382-110">Chcete-li přidat nebo odebrat data z jednoho z těchto seznamů, musíte přidat nebo odebrat <xref:System.DateTime> objektu.</span><span class="sxs-lookup"><span data-stu-id="38382-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="38382-111">K tomu jsou zobrazeny tučným písmem</span><span class="sxs-lookup"><span data-stu-id="38382-111">To make a date appear in bold type</span></span>  
  
1.  <span data-ttu-id="38382-112">Vytvořte <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="38382-112">Create the <xref:System.DateTime> objects.</span></span>  
  
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
  
2.  <span data-ttu-id="38382-113">Tučné jedním datumovým voláním <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> metodu <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="38382-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
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
  
     <span data-ttu-id="38382-114">– nebo –</span><span class="sxs-lookup"><span data-stu-id="38382-114">–or–</span></span>  
  
     <span data-ttu-id="38382-115">Tučné sadu kalendářních dat všechny najednou tak, že vytvoříte pole <xref:System.DateTime> objekty a její přiřazení k jedné z vlastností.</span><span class="sxs-lookup"><span data-stu-id="38382-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="38382-116">Aby se data zobrazí v pravidelných písma</span><span class="sxs-lookup"><span data-stu-id="38382-116">To make a date appear in the regular font</span></span>  
  
1.  <span data-ttu-id="38382-117">Ujistěte se, jeden tučné datum zobrazí v pravidelných písma voláním <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="38382-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="38382-118">– nebo –</span><span class="sxs-lookup"><span data-stu-id="38382-118">–or–</span></span>  
  
     <span data-ttu-id="38382-119">Odebrat všechny tučné datum z jednoho z těchto tří seznamů voláním <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="38382-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  <span data-ttu-id="38382-120">Aktualizovat vzhled písma tak, že volání <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="38382-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="38382-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38382-121">See also</span></span>
- [<span data-ttu-id="38382-122">Ovládací prvek MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="38382-122">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="38382-123">Postupy: Vyberte rozsah dat v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="38382-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="38382-124">Postupy: Změna vzhledu Windows Forms MonthCalendar ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="38382-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
- [<span data-ttu-id="38382-125">Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="38382-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
