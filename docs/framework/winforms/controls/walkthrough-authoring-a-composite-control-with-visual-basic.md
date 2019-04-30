---
title: 'Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu'
ms.date: 03/30/2017
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
ms.openlocfilehash: 6404e5933f886578b4ad8afd0d3da324541fc3f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792246"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="c2350-102">Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu</span><span class="sxs-lookup"><span data-stu-id="c2350-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="c2350-103">Složené ovládací prvky poskytují způsob, kterým lze vytvořit vlastní grafické rozhraní a znovu použít.</span><span class="sxs-lookup"><span data-stu-id="c2350-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="c2350-104">Složený ovládací prvek je v podstatě komponent pomocí vizuální reprezentace.</span><span class="sxs-lookup"><span data-stu-id="c2350-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="c2350-105">V důsledku toho může obsahovat jeden nebo více Windows Forms ovládací prvky, komponenty nebo bloky kódu, který můžete rozšířit funkce ověřování uživatelského vstupu, změnou zobrazení vlastností nebo provádění jiných úloh vyžaduje autorem.</span><span class="sxs-lookup"><span data-stu-id="c2350-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="c2350-106">Složené ovládací prvky mohou být umístěny ve Windows Forms stejným způsobem jako ostatní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c2350-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="c2350-107">V první části tohoto návodu vytvoříte jednoduchou složeného ovládacího prvku volá `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="c2350-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="c2350-108">V druhé části tohoto průvodce, které rozšiřují funkce nástroje `ctlClock` prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="c2350-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2350-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="c2350-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c2350-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c2350-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c2350-111">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c2350-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="c2350-112">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="c2350-112">Creating the Project</span></span>  
 <span data-ttu-id="c2350-113">Když vytvoříte nový projekt, zadejte její název na nastavit kořenový obor názvů, název sestavení a název projektu a ujistěte se, že součást výchozí bude v správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c2350-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="c2350-114">Chcete-li vytvořit ctlClockLib Knihovna ovládacích prvků a ovládací prvek ctlClock</span><span class="sxs-lookup"><span data-stu-id="c2350-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1. <span data-ttu-id="c2350-115">Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu** otevřete **nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c2350-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="c2350-116">V seznamu projektů Visual Basic, vyberte **Knihovna ovládacích prvků Windows** šablony projektu, typ `ctlClockLib` v **název** pole a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="c2350-116">From the list of Visual Basic projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c2350-117">Název projektu `ctlClockLib`, je také přiřazený k oboru názvů root ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c2350-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="c2350-118">Kořenový obor názvů se používá k určení názvů součástí sestavení.</span><span class="sxs-lookup"><span data-stu-id="c2350-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="c2350-119">Například, pokud se dvě sestavení poskytují komponenty s názvem `ctlClock`, můžete zadat vaše `ctlClock` pomocí komponenty `ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="c2350-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3. <span data-ttu-id="c2350-120">V Průzkumníku řešení klikněte pravým tlačítkem na **UserControl1.vb**a potom klikněte na tlačítko **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="c2350-120">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="c2350-121">Změňte název souboru, aby `ctlClock.vb`.</span><span class="sxs-lookup"><span data-stu-id="c2350-121">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="c2350-122">Klikněte na tlačítko **Ano** tlačítko, pokud budete vyzváni, pokud chcete přejmenovat všechny odkazy na prvek kódu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="c2350-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c2350-123">Ve výchozím nastavení, zdědí složeného ovládacího prvku <xref:System.Windows.Forms.UserControl> třídy poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="c2350-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="c2350-124"><xref:System.Windows.Forms.UserControl> Třída poskytuje funkce vyžadované všech složených ovládacích prvků a implementuje standardní metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2350-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4. <span data-ttu-id="c2350-125">Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** chcete projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="c2350-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="c2350-126">Přidání Windows ovládacích prvků a komponent do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c2350-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="c2350-127">Vizuální rozhraní je zásadní součástí složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2350-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="c2350-128">Tento vizuální rozhraní je implementováno přidání jednoho nebo více ovládacích prvků Windows na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="c2350-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="c2350-129">V následující ukázce se začlenit ovládacích prvků Windows do složeného ovládacího prvku a napsat kód k implementaci funkcionality.</span><span class="sxs-lookup"><span data-stu-id="c2350-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="c2350-130">Přidejte popisek a časovač do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c2350-130">To add a Label and a Timer to your composite control</span></span>  
  
