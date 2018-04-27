---
title: 'Postupy: Simulace událostí myši a klávesnice v kódu'
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
- keyboards [Windows Forms], event simulation
- user input [Windows Forms], simulating
- SendKeys [Windows Forms], using
- mouse clicks [Windows Forms], simulating
- mouse [Windows Forms], event simulation
ms.assetid: 6abcb67e-3766-4af2-9590-bf5dabd17e41
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d606c8dbe79b3ca1114f79cbf9eb7d4f17a05742
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a><span data-ttu-id="89cf1-102">Postupy: Simulace událostí myši a klávesnice v kódu</span><span class="sxs-lookup"><span data-stu-id="89cf1-102">How to: Simulate Mouse and Keyboard Events in Code</span></span>
<span data-ttu-id="89cf1-103">Windows Forms poskytuje několik možností pro simulaci prostřednictvím kódu programu myši a vstup z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="89cf1-103">Windows Forms provides several options for programmatically simulating mouse and keyboard input.</span></span> <span data-ttu-id="89cf1-104">Toto téma obsahuje přehled těchto možností.</span><span class="sxs-lookup"><span data-stu-id="89cf1-104">This topic provides an overview of these options.</span></span>  
  
## <a name="simulating-mouse-input"></a><span data-ttu-id="89cf1-105">Simulaci vstup myši</span><span class="sxs-lookup"><span data-stu-id="89cf1-105">Simulating Mouse Input</span></span>  
 <span data-ttu-id="89cf1-106">Nejlepší způsob, jak simulace událostí myši je volat `On` *EventName* metoda, která se vyvolá událost, myš, kterou chcete simulovat.</span><span class="sxs-lookup"><span data-stu-id="89cf1-106">The best way to simulate mouse events is to call the `On`*EventName* method that raises the mouse event you want to simulate.</span></span> <span data-ttu-id="89cf1-107">Tuto možnost obvykle je možné pouze v rámci vlastní ovládací prvky a formulářů, protože metody, které vyvolávání událostí jsou chráněné a nelze přistupovat mimo ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="89cf1-107">This option is usually possible only within custom controls and forms, because the methods that raise events are protected and cannot be accessed outside the control or form.</span></span> <span data-ttu-id="89cf1-108">Například následující kroky ukazují, jak k simulaci, kliknete pravým tlačítkem myši v kódu.</span><span class="sxs-lookup"><span data-stu-id="89cf1-108">For example, the following steps illustrate how to simulate clicking the right mouse button in code.</span></span>  
  
#### <a name="to-programmatically-click-the-right-mouse-button"></a><span data-ttu-id="89cf1-109">Prostřednictvím kódu programu kliknout pravým tlačítkem myši</span><span class="sxs-lookup"><span data-stu-id="89cf1-109">To programmatically click the right mouse button</span></span>  
  
1.  <span data-ttu-id="89cf1-110">Vytvoření <xref:System.Windows.Forms.MouseEventArgs> jejichž <xref:System.Windows.Forms.MouseEventArgs.Button%2A> je nastavena na <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="89cf1-110">Create a <xref:System.Windows.Forms.MouseEventArgs> whose <xref:System.Windows.Forms.MouseEventArgs.Button%2A> property is set to the <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> value.</span></span>  
  
