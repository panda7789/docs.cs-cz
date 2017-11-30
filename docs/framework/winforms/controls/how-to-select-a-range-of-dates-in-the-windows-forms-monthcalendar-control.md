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
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a><span data-ttu-id="b6b0f-102">Postupy: Výběr rozsahu dat v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="b6b0f-102">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>
<span data-ttu-id="b6b0f-103">Důležitou součást Windows Forms <xref:System.Windows.Forms.MonthCalendar> ovládací prvek je, že si uživatel může vybrat rozsah kalendářních dat.</span><span class="sxs-lookup"><span data-stu-id="b6b0f-103">An important feature of the Windows Forms <xref:System.Windows.Forms.MonthCalendar> control is that the user can select a range of dates.</span></span> <span data-ttu-id="b6b0f-104">Tato funkce představuje vylepšení funkce výběru data <xref:System.Windows.Forms.DateTimePicker> řízení, které pouze umožňuje uživateli vybrat hodnotu jedné datum a čas.</span><span class="sxs-lookup"><span data-stu-id="b6b0f-104">This feature is an improvement over the date-selection feature of the <xref:System.Windows.Forms.DateTimePicker> control, which only enables the user to select a single date/time value.</span></span> <span data-ttu-id="b6b0f-105">Můžete nastavit rozsah kalendářních dat nebo získat výběr rozsahu nastavená uživatelem pomocí vlastnosti <xref:System.Windows.Forms.MonthCalendar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b6b0f-105">You can set a range of dates or get a selection range set by the user by using properties of the <xref:System.Windows.Forms.MonthCalendar> control.</span></span> <span data-ttu-id="b6b0f-106">Následující příklad kódu ukazuje, jak nastavit výběr rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b6b0f-106">The following code example demonstrates how to set a selection range.</span></span>  
  
### <a name="to-select-a-range-of-dates"></a><span data-ttu-id="b6b0f-107">Chcete-li vybrat rozsah kalendářních dat</span><span class="sxs-lookup"><span data-stu-id="b6b0f-107">To select a range of dates</span></span>  
  
1.  <span data-ttu-id="b6b0f-108">Vytvoření <xref:System.DateTime> objekty, které představují první a poslední datum v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b6b0f-108">Create <xref:System.DateTime> objects that represent the first and last dates in a range.</span></span>  
  
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
  
2.  <span data-ttu-id="b6b0f-109">Nastavte <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b6b0f-109">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> property.</span></span>  
  
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
  
     <span data-ttu-id="b6b0f-110">– nebo –</span><span class="sxs-lookup"><span data-stu-id="b6b0f-110">–or–</span></span>  
  
     <span data-ttu-id="b6b0f-111">Nastavte <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> a <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b6b0f-111">Set the <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> and <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> properties.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b6b0f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6b0f-112">See Also</span></span>  
 [<span data-ttu-id="b6b0f-113">MonthCalendar – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b6b0f-113">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="b6b0f-114">Postupy: Změna vzhledu Windows Forms MonthCalendar ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="b6b0f-114">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 [<span data-ttu-id="b6b0f-115">Postupy: zobrazení Bold konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b6b0f-115">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [<span data-ttu-id="b6b0f-116">Postupy: zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="b6b0f-116">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
