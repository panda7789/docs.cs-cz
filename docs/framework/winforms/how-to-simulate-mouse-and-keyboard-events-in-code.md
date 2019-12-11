---
title: 'Postupy: Simulace událostí myši a klávesnice v kódu'
ms.date: 03/30/2017
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
ms.openlocfilehash: 52f89df8d7f28f0e00c3becd9005b46e52b5532c
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960202"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a><span data-ttu-id="3db99-102">Postupy: Simulace událostí myši a klávesnice v kódu</span><span class="sxs-lookup"><span data-stu-id="3db99-102">How to: Simulate Mouse and Keyboard Events in Code</span></span>

<span data-ttu-id="3db99-103">Model Windows Forms poskytuje několik možností pro programové simulaci vstupu myši a klávesnice.</span><span class="sxs-lookup"><span data-stu-id="3db99-103">Windows Forms provides several options for programmatically simulating mouse and keyboard input.</span></span> <span data-ttu-id="3db99-104">Toto téma poskytuje přehled těchto možností.</span><span class="sxs-lookup"><span data-stu-id="3db99-104">This topic provides an overview of these options.</span></span>

## <a name="simulating-mouse-input"></a><span data-ttu-id="3db99-105">Simulace vstupu myši</span><span class="sxs-lookup"><span data-stu-id="3db99-105">Simulating Mouse Input</span></span>

<span data-ttu-id="3db99-106">Nejlepším způsobem, jak simulovat události myši, je zavolat metodu `On`*EventName* , která vyvolává událost myši, kterou chcete simulovat.</span><span class="sxs-lookup"><span data-stu-id="3db99-106">The best way to simulate mouse events is to call the `On`*EventName* method that raises the mouse event you want to simulate.</span></span> <span data-ttu-id="3db99-107">Tato možnost je obvykle k dispozici pouze v rámci vlastních ovládacích prvků a formulářů, protože metody, které vyvolávají události, jsou chráněny a nelze je používat mimo ovládací prvek nebo formulář.</span><span class="sxs-lookup"><span data-stu-id="3db99-107">This option is usually possible only within custom controls and forms, because the methods that raise events are protected and cannot be accessed outside the control or form.</span></span> <span data-ttu-id="3db99-108">Následující kroky například ukazují, jak simulovat kliknutí pravým tlačítkem myši v kódu.</span><span class="sxs-lookup"><span data-stu-id="3db99-108">For example, the following steps illustrate how to simulate clicking the right mouse button in code.</span></span>

#### <a name="to-programmatically-click-the-right-mouse-button"></a><span data-ttu-id="3db99-109">Postup při programovém kliknutí pravým tlačítkem myši</span><span class="sxs-lookup"><span data-stu-id="3db99-109">To programmatically click the right mouse button</span></span>

1. <span data-ttu-id="3db99-110">Vytvořte <xref:System.Windows.Forms.MouseEventArgs>, jehož vlastnost <xref:System.Windows.Forms.MouseEventArgs.Button%2A> je nastavena na hodnotu <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3db99-110">Create a <xref:System.Windows.Forms.MouseEventArgs> whose <xref:System.Windows.Forms.MouseEventArgs.Button%2A> property is set to the <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> value.</span></span>

2. <span data-ttu-id="3db99-111">Jako argument volejte metodu <xref:System.Windows.Forms.Control.OnMouseClick%2A> s tímto <xref:System.Windows.Forms.MouseEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="3db99-111">Call the <xref:System.Windows.Forms.Control.OnMouseClick%2A> method with this <xref:System.Windows.Forms.MouseEventArgs> as the argument.</span></span>