1. <span data-ttu-id="c2350-131">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClock.vb**a potom klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="c2350-131">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>  
  
2. <span data-ttu-id="c2350-132">Na panelu nástrojů rozbalte **běžné ovládací prvky** uzel a poté dvojitým kliknutím **popisek**.</span><span class="sxs-lookup"><span data-stu-id="c2350-132">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="c2350-133">A <xref:System.Windows.Forms.Label> ovládací prvek s názvem `Label1` se přidá do vašeho ovládacího prvku na návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="c2350-133">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>  
  
3. <span data-ttu-id="c2350-134">V návrháři, klikněte na tlačítko **Label1**.</span><span class="sxs-lookup"><span data-stu-id="c2350-134">In the designer, click **Label1**.</span></span> <span data-ttu-id="c2350-135">V okně Vlastnosti nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2350-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="c2350-136">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c2350-136">Property</span></span>|<span data-ttu-id="c2350-137">Změňte na</span><span class="sxs-lookup"><span data-stu-id="c2350-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="c2350-138">**Název**</span><span class="sxs-lookup"><span data-stu-id="c2350-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="c2350-139">**Text**</span><span class="sxs-lookup"><span data-stu-id="c2350-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="c2350-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="c2350-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="c2350-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="c2350-141">**Font.Size**</span></span>|`14`|  
  
4. <span data-ttu-id="c2350-142">V **nástrojů**, rozbalte **součásti** uzel a poté dvojitým kliknutím **časovače**.</span><span class="sxs-lookup"><span data-stu-id="c2350-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="c2350-143">Protože <xref:System.Windows.Forms.Timer> je komponenta, nemá žádný vizuální reprezentace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="c2350-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="c2350-144">Proto se zřejmě není u ovládacích prvků na návrhové ploše, ale v Návrháři součástí (na hlavním panelu v dolní části na plochu návrháře).</span><span class="sxs-lookup"><span data-stu-id="c2350-144">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>  
  
5. <span data-ttu-id="c2350-145">V Návrháři součástí klikněte na tlačítko **Timer1**a pak nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `1000` a <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `True`.</span><span class="sxs-lookup"><span data-stu-id="c2350-145">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>  
  
     <span data-ttu-id="c2350-146"><xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost řídí frekvenci, se kterým komponenty timer značek.</span><span class="sxs-lookup"><span data-stu-id="c2350-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="c2350-147">Pokaždé, když `Timer1` tiků, spustí kód, který `Timer1_Tick` událostí.</span><span class="sxs-lookup"><span data-stu-id="c2350-147">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="c2350-148">Interval představuje počet milisekund mezi značkami.</span><span class="sxs-lookup"><span data-stu-id="c2350-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6. <span data-ttu-id="c2350-149">V Návrháři součástí, dvakrát klikněte na panel **Timer1** přejdete `Timer1_Tick` událost pro `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="c2350-149">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>  
  
7. <span data-ttu-id="c2350-150">Upravte kód tak, aby vypadá podobně jako následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="c2350-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="c2350-151">Nezapomeňte změnit modifikátor přístupu z `Private` k `Protected`.</span><span class="sxs-lookup"><span data-stu-id="c2350-151">Be sure to change the access modifier from `Private` to `Protected`.</span></span>  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     <span data-ttu-id="c2350-152">Tento kód způsobí, že aktuální čas v `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="c2350-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="c2350-153">Protože interval `Timer1` byl nastaven na `1000`, dojde k této události každých tisíců milisekund, tedy aktualizuje aktuální čas každou sekundu.</span><span class="sxs-lookup"><span data-stu-id="c2350-153">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8. <span data-ttu-id="c2350-154">Upravte metodu k možné overridable.</span><span class="sxs-lookup"><span data-stu-id="c2350-154">Modify the method to be overridable.</span></span> <span data-ttu-id="c2350-155">Další informace naleznete v části "Dědění z uživatelského ovládacího prvku" níže.</span><span class="sxs-lookup"><span data-stu-id="c2350-155">For more information, see the "Inheriting from a User Control" section below.</span></span>  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. <span data-ttu-id="c2350-156">Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** chcete projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="c2350-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="c2350-157">Přidání vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c2350-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="c2350-158">Ovládací prvek hodiny nyní zapouzdřuje <xref:System.Windows.Forms.Label> ovládacího prvku a <xref:System.Windows.Forms.Timer> komponenty, každý s vlastní sadou vlastní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2350-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="c2350-159">I když jednotlivé vlastnosti těchto ovládacích prvků nebudou přístupné uživatelům následné ovládacího prvku, můžete vytvořit a vystavit vlastní vlastnosti napsáním příslušné bloky kódu.</span><span class="sxs-lookup"><span data-stu-id="c2350-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="c2350-160">V následujícím postupu přidejte vlastnosti do ovládacího prvku, který uživateli umožňuje změnit barvu pozadí a textu.</span><span class="sxs-lookup"><span data-stu-id="c2350-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="c2350-161">Přidání vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c2350-161">To add a property to your composite control</span></span>  
  
