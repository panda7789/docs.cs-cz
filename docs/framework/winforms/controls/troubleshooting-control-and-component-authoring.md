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
ms.openlocfilehash: c05e849705f851b51a362d3a1d1d3f81a9eaf0e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923600"
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="62358-102">Řešení potíží s vytvářením ovládacích prvků a komponent</span><span class="sxs-lookup"><span data-stu-id="62358-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="62358-103">Toto téma uvádí následující běžné problémy, které vznikají při vývoji komponent a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="62358-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="62358-104">Další informace najdete v tématu [programování s komponentami](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="62358-104">For more information, see [Programming with Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
- <span data-ttu-id="62358-105">Nelze přidat ovládací prvek do panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="62358-105">Cannot Add Control to Toolbox</span></span>  
  
- <span data-ttu-id="62358-106">Nelze ladit model Windows Forms uživatelský ovládací prvek nebo komponentu</span><span class="sxs-lookup"><span data-stu-id="62358-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
- <span data-ttu-id="62358-107">Událost je vyvolána dvakrát v zděděném ovládacím prvku nebo komponentě.</span><span class="sxs-lookup"><span data-stu-id="62358-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
- <span data-ttu-id="62358-108">Chyba v době návrhu: "Nepovedlo se vytvořit součást s*názvem součásti*".</span><span class="sxs-lookup"><span data-stu-id="62358-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
- <span data-ttu-id="62358-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="62358-109">STAThreadAttribute</span></span>  
  
- <span data-ttu-id="62358-110">Ikona součásti se nezobrazí v sadě nástrojů.</span><span class="sxs-lookup"><span data-stu-id="62358-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="62358-111">Nelze přidat ovládací prvek do panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="62358-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="62358-112">Chcete-li přidat vlastní ovládací prvek, který jste vytvořili v jiném projektu nebo ovládacím prvku třetí strany do **sady nástrojů**, musíte to provést ručně.</span><span class="sxs-lookup"><span data-stu-id="62358-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="62358-113">Pokud aktuální projekt obsahuje ovládací prvek nebo komponentu, měla by se automaticky zobrazit v **sadě nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="62358-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="62358-114">Další informace najdete v tématu [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="62358-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="62358-115">Přidání ovládacího prvku do panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="62358-115">To add a control to the Toolbox</span></span>  
  
1. <span data-ttu-id="62358-116">Klikněte pravým tlačítkem myši na **panel nástrojů** a v místní nabídce vyberte možnost **zvolit položky**.</span><span class="sxs-lookup"><span data-stu-id="62358-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2. <span data-ttu-id="62358-117">V dialogovém okně **zvolit položky sady nástrojů** přidejte komponentu:</span><span class="sxs-lookup"><span data-stu-id="62358-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    - <span data-ttu-id="62358-118">Chcete-li přidat komponentu .NET Framework nebo ovládací prvek, klikněte na kartu **komponenty .NET Framework** .</span><span class="sxs-lookup"><span data-stu-id="62358-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="62358-119">– nebo –</span><span class="sxs-lookup"><span data-stu-id="62358-119">– or –</span></span>  
  
    - <span data-ttu-id="62358-120">Chcete-li přidat komponentu modelu COM nebo ovládací prvek ActiveX, klikněte na kartu **komponenty modelu COM** .</span><span class="sxs-lookup"><span data-stu-id="62358-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3. <span data-ttu-id="62358-121">Pokud je ovládací prvek uveden v dialogovém okně, potvrďte jeho výběr a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="62358-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="62358-122">Ovládací prvek je přidán do **sady nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="62358-122">The control is added to the **Toolbox**.</span></span>  
  
4. <span data-ttu-id="62358-123">Pokud váš ovládací prvek není uveden v dialogovém okně, udělejte toto:</span><span class="sxs-lookup"><span data-stu-id="62358-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1. <span data-ttu-id="62358-124">Klikněte na tlačítko **Procházet** .</span><span class="sxs-lookup"><span data-stu-id="62358-124">Click the **Browse** button.</span></span>  
  
    2. <span data-ttu-id="62358-125">Přejděte do složky, která obsahuje soubor. dll, který obsahuje váš ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="62358-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3. <span data-ttu-id="62358-126">Vyberte soubor. dll a klikněte na **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="62358-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="62358-127">Ovládací prvek se zobrazí v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="62358-127">Your control appears in the dialog box.</span></span>  
  
    4. <span data-ttu-id="62358-128">Potvrďte, že je váš ovládací prvek vybraný, a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="62358-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="62358-129">Váš ovládací prvek je přidán do **sady nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="62358-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="62358-130">Nelze ladit model Windows Forms uživatelský ovládací prvek nebo komponentu</span><span class="sxs-lookup"><span data-stu-id="62358-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="62358-131">Pokud je váš ovládací prvek odvozen z <xref:System.Windows.Forms.UserControl> třídy, můžete ladit chování za běhu pomocí kontejneru testů.</span><span class="sxs-lookup"><span data-stu-id="62358-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="62358-132">Další informace najdete v tématu [jak: Otestuje chování prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)v době běhu.</span><span class="sxs-lookup"><span data-stu-id="62358-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="62358-133">Další vlastní ovládací prvky a komponenty nejsou samostatné projekty.</span><span class="sxs-lookup"><span data-stu-id="62358-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="62358-134">Musí být hostovány aplikací, jako je model Windows Forms projekt.</span><span class="sxs-lookup"><span data-stu-id="62358-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="62358-135">Chcete-li ladit ovládací prvek nebo komponentu, je nutné ji přidat do projektu model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="62358-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="62358-136">Ladění ovládacího prvku nebo komponenty</span><span class="sxs-lookup"><span data-stu-id="62358-136">To debug a control or component</span></span>  
  
1. <span data-ttu-id="62358-137">V nabídce **sestavení** klikněte na **Sestavit řešení** a sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="62358-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2. <span data-ttu-id="62358-138">V nabídce **soubor** zvolte možnost **Přidat**a pak **Nový projekt** a přidejte do své aplikace testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="62358-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3. <span data-ttu-id="62358-139">V dialogovém okně **Přidat nový projekt** vyberte možnost **aplikace systému Windows** pro typ projektu.</span><span class="sxs-lookup"><span data-stu-id="62358-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4. <span data-ttu-id="62358-140">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** pro nový projekt.</span><span class="sxs-lookup"><span data-stu-id="62358-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="62358-141">V místní nabídce klikněte na **Přidat odkaz** a přidejte odkaz na projekt, který obsahuje ovládací prvek nebo komponentu.</span><span class="sxs-lookup"><span data-stu-id="62358-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5. <span data-ttu-id="62358-142">Vytvořte instanci ovládacího prvku nebo komponenty v testovacím projektu.</span><span class="sxs-lookup"><span data-stu-id="62358-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="62358-143">Pokud je vaše komponenta v sadě **nástrojů**, můžete ji přetáhnout na plochu návrháře, nebo můžete instanci vytvořit programově, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="62358-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="62358-144">Nyní můžete ladit ovládací prvek nebo komponentu obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="62358-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="62358-145">Další informace o ladění naleznete v tématu [ladění v aplikaci Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) a [Návod: Ladění vlastních ovládacích prvků model Windows Forms v době](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)návrhu.</span><span class="sxs-lookup"><span data-stu-id="62358-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="62358-146">Událost je vyvolána dvakrát v zděděném ovládacím prvku nebo komponentě.</span><span class="sxs-lookup"><span data-stu-id="62358-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="62358-147">Pravděpodobnou příčinou je duplicitní `Handles` klauzule.</span><span class="sxs-lookup"><span data-stu-id="62358-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="62358-148">Další informace najdete v tématu [řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="62358-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="62358-149">Chyba v době návrhu: "Nepovedlo se vytvořit součást s názvem součásti".</span><span class="sxs-lookup"><span data-stu-id="62358-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="62358-150">Komponenta nebo ovládací prvek musí poskytovat konstruktor bez parametrů bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="62358-150">Your component or control must provide a parameterless constructor with no parameters.</span></span> <span data-ttu-id="62358-151">Když vývojové prostředí vytvoří instanci vaší komponenty nebo ovládacího prvku, nepokusí se poskytnout žádné parametry přetížení konstruktoru, které přijímají parametry.</span><span class="sxs-lookup"><span data-stu-id="62358-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="62358-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="62358-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="62358-153"><xref:System.STAThreadAttribute> Informuje modul CLR (Common Language Runtime), který model Windows Forms používá model Apartment s jedním vláknem.</span><span class="sxs-lookup"><span data-stu-id="62358-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="62358-154">Pokud nepoužijete tento atribut na `Main` metodu model Windows Forms aplikace, můžete si všimnout nezamýšleného chování.</span><span class="sxs-lookup"><span data-stu-id="62358-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="62358-155">Například obrázky na pozadí se nemusí zobrazit pro ovládací prvky jako <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="62358-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="62358-156">Některé ovládací prvky mohou také vyžadovat tento atribut pro správné automatické dokončování a chování při přetahování.</span><span class="sxs-lookup"><span data-stu-id="62358-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="62358-157">Ikona součásti se nezobrazí v sadě nástrojů.</span><span class="sxs-lookup"><span data-stu-id="62358-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="62358-158">Když použijete <xref:System.Drawing.ToolboxBitmapAttribute> nástroj k přidružení ikony k vlastní komponentě, bitmapa se nezobrazí v sadě nástrojů pro automaticky generované součásti.</span><span class="sxs-lookup"><span data-stu-id="62358-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="62358-159">Chcete-li zobrazit rastrový obrázek, načtěte ovládací prvek znovu pomocí dialogového okna **zvolit položky sady nástrojů** .</span><span class="sxs-lookup"><span data-stu-id="62358-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="62358-160">Další informace najdete v tématu [jak: Poskytnutí rastrového obrázku panelu nástrojů pro](how-to-provide-a-toolbox-bitmap-for-a-control.md)ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="62358-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62358-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62358-161">See also</span></span>

- [<span data-ttu-id="62358-162">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="62358-162">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="62358-163">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="62358-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="62358-164">Postupy: Testování chování prvku UserControl v době běhu</span><span class="sxs-lookup"><span data-stu-id="62358-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="62358-165">Návod: Ladění vlastních ovládacích prvků model Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="62358-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="62358-166">[Vytváření součástí](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="62358-166">[Component Authoring](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span></span>
- <span data-ttu-id="62358-167">[Řešení potíží s vývojem v době návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="62358-167">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
