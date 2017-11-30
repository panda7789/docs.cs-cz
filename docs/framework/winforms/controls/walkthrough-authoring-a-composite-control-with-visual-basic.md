---
title: "Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basic"
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
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c86a3d420b85c1287597cda738c6d72f0433d0f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="6ee28-102">Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6ee28-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="6ee28-103">Složené ovládací prvky poskytují prostředky, pomocí kterého lze vytvořit vlastní grafické rozhraní a znovu použít.</span><span class="sxs-lookup"><span data-stu-id="6ee28-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="6ee28-104">Složeného ovládacího prvku je v podstatě součást s vizuální reprezentace.</span><span class="sxs-lookup"><span data-stu-id="6ee28-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="6ee28-105">Takto může obsahovat jeden nebo více Windows Forms – ovládací prvky, komponenty nebo bloky kódu, který můžete rozšířit funkce ověřování uživatelského vstupu, změnou vlastností zobrazení nebo provádění jiných úloh vyžaduje autorem.</span><span class="sxs-lookup"><span data-stu-id="6ee28-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="6ee28-106">Složené ovládací prvky můžete umístit v rozhraní Windows Forms stejným způsobem jako další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="6ee28-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="6ee28-107">V první části tohoto návodu, vytvořte jednoduché složeného ovládacího prvku názvem `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="6ee28-108">V druhé části tohoto průvodce, můžete rozšířit funkce `ctlClock` prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="6ee28-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ee28-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="6ee28-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6ee28-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="6ee28-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6ee28-111">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="6ee28-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="6ee28-112">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="6ee28-112">Creating the Project</span></span>  
 <span data-ttu-id="6ee28-113">Když vytvoříte nový projekt, je třeba zadat jeho název nastavení kořenového oboru názvů, název sestavení a název projektu a ujistěte se, že komponentu výchozí bude ve správném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6ee28-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="6ee28-114">K vytvoření knihovny řízení ctlClockLib a ctlClock ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="6ee28-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="6ee28-115">Na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu** otevřete **nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="6ee28-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="6ee28-116">Ze seznamu [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projekty, vyberte **knihovny ovládacích prvků Windows** šablona projektu, typ `ctlClockLib` v **název** pole a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-116">From the list of [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="6ee28-117">Název projektu `ctlClockLib`, je také přiřazený k oboru názvů root ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="6ee28-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="6ee28-118">Kořenový obor názvů se použijí pro kvalifikaci názvy součásti v sestavení.</span><span class="sxs-lookup"><span data-stu-id="6ee28-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="6ee28-119">Například, pokud dvě sestavení poskytují komponenty s názvem `ctlClock`, můžete zadat vaše `ctlClock` pomocí součásti`ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="6ee28-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="6ee28-120">V Průzkumníku řešení klikněte pravým tlačítkem na **UserControl1.vb**a potom klikněte na **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-120">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="6ee28-121">Změňte název souboru `ctlClock.vb`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-121">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="6ee28-122">Klikněte **Ano** tlačítko po zobrazení dotazu, pokud chcete přejmenovat všechny odkazy na tento element kódu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="6ee28-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ee28-123">Ve výchozím nastavení, zdědí složeného ovládacího prvku <xref:System.Windows.Forms.UserControl> třída poskytuje systém.</span><span class="sxs-lookup"><span data-stu-id="6ee28-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="6ee28-124"><xref:System.Windows.Forms.UserControl> Třída poskytuje funkce, které vyžadují všechny složené ovládací prvky a implementuje standardní metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6ee28-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="6ee28-125">Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** k uložení projektu.</span><span class="sxs-lookup"><span data-stu-id="6ee28-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="6ee28-126">Přidání Windows ovládací prvky a součásti složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="6ee28-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="6ee28-127">Vizuální rozhraní je zásadní součástí vaší složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6ee28-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="6ee28-128">Toto visual rozhraní je implementováno modulem přidání jednoho nebo více ovládacích prvků Windows na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="6ee28-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="6ee28-129">V následující ukázce se ovládací prvky Windows začlenit do vaší složeného ovládacího prvku a napsat kód pro implementaci funkcí.</span><span class="sxs-lookup"><span data-stu-id="6ee28-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="6ee28-130">Přidat k vaší složeného ovládacího prvku popisek a časovač</span><span class="sxs-lookup"><span data-stu-id="6ee28-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="6ee28-131">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClock.vb**a potom klikněte na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-131">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="6ee28-132">V sadě nástrojů, rozbalte **běžné ovládací prvky** uzel a poté dvojitým kliknutím **popisek**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-132">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="6ee28-133">A <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1` se přidá do vašeho ovládacího prvku na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="6ee28-133">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="6ee28-134">V návrháři, klikněte na tlačítko **Label1**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-134">In the designer, click **Label1**.</span></span> <span data-ttu-id="6ee28-135">V okně vlastností nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6ee28-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="6ee28-136">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="6ee28-136">Property</span></span>|<span data-ttu-id="6ee28-137">Změňte na</span><span class="sxs-lookup"><span data-stu-id="6ee28-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="6ee28-138">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="6ee28-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="6ee28-139">**Text**</span><span class="sxs-lookup"><span data-stu-id="6ee28-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="6ee28-140">**Zarovnání textu**</span><span class="sxs-lookup"><span data-stu-id="6ee28-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="6ee28-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="6ee28-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="6ee28-142">V **sada nástrojů**, rozbalte **součásti** uzel a poté dvojitým kliknutím **časovače**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="6ee28-143">Protože <xref:System.Windows.Forms.Timer> je komponenta, nemá žádné vizuální znázornění za běhu.</span><span class="sxs-lookup"><span data-stu-id="6ee28-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="6ee28-144">Proto se nezobrazí s ovládacími prvky na plochu návrháře, ale v Návrháři součástí (panelu v dolní části plochu návrháře).</span><span class="sxs-lookup"><span data-stu-id="6ee28-144">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="6ee28-145">V Návrháři součástí, klikněte na tlačítko **Timer1**a poté nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `1000` a <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `True`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-145">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>  
  
     <span data-ttu-id="6ee28-146"><xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost řídí frekvenci, se kterým komponenta časovač značek.</span><span class="sxs-lookup"><span data-stu-id="6ee28-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="6ee28-147">Pokaždé, když `Timer1` rysky, spuštěním kódu `Timer1_Tick` událostí.</span><span class="sxs-lookup"><span data-stu-id="6ee28-147">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="6ee28-148">Interval představuje počet milisekund, po mezi značky.</span><span class="sxs-lookup"><span data-stu-id="6ee28-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="6ee28-149">V Návrháři součástí, klikněte dvakrát na **Timer1** přejít na `Timer1_Tick` událost pro `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-149">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="6ee28-150">Upravte kód tak, aby je podobná následující ukázka kódu.</span><span class="sxs-lookup"><span data-stu-id="6ee28-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="6ee28-151">Ujistěte se, chcete-li změnit – modifikátor přístupu z `Private` k `Protected`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-151">Be sure to change the access modifier from `Private` to `Protected`.</span></span>  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     <span data-ttu-id="6ee28-152">Tento kód způsobí, že aktuální čas zobrazený v `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="6ee28-153">Protože interval `Timer1` byla nastavena na `1000`, tato událost se stane každých tisíc milisekund, proto aktualizace aktuální čas každou sekundu.</span><span class="sxs-lookup"><span data-stu-id="6ee28-153">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="6ee28-154">Změňte metodu být přepisovatelné.</span><span class="sxs-lookup"><span data-stu-id="6ee28-154">Modify the method to be overridable.</span></span> <span data-ttu-id="6ee28-155">Další informace najdete v části ", která dědí z uživatelského ovládacího prvku" níže.</span><span class="sxs-lookup"><span data-stu-id="6ee28-155">For more information, see the "Inheriting from a User Control" section below.</span></span>  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. <span data-ttu-id="6ee28-156">Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** k uložení projektu.</span><span class="sxs-lookup"><span data-stu-id="6ee28-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="6ee28-157">Přidání vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="6ee28-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="6ee28-158">Vlastní ovládací prvek hodiny nyní zapouzdří <xref:System.Windows.Forms.Label> řízení a <xref:System.Windows.Forms.Timer> součást, každou s vlastní sadou vyplývajících vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6ee28-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="6ee28-159">Zatímco jednotlivé vlastnosti těchto ovládacích prvků nebude přístupný uživatelům následné ovládacího prvku, můžete vytvořit a vystavení vlastní vlastnosti napsáním odpovídající bloky kódu.</span><span class="sxs-lookup"><span data-stu-id="6ee28-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="6ee28-160">V následujícím postupu bude přidávat vlastnosti pro vaše ovládací prvek, který uživateli umožňuje změnit barvu pozadí a text.</span><span class="sxs-lookup"><span data-stu-id="6ee28-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="6ee28-161">Přidání vlastnosti do vašeho složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="6ee28-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="6ee28-162">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClock.vb**a potom klikněte na **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-162">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="6ee28-163">Otevře se Editor kódu pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="6ee28-163">The Code Editor for your control opens.</span></span>  
  
