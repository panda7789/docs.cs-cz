---
title: Řešení potíží s vytvářením ovládacích prvků a komponent
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5d3aa715590a10391bafa08a85265842ee8cedfb
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197114"
---
# <a name="troubleshoot-control-and-component-authoring"></a><span data-ttu-id="c014a-102">Řešení potíží s vytvářením ovládacích prvků a komponent</span><span class="sxs-lookup"><span data-stu-id="c014a-102">Troubleshoot Control and Component Authoring</span></span>

<span data-ttu-id="c014a-103">Toto téma uvádí následující běžné problémy, které vznikají při vývoji komponent a ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="c014a-103">This topic lists the following common problems that arise when developing components and controls:</span></span>

- <span data-ttu-id="c014a-104">Nelze přidat ovládací prvek do panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="c014a-104">Cannot Add Control to Toolbox</span></span>

- <span data-ttu-id="c014a-105">Nelze ladit model Windows Forms uživatelský ovládací prvek nebo komponentu</span><span class="sxs-lookup"><span data-stu-id="c014a-105">Cannot Debug the Windows Forms User Control or Component</span></span>

- <span data-ttu-id="c014a-106">Událost je vyvolána dvakrát v zděděném ovládacím prvku nebo komponentě.</span><span class="sxs-lookup"><span data-stu-id="c014a-106">Event Is Raised Twice in Inherited Control or Component</span></span>

- <span data-ttu-id="c014a-107">Chyba návrhu: Nepodařilo se vytvořit součást s*názvem*.</span><span class="sxs-lookup"><span data-stu-id="c014a-107">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>

- <span data-ttu-id="c014a-108">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="c014a-108">STAThreadAttribute</span></span>

- <span data-ttu-id="c014a-109">Ikona součásti se nezobrazí v sadě nástrojů.</span><span class="sxs-lookup"><span data-stu-id="c014a-109">Component Icon Does Not Appear in Toolbox</span></span>

## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="c014a-110">Nelze přidat ovládací prvek do panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="c014a-110">Cannot Add Control to Toolbox</span></span>