1. <span data-ttu-id="c2350-162">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClock.vb**a potom klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="c2350-162">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="c2350-163">Otevře se Editor kódu pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c2350-163">The Code Editor for your control opens.</span></span>  
  
2. <span data-ttu-id="c2350-164">Vyhledejte `Public Class ctlClock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c2350-164">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="c2350-165">Pod ní zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="c2350-165">Beneath it, type the following code.</span></span>  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     <span data-ttu-id="c2350-166">Tyto příkazy vytvořit soukromé proměnné, které budete používat k ukládání hodnot pro vlastnosti, které se chystáte vytvořit.</span><span class="sxs-lookup"><span data-stu-id="c2350-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3. <span data-ttu-id="c2350-167">Vložte následující kód pod deklarace proměnných z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="c2350-167">Insert the following code beneath the variable declarations from step 2.</span></span>  
  
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
  
     <span data-ttu-id="c2350-168">Předchozí kód provede dvě vlastní vlastnosti `ClockForeColor` a `ClockBackColor`, která je dostupná uživatelům následné tohoto ovládacího prvku vyvoláním `Property` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c2350-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="c2350-169">`Get` a `Set` příkazy zajišťují pro ukládání a načítání hodnoty vlastnosti, jakož i kód k implementaci funkcionality odpovídající vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2350-169">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4. <span data-ttu-id="c2350-170">Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** chcete projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="c2350-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="c2350-171">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c2350-171">Testing the Control</span></span>  
 <span data-ttu-id="c2350-172">Ovládací prvky nejsou samostatné projekty; musí být uložen v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c2350-172">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="c2350-173">Chování ovládacího prvku za běhu testu přestal pracovat a s jeho vlastnosti **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="c2350-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="c2350-174">Další informace najdete v tématu [jak: Testování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="c2350-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="c2350-175">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c2350-175">To test your control</span></span>  
  
1. <span data-ttu-id="c2350-176">Stisknutím klávesy F5 sestavte projekt a spusťte váš ovládací prvek **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="c2350-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2. <span data-ttu-id="c2350-177">V mřížce vlastností kontejner testu, vyberte `ClockBackColor` vlastnost a poté klikněte na šipku rozevíracího seznamu k zobrazení palety barev.</span><span class="sxs-lookup"><span data-stu-id="c2350-177">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>  
  
3. <span data-ttu-id="c2350-178">Kliknutím zvolte barvu.</span><span class="sxs-lookup"><span data-stu-id="c2350-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="c2350-179">Barva pozadí ovládacího prvku změní barvu, kterou jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="c2350-179">The background color of your control changes to the color you selected.</span></span>  
  
4. <span data-ttu-id="c2350-180">Ověřte, že pomocí podobně jako posloupnost událostí `ClockForeColor` vlastnost funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="c2350-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
5. <span data-ttu-id="c2350-181">Klikněte na tlačítko **zavřete** zavřete **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="c2350-181">Click **Close** to close the **UserControl Test Container**.</span></span>  
  
     <span data-ttu-id="c2350-182">V této části a v předchozích částech, jste viděli, jak mohou být kombinovány komponent a ovládacích prvků Windows s kódem a balení poskytují vlastní funkce v podobě složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2350-182">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="c2350-183">Naučili jste se vystavení vlastností v složeného ovládacího prvku a po dokončení testování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2350-183">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="c2350-184">V další části se dozvíte, jak vytvořit objekt zděděné složeného ovládacího prvku pomocí `ctlClock` jako základ.</span><span class="sxs-lookup"><span data-stu-id="c2350-184">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="c2350-185">Dědění z složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c2350-185">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="c2350-186">V předchozích částech jste zjistili, jak zkombinovat ovládací prvky, komponenty a kódu Windows do opakovaně použitelného složených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="c2350-186">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="c2350-187">Složený ovládací prvek je nyní možné jako základ, na kterém je možné sestavovat další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c2350-187">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="c2350-188">Proces odvození třídy ze základní třídy se nazývá *dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="c2350-188">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="c2350-189">V této části vytvoříte složeného ovládacího prvku volá `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="c2350-189">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="c2350-190">Tento ovládací prvek bude odvozený z jeho nadřazenému ovládacímu prvku `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="c2350-190">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="c2350-191">Se dozvíte, jak rozšířit funkce `ctlClock` nadřazené metody přepsání a přidáním nových metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="c2350-191">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="c2350-192">Prvním krokem při vytváření zděděný ovládací prvek je odvozen od svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="c2350-192">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="c2350-193">Tato akce vytvoří nový ovládací prvek, který má všechny vlastnosti, metody a grafické vlastnosti nadřazeného ovládacího prvku, ale mohou chovat i jako základ pro přidání nové nebo upravené funkce.</span><span class="sxs-lookup"><span data-stu-id="c2350-193">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="c2350-194">Chcete-li vytvořit zděděný ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="c2350-194">To create the inherited control</span></span>  
  
1. <span data-ttu-id="c2350-195">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClockLib**, přejděte na **přidat**a potom klikněte na tlačítko **uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="c2350-195">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="c2350-196">**Přidat novou položku** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c2350-196">The **Add New Item** dialog box opens.</span></span>  
  
2. <span data-ttu-id="c2350-197">Vyberte **zděděné uživatelský ovládací prvek** šablony.</span><span class="sxs-lookup"><span data-stu-id="c2350-197">Select the **Inherited User Control** template.</span></span>  
  
3. <span data-ttu-id="c2350-198">V **název** zadejte `ctlAlarmClock.vb`a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="c2350-198">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="c2350-199">**Výběr dědičnosti** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c2350-199">The **Inheritance Picker** dialog box appears.</span></span>  
  
4. <span data-ttu-id="c2350-200">V části **název komponenty**, dvakrát klikněte na panel **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="c2350-200">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5. <span data-ttu-id="c2350-201">V Průzkumníku řešení projděte si aktuální projekty.</span><span class="sxs-lookup"><span data-stu-id="c2350-201">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c2350-202">Soubor s názvem **ctlAlarmClock.vb** byl přidán do aktuálního projektu.</span><span class="sxs-lookup"><span data-stu-id="c2350-202">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="c2350-203">Přidání vlastností upozornění</span><span class="sxs-lookup"><span data-stu-id="c2350-203">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="c2350-204">Vlastnosti jsou přidány do zděděný ovládací prvek stejným způsobem, které se přidají do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2350-204">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="c2350-205">Teď použijete syntaxi deklarace vlastností přidat dvě vlastnosti do ovládacího prvku: `AlarmTime`, která bude uchovávat hodnotu Datum a čas vypnutí, a `AlarmSet`, která indikuje, jestli je nastavit alarm.</span><span class="sxs-lookup"><span data-stu-id="c2350-205">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="c2350-206">Přidání vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c2350-206">To add properties to your composite control</span></span>  
  
1. <span data-ttu-id="c2350-207">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock**a potom klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="c2350-207">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2. <span data-ttu-id="c2350-208">Vyhledejte prohlášení třídy ctlAlarmClock ovládacího prvku, který se zobrazí jako `Public Class ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="c2350-208">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="c2350-209">V deklaraci třídy vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="c2350-209">In the class declaration, insert the following code.</span></span>  
  
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
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="c2350-210">Přidávání do rozhraní grafického ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c2350-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="c2350-211">Zděděný ovládací prvek má grafické rozhraní, který je stejný jako ovládací prvek, který dědí z.</span><span class="sxs-lookup"><span data-stu-id="c2350-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="c2350-212">Má stejné základní ovládací prvky jako jeho nadřazený ovládací prvek, ale vlastností základních ovládacích prvků nebude k dispozici, pokud výslovně vystavený.</span><span class="sxs-lookup"><span data-stu-id="c2350-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="c2350-213">Můžete přidat grafické rozhraní zděděných složeného ovládacího prvku stejným způsobem jako můžete přidat do jakékoli složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2350-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="c2350-214">Pokračujte v přidávání do vašeho budíku vizuální rozhraní, přidejte ovládací prvek popisku, který bude flash, když je zvukově alarm.</span><span class="sxs-lookup"><span data-stu-id="c2350-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="c2350-215">Chcete-li přidat ovládací prvek popisek</span><span class="sxs-lookup"><span data-stu-id="c2350-215">To add the label control</span></span>  
  