2.  <span data-ttu-id="6ee28-164">Vyhledejte `Public Class ctlClock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6ee28-164">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="6ee28-165">Pod, zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="6ee28-165">Beneath it, type the following code.</span></span>  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     <span data-ttu-id="6ee28-166">Tyto příkazy vytvářet soukromé proměnné, které budete používat k ukládání hodnoty pro vlastnosti, které se chystáte vytvořit.</span><span class="sxs-lookup"><span data-stu-id="6ee28-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="6ee28-167">Vložte následující kód pod deklarace proměnných z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="6ee28-167">Insert the following code beneath the variable declarations from step 2.</span></span>  
  
    ```vb  
    ' Declares the name and type of the property.  
    Property ClockBackColor() as Color  
        ' Retrieves the value of the private variable colBColor.  
        Get  
            Return colBColor  
        End Get  
        ' Stores the selected value in the private variable colBColor, and   
        ' updates the background color of the label control lblDisplay.  
        Set(ByVal value as Color)  
            colBColor = value  
            lblDisplay.BackColor = colBColor     
        End Set  
  
    End Property  
    ' Provides a similar set of instructions for the foreground color.  
    Property ClockForeColor() as Color  
        Get  
            Return colFColor  
        End Get  
        Set(ByVal value as Color)  
            colFColor = value  
            lblDisplay.ForeColor = colFColor  
        End Set  
    End Property  
    ```  
  
     <span data-ttu-id="6ee28-168">Předchozí kód vytvoří dvě vlastní vlastnosti `ClockForeColor` a `ClockBackColor`, k dispozici pro další uživatelé tohoto ovládacího prvku vyvoláním `Property` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6ee28-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="6ee28-169">`Get` a `Set` příkazy zadat pro ukládání a načítání hodnotu vlastnosti, jakož i kód implementovat funkce, které jsou vhodné pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6ee28-169">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="6ee28-170">Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** k uložení projektu.</span><span class="sxs-lookup"><span data-stu-id="6ee28-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="6ee28-171">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="6ee28-171">Testing the Control</span></span>  
 <span data-ttu-id="6ee28-172">Ovládací prvky nejsou samostatné projekty; musí být hostované v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6ee28-172">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="6ee28-173">Testování chování ovládacího prvku a jeho vlastnosti s vykonávat **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="6ee28-174">Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="6ee28-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="6ee28-175">K otestování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="6ee28-175">To test your control</span></span>  
  
1.  <span data-ttu-id="6ee28-176">Stiskněte klávesu F5, aby se projekt sestavil a spuštění vlastního ovládacího prvku v **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="6ee28-177">V mřížce vlastnost kontejner testů, vyberte `ClockBackColor` vlastnost a potom klikněte na šipku rozevíracího seznamu zobrazíte paletu barev.</span><span class="sxs-lookup"><span data-stu-id="6ee28-177">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>  
  
3.  <span data-ttu-id="6ee28-178">Vyberte barvu kliknutím.</span><span class="sxs-lookup"><span data-stu-id="6ee28-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="6ee28-179">Barva pozadí ovládacího prvku změny barev, které jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="6ee28-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="6ee28-180">Ověřte, že pomocí posloupnost událostí, podobně jako `ClockForeColor` vlastnost funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="6ee28-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
5.  <span data-ttu-id="6ee28-181">Klikněte na tlačítko **zavřete** zavřete **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-181">Click **Close** to close the **UserControl Test Container**.</span></span>  
  
     <span data-ttu-id="6ee28-182">V této části a v předchozích částech, jste viděli, jak mohou být kombinovány komponenty a ovládací prvky Windows s kódem a balení vlastní nakonfigurovánu ve formě složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6ee28-182">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="6ee28-183">Naučili jste se vystavení vlastností ve vaší složeného ovládacího prvku a po dokončení testování vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6ee28-183">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="6ee28-184">V další části se dozvíte, jak vytvořit k zděděné složeného ovládacího prvku pomocí `ctlClock` jako základ.</span><span class="sxs-lookup"><span data-stu-id="6ee28-184">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="6ee28-185">Dědění z složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="6ee28-185">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="6ee28-186">V předchozích částech jste zjistili, jak kombinovat ovládací prvky systému Windows, komponent a kód do opakovatelně použitelných složené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="6ee28-186">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="6ee28-187">Vaše složeného ovládacího prvku nyní slouží jako základ, na kterém se dají vytvářet další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="6ee28-187">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="6ee28-188">Proces odvození třídy z základní třídy se nazývá *dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="6ee28-188">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="6ee28-189">V této části vytvoříte složeného ovládacího prvku názvem `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-189">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="6ee28-190">Tento ovládací prvek bude odvozena z jeho nadřazenému ovládacímu prvku `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-190">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="6ee28-191">Naučíte se rozšířit funkce `ctlClock` přepsání metody nadřazené a přidáním nových metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="6ee28-191">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="6ee28-192">Prvním krokem při vytvoření ovládacího prvku zděděné je odvozena z nadřazené.</span><span class="sxs-lookup"><span data-stu-id="6ee28-192">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="6ee28-193">Tato akce vytvoří nový ovládací prvek, který má všechny vlastnosti, metod a grafické vlastnosti nadřazeného ovládacího prvku, ale mohou chovat i jako základ pro přidání nové nebo změněné funkce.</span><span class="sxs-lookup"><span data-stu-id="6ee28-193">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="6ee28-194">Vytvoření zděděné ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="6ee28-194">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="6ee28-195">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClockLib**, přejděte na příkaz **přidat**a potom klikněte na **uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-195">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="6ee28-196">**Přidat novou položku** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="6ee28-196">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="6ee28-197">Vyberte **zděděná uživatelský ovládací prvek** šablony.</span><span class="sxs-lookup"><span data-stu-id="6ee28-197">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="6ee28-198">V **název** zadejte `ctlAlarmClock.vb`a potom klikněte na **přidat**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-198">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="6ee28-199">**Výběr dědičnosti** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="6ee28-199">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="6ee28-200">V části **název komponenty**, dvakrát klikněte na **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-200">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="6ee28-201">V Průzkumníku řešení procházet aktuální projekty.</span><span class="sxs-lookup"><span data-stu-id="6ee28-201">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ee28-202">Soubor nazývá **ctlAlarmClock.vb** byla přidána do aktuálního projektu.</span><span class="sxs-lookup"><span data-stu-id="6ee28-202">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="6ee28-203">Přidání vlastnosti výstrahy</span><span class="sxs-lookup"><span data-stu-id="6ee28-203">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="6ee28-204">Vlastnosti jsou přidány do ovládacího prvku zděděné stejným způsobem, které budou přidány do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6ee28-204">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="6ee28-205">Teď použijete syntaxe deklarace vlastnost přidat dvě vlastnosti do vlastního ovládacího prvku: `AlarmTime`, který uloží hodnotu data a je čas vypnutí, a `AlarmSet`, který udává, zda je nastaven na upozornění.</span><span class="sxs-lookup"><span data-stu-id="6ee28-205">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="6ee28-206">Přidání vlastnosti do složených prvků</span><span class="sxs-lookup"><span data-stu-id="6ee28-206">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="6ee28-207">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock**a potom klikněte na **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-207">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="6ee28-208">Vyhledejte deklaraci třídy pro řízení ctlAlarmClock, které se zobrazí jako `Public Class ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-208">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="6ee28-209">V deklaraci třídy vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="6ee28-209">In the class declaration, insert the following code.</span></span>  
  
    ```vb  
    Private dteAlarmTime As Date  
    Private blnAlarmSet As Boolean  
    ' These properties will be declared as Public to allow future   
    ' developers to access them.  
    Public Property AlarmTime() As Date  
        Get  
            Return dteAlarmTime  
        End Get  
        Set(ByVal value as Date)  
            dteAlarmTime = value  
        End Set  
    End Property  
    Public Property AlarmSet() As Boolean  
        Get  
            Return blnAlarmSet  
        End Get  
        Set(ByVal value as Boolean)  
            blnAlarmSet = value  
        End Set  
    End Property  
    ```  
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="6ee28-210">Přidávání do grafické rozhraní ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="6ee28-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="6ee28-211">Vizuální rozhraní, který je stejný jako ovládací prvek, který dědí z má vlastní zděděné ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="6ee28-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="6ee28-212">Má k dispozici stejný základní ovládací prvky jako jeho nadřazenému ovládacímu prvku, ale vlastností základních ovládacích prvků nebudete mít k dispozici, pokud byly konkrétně vystavené.</span><span class="sxs-lookup"><span data-stu-id="6ee28-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="6ee28-213">Můžete přidat na grafické rozhraní zděděné složeného ovládacího prvku stejným způsobem jako přidáváte do jakékoli složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6ee28-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="6ee28-214">Chcete-li pokračovat, přidávání do rozhraní visual alarmů hodiny, přidáte ovládacího prvku popisek, který bude flash, když je zvukově na upozornění.</span><span class="sxs-lookup"><span data-stu-id="6ee28-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="6ee28-215">Přidání ovládacího prvku popisek</span><span class="sxs-lookup"><span data-stu-id="6ee28-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="6ee28-216">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock**a klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-216">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>  
  
     <span data-ttu-id="6ee28-217">Návrhář pro `ctlAlarmClock` otevře v hlavním okně.</span><span class="sxs-lookup"><span data-stu-id="6ee28-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="6ee28-218">Klikněte na tlačítko `lblDisplay` (část zobrazení ovládacího prvku) a zobrazte okno vlastností.</span><span class="sxs-lookup"><span data-stu-id="6ee28-218">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ee28-219">Když se zobrazí všechny vlastnosti, jsou neaktivní.</span><span class="sxs-lookup"><span data-stu-id="6ee28-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="6ee28-220">To znamená, že tyto vlastnosti jsou nativní pro `lblDisplay` a nelze změnit ani získat přístup v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6ee28-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="6ee28-221">Ve výchozím nastavení, jsou součástí složeného ovládacího prvku – ovládací prvky `Private`, a jejich vlastnosti nejsou dostupné žádné prostředky.</span><span class="sxs-lookup"><span data-stu-id="6ee28-221">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ee28-222">Pokud chcete další uživatelé složeného ovládacího prvku tak, aby měl přístup k jeho interní kontrolní mechanismy, deklarovat je jako `Public` nebo `Protected`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="6ee28-223">To vám umožní nastavit a úpravy vlastností ovládacích prvků, které jsou obsažené v rámci vaší složeného ovládacího prvku pomocí správný kód.</span><span class="sxs-lookup"><span data-stu-id="6ee28-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="6ee28-224">Přidat <xref:System.Windows.Forms.Label> řízení pro vaše složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6ee28-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="6ee28-225">Pomocí myši, přetáhněte <xref:System.Windows.Forms.Label> ovládací prvek bezprostředně pod rozevíracím seznamu zobrazit.</span><span class="sxs-lookup"><span data-stu-id="6ee28-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="6ee28-226">V okně vlastností nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6ee28-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="6ee28-227">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="6ee28-227">Property</span></span>|<span data-ttu-id="6ee28-228">Nastavení</span><span class="sxs-lookup"><span data-stu-id="6ee28-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="6ee28-229">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="6ee28-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="6ee28-230">**Text**</span><span class="sxs-lookup"><span data-stu-id="6ee28-230">**Text**</span></span>|<span data-ttu-id="6ee28-231">**Varování!**</span><span class="sxs-lookup"><span data-stu-id="6ee28-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="6ee28-232">**Zarovnání textu**</span><span class="sxs-lookup"><span data-stu-id="6ee28-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="6ee28-233">**Viditelné**</span><span class="sxs-lookup"><span data-stu-id="6ee28-233">**Visible**</span></span>|`False`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="6ee28-234">Přidání funkce výstrahy</span><span class="sxs-lookup"><span data-stu-id="6ee28-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="6ee28-235">V předchozích postupech jste přidali, vlastnosti a ovládací prvek, který vám umožní alarmů funkce ve vašem složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6ee28-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="6ee28-236">V tomto postupu přidáte kód, který porovná aktuální čas je čas alarmů a, pokud jsou stejné, a zvukových flash alarm.</span><span class="sxs-lookup"><span data-stu-id="6ee28-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="6ee28-237">Přepsáním `Timer1_Tick` metodu `ctlClock` a přidání další kód do, bude rozšířit schopnosti produktu `ctlAlarmClock` při zachování všech vyplývajících funkce `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-237">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="6ee28-238">Chcete-li přepsat metodě Timer1_Tick ctlClock</span><span class="sxs-lookup"><span data-stu-id="6ee28-238">To override the Timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="6ee28-239">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock.vb**a potom klikněte na **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-239">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="6ee28-240">Vyhledejte `Private blnAlarmSet As Boolean` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6ee28-240">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="6ee28-241">Bezprostředně pod něj přidejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="6ee28-241">Immediately beneath it, add the following statement.</span></span>  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  <span data-ttu-id="6ee28-242">Vyhledejte `End Class` příkaz v dolní části stránky.</span><span class="sxs-lookup"><span data-stu-id="6ee28-242">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="6ee28-243">Těsně před `End Class` prohlášení, přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="6ee28-243">Just before the `End Class` statement, add the following code.</span></span>  
  
    ```vb  
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _  
        As System.EventArgs)  
        ' Calls the Timer1_Tick method of ctlClock.  
        MyBase.Timer1_Tick(sender, e)  
        ' Checks to see if the Alarm is set.  
        If AlarmSet = False Then  
            Exit Sub  
        End If  
        ' If the date, hour, and minute of the alarm time are the same as  
        ' now, flash and beep an alarm.   
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _  
            AlarmTime.Minute = Now.Minute Then  
            ' Sounds an audible beep.  
            Beep()  
            ' Sets lblAlarmVisible to True, and changes the background color based on the   
            ' value of blnColorTicker. The background color of the label will   
            ' flash once per tick of the clock.  
            lblAlarm.Visible = True  
            If blnColorTicker = False Then  
                lblAlarm.BackColor = Color.PeachPuff  
                blnColorTicker = True  
            Else  
                lblAlarm.BackColor = Color.Plum  
                blnColorTicker = False  
            End If  
        Else  
            ' Once the alarm has sounded for a minute, the label is made   
            ' invisible again.  
            lblAlarm.Visible = False  
        End If  
    End Sub  
    ```  
  
     <span data-ttu-id="6ee28-244">Přidání tento kód provede několik úloh.</span><span class="sxs-lookup"><span data-stu-id="6ee28-244">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="6ee28-245">`Overrides` Příkaz přesměruje ovládací prvek, který chcete použít tuto metodu místo metody, která byla zděděna od základního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6ee28-245">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="6ee28-246">Když tato metoda je volána, zavolá metodu přepíše vyvoláním `MyBase.Timer1_Tick` prohlášení, zajistíte, že všechny funkce součástí původní ovládací prvek je uveden v tomto ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="6ee28-246">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="6ee28-247">Pak spustí další kód pro výstrahy funkce součástí.</span><span class="sxs-lookup"><span data-stu-id="6ee28-247">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="6ee28-248">Blikající ovládací prvek popisek se zobrazí při výskytu varování a zvukových zvukový signál bude buďte vyslyšeni.</span><span class="sxs-lookup"><span data-stu-id="6ee28-248">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ee28-249">Vzhledem k tomu, že přepíšete zděděné obslužnou rutinu, není nutné zadat událost s `Handles` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6ee28-249">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="6ee28-250">Události je již připojili.</span><span class="sxs-lookup"><span data-stu-id="6ee28-250">The event is already hooked up.</span></span> <span data-ttu-id="6ee28-251">Všechny, které jsou přepisování je implementace obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="6ee28-251">All you are overriding is the implementation of the handler.</span></span>  
  
     <span data-ttu-id="6ee28-252">Vlastní ovládací prvek alarmů hodiny je téměř dokončena.</span><span class="sxs-lookup"><span data-stu-id="6ee28-252">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="6ee28-253">Jediné, co zůstane je implementace způsob, jak ho vypnout.</span><span class="sxs-lookup"><span data-stu-id="6ee28-253">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="6ee28-254">K tomuto účelu přidáte kód, který `lblAlarm_Click` metoda.</span><span class="sxs-lookup"><span data-stu-id="6ee28-254">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="6ee28-255">Chcete-li implementovat metodu přístupnými</span><span class="sxs-lookup"><span data-stu-id="6ee28-255">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="6ee28-256">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock.vb**a potom klikněte na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-256">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="6ee28-257">V návrháři, klikněte dvakrát na **lblAlarm**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-257">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="6ee28-258">**Editor kódu** se otevře `Private Sub lblAlarm_Click` řádku.</span><span class="sxs-lookup"><span data-stu-id="6ee28-258">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>  
  
