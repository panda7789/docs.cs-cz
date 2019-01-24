---
title: 'Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar'
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
ms.openlocfilehash: 164369ab1a94249470b57e546db64be8e17b99bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582029"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="35501-102">Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="35501-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="35501-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek mohl zobrazit až 12 měsíců po jednom.</span><span class="sxs-lookup"><span data-stu-id="35501-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="35501-104">Ve výchozím nastavení ovládací prvek zobrazuje pouze jeden měsíc, ale můžete určit, kolik měsíců se zobrazí a jak jsou uspořádány v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="35501-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="35501-105">Pokud změníte rozměry kalendáře, ovládací prvek svou velikost, proto ujistěte se, že je dostatek volného místa ve formuláři pro nové dimenze.</span><span class="sxs-lookup"><span data-stu-id="35501-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="35501-106">Chcete-li zobrazit více měsíců</span><span class="sxs-lookup"><span data-stu-id="35501-106">To display multiple months</span></span>  
  
-   <span data-ttu-id="35501-107">Nastavte <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> na počet měsíců k zobrazení vodorovně a svisle.</span><span class="sxs-lookup"><span data-stu-id="35501-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="35501-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35501-108">See also</span></span>
- [<span data-ttu-id="35501-109">Ovládací prvek MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="35501-109">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="35501-110">Postupy: Vyberte rozsah dat v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="35501-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="35501-111">Postupy: Změna vzhledu Windows Forms MonthCalendar ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="35501-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
