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
ms.openlocfilehash: c2252ccf1c8fec0dcaba634e6da093ab976ce1f6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614767"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="4c365-102">Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="4c365-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="4c365-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek mohl zobrazit až 12 měsíců po jednom.</span><span class="sxs-lookup"><span data-stu-id="4c365-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="4c365-104">Ve výchozím nastavení ovládací prvek zobrazuje pouze jeden měsíc, ale můžete určit, kolik měsíců se zobrazí a jak jsou uspořádány v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="4c365-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="4c365-105">Pokud změníte rozměry kalendáře, ovládací prvek svou velikost, proto ujistěte se, že je dostatek volného místa ve formuláři pro nové dimenze.</span><span class="sxs-lookup"><span data-stu-id="4c365-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="4c365-106">Chcete-li zobrazit více měsíců</span><span class="sxs-lookup"><span data-stu-id="4c365-106">To display multiple months</span></span>  
  
- <span data-ttu-id="4c365-107">Nastavte <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> na počet měsíců k zobrazení vodorovně a svisle.</span><span class="sxs-lookup"><span data-stu-id="4c365-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4c365-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c365-108">See also</span></span>

- [<span data-ttu-id="4c365-109">Ovládací prvek MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="4c365-109">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="4c365-110">Postupy: Vyberte rozsah dat v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="4c365-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="4c365-111">Postupy: Změna vzhledu Windows Forms MonthCalendar ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="4c365-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