3.  <span data-ttu-id="6ee28-259">Upravte tuto metodu tak, aby je podobná následující kód.</span><span class="sxs-lookup"><span data-stu-id="6ee28-259">Modify this method so that it resembles the following code.</span></span>  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  <span data-ttu-id="6ee28-260">Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** k uložení projektu.</span><span class="sxs-lookup"><span data-stu-id="6ee28-260">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="6ee28-261">Použití zděděné ovládacího prvku ve formuláři</span><span class="sxs-lookup"><span data-stu-id="6ee28-261">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="6ee28-262">Můžete otestovat zděděné kontrolu nad stejným způsobem jako otestovat základní třída prvku, `ctlClock`: stisknutím klávesy F5 se projekt sestavil a spuštění vlastního ovládacího prvku v **UserControl Test kontejneru**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="6ee28-263">Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="6ee28-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="6ee28-264">Vložit ovládací prvek použít, musíte ji hostovat ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="6ee28-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="6ee28-265">Stejně jako u standardní složeného ovládacího prvku, zděděné složeného ovládacího prvku nelze samostatná a musí být uloženy ve formuláři nebo jiných kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6ee28-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="6ee28-266">Vzhledem k tomu `ctlAlarmClock` má větší hloubky funkcí, je potřeba otestovat další kód.</span><span class="sxs-lookup"><span data-stu-id="6ee28-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="6ee28-267">V tomto postupu budete psát jednoduché program k testování funkčnosti `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="6ee28-268">Budete psát kód k nastavení a zobrazit `AlarmTime` vlastnost `ctlAlarmClock`a testovat své vyplývajících funkce.</span><span class="sxs-lookup"><span data-stu-id="6ee28-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="6ee28-269">Sestavení a přidat do formuláře testu</span><span class="sxs-lookup"><span data-stu-id="6ee28-269">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="6ee28-270">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClockLib**a potom klikněte na **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-270">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="6ee28-271">Na **soubor** nabídky, přejděte na příkaz **přidat**a potom klikněte na **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-271">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
3.  <span data-ttu-id="6ee28-272">Přidejte nový **aplikace Windows** projektu k řešení a pojmenujte ji `Test`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-272">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
     <span data-ttu-id="6ee28-273">**Test** projekt je přidán do Průzkumníka řešení.</span><span class="sxs-lookup"><span data-stu-id="6ee28-273">The **Test** project is added to Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="6ee28-274">V Průzkumníku řešení klikněte pravým tlačítkem myši `Test` uzel projektu a pak klikněte na **přidat odkaz na** zobrazíte **přidat odkaz na** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="6ee28-274">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="6ee28-275">Klikněte na kartu s názvem bez přípony **projekty**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-275">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="6ee28-276">Projekt **ctlClockLib** bude uvedena v **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-276">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="6ee28-277">Klikněte dvakrát na **ctlClockLib** se přidat odkaz na projekt test.</span><span class="sxs-lookup"><span data-stu-id="6ee28-277">Double-click **ctlClockLib** to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="6ee28-278">V Průzkumníku řešení klikněte pravým tlačítkem na **Test**a potom klikněte na **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-278">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
