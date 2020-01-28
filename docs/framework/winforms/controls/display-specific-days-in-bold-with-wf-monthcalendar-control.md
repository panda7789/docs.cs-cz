---
title: Zobrazit konkrétní dny tučně pomocí ovládacího prvku MonthCalendar
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
ms.openlocfilehash: 377eb76f562fff20aae2136ddb7130516d2d76f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745878"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="b689d-102">Postupy: Tučné zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="b689d-102">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="b689d-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.MonthCalendar> může zobrazovat dny tučným písmem, a to buď jako jednotné datum, nebo na opakující se.</span><span class="sxs-lookup"><span data-stu-id="b689d-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display days in bold type, either as singular dates or on a repeating basis.</span></span> <span data-ttu-id="b689d-104">Můžete to udělat tak, abyste nakreslili pozornost na zvláštní data, jako jsou svátky a víkendy.</span><span class="sxs-lookup"><span data-stu-id="b689d-104">You might do this to draw attention to special dates, such as holidays and weekends.</span></span>  
  
 <span data-ttu-id="b689d-105">Tuto funkci řídí tři vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b689d-105">Three properties control this feature.</span></span> <span data-ttu-id="b689d-106">Vlastnost <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> obsahuje jednotlivá data.</span><span class="sxs-lookup"><span data-stu-id="b689d-106">The <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> property contains single dates.</span></span> <span data-ttu-id="b689d-107">Vlastnost <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> obsahuje data, která se zobrazují tučně každý rok.</span><span class="sxs-lookup"><span data-stu-id="b689d-107">The <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> property contains dates that appear in bold every year.</span></span> <span data-ttu-id="b689d-108">Vlastnost <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> obsahuje data, která se zobrazují tučně každý měsíc.</span><span class="sxs-lookup"><span data-stu-id="b689d-108">The <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> property contains dates that appear in bold every month.</span></span> <span data-ttu-id="b689d-109">Každá z těchto vlastností obsahuje pole objektů <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="b689d-109">Each of these properties contains an array of <xref:System.DateTime> objects.</span></span> <span data-ttu-id="b689d-110">Chcete-li přidat nebo odebrat datum z jednoho z těchto seznamů, je nutné přidat nebo odebrat objekt <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="b689d-110">To add or remove a date from one of these lists, you must add or remove a <xref:System.DateTime> object.</span></span>  
  
### <a name="to-make-a-date-appear-in-bold-type"></a><span data-ttu-id="b689d-111">Chcete-li zobrazit datum v tučném typu</span><span class="sxs-lookup"><span data-stu-id="b689d-111">To make a date appear in bold type</span></span>  
  
1. <span data-ttu-id="b689d-112">Vytvořte <xref:System.DateTime> objekty.</span><span class="sxs-lookup"><span data-stu-id="b689d-112">Create the <xref:System.DateTime> objects.</span></span>  
  
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
  
2. <span data-ttu-id="b689d-113">Vytvořte tučné jednoduché datum voláním metody <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>nebo <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> ovládacího prvku <xref:System.Windows.Forms.MonthCalendar>.</span><span class="sxs-lookup"><span data-stu-id="b689d-113">Make a single date bold by calling the <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> method of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span>  
  
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
  
     <span data-ttu-id="b689d-114">– nebo –</span><span class="sxs-lookup"><span data-stu-id="b689d-114">–or–</span></span>  
  
     <span data-ttu-id="b689d-115">Vytvořte sadu kalendářních dat na jednom místě tak, že vytvoříte pole objektů <xref:System.DateTime> a přiřadíte je k jedné z vlastností.</span><span class="sxs-lookup"><span data-stu-id="b689d-115">Make a set of dates bold all at once by creating an array of <xref:System.DateTime> objects and assigning it to one of the properties.</span></span>  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a><span data-ttu-id="b689d-116">Aby se zobrazilo datum v normálním písmu</span><span class="sxs-lookup"><span data-stu-id="b689d-116">To make a date appear in the regular font</span></span>  
  
1. <span data-ttu-id="b689d-117">Zajistěte, aby se v normálním písmu zobrazilo jedno tučné datum zavoláním metody <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>nebo <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A>.</span><span class="sxs-lookup"><span data-stu-id="b689d-117">Make a single bolded date appear in the regular font by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> method.</span></span>  
  
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
  
     <span data-ttu-id="b689d-118">– nebo –</span><span class="sxs-lookup"><span data-stu-id="b689d-118">–or–</span></span>  
  
     <span data-ttu-id="b689d-119">Odeberte všechna Tučná data z jednoho ze tří seznamů voláním metody <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>nebo <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A>.</span><span class="sxs-lookup"><span data-stu-id="b689d-119">Remove all the bolded dates from one of the three lists by calling the <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, or <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2. <span data-ttu-id="b689d-120">Aktualizujte vzhled písma voláním metody <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A>.</span><span class="sxs-lookup"><span data-stu-id="b689d-120">Update the appearance of the font by calling the <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> method.</span></span>  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b689d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b689d-121">See also</span></span>

- [<span data-ttu-id="b689d-122">Ovládací prvek MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="b689d-122">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="b689d-123">Postupy: Výběr rozsahu kalendářních dat v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="b689d-123">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="b689d-124">Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="b689d-124">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
- [<span data-ttu-id="b689d-125">Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="b689d-125">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
