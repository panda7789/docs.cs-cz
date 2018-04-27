---
title: 'Postupy: Změna ovládacího prvku Windows Forms MonthCalendar&#39;s vzhledu'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d2a3f12368d5215f7fe7611aa2f06e6b0fb1192
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a><span data-ttu-id="07e3c-102">Postupy: Změna ovládacího prvku Windows Forms MonthCalendar&#39;s vzhledu</span><span class="sxs-lookup"><span data-stu-id="07e3c-102">How to: Change the Windows Forms MonthCalendar Control&#39;s Appearance</span></span>
<span data-ttu-id="07e3c-103">Windows Forms <xref:System.Windows.Forms.MonthCalendar> řízení umožňuje přizpůsobení vzhledu kalendáře mnoha způsoby.</span><span class="sxs-lookup"><span data-stu-id="07e3c-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control allows you to customize the calendar's appearance in many ways.</span></span> <span data-ttu-id="07e3c-104">Můžete například nastavit barevné schéma a vyberte k zobrazení nebo skrytí čísla týdne a aktuálním datem.</span><span class="sxs-lookup"><span data-stu-id="07e3c-104">For example, you can set the color scheme and choose to display or hide week numbers and the current date.</span></span>  
  
### <a name="to-change-the-month-calendars-color-scheme"></a><span data-ttu-id="07e3c-105">Chcete-li změnit barevné schéma měsíční kalendář</span><span class="sxs-lookup"><span data-stu-id="07e3c-105">To change the month calendar's color scheme</span></span>  
  
-   <span data-ttu-id="07e3c-106">Nastavte vlastnosti, jako je třeba <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> a <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="07e3c-106">Set properties such as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> and <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span></span> <span data-ttu-id="07e3c-107"><xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Vlastnosti také určuje barvu písma pro dny v týdnu.</span><span class="sxs-lookup"><span data-stu-id="07e3c-107">The <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> property also determines the font color for the days of the week.</span></span> <span data-ttu-id="07e3c-108"><xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Vlastnost určuje barvu kalendářních dat, které předcházet a postupujte podle zobrazených měsíc nebo měsíce.</span><span class="sxs-lookup"><span data-stu-id="07e3c-108">The <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> property determines the color of the dates that precede and follow the displayed month or months.</span></span>  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="07e3c-109">Spouští se systémem Windows Vista a v závislosti na motiv, nastavení některé vlastnosti nemusí Změna vzhledu kalendáře.</span><span class="sxs-lookup"><span data-stu-id="07e3c-109">Starting with Windows Vista and depending on the theme, setting some properties might not change the appearance of the calendar.</span></span> <span data-ttu-id="07e3c-110">Například pokud Windows je nastavena pro použití motivu Aero, nastavení <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, nebo <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> vlastnosti nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="07e3c-110">For example, if Windows is set to use the Aero theme, setting the <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, or <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> properties has no effect.</span></span> <span data-ttu-id="07e3c-111">Je to proto, že je aktualizovaná verze kalendáře vykreslen vzhledově odvozený v době běhu z aktuálního motivu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="07e3c-111">This is because an updated version of the calendar is rendered with an appearance that is derived at run time from the current operating system theme.</span></span> <span data-ttu-id="07e3c-112">Pokud chcete použít tyto vlastnosti a povolit v předchozích verzích kalendáře, můžete zakázat vizuální styly pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="07e3c-112">If you want to use these properties and enable the earlier version of the calendar, you can disable visual styles for your application.</span></span> <span data-ttu-id="07e3c-113">Zakázání vizuální styly může ovlivnit vzhled a chování další ovládací prvky v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="07e3c-113">Disabling visual styles might affect the appearance and behavior of other controls in your application.</span></span> <span data-ttu-id="07e3c-114">Zakázání stylů v jazyce Visual Basic, otevřete v Návrháři projektu a zrušte zaškrtnutí políčka **vizuální styly XP povolit** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="07e3c-114">To disable visual styles in Visual Basic, open the Project Designer and uncheck the **Enable XP visual styles** check box.</span></span> <span data-ttu-id="07e3c-115">Chcete-li zakázat vizuální styly v jazyce C#, otevřete Program.cs a komentář `Application.EnableVisualStyles();`.</span><span class="sxs-lookup"><span data-stu-id="07e3c-115">To disable visual styles in C#, open Program.cs and comment out `Application.EnableVisualStyles();`.</span></span> <span data-ttu-id="07e3c-116">Další informace o vizuální styly najdete v tématu [postupy: povolení vizuální styly XP Windows](http://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).</span><span class="sxs-lookup"><span data-stu-id="07e3c-116">For more information about visual styles, see [How to: Enable Windows XP Visual Styles](http://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).</span></span>  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a><span data-ttu-id="07e3c-117">Chcete-li zobrazit aktuální datum v dolní části ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="07e3c-117">To display the current date at the bottom of the control</span></span>  
  
-   <span data-ttu-id="07e3c-118">Nastavte <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="07e3c-118">Set the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> property to `true`.</span></span> <span data-ttu-id="07e3c-119">Následující příklad Přepne mezi zobrazení a vynechání dnešní datum, když je formulář dvakrát kliknete.</span><span class="sxs-lookup"><span data-stu-id="07e3c-119">The example below toggles between displaying and omitting today's date when the form is double-clicked.</span></span>  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     <span data-ttu-id="07e3c-120">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="07e3c-120">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a><span data-ttu-id="07e3c-121">Zobrazení čísla týdne</span><span class="sxs-lookup"><span data-stu-id="07e3c-121">To display week numbers</span></span>  
  
-   <span data-ttu-id="07e3c-122">Nastavte <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="07e3c-122">Set the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="07e3c-123">Tuto vlastnost lze nastavit v kódu nebo v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="07e3c-123">You can set this property either in code or in the Properties window.</span></span>  
  
     <span data-ttu-id="07e3c-124">Týden čísla se zobrazí v samotném sloupci nalevo od první den v týdnu.</span><span class="sxs-lookup"><span data-stu-id="07e3c-124">Week numbers appear in a separate column to the left of the first day of the week.</span></span>  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="07e3c-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="07e3c-125">See Also</span></span>  
 [<span data-ttu-id="07e3c-126">Ovládací prvek MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="07e3c-126">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="07e3c-127">Postupy: Výběr rozsahu kalendářních dat v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="07e3c-127">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="07e3c-128">Postupy: Tučné zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="07e3c-128">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [<span data-ttu-id="07e3c-129">Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="07e3c-129">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
