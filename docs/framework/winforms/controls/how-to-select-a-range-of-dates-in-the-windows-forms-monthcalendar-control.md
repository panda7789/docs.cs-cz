---
title: Výběr rozsahu kalendářních dat v ovládacím prvku MonthCalendar
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
ms.openlocfilehash: bda96af21a8f86a54d5c0fe0204546b980076d26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732894"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Postupy: Výběr rozsahu dat v ovládacím prvku Windows Forms MonthCalendar
Důležitou funkcí ovládacího prvku model Windows Forms <xref:System.Windows.Forms.MonthCalendar> je to, že uživatel může vybrat rozsah kalendářních dat. Tato funkce je zdokonalená nad funkcí pro výběr data ovládacího prvku <xref:System.Windows.Forms.DateTimePicker>, která umožňuje uživateli vybrat jenom jednu hodnotu data a času. Můžete nastavit rozsah kalendářních dat nebo získat rozsah výběru nastavený uživatelem pomocí vlastností ovládacího prvku <xref:System.Windows.Forms.MonthCalendar>. Následující příklad kódu ukazuje, jak nastavit rozsah výběru.  
  
### <a name="to-select-a-range-of-dates"></a>Výběr rozsahu kalendářních dat  
  
1. Vytvoří <xref:System.DateTime> objekty, které reprezentují první a poslední kalendářní data v rozsahu.  
  
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
  
2. Nastavte vlastnost <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>.  
  
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
  
     Nastavte vlastnosti <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> a <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A>.  
  
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

- [Ovládací prvek MonthCalendar](monthcalendar-control-windows-forms.md)
- [Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar](how-to-change-monthcalendar-control-appearance.md)
- [Postupy: Tučné zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar](display-more-than-one-month-wf-monthcalendar-control.md)
