---
title: 'Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: 5582624d881b2d8039bcd5e8ac45e548c7b38f57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929050"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a><span data-ttu-id="04585-102">Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="04585-102">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>
<span data-ttu-id="04585-103">Ovládací prvek <xref:System.Windows.Forms.MonthCalendar> model Windows Forms umožňuje přizpůsobit vzhled kalendáře mnoha způsoby.</span><span class="sxs-lookup"><span data-stu-id="04585-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control allows you to customize the calendar's appearance in many ways.</span></span> <span data-ttu-id="04585-104">Můžete například nastavit barevné schéma a zvolit zobrazení nebo skrytí čísel týdnů a aktuálního data.</span><span class="sxs-lookup"><span data-stu-id="04585-104">For example, you can set the color scheme and choose to display or hide week numbers and the current date.</span></span>  
  
### <a name="to-change-the-month-calendars-color-scheme"></a><span data-ttu-id="04585-105">Změna barevného schématu měsíčního kalendáře</span><span class="sxs-lookup"><span data-stu-id="04585-105">To change the month calendar's color scheme</span></span>  
  
- <span data-ttu-id="04585-106">Nastavte vlastnosti <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, jako jsou <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> a <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="04585-106">Set properties such as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> and <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span></span> <span data-ttu-id="04585-107"><xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Vlastnost také určuje barvu písma pro dny v týdnu.</span><span class="sxs-lookup"><span data-stu-id="04585-107">The <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> property also determines the font color for the days of the week.</span></span> <span data-ttu-id="04585-108"><xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Vlastnost určuje barvu kalendářních dat, která předchází, a následují po zobrazených měsících nebo měsících.</span><span class="sxs-lookup"><span data-stu-id="04585-108">The <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> property determines the color of the dates that precede and follow the displayed month or months.</span></span>  
  
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
    > <span data-ttu-id="04585-109">Počínaje systémem Windows Vista a v závislosti na motivu se může stát, že nastavením některých vlastností se nezmění vzhled kalendáře.</span><span class="sxs-lookup"><span data-stu-id="04585-109">Starting with Windows Vista and depending on the theme, setting some properties might not change the appearance of the calendar.</span></span> <span data-ttu-id="04585-110">Pokud je <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>například Windows nastavené na použití motivu Aero, nastavení vlastností, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>nebo <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="04585-110">For example, if Windows is set to use the Aero theme, setting the <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, or <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> properties has no effect.</span></span> <span data-ttu-id="04585-111">Je to proto, že aktualizovaná verze kalendáře je vykreslena s vzhled, který je odvozen v době běhu z aktuálního motivu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="04585-111">This is because an updated version of the calendar is rendered with an appearance that is derived at run time from the current operating system theme.</span></span> <span data-ttu-id="04585-112">Pokud chcete tyto vlastnosti použít a povolit starší verzi kalendáře, můžete pro svou aplikaci zakázat vizuální styly.</span><span class="sxs-lookup"><span data-stu-id="04585-112">If you want to use these properties and enable the earlier version of the calendar, you can disable visual styles for your application.</span></span> <span data-ttu-id="04585-113">Zakázání vizuálních stylů může mít vliv na vzhled a chování jiných ovládacích prvků v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="04585-113">Disabling visual styles might affect the appearance and behavior of other controls in your application.</span></span> <span data-ttu-id="04585-114">Chcete-li zakázat vizuální styly v Visual Basic, otevřete Návrháře projektu a zrušte zaškrtnuté políčko **Povolit vizuální styly pro XP** .</span><span class="sxs-lookup"><span data-stu-id="04585-114">To disable visual styles in Visual Basic, open the Project Designer and uncheck the **Enable XP visual styles** check box.</span></span> <span data-ttu-id="04585-115">Chcete-li zakázat vizuální C#styly v nástroji, otevřete program.cs `Application.EnableVisualStyles();`a přidejte komentář.</span><span class="sxs-lookup"><span data-stu-id="04585-115">To disable visual styles in C#, open Program.cs and comment out `Application.EnableVisualStyles();`.</span></span> <span data-ttu-id="04585-116">Další informace o vizuálních stylech naleznete v tématu [Povolení vizuálních stylů](/windows/desktop/controls/cookbook-overview).</span><span class="sxs-lookup"><span data-stu-id="04585-116">For more information about visual styles, see [Enabling Visual Styles](/windows/desktop/controls/cookbook-overview).</span></span>  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a><span data-ttu-id="04585-117">Zobrazení aktuálního data v dolní části ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="04585-117">To display the current date at the bottom of the control</span></span>  
  
- <span data-ttu-id="04585-118">Nastavte <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="04585-118">Set the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> property to `true`.</span></span> <span data-ttu-id="04585-119">Následující příklad přepíná mezi zobrazením a vynecháním dnešního data při dvojitém kliknutí na formulář.</span><span class="sxs-lookup"><span data-stu-id="04585-119">The example below toggles between displaying and omitting today's date when the form is double-clicked.</span></span>  
  
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
  
     <span data-ttu-id="04585-120">(Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="04585-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a><span data-ttu-id="04585-121">Zobrazení čísel týdnů</span><span class="sxs-lookup"><span data-stu-id="04585-121">To display week numbers</span></span>  
  
- <span data-ttu-id="04585-122">Nastavte <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="04585-122">Set the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="04585-123">Tuto vlastnost lze nastavit buď v kódu, nebo v okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="04585-123">You can set this property either in code or in the Properties window.</span></span>  
  
     <span data-ttu-id="04585-124">Čísla týdnů se zobrazí v samostatném sloupci nalevo od prvního dne v týdnu.</span><span class="sxs-lookup"><span data-stu-id="04585-124">Week numbers appear in a separate column to the left of the first day of the week.</span></span>  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="04585-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04585-125">See also</span></span>

- [<span data-ttu-id="04585-126">Ovládací prvek MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="04585-126">MonthCalendar Control</span></span>](monthcalendar-control-windows-forms.md)
- [<span data-ttu-id="04585-127">Postupy: Vyberte rozsah dat v ovládacím prvku model Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="04585-127">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [<span data-ttu-id="04585-128">Postupy: Zobrazit konkrétní dny tučně pomocí ovládacího prvku model Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="04585-128">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [<span data-ttu-id="04585-129">Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku model Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="04585-129">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](display-more-than-one-month-wf-monthcalendar-control.md)