2.  <span data-ttu-id="89cf1-111">Volání <xref:System.Windows.Forms.Control.OnMouseClick%2A> metoda pomocí této <xref:System.Windows.Forms.MouseEventArgs> jako argument.</span><span class="sxs-lookup"><span data-stu-id="89cf1-111">Call the <xref:System.Windows.Forms.Control.OnMouseClick%2A> method with this <xref:System.Windows.Forms.MouseEventArgs> as the argument.</span></span>  
  
 <span data-ttu-id="89cf1-112">Další informace o vlastních ovládacích prvcích najdete v tématu [vývoj ovládacích prvků Windows Forms v době návrhu](../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="89cf1-112">For more information on custom controls, see [Developing Windows Forms Controls at Design Time](../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span>  
  
 <span data-ttu-id="89cf1-113">Pro simulaci vstup z myši i jinými způsoby.</span><span class="sxs-lookup"><span data-stu-id="89cf1-113">There are other ways to simulate mouse input.</span></span> <span data-ttu-id="89cf1-114">Například můžete programově nastavit řízení vlastnost, která představuje stav, který se obvykle nastavuje prostřednictvím vstup z myši (například <xref:System.Windows.Forms.CheckBox.Checked%2A> vlastnost <xref:System.Windows.Forms.CheckBox> ovládací prvek), nebo přímo volat delegáta, který je připojen k události je Chcete simulovat.</span><span class="sxs-lookup"><span data-stu-id="89cf1-114">For example, you can programmatically set a control property that represents a state that is typically set through mouse input (such as the <xref:System.Windows.Forms.CheckBox.Checked%2A> property of the <xref:System.Windows.Forms.CheckBox> control), or you can directly call the delegate that is attached to the event you want to simulate.</span></span>  
  
## <a name="simulating-keyboard-input"></a><span data-ttu-id="89cf1-115">Simulaci vstup z klávesnice</span><span class="sxs-lookup"><span data-stu-id="89cf1-115">Simulating Keyboard Input</span></span>  
 <span data-ttu-id="89cf1-116">I když můžete simulovat vstup z klávesnice s použitím strategie výše popsané pro vstup z myši, Windows Forms poskytuje taky <xref:System.Windows.Forms.SendKeys> třídu pro odesílání stisknutí kláves aplikace aktivní.</span><span class="sxs-lookup"><span data-stu-id="89cf1-116">Although you can simulate keyboard input by using the strategies discussed above for mouse input, Windows Forms also provides the <xref:System.Windows.Forms.SendKeys> class for sending keystrokes to the active application.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="89cf1-117">Pokud vaše aplikace je určená pro mezinárodní s různými klávesnice, použití <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> může vést k neočekávaným výsledkům yield a je nutno.</span><span class="sxs-lookup"><span data-stu-id="89cf1-117">If your application is intended for international use with a variety of keyboards, the use of <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> could yield unpredictable results and should be avoided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89cf1-118"><xref:System.Windows.Forms.SendKeys> Třída byla aktualizována pro rozhraní .NET Framework 3.0, aby jeho použití v aplikacích, které běží na systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="89cf1-118">The <xref:System.Windows.Forms.SendKeys> class has been updated for the .NET Framework 3.0 to enable its use in applications that run on Windows Vista.</span></span> <span data-ttu-id="89cf1-119">Rozšířené zabezpečení systému Windows Vista (označované jako řízení uživatelských účtů nebo nástroje Řízení uživatelských účtů) zabraňuje předchozí implementace z pracovní podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="89cf1-119">The enhanced security of Windows Vista (known as User Account Control or UAC) prevents the previous implementation from working as expected.</span></span>  
>   
>  <span data-ttu-id="89cf1-120"><xref:System.Windows.Forms.SendKeys> Třída je ohrožena útoky založenými na problémy načasování, kterým byly někteří vývojáři obejít.</span><span class="sxs-lookup"><span data-stu-id="89cf1-120">The <xref:System.Windows.Forms.SendKeys> class is susceptible to timing issues, which some developers have had to work around.</span></span> <span data-ttu-id="89cf1-121">Aktualizované implementace přesto náchylné k problémy načasování, ale je mírně rychlejší a může vyžadovat změny řešení.</span><span class="sxs-lookup"><span data-stu-id="89cf1-121">The updated implementation is still susceptible to timing issues, but is slightly faster and may require changes to the workarounds.</span></span> <span data-ttu-id="89cf1-122"><xref:System.Windows.Forms.SendKeys> Třídy pokusí nejdříve použít předchozí implementace a pokud to nepomůže, používá novou implementací.</span><span class="sxs-lookup"><span data-stu-id="89cf1-122">The <xref:System.Windows.Forms.SendKeys> class tries to use the previous implementation first, and if that fails, uses the new implementation.</span></span> <span data-ttu-id="89cf1-123">V důsledku toho <xref:System.Windows.Forms.SendKeys> třída může chovat jinak v různých operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="89cf1-123">As a result, the <xref:System.Windows.Forms.SendKeys> class may behave differently on different operating systems.</span></span> <span data-ttu-id="89cf1-124">Kromě toho, když <xref:System.Windows.Forms.SendKeys> třída používá nové implementace <xref:System.Windows.Forms.SendKeys.SendWait%2A> metoda nebude čekat na zprávy, které mají být zpracovány odeslání na jiný proces.</span><span class="sxs-lookup"><span data-stu-id="89cf1-124">Additionally, when the <xref:System.Windows.Forms.SendKeys> class uses the new implementation, the <xref:System.Windows.Forms.SendKeys.SendWait%2A> method will not wait for messages to be processed when they are sent to another process.</span></span>  
>   
>  <span data-ttu-id="89cf1-125">Pokud vaše aplikace závisí na konzistentní chování bez ohledu na operační systém, můžete vynutit <xref:System.Windows.Forms.SendKeys> třídu se má použít novou implementací přidáním následující nastavení aplikace do souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="89cf1-125">If your application relies on consistent behavior regardless of the operating system, you can force the <xref:System.Windows.Forms.SendKeys> class to use the new implementation by adding the following application setting to your app.config file.</span></span>  
>   
>  `<appSettings>`  
>   
>  `<add key="SendKeys" value="SendInput"/>`  
>   
>  `</appSettings>`  
>   
>  <span data-ttu-id="89cf1-126">Chcete-li vynutit <xref:System.Windows.Forms.SendKeys> třídy, které chcete použít předchozí implementace, použijte hodnotu `"JournalHook"` místo.</span><span class="sxs-lookup"><span data-stu-id="89cf1-126">To force the <xref:System.Windows.Forms.SendKeys> class to use the previous implementation, use the value `"JournalHook"` instead.</span></span>  
  
#### <a name="to-send-a-keystroke-to-the-same-application"></a><span data-ttu-id="89cf1-127">K odeslání stisknutí klávesy stejná aplikace</span><span class="sxs-lookup"><span data-stu-id="89cf1-127">To send a keystroke to the same application</span></span>  
  
1.  <span data-ttu-id="89cf1-128">Volání <xref:System.Windows.Forms.SendKeys.Send%2A> nebo <xref:System.Windows.Forms.SendKeys.SendWait%2A> metodu <xref:System.Windows.Forms.SendKeys> třídy.</span><span class="sxs-lookup"><span data-stu-id="89cf1-128">Call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method of the <xref:System.Windows.Forms.SendKeys> class.</span></span> <span data-ttu-id="89cf1-129">Zadaný stisknutí kláves dostane aktivní ovládací prvek aplikace.</span><span class="sxs-lookup"><span data-stu-id="89cf1-129">The specified keystrokes will be received by the active control of the application.</span></span> <span data-ttu-id="89cf1-130">Následující příklad kódu používá <xref:System.Windows.Forms.SendKeys.Send%2A> k simulaci při poklepání prostor ve tvaru, stisknete klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="89cf1-130">The following code example uses <xref:System.Windows.Forms.SendKeys.Send%2A> to simulate pressing the ENTER key when the user double-clicks the surface of the form.</span></span> <span data-ttu-id="89cf1-131">Tento příklad předpokládá <xref:System.Windows.Forms.Form> s jedním <xref:System.Windows.Forms.Button> ovládací prvek, který má pořadové číslo 0.</span><span class="sxs-lookup"><span data-stu-id="89cf1-131">This example assumes a <xref:System.Windows.Forms.Form> with a single <xref:System.Windows.Forms.Button> control that has a tab index of 0.</span></span>  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]  
  
#### <a name="to-send-a-keystroke-to-a-different-application"></a><span data-ttu-id="89cf1-132">K odeslání stisknutí klávesy jinou aplikaci</span><span class="sxs-lookup"><span data-stu-id="89cf1-132">To send a keystroke to a different application</span></span>  
  
1.  <span data-ttu-id="89cf1-133">Aktivovat okna aplikace, která bude přijímat stisknutí kláves a potom zavolejte <xref:System.Windows.Forms.SendKeys.Send%2A> nebo <xref:System.Windows.Forms.SendKeys.SendWait%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="89cf1-133">Activate the application window that will receive the keystrokes, and then call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method.</span></span> <span data-ttu-id="89cf1-134">Protože neexistuje žádná metoda spravované aktivovat jiná aplikace, je nutné použít nativní metody Windows vynutit fokus na jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="89cf1-134">Because there is no managed method to activate another application, you must use native Windows methods to force focus on other applications.</span></span> <span data-ttu-id="89cf1-135">Vyvolání platformou používá následující příklad kódu pro volání `FindWindow` a `SetForegroundWindow` metody aktivace okna aplikace kalkulačky a poté zavolá <xref:System.Windows.Forms.SendKeys.SendWait%2A> vystavit řadu Výpočty kalkulačky aplikace.</span><span class="sxs-lookup"><span data-stu-id="89cf1-135">The following code example uses platform invoke to call the `FindWindow` and `SetForegroundWindow` methods to activate the Calculator application window, and then calls <xref:System.Windows.Forms.SendKeys.SendWait%2A> to issue a series of calculations to the Calculator application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="89cf1-136">Správné parametry `FindWindow` volání, která vyhledává aplikace Kalkulačka lišit v závislosti na vaší verzi systému Windows.</span><span class="sxs-lookup"><span data-stu-id="89cf1-136">The correct parameters of the `FindWindow` call that locates the Calculator application vary based on your version of Windows.</span></span>  <span data-ttu-id="89cf1-137">Následující kód vyhledá aplikace Kalkulačka v [!INCLUDE[win7](../../../includes/win7-md.md)].</span><span class="sxs-lookup"><span data-stu-id="89cf1-137">The following code finds the Calculator application on [!INCLUDE[win7](../../../includes/win7-md.md)].</span></span> <span data-ttu-id="89cf1-138">Na [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], změňte první parametr "SciCalc".</span><span class="sxs-lookup"><span data-stu-id="89cf1-138">On [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], change the first parameter to "SciCalc".</span></span> <span data-ttu-id="89cf1-139">Nástroje Spy ++ nástroj, zahrnutá v sadě Visual Studio, můžete určit správné parametry.</span><span class="sxs-lookup"><span data-stu-id="89cf1-139">You can use the Spy++ tool, included with Visual Studio, to determine the correct parameters.</span></span>  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="89cf1-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="89cf1-140">Example</span></span>  
 <span data-ttu-id="89cf1-141">Následující příklad kódu je hotové aplikace pro předchozí příklady kódu.</span><span class="sxs-lookup"><span data-stu-id="89cf1-141">The following code example is the complete application for the previous code examples.</span></span>  
  
 [!code-cpp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89cf1-142">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="89cf1-142">Compiling the Code</span></span>  
 <span data-ttu-id="89cf1-143">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="89cf1-143">This example requires:</span></span>  
  
-   <span data-ttu-id="89cf1-144">Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="89cf1-144">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="89cf1-145">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="89cf1-145">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="89cf1-146">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="89cf1-146">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="89cf1-147">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="89cf1-147">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89cf1-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="89cf1-148">See Also</span></span>  
 [<span data-ttu-id="89cf1-149">Uživatelský vstup ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89cf1-149">User Input in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-in-windows-forms.md)