1. <span data-ttu-id="c2350-216">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock**a klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="c2350-216">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>  
  
     <span data-ttu-id="c2350-217">Návrhář pro `ctlAlarmClock` otevře v hlavním okně.</span><span class="sxs-lookup"><span data-stu-id="c2350-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2. <span data-ttu-id="c2350-218">Klikněte na tlačítko `lblDisplay` (zobrazené části ovládacího prvku) a zobrazte v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2350-218">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c2350-219">Když se zobrazí všechny vlastnosti, jsou neaktivní.</span><span class="sxs-lookup"><span data-stu-id="c2350-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="c2350-220">To znamená, že tyto vlastnosti jsou pro nativní `lblDisplay` a nelze změnit ani získat přístup v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2350-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="c2350-221">Ve výchozím nastavení, ovládacích prvcích obsažených složeného ovládacího prvku jsou `Private`, a jejich vlastnosti nejsou dostupné žádné prostředky.</span><span class="sxs-lookup"><span data-stu-id="c2350-221">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c2350-222">Pokud chcete mít přístup k jeho interní kontrolní mechanismy následné uživatelé složeného ovládacího prvku, je jako deklarovat `Public` nebo `Protected`.</span><span class="sxs-lookup"><span data-stu-id="c2350-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="c2350-223">To vám umožní nastavit a změnit vlastnosti ovládacích prvků uvnitř složeného ovládacího prvku pomocí odpovídající kód.</span><span class="sxs-lookup"><span data-stu-id="c2350-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3. <span data-ttu-id="c2350-224">Přidat <xref:System.Windows.Forms.Label> ovládacího prvku do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2350-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4. <span data-ttu-id="c2350-225">Pomocí myši přetáhnout <xref:System.Windows.Forms.Label> ovládací prvek bezprostředně pod rozevíracím seznamu zobrazit.</span><span class="sxs-lookup"><span data-stu-id="c2350-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="c2350-226">V okně Vlastnosti nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c2350-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="c2350-227">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c2350-227">Property</span></span>|<span data-ttu-id="c2350-228">Nastavení</span><span class="sxs-lookup"><span data-stu-id="c2350-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="c2350-229">**Název**</span><span class="sxs-lookup"><span data-stu-id="c2350-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="c2350-230">**Text**</span><span class="sxs-lookup"><span data-stu-id="c2350-230">**Text**</span></span>|<span data-ttu-id="c2350-231">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="c2350-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="c2350-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="c2350-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="c2350-233">**Viditelné**</span><span class="sxs-lookup"><span data-stu-id="c2350-233">**Visible**</span></span>|`False`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="c2350-234">Přidání funkce upozornění</span><span class="sxs-lookup"><span data-stu-id="c2350-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="c2350-235">V předchozích postupů jste přidali, vlastností a ovládací prvek, který vám umožní alarmů funkcí do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2350-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="c2350-236">V tomto postupu přidáte kód, který porovná aktuální čas na čas alarmu, a pokud se shodují, zvuk a flash alarm.</span><span class="sxs-lookup"><span data-stu-id="c2350-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="c2350-237">Přepsáním `Timer1_Tick` metoda `ctlClock` a do ní přidáte další kód, budou rozšíření možností objektu `ctlAlarmClock` při zachování všech funkcí inherentní `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="c2350-237">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="c2350-238">Chcete-li přepsat metodu Timer1_Tick ctlClock</span><span class="sxs-lookup"><span data-stu-id="c2350-238">To override the Timer1_Tick method of ctlClock</span></span>  
  
1. <span data-ttu-id="c2350-239">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock.vb**a potom klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="c2350-239">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>  
  
2. <span data-ttu-id="c2350-240">Vyhledejte `Private blnAlarmSet As Boolean` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c2350-240">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="c2350-241">Bezprostředně pod něj přidejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="c2350-241">Immediately beneath it, add the following statement.</span></span>  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3. <span data-ttu-id="c2350-242">Vyhledejte `End Class` příkaz v dolní části stránky.</span><span class="sxs-lookup"><span data-stu-id="c2350-242">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="c2350-243">Těsně před `End Class` příkaz, přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="c2350-243">Just before the `End Class` statement, add the following code.</span></span>  
  
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
  
     <span data-ttu-id="c2350-244">Tento kód provede několik úloh.</span><span class="sxs-lookup"><span data-stu-id="c2350-244">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="c2350-245">`Overrides` Příkaz přesměruje ovládacího prvku, aby používali tuto metodu místo metody, která se dědí ze základního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2350-245">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="c2350-246">Když tato metoda je volána, volá metodu přepíše vyvoláním `MyBase.Timer1_Tick` příkaz zajistí, že všechny funkce součástí původního ovládacího prvku je uveden v tomto ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="c2350-246">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="c2350-247">Pak spustí další kód začlenit funkce alarm.</span><span class="sxs-lookup"><span data-stu-id="c2350-247">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="c2350-248">Blikající ovládací prvek popisku se zobrazí při výskytu varování a uslyší zvukový signál.</span><span class="sxs-lookup"><span data-stu-id="c2350-248">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c2350-249">Protože jsou přepsání zděděné obslužnou rutinu, není potřeba událostí s `Handles` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c2350-249">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="c2350-250">Událost je už připojili.</span><span class="sxs-lookup"><span data-stu-id="c2350-250">The event is already hooked up.</span></span> <span data-ttu-id="c2350-251">Všechno, co jsou přepsání je implementace obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="c2350-251">All you are overriding is the implementation of the handler.</span></span>  
  
     <span data-ttu-id="c2350-252">Ovládací prvek budíku je skoro hotová.</span><span class="sxs-lookup"><span data-stu-id="c2350-252">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="c2350-253">Jediné, co, která zůstává je implementace způsob, jak ji vypnout.</span><span class="sxs-lookup"><span data-stu-id="c2350-253">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="c2350-254">K tomu přidáte kód, který `lblAlarm_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="c2350-254">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="c2350-255">K implementaci přístupnými – metoda</span><span class="sxs-lookup"><span data-stu-id="c2350-255">To implement the shutoff method</span></span>  
  
