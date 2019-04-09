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
ms.openlocfilehash: 988121bce1fd63c9560fb77fea6dedddd318c4ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168061"
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="fcc1f-102">Řešení potíží s vytvářením ovládacích prvků a komponent</span><span class="sxs-lookup"><span data-stu-id="fcc1f-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="fcc1f-103">Toto téma uvádí následující běžné problémy, které vznikají při vývoji komponent a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="fcc1f-104">Další informace najdete v tématu [programování pomocí komponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="fcc1f-104">For more information, see [Programming with Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
-   <span data-ttu-id="fcc1f-105">Nelze přidat ovládací prvek na panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="fcc1f-105">Cannot Add Control to Toolbox</span></span>  
  
-   <span data-ttu-id="fcc1f-106">Nelze ladit uživatelského ovládacího prvku formulářů Windows nebo komponenty</span><span class="sxs-lookup"><span data-stu-id="fcc1f-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
-   <span data-ttu-id="fcc1f-107">Událost se vyvolá dvakrát v zděděný ovládací prvek nebo komponenty</span><span class="sxs-lookup"><span data-stu-id="fcc1f-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
-   <span data-ttu-id="fcc1f-108">Chyba návrhu: "Nepovedlo se vytvořit komponentu '*název komponenty*."</span><span class="sxs-lookup"><span data-stu-id="fcc1f-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
-   <span data-ttu-id="fcc1f-109">Atribut STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="fcc1f-109">STAThreadAttribute</span></span>  
  
