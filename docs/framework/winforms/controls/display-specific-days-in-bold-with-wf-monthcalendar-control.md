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
ms.openlocfilehash: 27b19e47d108b9af43a6d8882264d62c726ffe56
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343260"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>Postupy: Tučné zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar
Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek mohl zobrazit dnů tučně, jako jednotný data nebo na základě s opakováním. Můžete tak učinit k přitažení pozornosti ke speciální kalendářních dat, jako je například svátků a o víkendech.  
  
 Tři vlastnosti řízení této funkce. <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A> Vlastnost obsahuje jeden kalendářní data. <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A> Vlastnost obsahuje kalendářní data zobrazená tučným písmem každý rok. <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A> Vlastnost obsahuje kalendářní data zobrazená tučným písmem každý měsíc. Každá z těchto vlastností obsahuje celou řadu <xref:System.DateTime> objekty. Chcete-li přidat nebo odebrat data z jednoho z těchto seznamů, musíte přidat nebo odebrat <xref:System.DateTime> objektu.  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>K tomu jsou zobrazeny tučným písmem  
  
1. Vytvořte <xref:System.DateTime> objekty.  
  
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
  
2. Tučné jedním datumovým voláním <xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A> metodu <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku.  
  
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
  
     Tučné sadu kalendářních dat všechny najednou tak, že vytvoříte pole <xref:System.DateTime> objekty a její přiřazení k jedné z vlastností.  
  
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
  
1. Ujistěte se, jeden tučné datum zobrazí v pravidelných písma voláním <xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A> metody.  
  
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
  
     Odebrat všechny tučné datum z jednoho z těchto tří seznamů voláním <xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>, <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A> metody.  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2. Aktualizovat vzhled písma tak, že volání <xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A> metody.  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek MonthCalendar](monthcalendar-control-windows-forms.md)
- [Postupy: Vyberte rozsah dat v ovládacím prvku Windows Forms MonthCalendar](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Postupy: Změna vzhledu Windows Forms MonthCalendar ovládacího prvku](how-to-change-monthcalendar-control-appearance.md)
- [Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar](display-more-than-one-month-wf-monthcalendar-control.md)