<span data-ttu-id="c014a-111">Chcete-li přidat vlastní ovládací prvek, který jste vytvořili v jiném projektu nebo ovládacím prvku třetí strany do **sady nástrojů**, musíte to provést ručně.</span><span class="sxs-lookup"><span data-stu-id="c014a-111">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="c014a-112">Pokud aktuální projekt obsahuje ovládací prvek nebo komponentu, měla by se automaticky zobrazit v **sadě nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="c014a-112">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="c014a-113">Další informace najdete v tématu [Návod: automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="c014a-113">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="c014a-114">Přidání ovládacího prvku do panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="c014a-114">To add a control to the Toolbox</span></span>

1. <span data-ttu-id="c014a-115">Klikněte pravým tlačítkem myši na **panel nástrojů** a v místní nabídce vyberte možnost **zvolit položky**.</span><span class="sxs-lookup"><span data-stu-id="c014a-115">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>

2. <span data-ttu-id="c014a-116">V dialogovém okně **zvolit položky sady nástrojů** přidejte komponentu:</span><span class="sxs-lookup"><span data-stu-id="c014a-116">In the **Choose Toolbox Items** dialog box, add the component:</span></span>

    - <span data-ttu-id="c014a-117">Chcete-li přidat komponentu .NET Framework nebo ovládací prvek, klikněte na kartu **komponenty .NET Framework** .</span><span class="sxs-lookup"><span data-stu-id="c014a-117">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>

         <span data-ttu-id="c014a-118">ani</span><span class="sxs-lookup"><span data-stu-id="c014a-118">– or –</span></span>

    - <span data-ttu-id="c014a-119">Chcete-li přidat komponentu modelu COM nebo ovládací prvek ActiveX, klikněte na kartu **komponenty modelu COM** .</span><span class="sxs-lookup"><span data-stu-id="c014a-119">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>

3. <span data-ttu-id="c014a-120">Pokud je ovládací prvek uveden v dialogovém okně, potvrďte jeho výběr a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c014a-120">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>

     <span data-ttu-id="c014a-121">Ovládací prvek je přidán do **sady nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="c014a-121">The control is added to the **Toolbox**.</span></span>

4. <span data-ttu-id="c014a-122">Pokud váš ovládací prvek není uveden v dialogovém okně, udělejte toto:</span><span class="sxs-lookup"><span data-stu-id="c014a-122">If your control is not listed in the dialog box, do the following:</span></span>

    1. <span data-ttu-id="c014a-123">Klikněte na tlačítko **Procházet** .</span><span class="sxs-lookup"><span data-stu-id="c014a-123">Click the **Browse** button.</span></span>

    2. <span data-ttu-id="c014a-124">Přejděte do složky, která obsahuje soubor. dll, který obsahuje váš ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c014a-124">Browse to the folder that contains the .dll file that contains your control.</span></span>

    3. <span data-ttu-id="c014a-125">Vyberte soubor. dll a klikněte na **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="c014a-125">Select the .dll file and click **Open**.</span></span>

         <span data-ttu-id="c014a-126">Ovládací prvek se zobrazí v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="c014a-126">Your control appears in the dialog box.</span></span>

    4. <span data-ttu-id="c014a-127">Potvrďte, že je váš ovládací prvek vybraný, a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="c014a-127">Confirm that your control is selected, and then click **OK**.</span></span>

         <span data-ttu-id="c014a-128">Váš ovládací prvek je přidán do **sady nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="c014a-128">Your control is added to the **Toolbox**.</span></span>

## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="c014a-129">Nelze ladit model Windows Forms uživatelský ovládací prvek nebo komponentu</span><span class="sxs-lookup"><span data-stu-id="c014a-129">Cannot Debug the Windows Forms User Control or Component</span></span>

<span data-ttu-id="c014a-130">Pokud je váš ovládací prvek odvozen z třídy <xref:System.Windows.Forms.UserControl>, můžete ladit chování za běhu pomocí kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="c014a-130">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="c014a-131">Další informace naleznete v tématu [How to: test runtime Behavior prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="c014a-131">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="c014a-132">Další vlastní ovládací prvky a komponenty nejsou samostatné projekty.</span><span class="sxs-lookup"><span data-stu-id="c014a-132">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="c014a-133">Musí být hostovány aplikací, jako je model Windows Forms projekt.</span><span class="sxs-lookup"><span data-stu-id="c014a-133">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="c014a-134">Chcete-li ladit ovládací prvek nebo komponentu, je nutné ji přidat do projektu model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c014a-134">To debug a control or component, you must add it to a Windows Forms project.</span></span>

### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="c014a-135">Ladění ovládacího prvku nebo komponenty</span><span class="sxs-lookup"><span data-stu-id="c014a-135">To debug a control or component</span></span>

1. <span data-ttu-id="c014a-136">V nabídce **sestavení** klikněte na **Sestavit řešení** a sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="c014a-136">From the **Build** menu, click **Build Solution** to build your solution.</span></span>

2. <span data-ttu-id="c014a-137">V nabídce **soubor** zvolte možnost **Přidat**a pak **Nový projekt** a přidejte do své aplikace testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="c014a-137">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>

3. <span data-ttu-id="c014a-138">V dialogovém okně **Přidat nový projekt** vyberte možnost **aplikace systému Windows** pro typ projektu.</span><span class="sxs-lookup"><span data-stu-id="c014a-138">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>

4. <span data-ttu-id="c014a-139">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** pro nový projekt.</span><span class="sxs-lookup"><span data-stu-id="c014a-139">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="c014a-140">V místní nabídce klikněte na **Přidat odkaz** a přidejte odkaz na projekt, který obsahuje ovládací prvek nebo komponentu.</span><span class="sxs-lookup"><span data-stu-id="c014a-140">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>

5. <span data-ttu-id="c014a-141">Vytvořte instanci ovládacího prvku nebo komponenty v testovacím projektu.</span><span class="sxs-lookup"><span data-stu-id="c014a-141">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="c014a-142">Pokud je vaše komponenta v sadě **nástrojů**, můžete ji přetáhnout na plochu návrháře, nebo můžete instanci vytvořit programově, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="c014a-142">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>

    ```vb
    Dim Component1 As New MyNeatComponent()
    ```

    ```csharp
    MyNeatComponent Component1 = new MyNeatComponent();
    ```

   <span data-ttu-id="c014a-143">Nyní můžete ladit ovládací prvek nebo komponentu obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="c014a-143">You can now debug your control or component as usual.</span></span>

<span data-ttu-id="c014a-144">Další informace o ladění naleznete v tématu [ladění v aplikaci Visual Studio](/visualstudio/debugger/debugger-feature-tour) a [Návod: ladění vlastních ovládacích prvků model Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="c014a-144">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugger-feature-tour) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="c014a-145">Událost je vyvolána dvakrát v zděděném ovládacím prvku nebo komponentě.</span><span class="sxs-lookup"><span data-stu-id="c014a-145">Event Is Raised Twice in Inherited Control or Component</span></span>

<span data-ttu-id="c014a-146">To je pravděpodobně způsobeno duplicitní `Handles` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="c014a-146">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="c014a-147">Další informace najdete v tématu [řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="c014a-147">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>

## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="c014a-148">Chyba návrhu: Nepodařilo se vytvořit součást s názvem.</span><span class="sxs-lookup"><span data-stu-id="c014a-148">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>

<span data-ttu-id="c014a-149">Komponenta nebo ovládací prvek musí poskytovat konstruktor bez parametrů bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="c014a-149">Your component or control must provide a parameterless constructor with no parameters.</span></span> <span data-ttu-id="c014a-150">Když vývojové prostředí vytvoří instanci vaší komponenty nebo ovládacího prvku, nepokusí se poskytnout žádné parametry přetížení konstruktoru, které přijímají parametry.</span><span class="sxs-lookup"><span data-stu-id="c014a-150">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>

## <a name="stathreadattribute"></a><span data-ttu-id="c014a-151">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="c014a-151">STAThreadAttribute</span></span>

<span data-ttu-id="c014a-152"><xref:System.STAThreadAttribute> informuje modul CLR (Common Language Runtime), který model Windows Forms používá model Apartment s jedním vláknem.</span><span class="sxs-lookup"><span data-stu-id="c014a-152">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="c014a-153">Pokud nepoužijete tento atribut na metodu `Main` model Windows Forms vaší aplikace, můžete si všimnout nezamýšleného chování.</span><span class="sxs-lookup"><span data-stu-id="c014a-153">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="c014a-154">Například obrázky na pozadí se nemusí zobrazit pro ovládací prvky jako <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="c014a-154">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="c014a-155">Některé ovládací prvky mohou také vyžadovat tento atribut pro správné automatické dokončování a chování při přetahování.</span><span class="sxs-lookup"><span data-stu-id="c014a-155">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>

## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="c014a-156">Ikona součásti se nezobrazí v sadě nástrojů.</span><span class="sxs-lookup"><span data-stu-id="c014a-156">Component Icon Does Not Appear in Toolbox</span></span>

<span data-ttu-id="c014a-157">Když použijete <xref:System.Drawing.ToolboxBitmapAttribute> k přidružení ikony k vlastní komponentě, bitmapa se nezobrazí v sadě nástrojů pro automaticky generované součásti.</span><span class="sxs-lookup"><span data-stu-id="c014a-157">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="c014a-158">Chcete-li zobrazit rastrový obrázek, načtěte ovládací prvek znovu pomocí dialogového okna **zvolit položky sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="c014a-158">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="c014a-159">Další informace naleznete v tématu [How to: poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="c014a-159">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c014a-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c014a-160">See also</span></span>

- [<span data-ttu-id="c014a-161">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="c014a-161">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="c014a-162">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="c014a-162">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="c014a-163">Postupy: Otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="c014a-163">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="c014a-164">Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu</span><span class="sxs-lookup"><span data-stu-id="c014a-164">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
