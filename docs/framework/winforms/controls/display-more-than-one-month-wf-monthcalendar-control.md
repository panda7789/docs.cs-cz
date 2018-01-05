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
# <a name="how-to-display-more-than-one-month-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="f9231-102">Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="f9231-102">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="f9231-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek může zobrazovat až po dobu 12 měsíců najednou.</span><span class="sxs-lookup"><span data-stu-id="f9231-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control can display up to 12 months at a time.</span></span> <span data-ttu-id="f9231-104">Ve výchozím nastavení tento ovládací prvek zobrazí pouze jeden měsíc, ale můžete určit, kolik měsíců se zobrazí a jak jsou uspořádány do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f9231-104">By default, the control displays only one month, but you can specify how many months are displayed and how they are arranged within the control.</span></span> <span data-ttu-id="f9231-105">Když změníte dimenze kalendáře, se změnila velikost ovládacího prvku, proto ujistěte se, že je dostatek místa na formuláři pro nové dimenze.</span><span class="sxs-lookup"><span data-stu-id="f9231-105">When you change the calendar dimensions, the control is resized, so be sure there is enough room on the form for the new dimensions.</span></span>  
  
### <a name="to-display-multiple-months"></a><span data-ttu-id="f9231-106">Chcete-li zobrazit více měsíců</span><span class="sxs-lookup"><span data-stu-id="f9231-106">To display multiple months</span></span>  
  
-   <span data-ttu-id="f9231-107">Nastavte <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> vlastnost počet měsíců k zobrazení vodorovně a svisle.</span><span class="sxs-lookup"><span data-stu-id="f9231-107">Set the <xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A> property to the number of months to display horizontally and vertically.</span></span>  
  
    ```vb  
    MonthCalendar1.CalendarDimensions = New System.Drawing.Size (3,2)  
    ```  
  
    ```csharp  
    monthCalendar1.CalendarDimensions = new System.Drawing.Size (3,2);  
    ```  
  
    ```cpp  
    monthCalendar1->CalendarDimensions = System::Drawing::Size (3,2);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f9231-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9231-108">See Also</span></span>  
 [<span data-ttu-id="f9231-109">Ovládací prvek MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="f9231-109">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="f9231-110">Postupy: Výběr rozsahu kalendářních dat v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="f9231-110">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="f9231-111">Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="f9231-111">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)