7.  <span data-ttu-id="6ee28-279">V **sada nástrojů**, rozbalte **ctlClockLib součásti** uzlu.</span><span class="sxs-lookup"><span data-stu-id="6ee28-279">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
8.  <span data-ttu-id="6ee28-280">Klikněte dvakrát na **ctlAlarmClock** přidat instanci `ctlAlarmClock` do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="6ee28-280">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>  
  
9. <span data-ttu-id="6ee28-281">V **sada nástrojů**, vyhledejte a dvakrát klikněte na **DateTimePicker** přidat <xref:System.Windows.Forms.DateTimePicker> řízení do svého formuláře a poté přidejte <xref:System.Windows.Forms.Label> řízení dvojitým kliknutím na soubor **popisek**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-281">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
10. <span data-ttu-id="6ee28-282">Umístění ovládacích prvků na vhodné místo na formuláři pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="6ee28-282">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
11. <span data-ttu-id="6ee28-283">Nastavte vlastnosti tyto ovládací prvky následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="6ee28-283">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="6ee28-284">Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="6ee28-284">Control</span></span>|<span data-ttu-id="6ee28-285">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="6ee28-285">Property</span></span>|<span data-ttu-id="6ee28-286">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6ee28-286">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="6ee28-287">**Text**</span><span class="sxs-lookup"><span data-stu-id="6ee28-287">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="6ee28-288">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="6ee28-288">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="6ee28-289">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="6ee28-289">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="6ee28-290">**Formát**</span><span class="sxs-lookup"><span data-stu-id="6ee28-290">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. <span data-ttu-id="6ee28-291">V návrháři, klikněte dvakrát na **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-291">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="6ee28-292">**Editor kódu** otevře `Private Sub dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-292">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>  
  
13. <span data-ttu-id="6ee28-293">Upravte kód tak, aby vypadá přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="6ee28-293">Modify the code so that it resembles the following.</span></span>  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. <span data-ttu-id="6ee28-294">V Průzkumníku řešení klikněte pravým tlačítkem na **Test**a potom klikněte na **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-294">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
15. <span data-ttu-id="6ee28-295">Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="6ee28-295">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="6ee28-296">Test program spustí.</span><span class="sxs-lookup"><span data-stu-id="6ee28-296">The test program starts.</span></span> <span data-ttu-id="6ee28-297">Všimněte si, že je aktuální čas aktualizován v `ctlAlarmClock` ovládací prvek, a že počáteční čas je zobrazen v nabídce <xref:System.Windows.Forms.DateTimePicker> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6ee28-297">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
16. <span data-ttu-id="6ee28-298">Klikněte <xref:System.Windows.Forms.DateTimePicker> kde se zobrazují počet minut za hodinu.</span><span class="sxs-lookup"><span data-stu-id="6ee28-298">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
17. <span data-ttu-id="6ee28-299">Pomocí klávesnice, nastavte hodnotu pro počet minut, který je větší než aktuální čas zobrazí jednu minutu `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-299">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="6ee28-300">Čas pro nastavení upozornění se zobrazí v `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-300">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="6ee28-301">Počkejte, než zobrazených dobu dosáhnout alarmů nastavení času.</span><span class="sxs-lookup"><span data-stu-id="6ee28-301">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="6ee28-302">Když zobrazených čas dosáhne čas, ke kterému je nastaven na upozornění, bude zvukový signál zvukových a `lblAlarm` bude flash.</span><span class="sxs-lookup"><span data-stu-id="6ee28-302">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>  
  