1. <span data-ttu-id="c2350-256">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock.vb**a potom klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="c2350-256">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>  
  
2. <span data-ttu-id="c2350-257">V Návrháři dvakrát klikněte na panel **lblAlarm**.</span><span class="sxs-lookup"><span data-stu-id="c2350-257">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="c2350-258">**Editor kódu** se otevře `Private Sub lblAlarm_Click` řádku.</span><span class="sxs-lookup"><span data-stu-id="c2350-258">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>  
  
3. <span data-ttu-id="c2350-259">Upravte tuto metodu tak, aby vypadá podobně jako následující kód.</span><span class="sxs-lookup"><span data-stu-id="c2350-259">Modify this method so that it resembles the following code.</span></span>  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4. <span data-ttu-id="c2350-260">Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** chcete projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="c2350-260">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="c2350-261">Pomocí zděděný ovládací prvek ve formuláři</span><span class="sxs-lookup"><span data-stu-id="c2350-261">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="c2350-262">Zděděný ovládací prvek můžete otestovat stejným způsobem můžete otestovat základní třídy ovládacího prvku, `ctlClock`: Stisknutím klávesy F5 sestavte projekt a spusťte váš ovládací prvek **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="c2350-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="c2350-263">Další informace najdete v tématu [jak: Testování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="c2350-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="c2350-264">Vložit ovládací prvek používat, musíte ho hostovat ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="c2350-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="c2350-265">Stejně jako u standardní složeného ovládacího prvku, zděděné složený ovládací prvek nemůže zůstat sama a musí být hostovaný ve formuláři nebo jiném kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c2350-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="c2350-266">Protože `ctlAlarmClock` větší hloubky funkce, je potřeba ji otestovat další kód.</span><span class="sxs-lookup"><span data-stu-id="c2350-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="c2350-267">V tomto postupu budete psát jednoduchý program k otestování funkce `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="c2350-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="c2350-268">Budete psát kód pro nastavení a zobrazení `AlarmTime` vlastnost `ctlAlarmClock`a testovat své vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="c2350-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="c2350-269">K vytvoření a přidání ovládacího prvku na formulář testu</span><span class="sxs-lookup"><span data-stu-id="c2350-269">To build and add your control to a test form</span></span>  
  
1. <span data-ttu-id="c2350-270">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClockLib**a potom klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="c2350-270">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2. <span data-ttu-id="c2350-271">Na **souboru** nabídky, přejděte k **přidat**a potom klikněte na tlačítko **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="c2350-271">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
3. <span data-ttu-id="c2350-272">Přidat nový **aplikace Windows** projektu do řešení a pojmenujte ho `Test`.</span><span class="sxs-lookup"><span data-stu-id="c2350-272">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
     <span data-ttu-id="c2350-273">**Test** projekt je přidán do Průzkumníku řešení.</span><span class="sxs-lookup"><span data-stu-id="c2350-273">The **Test** project is added to Solution Explorer.</span></span>  
  
4. <span data-ttu-id="c2350-274">V Průzkumníku řešení klikněte pravým tlačítkem myši `Test` uzel projektu a pak klikněte na **přidat odkaz** zobrazíte **přidat odkaz** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="c2350-274">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>  
  
5. <span data-ttu-id="c2350-275">Klikněte na kartu **projekty**.</span><span class="sxs-lookup"><span data-stu-id="c2350-275">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="c2350-276">Projekt **ctlClockLib** budou uvedeny pod **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="c2350-276">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="c2350-277">Dvakrát klikněte na panel **ctlClockLib** přidání odkazu do projektu testů.</span><span class="sxs-lookup"><span data-stu-id="c2350-277">Double-click **ctlClockLib** to add the reference to the test project.</span></span>  
  
6. <span data-ttu-id="c2350-278">V Průzkumníku řešení klikněte pravým tlačítkem na **testovací**a potom klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="c2350-278">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
7. <span data-ttu-id="c2350-279">V **nástrojů**, rozbalte **ctlClockLib součásti** uzlu.</span><span class="sxs-lookup"><span data-stu-id="c2350-279">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
8. <span data-ttu-id="c2350-280">Dvakrát klikněte na panel **ctlAlarmClock** přidat instanci `ctlAlarmClock` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="c2350-280">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>  
  
9. <span data-ttu-id="c2350-281">V **nástrojů**, vyhledejte a dvakrát klikněte na panel **ovládacího prvku DateTimePicker** přidat <xref:System.Windows.Forms.DateTimePicker> ovládací prvek do formuláře a poté přidejte <xref:System.Windows.Forms.Label> ovládací prvek dvojitým kliknutím **popisek**.</span><span class="sxs-lookup"><span data-stu-id="c2350-281">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
10. <span data-ttu-id="c2350-282">Pokud chcete umístit ovládací prvky v místě na formuláři pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="c2350-282">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
11. <span data-ttu-id="c2350-283">Následujícím způsobem nastavte vlastnosti těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="c2350-283">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="c2350-284">Control</span><span class="sxs-lookup"><span data-stu-id="c2350-284">Control</span></span>|<span data-ttu-id="c2350-285">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c2350-285">Property</span></span>|<span data-ttu-id="c2350-286">Value</span><span class="sxs-lookup"><span data-stu-id="c2350-286">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="c2350-287">**Text**</span><span class="sxs-lookup"><span data-stu-id="c2350-287">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="c2350-288">**Název**</span><span class="sxs-lookup"><span data-stu-id="c2350-288">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="c2350-289">**Název**</span><span class="sxs-lookup"><span data-stu-id="c2350-289">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="c2350-290">**Formát**</span><span class="sxs-lookup"><span data-stu-id="c2350-290">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. <span data-ttu-id="c2350-291">V Návrháři dvakrát klikněte na panel **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="c2350-291">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="c2350-292">**Editor kódu** otevře `Private Sub dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="c2350-292">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>  
  
