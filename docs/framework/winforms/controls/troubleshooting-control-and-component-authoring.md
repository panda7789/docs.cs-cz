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
ms.openlocfilehash: 9100d6dc41f982af340d747ad447009a183b3c7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540976"
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="ba196-102">Řešení potíží s vytvářením ovládacích prvků a komponent</span><span class="sxs-lookup"><span data-stu-id="ba196-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="ba196-103">Toto téma obsahuje následující běžné problémy, které nastat při vývoji komponent a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ba196-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="ba196-104">Další informace najdete v tématu [programování s komponentami](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span><span class="sxs-lookup"><span data-stu-id="ba196-104">For more information, see [Programming with Components](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span></span>  
  
-   <span data-ttu-id="ba196-105">Ovládací prvek nelze přidat do sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="ba196-105">Cannot Add Control to Toolbox</span></span>  
  
-   <span data-ttu-id="ba196-106">Nelze ladění ovládacího prvku Windows Forms uživatele nebo součást</span><span class="sxs-lookup"><span data-stu-id="ba196-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
-   <span data-ttu-id="ba196-107">Událost se vyvolá dvakrát v komponenta nebo ovládací prvek zděděné</span><span class="sxs-lookup"><span data-stu-id="ba196-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
-   <span data-ttu-id="ba196-108">Chyba při návrhu: "Nepodařilo se vytvořit komponentu '*název komponenty*'"</span><span class="sxs-lookup"><span data-stu-id="ba196-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
-   <span data-ttu-id="ba196-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="ba196-109">STAThreadAttribute</span></span>  
  