18. <span data-ttu-id="6ee28-303">Vypnout varování kliknutím `lblAlarm`.</span><span class="sxs-lookup"><span data-stu-id="6ee28-303">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="6ee28-304">Teď může resetovat na upozornění.</span><span class="sxs-lookup"><span data-stu-id="6ee28-304">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="6ee28-305">Tento názorný postup obsahuje zahrnutých počet klíčových konceptů.</span><span class="sxs-lookup"><span data-stu-id="6ee28-305">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="6ee28-306">Jste se naučili vytvoření složeného ovládacího prvku kombinací ovládací prvky a součásti do kontejneru složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6ee28-306">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="6ee28-307">Jste se naučili přidání vlastnosti do vlastního ovládacího prvku a napsat kód pro implementaci vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="6ee28-307">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="6ee28-308">V poslední části jste se dozvěděli rozšířit funkce dané složeného ovládacího prvku prostřednictvím dědičnosti a změnit funkce hostitele metody přepsání těchto metod.</span><span class="sxs-lookup"><span data-stu-id="6ee28-308">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee28-309">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ee28-309">See Also</span></span>  
 [<span data-ttu-id="6ee28-310">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="6ee28-310">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="6ee28-311">Postupy: vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="6ee28-311">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [<span data-ttu-id="6ee28-312">Postupy: zobrazení ovládacího prvku v výběr položek sady nástrojů – dialogové okno</span><span class="sxs-lookup"><span data-stu-id="6ee28-312">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="6ee28-313">Součást pro vytváření obsahu návody</span><span class="sxs-lookup"><span data-stu-id="6ee28-313">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