13. <span data-ttu-id="c2350-293">Upravte kód tak, aby se podobá následující.</span><span class="sxs-lookup"><span data-stu-id="c2350-293">Modify the code so that it resembles the following.</span></span>  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. <span data-ttu-id="c2350-294">V Průzkumníku řešení klikněte pravým tlačítkem na **testovací**a potom klikněte na tlačítko **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="c2350-294">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
15. <span data-ttu-id="c2350-295">Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="c2350-295">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="c2350-296">Testovací program spustí.</span><span class="sxs-lookup"><span data-stu-id="c2350-296">The test program starts.</span></span> <span data-ttu-id="c2350-297">Všimněte si, že aktuální čas je aktualizace v `ctlAlarmClock` ovládacího prvku a, počáteční čas je zobrazena ve <xref:System.Windows.Forms.DateTimePicker> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c2350-297">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
16. <span data-ttu-id="c2350-298">Klikněte na tlačítko <xref:System.Windows.Forms.DateTimePicker> ve kterém se zobrazují minuty v hodině.</span><span class="sxs-lookup"><span data-stu-id="c2350-298">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
17. <span data-ttu-id="c2350-299">Pomocí klávesnice, nastavte hodnotu minut, který je větší než aktuální čas zobrazí jednu minutu `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="c2350-299">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="c2350-300">Čas potřebný pro nastavení upozornění se zobrazí v `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="c2350-300">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="c2350-301">Počkejte zobrazeném čase k nastavení doby alarm.</span><span class="sxs-lookup"><span data-stu-id="c2350-301">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="c2350-302">Čas, ke kterému je nastavit alarm dosáhne zobrazeném čase se zvuk zvukový signál a `lblAlarm` bude flash.</span><span class="sxs-lookup"><span data-stu-id="c2350-302">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>  
  