-   <span data-ttu-id="ba196-110">Ikona součást nezobrazí v sadě nástrojů</span><span class="sxs-lookup"><span data-stu-id="ba196-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="ba196-111">Ovládací prvek nelze přidat do sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="ba196-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="ba196-112">Pokud chcete přidat vlastní ovládací prvek, který jste vytvořili v jiném projektu nebo ovládacím prvkem třetí strany, který **sada nástrojů**, je potřeba udělat to ručně.</span><span class="sxs-lookup"><span data-stu-id="ba196-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="ba196-113">Pokud aktuální projekt obsahuje komponenta nebo ovládací prvek, mělo by se zobrazit v **sada nástrojů** automaticky.</span><span class="sxs-lookup"><span data-stu-id="ba196-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="ba196-114">Další informace najdete v tématu [návod: Automatické vyplnění nástrojů s komponentami vlastní](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="ba196-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="ba196-115">Přidání ovládacího prvku do sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="ba196-115">To add a control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="ba196-116">Klikněte pravým tlačítkem myši **sada nástrojů** a z místní nabídky vyberte **zvolit položky**.</span><span class="sxs-lookup"><span data-stu-id="ba196-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2.  <span data-ttu-id="ba196-117">V **výběr položek sady nástrojů** dialogové okno pole, přidejte komponentu:</span><span class="sxs-lookup"><span data-stu-id="ba196-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    -   <span data-ttu-id="ba196-118">Pokud chcete přidat součásti rozhraní .NET Framework nebo ovládací prvek, klikněte **součásti rozhraní .NET Framework** kartě.</span><span class="sxs-lookup"><span data-stu-id="ba196-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="ba196-119">– nebo –</span><span class="sxs-lookup"><span data-stu-id="ba196-119">– or –</span></span>  
  
    -   <span data-ttu-id="ba196-120">Pokud chcete přidat komponenty modelu COM nebo ovládací prvek ActiveX, klikněte **COM – součásti** kartě.</span><span class="sxs-lookup"><span data-stu-id="ba196-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3.  <span data-ttu-id="ba196-121">Pokud vlastní ovládací prvek je uveden v dialogovém okně, potvrďte je vybrána a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="ba196-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ba196-122">Ovládací prvek je přidán do **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="ba196-122">The control is added to the **Toolbox**.</span></span>  
  
4.  <span data-ttu-id="ba196-123">Pokud vlastní ovládací prvek není uveden v dialogovém okně, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="ba196-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="ba196-124">Klikněte **Procházet** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="ba196-124">Click the **Browse** button.</span></span>  
  
    2.  <span data-ttu-id="ba196-125">Přejděte do složky, která obsahuje soubor .dll, který obsahuje vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ba196-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3.  <span data-ttu-id="ba196-126">Vyberte soubor .dll a klikněte na tlačítko **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="ba196-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="ba196-127">V dialogovém okně se zobrazí vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba196-127">Your control appears in the dialog box.</span></span>  
  
    4.  <span data-ttu-id="ba196-128">Potvrďte, že je vybraná vlastního ovládacího prvku a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="ba196-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="ba196-129">Vlastní ovládací prvek je přidán do **sada nástrojů**.</span><span class="sxs-lookup"><span data-stu-id="ba196-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="ba196-130">Nelze ladění ovládacího prvku Windows Forms uživatele nebo součást</span><span class="sxs-lookup"><span data-stu-id="ba196-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="ba196-131">Pokud vaše ovládací prvek odvozen z <xref:System.Windows.Forms.UserControl> třídu, můžete ladit, její chování pomocí testovacího kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ba196-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="ba196-132">Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="ba196-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="ba196-133">Další vlastní ovládací prvky a součásti nejsou samostatné projekty.</span><span class="sxs-lookup"><span data-stu-id="ba196-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="ba196-134">Musí být hostované aplikací, třeba Windows Forms projektu.</span><span class="sxs-lookup"><span data-stu-id="ba196-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="ba196-135">Chcete-li ladit komponenta nebo ovládací prvek, musíte jej přidat do projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ba196-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="ba196-136">Chcete-li ladit komponenta nebo ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="ba196-136">To debug a control or component</span></span>  
  
1.  <span data-ttu-id="ba196-137">Z **sestavení** nabídky, klikněte na tlačítko **sestavit řešení** k vytvoření vlastního řešení.</span><span class="sxs-lookup"><span data-stu-id="ba196-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2.  <span data-ttu-id="ba196-138">Z **soubor** nabídce zvolte **přidat**a potom **nový projekt** k přidání testovacího projektu do aplikace.</span><span class="sxs-lookup"><span data-stu-id="ba196-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3.  <span data-ttu-id="ba196-139">V **přidat nový projekt** dialogové okno Vybrat **aplikace Windows** pro typ projektu.</span><span class="sxs-lookup"><span data-stu-id="ba196-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4.  <span data-ttu-id="ba196-140">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** uzel pro nový projekt.</span><span class="sxs-lookup"><span data-stu-id="ba196-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="ba196-141">V místní nabídce klikněte na tlačítko **přidat odkaz na** se přidat odkaz na projekt obsahující komponenta nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ba196-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5.  <span data-ttu-id="ba196-142">Vytvoření instance komponenta nebo ovládací prvek v k testovacímu projektu.</span><span class="sxs-lookup"><span data-stu-id="ba196-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="ba196-143">Pokud příslušné součásti **sada nástrojů**, přetáhněte jej do vaší plochu návrháře, nebo můžete vytvořit instanci programově, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="ba196-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="ba196-144">Můžete teď ladit komponenta nebo ovládací prvek jako obvykle.</span><span class="sxs-lookup"><span data-stu-id="ba196-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="ba196-145">Další informace o ladění najdete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) a [návod: ladění vlastních ovládacích prvků Windows Forms v době návrhu](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="ba196-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="ba196-146">Událost se vyvolá dvakrát v komponenta nebo ovládací prvek zděděné</span><span class="sxs-lookup"><span data-stu-id="ba196-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="ba196-147">Je to pravděpodobně z důvodu duplicitní `Handles` klauzule.</span><span class="sxs-lookup"><span data-stu-id="ba196-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="ba196-148">Další informace najdete v tématu [řešení potíží s zděděná obslužné rutiny událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="ba196-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="ba196-149">Chyba při návrhu: "Nepodařilo se vytvořit komponentu 'název komponenty."</span><span class="sxs-lookup"><span data-stu-id="ba196-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="ba196-150">Komponenta nebo ovládací prvek, musíte zadat výchozí konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="ba196-150">Your component or control must provide a default constructor with no parameters.</span></span> <span data-ttu-id="ba196-151">Při návrhu prostředí vytvoří instanci komponenta nebo ovládací prvek, nepokouší poskytnout ke konstruktor přetížení, které provést parametry žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="ba196-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="ba196-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="ba196-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="ba196-153"><xref:System.STAThreadAttribute> Common language runtime (CLR) informuje, že Windows Forms používá model single-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="ba196-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="ba196-154">Nežádoucí chování může dojít, pokud tento atribut nelze použít k vaší aplikaci Windows Forms `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="ba196-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="ba196-155">Obrázky na pozadí nemusí zobrazit třeba pro ovládací prvky <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="ba196-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="ba196-156">Některé ovládací prvky může také vyžadovat tento atribut pro správné automatického dokončování a chování přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="ba196-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="ba196-157">Ikona součást nezobrazí v sadě nástrojů</span><span class="sxs-lookup"><span data-stu-id="ba196-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="ba196-158">Při použití <xref:System.Drawing.ToolboxBitmapAttribute> pro vaše vlastní komponenta přidružit ikonu, bitmapy nezobrazí v sadě nástrojů pro součásti generován automaticky.</span><span class="sxs-lookup"><span data-stu-id="ba196-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="ba196-159">Informace o bitové mapy, znovu načíst ovládacího prvku pomocí **výběr položek sady nástrojů** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="ba196-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="ba196-160">Další informace najdete v tématu [postupy: poskytování rastrového obrázku panelu nástrojů pro ovládací prvek](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="ba196-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba196-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba196-161">See Also</span></span>  
 [<span data-ttu-id="ba196-162">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="ba196-162">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="ba196-163">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="ba196-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [<span data-ttu-id="ba196-164">Postupy: Otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="ba196-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [<span data-ttu-id="ba196-165">Návod: Ladění vlastních ovládacích prvků Windows Forms během návrhu</span><span class="sxs-lookup"><span data-stu-id="ba196-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="ba196-166">Tvorba komponent</span><span class="sxs-lookup"><span data-stu-id="ba196-166">Component Authoring</span></span>](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 [<span data-ttu-id="ba196-167">Řešení potíží s vývoj návrhu</span><span class="sxs-lookup"><span data-stu-id="ba196-167">Troubleshooting Design-Time Development</span></span>](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [<span data-ttu-id="ba196-168">Programování s komponentami</span><span class="sxs-lookup"><span data-stu-id="ba196-168">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