-   <span data-ttu-id="fcc1f-110">Ikona komponenty se nezobrazují v panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="fcc1f-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="fcc1f-111">Nelze přidat ovládací prvek na panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="fcc1f-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="fcc1f-112">Pokud chcete přidat vlastní ovládací prvek, který jste vytvořili v jiném projektu nebo ovládací prvek třetích stran pro **nástrojů**, musíte to udělat ručně.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="fcc1f-113">Pokud projekt obsahuje ovládacího prvku nebo komponenty, měl by se zobrazit v **nástrojů** automaticky.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="fcc1f-114">Další informace najdete v tématu [názorný postup: Automatické vyplnění nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="fcc1f-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="fcc1f-115">Přidání ovládacího prvku na panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="fcc1f-115">To add a control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="fcc1f-116">Klikněte pravým tlačítkem myši **nástrojů** a v místní nabídce vyberte **zvolit položky**.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2.  <span data-ttu-id="fcc1f-117">V **zvolit položky nástrojů** dialogovém okně přidejte komponentu:</span><span class="sxs-lookup"><span data-stu-id="fcc1f-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    -   <span data-ttu-id="fcc1f-118">Pokud chcete přidat do součásti rozhraní .NET Framework nebo ovládacího prvku, klikněte na tlačítko **součásti rozhraní .NET Framework** kartu.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="fcc1f-119">– nebo –</span><span class="sxs-lookup"><span data-stu-id="fcc1f-119">– or –</span></span>  
  
    -   <span data-ttu-id="fcc1f-120">Pokud chcete přidat komponenty modelu COM nebo ovládacího prvku ActiveX, klikněte na tlačítko **komponenty modelu COM** kartu.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3.  <span data-ttu-id="fcc1f-121">Pokud váš ovládací prvek je uvedený v dialogovém okně, potvrďte je vybraná a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="fcc1f-122">Ovládací prvek je přidán do **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-122">The control is added to the **Toolbox**.</span></span>  
  
4.  <span data-ttu-id="fcc1f-123">Pokud váš ovládací prvek není uveden v dialogovém okně, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="fcc1f-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="fcc1f-124">Klikněte na tlačítko **Procházet** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-124">Click the **Browse** button.</span></span>  
  
    2.  <span data-ttu-id="fcc1f-125">Přejděte do složky obsahující soubor .dll, který obsahuje ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3.  <span data-ttu-id="fcc1f-126">Vyberte soubor .dll a klikněte na tlačítko **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="fcc1f-127">V dialogovém okně se zobrazí váš ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-127">Your control appears in the dialog box.</span></span>  
  
    4.  <span data-ttu-id="fcc1f-128">Potvrďte, že je vybraný ovládací prvek a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="fcc1f-129">Váš ovládací prvek je přidán do **nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="fcc1f-130">Nelze ladit uživatelského ovládacího prvku formulářů Windows nebo komponenty</span><span class="sxs-lookup"><span data-stu-id="fcc1f-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="fcc1f-131">Pokud váš ovládací prvek odvozen z <xref:System.Windows.Forms.UserControl> třídy, můžete ladit jeho chování za běhu pomocí testovacího kontejneru.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="fcc1f-132">Další informace najdete v tématu [jak: Testování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="fcc1f-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="fcc1f-133">Další vlastní ovládací prvky a součásti nejsou samostatné projekty.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="fcc1f-134">Musí být hostovaný jako je například projekt aplikace Windows Forms a aplikací.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="fcc1f-135">Chcete-li ladit ovládací prvek nebo komponenty, třeba přidat ji do projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="fcc1f-136">Chcete-li ladit ovládací prvek nebo komponenty</span><span class="sxs-lookup"><span data-stu-id="fcc1f-136">To debug a control or component</span></span>  
  
1.  <span data-ttu-id="fcc1f-137">Z **sestavení** nabídky, klikněte na tlačítko **sestavit řešení** sestavení potřebného řešení.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2.  <span data-ttu-id="fcc1f-138">Z **souboru** nabídce zvolte **přidat**a potom **nový projekt** přidáte projekt testu do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3.  <span data-ttu-id="fcc1f-139">V **přidat nový projekt** dialogové okno zvolit **aplikace Windows** pro typ projektu.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4.  <span data-ttu-id="fcc1f-140">V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **odkazy** uzlu pro nový projekt.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="fcc1f-141">V místní nabídce klikněte na tlačítko **přidat odkaz** přidáte odkaz na projekt, který obsahuje ovládací prvek nebo komponenty.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5.  <span data-ttu-id="fcc1f-142">Vytvořte instanci ovládacího prvku nebo komponenty v testovém projektu.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="fcc1f-143">Pokud vaše komponenta je v **nástrojů**, ji můžete přetáhnout do návrhové ploše, nebo můžete vytvořit instanci prostřednictvím kódu programu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="fcc1f-144">Teď můžete ladit ovládacího prvku nebo komponenty jako obvykle.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="fcc1f-145">Další informace o ladění naleznete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) a [názorný postup: Ovládací prvky ladění vlastního Windows Forms v době návrhu](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="fcc1f-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="fcc1f-146">Událost se vyvolá dvakrát v zděděný ovládací prvek nebo komponenty</span><span class="sxs-lookup"><span data-stu-id="fcc1f-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="fcc1f-147">To je pravděpodobně v důsledku duplikovaného `Handles` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="fcc1f-148">Další informace najdete v tématu [řešení potíží s zděděné obslužných rutin událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="fcc1f-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="fcc1f-149">Chyba návrhu: "Nepovedlo se vytvořit komponentu 'název součásti."</span><span class="sxs-lookup"><span data-stu-id="fcc1f-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="fcc1f-150">Součást nebo ovládací prvek, musíte zadat výchozí konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-150">Your component or control must provide a default constructor with no parameters.</span></span> <span data-ttu-id="fcc1f-151">Při návrhu prostředí vytvoří instanci součást nebo ovládací prvek, nebude pokoušet o poskytovat žádné parametry pro přetížení konstruktoru, které přijímají parametry.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="fcc1f-152">Atribut STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="fcc1f-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="fcc1f-153"><xref:System.STAThreadAttribute> Informuje common language runtime (CLR), Windows Forms používá jednovláknový apartment modelu.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="fcc1f-154">Pokud použijete tento atribut není pro aplikace Windows Forms může dojít k neúmyslnému chování `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="fcc1f-155">Například nemusí zobrazit obrázky na pozadí pro ovládací prvky jako <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="fcc1f-156">Některé ovládací prvky budete možná muset tento atribut pro správné funkce automatického dokončování a chování a přetažení.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="fcc1f-157">Ikona komponenty se nezobrazují v panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="fcc1f-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="fcc1f-158">Při použití <xref:System.Drawing.ToolboxBitmapAttribute> na vlastní komponentu přidružit ikonu, nezobrazí rastrového obrázku panelu nástrojů pro automaticky generované součásti.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="fcc1f-159">Rastrový obrázek zobrazíte načtěte pomocí ovládacího prvku **zvolit položky nástrojů** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="fcc1f-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="fcc1f-160">Další informace najdete v tématu [jak: Poskytnutí rastrového obrázku panelu nástrojů pro ovládací prvek](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="fcc1f-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc1f-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcc1f-161">See also</span></span>

- [<span data-ttu-id="fcc1f-162">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="fcc1f-162">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="fcc1f-163">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="fcc1f-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="fcc1f-164">Postupy: Otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="fcc1f-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="fcc1f-165">Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu</span><span class="sxs-lookup"><span data-stu-id="fcc1f-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="fcc1f-166">Tvorba komponent</span><span class="sxs-lookup"><span data-stu-id="fcc1f-166">Component Authoring</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))
- [<span data-ttu-id="fcc1f-167">Řešení potíží s vývojem během návrhu</span><span class="sxs-lookup"><span data-stu-id="fcc1f-167">Troubleshooting Design-Time Development</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
