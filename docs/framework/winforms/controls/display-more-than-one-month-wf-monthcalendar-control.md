---
title: Zobrazení více než jednoho měsíce v ovládacím prvku MonthCalendar
ms.date: 03/30/2017
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
ms.openlocfilehash: 5d3925bc19ddcd67742f0ab8b5b2e45530820f38
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745897"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a>Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar
Ovládací prvek model Windows Forms <xref:System.Windows.Forms.MonthCalendar> se může zobrazit po dobu až 12 měsíců najednou. Ve výchozím nastavení se ovládací prvek zobrazí jenom jeden měsíc, ale můžete zadat, kolik měsíců se zobrazí a jak se uspořádají v rámci ovládacího prvku. Když změníte rozměry kalendáře, změní se velikost ovládacího prvku, takže se ujistěte, že je ve formuláři dostatek místa pro nové rozměry.  
  
### <a name="to-display-multiple-months"></a>Zobrazení více měsíců  
  
- Nastavte vlastnost <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> na počet měsíců, které se mají zobrazit vodorovně a svisle.  
  
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

- [Ovládací prvek MonthCalendar](monthcalendar-control-windows-forms.md)
- [Postupy: Výběr rozsahu kalendářních dat v ovládacím prvku Windows Forms MonthCalendar](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar](how-to-change-monthcalendar-control-appearance.md)
