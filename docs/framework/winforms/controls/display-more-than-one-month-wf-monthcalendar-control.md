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
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="d022f-102">Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="d022f-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="d022f-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.MonthCalendar> se může zobrazit po dobu až 12 měsíců najednou.</span><span class="sxs-lookup"><span data-stu-id="d022f-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="d022f-104">Ve výchozím nastavení se ovládací prvek zobrazí jenom jeden měsíc, ale můžete zadat, kolik měsíců se zobrazí a jak se uspořádají v rámci ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d022f-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="d022f-105">Když změníte rozměry kalendáře, změní se velikost ovládacího prvku, takže se ujistěte, že je ve formuláři dostatek místa pro nové rozměry.</span><span class="sxs-lookup"><span data-stu-id="d022f-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="d022f-106">Zobrazení více měsíců</span><span class="sxs-lookup"><span data-stu-id="d022f-106">To display multiple months</span></span>  
  
- <span data-ttu-id="d022f-107">Nastavte vlastnost <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> na počet měsíců, které se mají zobrazit vodorovně a svisle.</span><span class="sxs-lookup"><span data-stu-id="d022f-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d022f-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="d022f-108">See also</span></span>

- [<span data-ttu-id="d022f-109">Ovládací prvek MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="d022f-109">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="d022f-110">Postupy: Výběr rozsahu kalendářních dat v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="d022f-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="d022f-111">Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="d022f-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
