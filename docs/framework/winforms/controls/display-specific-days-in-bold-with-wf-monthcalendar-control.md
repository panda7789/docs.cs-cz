---
title: 'Postupy: Tučné zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar'
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
ms.openlocfilehash: 0ee89fb4cfb6ddbf975eb0e85e7dd1bab30f08d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528528"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>Postupy: Tučné zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar
Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek může zobrazit dnů tučným písmem jako singulární kalendářní data nebo na základě opakovaných. Můžete takto například k upozornění speciální datum, jako je například svátků a víkendech.  
  
 Tři vlastnosti řízení této funkce. <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> Vlastnost obsahuje jeden kalendářní data. <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> Vlastnost obsahuje data, která se zobrazují tučným písmem každý rok. <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> Vlastnost obsahuje data, která se zobrazují tučným písmem každý měsíc. Každý z těchto vlastností obsahuje pole <xref:System.DateTime> objekty. Chcete-li přidat nebo odebrat data z jednoho z těchto seznamů, musíte přidat nebo odebrat <xref:System.DateTime> objektu.  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>K tomu jsou zobrazeny tučným písmem  
  
1.  Vytvořte <xref:System.DateTime> objekty.  
  
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
  
2.  Tučně souběžného voláním <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> metodu <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku.  
  
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
  
     – nebo –  
  
     Tučně sadu kalendářních dat všechny najednou tak, že vytvoříte pole <xref:System.DateTime> objektů a jeho přiřazení k jedné z vlastností.  
  
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
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a>Aby se data zobrazí v pravidelných písma  
  
1.  Zkontrolujte datum jeden uveden tučně objeví v pravidelných písmo voláním <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> metoda.  
  
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
  
     – nebo –  
  
     Odeberte všechny tučné datum z jedné z těchto tří seznamů voláním <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> metoda.  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  Aktualizujte vzhled písma tak, že volání <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> metoda.  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Postupy: Výběr rozsahu kalendářních dat v ovládacím prvku Windows Forms MonthCalendar](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