<span data-ttu-id="3db99-112">Další informace o vlastních ovládacích prvcích najdete v tématu [vývoj model Windows Formsch ovládacích prvků v době návrhu](./controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="3db99-112">For more information on custom controls, see [Developing Windows Forms Controls at Design Time](./controls/developing-windows-forms-controls-at-design-time.md).</span></span>

<span data-ttu-id="3db99-113">Existují i jiné způsoby, jak simulovat vstup z myši.</span><span class="sxs-lookup"><span data-stu-id="3db99-113">There are other ways to simulate mouse input.</span></span> <span data-ttu-id="3db99-114">Můžete například programově nastavit vlastnost ovládacího prvku, která představuje stav, který je obvykle nastaven prostřednictvím vstupu myši (například vlastnost <xref:System.Windows.Forms.CheckBox.Checked%2A> ovládacího prvku <xref:System.Windows.Forms.CheckBox>), nebo můžete přímo volat delegáta, který je připojen k události, kterou chcete simulovat.</span><span class="sxs-lookup"><span data-stu-id="3db99-114">For example, you can programmatically set a control property that represents a state that is typically set through mouse input (such as the <xref:System.Windows.Forms.CheckBox.Checked%2A> property of the <xref:System.Windows.Forms.CheckBox> control), or you can directly call the delegate that is attached to the event you want to simulate.</span></span>

## <a name="simulating-keyboard-input"></a><span data-ttu-id="3db99-115">Simulace vstupu z klávesnice</span><span class="sxs-lookup"><span data-stu-id="3db99-115">Simulating Keyboard Input</span></span>

<span data-ttu-id="3db99-116">I když můžete simulovat vstup z klávesnice pomocí výše popsaných strategií pro vstup myši, model Windows Forms taky poskytuje <xref:System.Windows.Forms.SendKeys>ou třídu pro posílání klávesových úhozů do aktivní aplikace.</span><span class="sxs-lookup"><span data-stu-id="3db99-116">Although you can simulate keyboard input by using the strategies discussed above for mouse input, Windows Forms also provides the <xref:System.Windows.Forms.SendKeys> class for sending keystrokes to the active application.</span></span>

> [!CAUTION]
> <span data-ttu-id="3db99-117">Pokud je vaše aplikace určena pro mezinárodní použití s celou řadou klávesnic, použití <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> může přinést nepředvídatelné výsledky a je třeba se jim vyhnout.</span><span class="sxs-lookup"><span data-stu-id="3db99-117">If your application is intended for international use with a variety of keyboards, the use of <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> could yield unpredictable results and should be avoided.</span></span>

> [!NOTE]
> <span data-ttu-id="3db99-118"><xref:System.Windows.Forms.SendKeys> třída byla aktualizována pro .NET Framework 3,0, aby ji bylo možné použít v aplikacích, které jsou spuštěny v systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="3db99-118">The <xref:System.Windows.Forms.SendKeys> class has been updated for the .NET Framework 3.0 to enable its use in applications that run on Windows Vista.</span></span> <span data-ttu-id="3db99-119">Vyšší zabezpečení systému Windows Vista (označované jako řízení uživatelských účtů nebo UAC) brání předchozí implementaci v práci podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="3db99-119">The enhanced security of Windows Vista (known as User Account Control or UAC) prevents the previous implementation from working as expected.</span></span>
>
> <span data-ttu-id="3db99-120">Třída <xref:System.Windows.Forms.SendKeys> je náchylná k časování problémů, které někteří vývojáři museli obejít.</span><span class="sxs-lookup"><span data-stu-id="3db99-120">The <xref:System.Windows.Forms.SendKeys> class is susceptible to timing issues, which some developers have had to work around.</span></span> <span data-ttu-id="3db99-121">Aktualizovaná implementace je stále náchylná k problémům časování, ale je mírně rychlejší a může vyžadovat změny v alternativním řešení.</span><span class="sxs-lookup"><span data-stu-id="3db99-121">The updated implementation is still susceptible to timing issues, but is slightly faster and may require changes to the workarounds.</span></span> <span data-ttu-id="3db99-122">Třída <xref:System.Windows.Forms.SendKeys> se pokusí použít nejprve předchozí implementaci a v případě, že dojde k chybě, použije novou implementaci.</span><span class="sxs-lookup"><span data-stu-id="3db99-122">The <xref:System.Windows.Forms.SendKeys> class tries to use the previous implementation first, and if that fails, uses the new implementation.</span></span> <span data-ttu-id="3db99-123">V důsledku toho se třída <xref:System.Windows.Forms.SendKeys> může chovat odlišně v různých operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="3db99-123">As a result, the <xref:System.Windows.Forms.SendKeys> class may behave differently on different operating systems.</span></span> <span data-ttu-id="3db99-124">Kromě toho, pokud <xref:System.Windows.Forms.SendKeys> třída používá novou implementaci, metoda <xref:System.Windows.Forms.SendKeys.SendWait%2A> nečeká na zpracování zpráv při jejich odeslání do jiného procesu.</span><span class="sxs-lookup"><span data-stu-id="3db99-124">Additionally, when the <xref:System.Windows.Forms.SendKeys> class uses the new implementation, the <xref:System.Windows.Forms.SendKeys.SendWait%2A> method will not wait for messages to be processed when they are sent to another process.</span></span>
>
> <span data-ttu-id="3db99-125">Pokud vaše aplikace spoléhá na konzistentní chování bez ohledu na operační systém, můžete vynutit, aby třída <xref:System.Windows.Forms.SendKeys> používala novou implementaci přidáním následujícího nastavení aplikace do souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="3db99-125">If your application relies on consistent behavior regardless of the operating system, you can force the <xref:System.Windows.Forms.SendKeys> class to use the new implementation by adding the following application setting to your app.config file.</span></span>
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> <span data-ttu-id="3db99-126">Chcete-li vynutit, aby třída <xref:System.Windows.Forms.SendKeys> používala předchozí implementaci, použijte místo toho hodnotu `"JournalHook"`.</span><span class="sxs-lookup"><span data-stu-id="3db99-126">To force the <xref:System.Windows.Forms.SendKeys> class to use the previous implementation, use the value `"JournalHook"` instead.</span></span>

#### <a name="to-send-a-keystroke-to-the-same-application"></a><span data-ttu-id="3db99-127">Odeslání stisknutí klávesy ke stejné aplikaci</span><span class="sxs-lookup"><span data-stu-id="3db99-127">To send a keystroke to the same application</span></span>

1. <span data-ttu-id="3db99-128">Zavolejte metodu <xref:System.Windows.Forms.SendKeys.Send%2A> nebo <xref:System.Windows.Forms.SendKeys.SendWait%2A> třídy <xref:System.Windows.Forms.SendKeys>.</span><span class="sxs-lookup"><span data-stu-id="3db99-128">Call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method of the <xref:System.Windows.Forms.SendKeys> class.</span></span> <span data-ttu-id="3db99-129">Zadané úhozy kláves budou přijímány aktivním ovládacím prvkem aplikace.</span><span class="sxs-lookup"><span data-stu-id="3db99-129">The specified keystrokes will be received by the active control of the application.</span></span> <span data-ttu-id="3db99-130">Následující příklad kódu používá <xref:System.Windows.Forms.SendKeys.Send%2A> pro simulaci stisknutí klávesy ENTER, když uživatel dvakrát klikne na povrch formuláře.</span><span class="sxs-lookup"><span data-stu-id="3db99-130">The following code example uses <xref:System.Windows.Forms.SendKeys.Send%2A> to simulate pressing the ENTER key when the user double-clicks the surface of the form.</span></span> <span data-ttu-id="3db99-131">Tento příklad předpokládá <xref:System.Windows.Forms.Form> s jedním <xref:System.Windows.Forms.Button> ovládacím prvkem, který má index karty 0.</span><span class="sxs-lookup"><span data-stu-id="3db99-131">This example assumes a <xref:System.Windows.Forms.Form> with a single <xref:System.Windows.Forms.Button> control that has a tab index of 0.</span></span>

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a><span data-ttu-id="3db99-132">Odeslání úhozu do jiné aplikace</span><span class="sxs-lookup"><span data-stu-id="3db99-132">To send a keystroke to a different application</span></span>

1. <span data-ttu-id="3db99-133">Aktivujte okno aplikace, které bude přijímat stisknutí kláves, a potom zavolejte metodu <xref:System.Windows.Forms.SendKeys.Send%2A> nebo <xref:System.Windows.Forms.SendKeys.SendWait%2A>.</span><span class="sxs-lookup"><span data-stu-id="3db99-133">Activate the application window that will receive the keystrokes, and then call the <xref:System.Windows.Forms.SendKeys.Send%2A> or <xref:System.Windows.Forms.SendKeys.SendWait%2A> method.</span></span> <span data-ttu-id="3db99-134">Vzhledem k tomu, že neexistuje žádná spravovaná metoda pro aktivaci jiné aplikace, je nutné použít nativní metody systému Windows k vynucení fokusu na jiné aplikace.</span><span class="sxs-lookup"><span data-stu-id="3db99-134">Because there is no managed method to activate another application, you must use native Windows methods to force focus on other applications.</span></span> <span data-ttu-id="3db99-135">Následující příklad kódu používá vyvolání platformy pro volání metod `FindWindow` a `SetForegroundWindow` k aktivaci okna aplikace kalkulačky a následné volání <xref:System.Windows.Forms.SendKeys.SendWait%2A> pro vydání řady výpočtů do aplikace kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="3db99-135">The following code example uses platform invoke to call the `FindWindow` and `SetForegroundWindow` methods to activate the Calculator application window, and then calls <xref:System.Windows.Forms.SendKeys.SendWait%2A> to issue a series of calculations to the Calculator application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3db99-136">Správné parametry `FindWindow` volání, které vyhledává aplikaci kalkulačky, se liší v závislosti na vaší verzi systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3db99-136">The correct parameters of the `FindWindow` call that locates the Calculator application vary based on your version of Windows.</span></span>  <span data-ttu-id="3db99-137">Následující kód vyhledá aplikaci kalkulačky ve Windows 7.</span><span class="sxs-lookup"><span data-stu-id="3db99-137">The following code finds the Calculator application on Windows 7.</span></span> <span data-ttu-id="3db99-138">V systému Windows Vista změňte první parametr na "SciCalc".</span><span class="sxs-lookup"><span data-stu-id="3db99-138">On Windows Vista, change the first parameter to "SciCalc".</span></span> <span data-ttu-id="3db99-139">K určení správných parametrů můžete použít nástroj Spy + +, který je součástí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3db99-139">You can use the Spy++ tool, included with Visual Studio, to determine the correct parameters.</span></span>

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a><span data-ttu-id="3db99-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="3db99-140">Example</span></span>

<span data-ttu-id="3db99-141">Následující příklad kódu je kompletní aplikace pro předchozí příklady kódu.</span><span class="sxs-lookup"><span data-stu-id="3db99-141">The following code example is the complete application for the previous code examples.</span></span>

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="3db99-142">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3db99-142">Compiling the Code</span></span>

<span data-ttu-id="3db99-143">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="3db99-143">This example requires:</span></span>

- <span data-ttu-id="3db99-144">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="3db99-144">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="3db99-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3db99-145">See also</span></span>

- [<span data-ttu-id="3db99-146">Uživatelský vstup ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3db99-146">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)
