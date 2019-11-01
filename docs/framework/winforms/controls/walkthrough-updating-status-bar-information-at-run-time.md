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
ms.openlocfilehash: f1d22079dfa3a6452efb74ef57530bb43e059a4a
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197098"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="a5935-102">Návod: Aktualizace informací stavového řádku za běhu</span><span class="sxs-lookup"><span data-stu-id="a5935-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
> <span data-ttu-id="a5935-103">Ovládací prvky <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> nahrazují a přidávají funkce ovládacím prvkům <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel>; ovládací prvky <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> se však uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="a5935-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="a5935-104">Program často zavolá za účelem dynamické aktualizace obsahu panelů stavového řádku v době běhu na základě změn stavu aplikace nebo jiné interakce uživatele.</span><span class="sxs-lookup"><span data-stu-id="a5935-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="a5935-105">To je běžný způsob, jak uživatele signalizovat, že jsou povolené klíče, jako je například Caps Lock, NUM LOCK nebo SCROLL LOCK, nebo aby jako pohodlný odkaz poskytovaly datum nebo hodiny.</span><span class="sxs-lookup"><span data-stu-id="a5935-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="a5935-106">V následujícím příkladu použijete instanci třídy <xref:System.Windows.Forms.StatusBarPanel> k hostování hodin.</span><span class="sxs-lookup"><span data-stu-id="a5935-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="a5935-107">Získání stavového řádku připraveného k aktualizaci</span><span class="sxs-lookup"><span data-stu-id="a5935-107">To get the status bar ready for updating</span></span>  
  
1. <span data-ttu-id="a5935-108">Vytvoří nový formulář Windows.</span><span class="sxs-lookup"><span data-stu-id="a5935-108">Create a new Windows form.</span></span>  
  
2. <span data-ttu-id="a5935-109">Přidejte ovládací prvek <xref:System.Windows.Forms.StatusBar> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="a5935-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="a5935-110">Podrobnosti naleznete v tématu [How to: Add Controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a5935-110">For details, see [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
3. <span data-ttu-id="a5935-111">Přidejte panel stavového řádku do ovládacího prvku <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="a5935-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="a5935-112">Podrobnosti najdete v tématu [Postup: přidání panelů do ovládacího prvku](how-to-add-panels-to-a-statusbar-control.md)stavový řádek.</span><span class="sxs-lookup"><span data-stu-id="a5935-112">For details, see [How to: Add Panels to a StatusBar Control](how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4. <span data-ttu-id="a5935-113">Pro ovládací prvek <xref:System.Windows.Forms.StatusBar>, který jste přidali do formuláře, nastavte vlastnost <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="a5935-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5. <span data-ttu-id="a5935-114">Přidejte do formuláře komponentu model Windows Forms <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="a5935-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a5935-115">Komponenta model Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> je navržena pro model Windows Forms prostředí.</span><span class="sxs-lookup"><span data-stu-id="a5935-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="a5935-116">Pokud potřebujete časovač, který je vhodný pro serverové prostředí, přečtěte si téma [Úvod k časovačům založeným na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a5935-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
6. <span data-ttu-id="a5935-117">Vlastnost <xref:System.Windows.Forms.Timer.Enabled%2A> nastavte na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="a5935-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7. <span data-ttu-id="a5935-118">Nastavte vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> <xref:System.Windows.Forms.Timer> na 30000.</span><span class="sxs-lookup"><span data-stu-id="a5935-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a5935-119">Vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> komponenty <xref:System.Windows.Forms.Timer> je nastavená na 30 sekund (30 000 milisekund), aby se zajistilo, že se v zobrazeném čase projeví přesné časy.</span><span class="sxs-lookup"><span data-stu-id="a5935-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="a5935-120">Implementace časovače k aktualizaci stavového řádku</span><span class="sxs-lookup"><span data-stu-id="a5935-120">To implement the timer to update the status bar</span></span>  
  
1. <span data-ttu-id="a5935-121">Vložte následující kód do obslužné rutiny události součásti <xref:System.Windows.Forms.Timer> pro aktualizaci panelu ovládacího prvku <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="a5935-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
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
  
     <span data-ttu-id="a5935-122">V tuto chvíli jste připraveni spustit aplikaci a sledovat, jak se na panelu stavového řádku spouští hodiny.</span><span class="sxs-lookup"><span data-stu-id="a5935-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="a5935-123">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="a5935-123">To test the application</span></span>  
  
1. <span data-ttu-id="a5935-124">Spusťte ladění aplikace a stisknutím klávesy F5 ji spusťte.</span><span class="sxs-lookup"><span data-stu-id="a5935-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="a5935-125">Podrobnosti o ladění naleznete v tématu [ladění v aplikaci Visual Studio](/visualstudio/debugger/debugger-feature-tour).</span><span class="sxs-lookup"><span data-stu-id="a5935-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugger-feature-tour).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a5935-126">Bude trvat přibližně 30 sekund, než se hodiny zobrazí ve stavovém řádku.</span><span class="sxs-lookup"><span data-stu-id="a5935-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="a5935-127">Tato možnost získá nejpřesnější čas.</span><span class="sxs-lookup"><span data-stu-id="a5935-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="a5935-128">Pokud naopak chcete, aby se hodiny zobrazovaly dříve, můžete snížit hodnotu vlastnosti <xref:System.Windows.Forms.Timer.Interval%2A>, kterou jste nastavili v kroku 7 v předchozím postupu.</span><span class="sxs-lookup"><span data-stu-id="a5935-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5935-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5935-129">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="a5935-130">Postupy: Přidání panelů do ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="a5935-130">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)
- [<span data-ttu-id="a5935-131">Postupy: Určení panelu v ovládacím prvku Windows Forms StatusBar označeného kliknutím</span><span class="sxs-lookup"><span data-stu-id="a5935-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="a5935-132">Přehled ovládacího prvku StatusBar</span><span class="sxs-lookup"><span data-stu-id="a5935-132">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