18. <span data-ttu-id="c2350-303">Vypnout alarmu, kliknutím na `lblAlarm`.</span><span class="sxs-lookup"><span data-stu-id="c2350-303">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="c2350-304">Nyní může resetovat alarm.</span><span class="sxs-lookup"><span data-stu-id="c2350-304">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="c2350-305">Tento názorný postup zahrnují několik klíčových konceptů.</span><span class="sxs-lookup"><span data-stu-id="c2350-305">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="c2350-306">Naučili jste se vytvoření složeného ovládacího prvku kombinací ovládacích prvků a komponent do složeného ovládacího prvku kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c2350-306">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="c2350-307">Jste se naučili přidání vlastnosti do ovládacího prvku a napsat kód k implementaci vlastních funkcí.</span><span class="sxs-lookup"><span data-stu-id="c2350-307">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="c2350-308">V předchozí části jste se dozvěděli k rozšíření funkčnosti dané složeného ovládacího prvku prostřednictvím dědičnosti a změnit funkci metody hostitele tak, že přepíšete tyto metody.</span><span class="sxs-lookup"><span data-stu-id="c2350-308">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2350-309">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2350-309">See also</span></span>

- [<span data-ttu-id="c2350-310">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="c2350-310">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="c2350-311">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="c2350-311">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="c2350-312">Postupy: Zobrazení ovládacího prvku v zvolit položky panelu nástrojů – dialogové okno</span><span class="sxs-lookup"><span data-stu-id="c2350-312">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
