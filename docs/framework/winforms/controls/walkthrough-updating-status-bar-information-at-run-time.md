---
title: 'Návod: Aktualizace informací stavového řádku za běhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
ms.openlocfilehash: 49722d5dadf694e8ee3037646652b921ddda3e91
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45558118"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="bb1ea-102">Návod: Aktualizace informací stavového řádku za běhu</span><span class="sxs-lookup"><span data-stu-id="bb1ea-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="bb1ea-103"><xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkce, které <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud jste Zvolte.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="bb1ea-104">Často program bude volat pro vás k aktualizaci obsahu stav panelu panelů dynamicky za běhu na základě změn stavu aplikace nebo jiných interakcí uživatele.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="bb1ea-105">Toto je běžný způsob signál uživatele, že jsou povolené kláves, jako jsou CAPS LOCK, NUM LOCK nebo SCROLL LOCK, nebo zadejte datum nebo čas jako pohodlný odkaz.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="bb1ea-106">V následujícím příkladu použijete instance <xref:System.Windows.Forms.StatusBarPanel> třídy k hostování hodin.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="bb1ea-107">Připravit na stavovém řádku pro aktualizaci</span><span class="sxs-lookup"><span data-stu-id="bb1ea-107">To get the status bar ready for updating</span></span>  
  
1.  <span data-ttu-id="bb1ea-108">Vytvoření nového formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-108">Create a new Windows form.</span></span>  
  
2.  <span data-ttu-id="bb1ea-109">Přidat <xref:System.Windows.Forms.StatusBar> ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="bb1ea-110">Podrobnosti najdete v tématu [postupy: Přidání ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="bb1ea-110">For details, see [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
3.  <span data-ttu-id="bb1ea-111">Přidat stav panelu panelu s vaší <xref:System.Windows.Forms.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="bb1ea-112">Podrobnosti najdete v tématu [postupy: přidání panelů do ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).</span><span class="sxs-lookup"><span data-stu-id="bb1ea-112">For details, see [How to: Add Panels to a StatusBar Control](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4.  <span data-ttu-id="bb1ea-113">Pro <xref:System.Windows.Forms.StatusBar> jste přidali do svého formuláře ovládací prvek nastavit <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5.  <span data-ttu-id="bb1ea-114">Přidání prvku Windows Forms <xref:System.Windows.Forms.Timer> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb1ea-115">Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> součásti je určen pro prostředí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="bb1ea-116">Pokud potřebujete časovač, který je vhodný pro prostředí serveru, přečtěte si [Úvod do serverových časovače](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="bb1ea-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
6.  <span data-ttu-id="bb1ea-117">Nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7.  <span data-ttu-id="bb1ea-118">Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost <xref:System.Windows.Forms.Timer> na 30000.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb1ea-119"><xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost <xref:System.Windows.Forms.Timer> komponenty nastavena na 30 sekund (30 000 milisekund) k zajištění, že v čase, zobrazí se projeví přesnému času.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="bb1ea-120">K implementaci časovače aktualizace stavového řádku</span><span class="sxs-lookup"><span data-stu-id="bb1ea-120">To implement the timer to update the status bar</span></span>  
  
1.  <span data-ttu-id="bb1ea-121">Vložte následující kód do obslužné rutiny události <xref:System.Windows.Forms.Timer> součásti na panelu aktualizovat <xref:System.Windows.Forms.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     <span data-ttu-id="bb1ea-122">V tuto chvíli jste připraveni ke spuštění aplikace a sledujte hodin spuštěna v panelu Stav panelu.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="bb1ea-123">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="bb1ea-123">To test the application</span></span>  
  
1.  <span data-ttu-id="bb1ea-124">Ladit aplikaci a stiskněte klávesu F5 a spusťte ho.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="bb1ea-125">Podrobnosti o ladění naleznete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="bb1ea-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb1ea-126">To bude trvat přibližně 30 sekund hodin se zobrazí ve stavovém řádku.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="bb1ea-127">Toto je získat nejpřesnější čas je to možné.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="bb1ea-128">Naopak, aby hodiny zobrazí dříve, můžete snížit hodnotu <xref:System.Windows.Forms.Timer.Interval%2A> vlastnosti, které jste nastavili v kroku 7 v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="bb1ea-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb1ea-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb1ea-129">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="bb1ea-130">Postupy: Přidání panelů do ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="bb1ea-130">How to: Add Panels to a StatusBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 [<span data-ttu-id="bb1ea-131">Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="bb1ea-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [<span data-ttu-id="bb1ea-132">Přehled ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="bb1ea-132">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
