---
title: "Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar"
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
- calendars [Windows Forms], formatting display
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], multiple months
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d197caa2-38a5-4cb4-acc3-562130c2ace3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c29ac094fb5149b4146701315f1458884a2701c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar
Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek může zobrazovat až po dobu 12 měsíců najednou. Ve výchozím nastavení tento ovládací prvek zobrazí pouze jeden měsíc, ale můžete určit, kolik měsíců se zobrazí a jak jsou uspořádány do ovládacího prvku. Když změníte dimenze kalendáře, se změnila velikost ovládacího prvku, proto ujistěte se, že je dostatek místa na formuláři pro nové dimenze.  
  
### <a name="to-display-multiple-months"></a>Chcete-li zobrazit více měsíců  
  
-   Nastavte <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> vlastnost počet měsíců k zobrazení vodorovně a svisle.  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek MonthCalendar](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Postupy: Výběr rozsahu kalendářních dat v ovládacím prvku Windows Forms MonthCalendar](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
