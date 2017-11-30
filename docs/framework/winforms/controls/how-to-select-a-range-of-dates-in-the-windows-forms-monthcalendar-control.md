---
title: "Postupy: Výběr rozsahu dat v ovládacím prvku Windows Forms MonthCalendar"
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
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d6a8d156e6e9a8c5331bd3db1c8e584be5ac154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>Postupy: Výběr rozsahu dat v ovládacím prvku Windows Forms MonthCalendar
Důležitou součást Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek je, že si uživatel může vybrat rozsah kalendářních dat. Tato funkce představuje vylepšení funkce výběru data <xref:System.Windows.Forms.DateTimePicker> řízení, které pouze umožňuje uživateli vybrat hodnotu jedné datum a čas. Můžete nastavit rozsah kalendářních dat nebo získat výběr rozsahu nastavená uživatelem pomocí vlastnosti <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku. Následující příklad kódu ukazuje, jak nastavit výběr rozsahu.  
  
### <a name="to-select-a-range-of-dates"></a>Chcete-li vybrat rozsah kalendářních dat  
  
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
  
## <a name="see-also"></a>Viz také  
 [MonthCalendar – ovládací prvek](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Postupy: Změna vzhledu Windows Forms MonthCalendar ovládacího prvku](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [Postupy: zobrazení Bold konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar – ovládací prvek](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [Postupy: zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
