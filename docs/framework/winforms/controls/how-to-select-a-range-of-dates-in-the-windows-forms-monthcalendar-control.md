---
title: 'Postupy: Vyberte rozsah dat v ovládacím prvku Windows Forms MonthCalendar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
ms.openlocfilehash: 4c7100f77c313d219cfd4cceff5ae3015eae4c18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558446"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Postupy: Vyberte rozsah dat v ovládacím prvku Windows Forms MonthCalendar
Důležitou funkcí Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek je, že uživatel může vybrat rozsah. Tato funkce je vylepšením oproti funkci Výběr data <xref:System.Windows.Forms.DateTimePicker> ovládací prvek, který pouze umožňuje uživateli vybrat hodnotu jednoho data a času. Můžete nastavit rozsah kalendářních dat nebo získat oblast výběru nastaven uživatelem s použitím vlastnosti <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku. Následující příklad kódu ukazuje, jak nastavit oblast výběru.  
  
### <a name="to-select-a-range-of-dates"></a>Vybrat rozsah kalendářních dat  
  
1.  Vytvoření <xref:System.DateTime> objekty, které představují první a poslední datum v rozsahu.  
  
    ```vb  
    Dim projectStart As Date = New DateTime(2001, 2, 13)  
    Dim projectEnd As Date = New DateTime(2001, 2, 28)  
    ```  
  
    ```csharp  
    DateTime projectStart = new DateTime(2001, 2, 13);  
    DateTime projectEnd = new DateTime(2001, 2, 28);  
    ```  
  
    ```cpp  
    DateTime projectStart = DateTime(2001, 2, 13);  
    DateTime projectEnd = DateTime(2001, 2, 28);  
    ```  
  
2.  Nastavte <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> vlastnost.  
  
    ```vb  
    MonthCalendar1.SelectionRange = New SelectionRange(projectStart, projectEnd)  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionRange = new SelectionRange(projectStart, projectEnd);  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionRange = gcnew  
       SelectionRange(projectStart, projectEnd);  
    ```  
  
     – nebo –  
  
     Nastavte <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> a <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> vlastnosti.  
  
    ```vb  
    MonthCalendar1.SelectionStart = projectStart  
    MonthCalendar1.SelectionEnd = projectEnd  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionStart = projectStart;  
    monthCalendar1.SelectionEnd = projectEnd;  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionStart = projectStart;  
    monthCalendar1->SelectionEnd = projectEnd;  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Ovládací prvek MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
- [Postupy: Změna vzhledu Windows Forms MonthCalendar ovládacího prvku](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
- [Postupy: Zobrazení konkrétních dnů Bold s Windows Forms MonthCalendar – ovládací prvek](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
