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
ms.openlocfilehash: 79100b52d8e0a5b651edb9d6555a4497287ed858
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209551"
---
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="8b7e9-102">Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="8b7e9-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="8b7e9-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek mohl zobrazit až 12 měsíců po jednom.</span><span class="sxs-lookup"><span data-stu-id="8b7e9-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="8b7e9-104">Ve výchozím nastavení ovládací prvek zobrazuje pouze jeden měsíc, ale můžete určit, kolik měsíců se zobrazí a jak jsou uspořádány v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="8b7e9-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="8b7e9-105">Pokud změníte rozměry kalendáře, ovládací prvek svou velikost, proto ujistěte se, že je dostatek volného místa ve formuláři pro nové dimenze.</span><span class="sxs-lookup"><span data-stu-id="8b7e9-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="8b7e9-106">Chcete-li zobrazit více měsíců</span><span class="sxs-lookup"><span data-stu-id="8b7e9-106">To display multiple months</span></span>  
  
-   <span data-ttu-id="8b7e9-107">Nastavte <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> na počet měsíců k zobrazení vodorovně a svisle.</span><span class="sxs-lookup"><span data-stu-id="8b7e9-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8b7e9-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b7e9-108">See also</span></span>

- [<span data-ttu-id="8b7e9-109">Ovládací prvek MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="8b7e9-109">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="8b7e9-110">Postupy: Vyberte rozsah dat v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="8b7e9-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="8b7e9-111">Postupy: Změna vzhledu Windows Forms MonthCalendar ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="8b7e9-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
