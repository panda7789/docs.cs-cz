---
title: 'Postupy: Výběr rozsahu dat v ovládacím prvku Windows Forms MonthCalendar'
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
ms.openlocfilehash: 0e032a6285c43d7e96c7d59444da6d6598bd8100
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129945"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="90683-102">Postupy: Výběr rozsahu dat v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="90683-102">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="90683-103">Důležitou funkcí Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek je, že uživatel může vybrat rozsah.</span><span class="sxs-lookup"><span data-stu-id="90683-103">An important feature of the Windows Forms <xref:System.Windows.Forms.MonthCalendar> control is that the user can select a range of dates.</span></span> <span data-ttu-id="90683-104">Tato funkce je vylepšením oproti funkci Výběr data <xref:System.Windows.Forms.DateTimePicker> ovládací prvek, který pouze umožňuje uživateli vybrat hodnotu jednoho data a času.</span><span class="sxs-lookup"><span data-stu-id="90683-104">This feature is an improvement over the date-selection feature of the <xref:System.Windows.Forms.DateTimePicker> control, which only enables the user to select a single date/time value.</span></span> <span data-ttu-id="90683-105">Můžete nastavit rozsah kalendářních dat nebo získat oblast výběru nastaven uživatelem s použitím vlastnosti <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="90683-105">You can set a range of dates or get a selection range set by the user by using properties of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span> <span data-ttu-id="90683-106">Následující příklad kódu ukazuje, jak nastavit oblast výběru.</span><span class="sxs-lookup"><span data-stu-id="90683-106">The following code example demonstrates how to set a selection range.</span></span>  
  
### <a name="to-select-a-range-of-dates"></a><span data-ttu-id="90683-107">Vybrat rozsah kalendářních dat</span><span class="sxs-lookup"><span data-stu-id="90683-107">To select a range of dates</span></span>  
  
1.  <span data-ttu-id="90683-108">Vytvoření <xref:System.DateTime> objekty, které představují první a poslední datum v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="90683-108">Create <xref:System.DateTime> objects that represent the first and last dates in a range.</span></span>  
  
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
  
2.  <span data-ttu-id="90683-109">Nastavte <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="90683-109">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> property.</span></span>  
  
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
  
     <span data-ttu-id="90683-110">– nebo –</span><span class="sxs-lookup"><span data-stu-id="90683-110">–or–</span></span>  
  
     <span data-ttu-id="90683-111">Nastavte <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> a <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="90683-111">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> and <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90683-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90683-112">See also</span></span>

- [<span data-ttu-id="90683-113">Ovládací prvek MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="90683-113">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="90683-114">Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="90683-114">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](how-to-change-monthcalendar-control-appearance.md)
- [<span data-ttu-id="90683-115">Postupy: Tučné zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="90683-115">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [<span data-ttu-id="90683-116">Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="90683-116">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
