---
title: "Návod: Aktualizace informací stavového řádku za běhu"
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
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8253d1d04d2bf2a70076ffb003eb27be2eb47d46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="b48ce-102">Návod: Aktualizace informací stavového řádku za běhu</span><span class="sxs-lookup"><span data-stu-id="b48ce-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="b48ce-103"><xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkcí do <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky jsou uchovány pro zpětnou kompatibilitu a budoucí použití, pokud jste Vyberte.</span><span class="sxs-lookup"><span data-stu-id="b48ce-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="b48ce-104">Často bude program volání pro aktualizaci obsahu stav panelu panelů dynamicky za běhu, na základě změn stavu aplikace nebo jiných interakci s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="b48ce-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="b48ce-105">Toto je běžným způsobem uživatelé signál, že jsou povoleny klíče například klávesy CAPS LOCK, NUMLOCK nebo SCROLL LOCK, nebo zadejte datum nebo hodiny jako pohodlný odkaz.</span><span class="sxs-lookup"><span data-stu-id="b48ce-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="b48ce-106">V následujícím příkladu použijete instanci <xref:System.Windows.Forms.StatusBarPanel> třída pro hostitele hodiny.</span><span class="sxs-lookup"><span data-stu-id="b48ce-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="b48ce-107">Připravit pro aktualizace stavového řádku</span><span class="sxs-lookup"><span data-stu-id="b48ce-107">To get the status bar ready for updating</span></span>  
  
1.  <span data-ttu-id="b48ce-108">Vytvoření nového formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="b48ce-108">Create a new Windows form.</span></span>  
  
2.  <span data-ttu-id="b48ce-109">Přidat <xref:System.Windows.Forms.StatusBar> ovládacího prvku do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="b48ce-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="b48ce-110">Podrobnosti najdete v tématu [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b48ce-110">For details, see [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
3.  <span data-ttu-id="b48ce-111">Přidat panel panelu Stav pro vaše <xref:System.Windows.Forms.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b48ce-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="b48ce-112">Podrobnosti najdete v tématu [postupy: přidání panelů do ovládacího prvku StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).</span><span class="sxs-lookup"><span data-stu-id="b48ce-112">For details, see [How to: Add Panels to a StatusBar Control](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4.  <span data-ttu-id="b48ce-113">Pro <xref:System.Windows.Forms.StatusBar> řízení, které jste přidali do svého formuláře nastavené <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="b48ce-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5.  <span data-ttu-id="b48ce-114">Přidat Windows Forms <xref:System.Windows.Forms.Timer> součásti pro formulář.</span><span class="sxs-lookup"><span data-stu-id="b48ce-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b48ce-115">Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> součásti je určen pro prostředí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b48ce-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="b48ce-116">Pokud potřebujete časovač, který je vhodný pro prostředí serveru, najdete v části [Úvod do serverové časovače](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="b48ce-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
6.  <span data-ttu-id="b48ce-117">Nastavte <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="b48ce-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7.  <span data-ttu-id="b48ce-118">Nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost <xref:System.Windows.Forms.Timer> na 30000.</span><span class="sxs-lookup"><span data-stu-id="b48ce-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b48ce-119"><xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost <xref:System.Windows.Forms.Timer> součást je nastaven na 30 sekund (30 000 milisekund) zajistit, že přesný čas se projeví v čase, zobrazí.</span><span class="sxs-lookup"><span data-stu-id="b48ce-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="b48ce-120">K implementaci časovače aktualizace stavového řádku</span><span class="sxs-lookup"><span data-stu-id="b48ce-120">To implement the timer to update the status bar</span></span>  
  
1.  <span data-ttu-id="b48ce-121">Vložte následující kód do obslužné rutiny události z <xref:System.Windows.Forms.Timer> součást aktualizovat na panelu <xref:System.Windows.Forms.StatusBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b48ce-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
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
  
     <span data-ttu-id="b48ce-122">V tomto okamžiku jste připraveni ke spuštění aplikace a sledovat hodiny spuštěné v panelu panelu stavu.</span><span class="sxs-lookup"><span data-stu-id="b48ce-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="b48ce-123">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="b48ce-123">To test the application</span></span>  
  
1.  <span data-ttu-id="b48ce-124">Ladění aplikace a stiskněte klávesu F5 a spusťte ho.</span><span class="sxs-lookup"><span data-stu-id="b48ce-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="b48ce-125">Podrobnosti o ladění najdete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="b48ce-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b48ce-126">To bude trvat přibližně 30 sekund pro hodiny se objeví ve stavovém řádku.</span><span class="sxs-lookup"><span data-stu-id="b48ce-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="b48ce-127">Toto je získat nejpřesnější čas možné.</span><span class="sxs-lookup"><span data-stu-id="b48ce-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="b48ce-128">Pokud naopak Pokud chcete, aby hodiny zobrazí dříve, můžete snížit hodnotu <xref:System.Windows.Forms.Timer.Interval%2A> vlastností nastavenou v kroku 7 v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="b48ce-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b48ce-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="b48ce-129">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="b48ce-130">Postupy: Přidání panelů do ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="b48ce-130">How to: Add Panels to a StatusBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 [<span data-ttu-id="b48ce-131">Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="b48ce-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [<span data-ttu-id="b48ce-132">Přehled ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="b48ce-132">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
