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
ms.openlocfilehash: cb54ef372e6da551b95f1edf61e3844b9dcba4c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950044"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="58426-102">Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu</span><span class="sxs-lookup"><span data-stu-id="58426-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="58426-103">Složené ovládací prvky poskytují prostředky, pomocí kterých lze vytvořit a znovu použít vlastní grafická rozhraní.</span><span class="sxs-lookup"><span data-stu-id="58426-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="58426-104">Složený ovládací prvek je v podstatě součástí vizuální reprezentace.</span><span class="sxs-lookup"><span data-stu-id="58426-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="58426-105">V takovém případě se může skládat z jednoho nebo více model Windows Forms ovládacích prvků, komponent nebo bloků kódu, které mohou rozšiřování funkcí pomocí ověření vstupu uživatele, změny vlastností zobrazení nebo provádění jiných úloh vyžadovaných autorem.</span><span class="sxs-lookup"><span data-stu-id="58426-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="58426-106">Složené ovládací prvky lze umístit na model Windows Forms stejným způsobem jako jiné ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="58426-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="58426-107">V první části tohoto návodu vytvoříte jednoduchý složený ovládací prvek s názvem `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="58426-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="58426-108">V druhé části návodu rozšíříte funkce `ctlClock` nástroje prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="58426-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="58426-109">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="58426-109">Creating the Project</span></span>
 <span data-ttu-id="58426-110">Při vytváření nového projektu zadáte jeho název pro nastavení kořenového oboru názvů, název sestavení a název projektu a zajistěte, aby byla výchozí komponenta ve správném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="58426-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="58426-111">Vytvoření knihovny ovládacích prvků ctlClockLib a ovládacího prvku ctlClock</span><span class="sxs-lookup"><span data-stu-id="58426-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="58426-112">V nabídce **soubor** přejděte na příkaz **Nový**a kliknutím na položku **projekt** otevřete dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="58426-112">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="58426-113">V seznamu Visual Basic projektů vyberte šablonu projektu **Knihovna ovládacích prvků systému Windows** , zadejte `ctlClockLib` do pole **název** a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="58426-113">From the list of Visual Basic projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>

     <span data-ttu-id="58426-114">Název projektu, `ctlClockLib`, je ve výchozím nastavení přiřazen ke kořenovému oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="58426-114">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="58426-115">Kořenový obor názvů slouží k získání názvů komponent v sestavení.</span><span class="sxs-lookup"><span data-stu-id="58426-115">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="58426-116">Například pokud dvě sestavení poskytují komponenty s názvem `ctlClock`, můžete určit svou `ctlClock` komponentu pomocí`ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="58426-116">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

3. <span data-ttu-id="58426-117">V Průzkumník řešení klikněte pravým tlačítkem na **UserControl1. vb**a pak klikněte na **Přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="58426-117">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="58426-118">Změňte název souboru na `ctlClock.vb`.</span><span class="sxs-lookup"><span data-stu-id="58426-118">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="58426-119">Pokud se zobrazí dotaz, zda chcete přejmenovat všechny odkazy na prvek kódu "UserControl1", klikněte na tlačítko **Ano** .</span><span class="sxs-lookup"><span data-stu-id="58426-119">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="58426-120">Ve výchozím nastavení dědí složený ovládací prvek ze <xref:System.Windows.Forms.UserControl> třídy poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="58426-120">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="58426-121"><xref:System.Windows.Forms.UserControl> Třída poskytuje funkce vyžadované všemi složenými ovládacími prvky a implementuje standardní metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="58426-121">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

4. <span data-ttu-id="58426-122">V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="58426-122">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="58426-123">Přidávání ovládacích prvků a součástí systému Windows do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="58426-123">Adding Windows Controls and Components to the Composite Control</span></span>
 <span data-ttu-id="58426-124">Vizuální rozhraní je podstatnou součástí složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="58426-124">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="58426-125">Toto vizuální rozhraní je implementováno přidáním jednoho nebo více ovládacích prvků Windows na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="58426-125">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="58426-126">V následující ukázce zahrnete ovládací prvky Windows do složeného ovládacího prvku a napíšete kód pro implementaci funkcí.</span><span class="sxs-lookup"><span data-stu-id="58426-126">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="58426-127">Přidání popisku a časovače do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="58426-127">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="58426-128">V Průzkumník řešení klikněte pravým tlačítkem myši na **ctlClock. vb**a potom klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="58426-128">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="58426-129">V sadě nástrojů rozbalte uzel **běžné ovládací prvky** a dvakrát klikněte na položku **popisek**.</span><span class="sxs-lookup"><span data-stu-id="58426-129">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="58426-130">Ovládací prvek s `Label1` názvem je přidán k ovládacímu prvku na návrhové ploše. <xref:System.Windows.Forms.Label></span><span class="sxs-lookup"><span data-stu-id="58426-130">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="58426-131">V návrháři klikněte na možnost **Label1**.</span><span class="sxs-lookup"><span data-stu-id="58426-131">In the designer, click **Label1**.</span></span> <span data-ttu-id="58426-132">V okno Vlastnosti nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="58426-132">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="58426-133">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="58426-133">Property</span></span>|<span data-ttu-id="58426-134">Změnit na</span><span class="sxs-lookup"><span data-stu-id="58426-134">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="58426-135">**Název**</span><span class="sxs-lookup"><span data-stu-id="58426-135">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="58426-136">**Text**</span><span class="sxs-lookup"><span data-stu-id="58426-136">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="58426-137">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="58426-137">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="58426-138">**Font. Size**</span><span class="sxs-lookup"><span data-stu-id="58426-138">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="58426-139">V sadě **nástrojů**rozbalte uzel **komponenty** a dvakrát klikněte na položku **časovač**.</span><span class="sxs-lookup"><span data-stu-id="58426-139">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="58426-140">Vzhledem k <xref:System.Windows.Forms.Timer> tomu, že se jedná o komponentu, nemá v době běhu žádná vizuální reprezentace.</span><span class="sxs-lookup"><span data-stu-id="58426-140">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="58426-141">Proto se nezobrazí s ovládacími prvky na návrhové ploše, ale spíše v Návrháři komponent (zásobník na spodní straně návrhové plochy).</span><span class="sxs-lookup"><span data-stu-id="58426-141">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="58426-142">V Návrháři komponent klikněte na **Timer1**a pak nastavte <xref:System.Windows.Forms.Timer.Interval%2A> <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost na `1000`. `True`</span><span class="sxs-lookup"><span data-stu-id="58426-142">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>

     <span data-ttu-id="58426-143"><xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost určuje četnost, se kterou se komponenta časovače zaškrtne.</span><span class="sxs-lookup"><span data-stu-id="58426-143">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="58426-144">Každé časové `Timer1` impulsy spustí kód `Timer1_Tick` v události.</span><span class="sxs-lookup"><span data-stu-id="58426-144">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="58426-145">Interval představuje počet milisekund mezi takty.</span><span class="sxs-lookup"><span data-stu-id="58426-145">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="58426-146">V Návrháři komponent poklikejte na **Timer1** a přejděte na `Timer1_Tick` událost pro. `ctlClock`</span><span class="sxs-lookup"><span data-stu-id="58426-146">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="58426-147">Upravte kód tak, aby vypadal jako následující ukázka kódu.</span><span class="sxs-lookup"><span data-stu-id="58426-147">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="58426-148">Nezapomeňte změnit modifikátor přístupu z `Private` na. `Protected`</span><span class="sxs-lookup"><span data-stu-id="58426-148">Be sure to change the access modifier from `Private` to `Protected`.</span></span>

    ```vb
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles Timer1.Tick
        ' Causes the label to display the current time.
        lblDisplay.Text = Format(Now, "hh:mm:ss")
    End Sub
    ```

     <span data-ttu-id="58426-149">Tento kód způsobí, že bude aktuální čas zobrazen v `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="58426-149">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="58426-150">Vzhledem k tomu, `Timer1` že interval byl `1000`nastaven na hodnotu, bude tato událost provedena každých tisíc milisekund, čímž se aktualizuje aktuální čas každou sekundu.</span><span class="sxs-lookup"><span data-stu-id="58426-150">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="58426-151">Upravte metodu, kterou chcete přepsat.</span><span class="sxs-lookup"><span data-stu-id="58426-151">Modify the method to be overridable.</span></span> <span data-ttu-id="58426-152">Další informace najdete v části "dědění z uživatelského ovládacího prvku" níže.</span><span class="sxs-lookup"><span data-stu-id="58426-152">For more information, see the "Inheriting from a User Control" section below.</span></span>

    ```vb
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _
        e As System.EventArgs) Handles Timer1.Tick
    ```

9. <span data-ttu-id="58426-153">V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="58426-153">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="58426-154">Přidání vlastností do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="58426-154">Adding Properties to the Composite Control</span></span>
 <span data-ttu-id="58426-155">Ovládací prvek hodiny nyní zapouzdřuje <xref:System.Windows.Forms.Label> ovládací prvek <xref:System.Windows.Forms.Timer> a komponentu, z nichž každá má svou vlastní sadu vlastností.</span><span class="sxs-lookup"><span data-stu-id="58426-155">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="58426-156">Přestože jednotlivé vlastnosti těchto ovládacích prvků nebudou k dispozici pro následné uživatele vašeho ovládacího prvku, můžete vytvořit a vystavit vlastní vlastnosti zápisem příslušných bloků kódu.</span><span class="sxs-lookup"><span data-stu-id="58426-156">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="58426-157">V následujícím postupu přidáte vlastnosti ovládacího prvku, který uživateli umožňuje změnit barvu pozadí a textu.</span><span class="sxs-lookup"><span data-stu-id="58426-157">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="58426-158">Přidání vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="58426-158">To add a property to your composite control</span></span>

1. <span data-ttu-id="58426-159">V Průzkumník řešení klikněte pravým tlačítkem na **ctlClock. vb**a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="58426-159">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>

     <span data-ttu-id="58426-160">Otevře se Editor kódu pro váš ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="58426-160">The Code Editor for your control opens.</span></span>

2. <span data-ttu-id="58426-161">`Public Class ctlClock` Vyhledejte příkaz.</span><span class="sxs-lookup"><span data-stu-id="58426-161">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="58426-162">Pod ní zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="58426-162">Beneath it, type the following code.</span></span>

    ```vb
    Private colFColor as Color
    Private colBColor as Color
    ```

     <span data-ttu-id="58426-163">Tyto příkazy vytvoří soukromé proměnné, které použijete k uložení hodnot pro vlastnosti, které se chystáte vytvořit.</span><span class="sxs-lookup"><span data-stu-id="58426-163">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="58426-164">Vložte následující kód pod deklarace proměnných z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="58426-164">Insert the following code beneath the variable declarations from step 2.</span></span>

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

     <span data-ttu-id="58426-165">Předchozí kód vytvoří dvě vlastní vlastnosti `ClockForeColor` a `ClockBackColor`zpřístupní pro následné uživatele tohoto `Property` ovládacího prvku vyvoláním příkazu.</span><span class="sxs-lookup"><span data-stu-id="58426-165">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="58426-166">Příkazy `Get` a`Set` poskytují úložiště a načtení hodnoty vlastnosti a také kód pro implementaci funkcí vhodných pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="58426-166">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="58426-167">V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="58426-167">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="testing-the-control"></a><span data-ttu-id="58426-168">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="58426-168">Testing the Control</span></span>
 <span data-ttu-id="58426-169">Ovládací prvky nejsou samostatné projekty; musí být hostovány v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="58426-169">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="58426-170">Otestujte chování ovládacího prvku za běhu a využijte jeho vlastnosti pomocí **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="58426-170">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="58426-171">Další informace najdete v tématu [jak: Otestuje chování prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)v době běhu.</span><span class="sxs-lookup"><span data-stu-id="58426-171">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="58426-172">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="58426-172">To test your control</span></span>

1. <span data-ttu-id="58426-173">Stisknutím klávesy F5 Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="58426-173">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="58426-174">V mřížce vlastností kontejneru testů vyberte `ClockBackColor` vlastnost a potom kliknutím na šipku rozevíracího seznamu zobrazte paletu barev.</span><span class="sxs-lookup"><span data-stu-id="58426-174">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>

3. <span data-ttu-id="58426-175">Vyberte barvu kliknutím na ni.</span><span class="sxs-lookup"><span data-stu-id="58426-175">Choose a color by clicking it.</span></span>

     <span data-ttu-id="58426-176">Barva pozadí ovládacího prvku se změní na barvu, kterou jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="58426-176">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="58426-177">Pomocí podobné posloupnosti událostí ověřte, zda `ClockForeColor` vlastnost pracuje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="58426-177">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

5. <span data-ttu-id="58426-178">Kliknutím na tlačítko **Zavřít** zavřete **kontejner testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="58426-178">Click **Close** to close the **UserControl Test Container**.</span></span>

     <span data-ttu-id="58426-179">V této části a předchozích částech jste viděli, jak mohou být komponenty a ovládací prvky systému Windows kombinovány s kódem a balíčkem, aby poskytovaly vlastní funkce ve formě složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="58426-179">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="58426-180">Naučili jste se vystavit vlastnosti ve složeném ovládacím prvku a jak otestovat ovládací prvek po jeho dokončení.</span><span class="sxs-lookup"><span data-stu-id="58426-180">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="58426-181">V další části se dozvíte, jak vytvořit zděděný složený ovládací prvek pomocí `ctlClock` jako základu.</span><span class="sxs-lookup"><span data-stu-id="58426-181">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="58426-182">Dědění ze složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="58426-182">Inheriting from a Composite Control</span></span>
 <span data-ttu-id="58426-183">V předchozích částech jste zjistili, jak zkombinovat ovládací prvky, komponenty a kód Windows do opakovaně použitelných složených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="58426-183">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="58426-184">Složený ovládací prvek se teď dá použít jako základ, na kterém můžou být sestavené další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="58426-184">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="58426-185">Proces odvození třídy ze základní třídy se nazývá *Dědičnost*.</span><span class="sxs-lookup"><span data-stu-id="58426-185">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="58426-186">V této části vytvoříte složený ovládací prvek, který se nazývá `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="58426-186">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="58426-187">Tento ovládací prvek bude odvozen z jeho nadřazeného ovládacího prvku `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="58426-187">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="58426-188">Naučíte se rozšíření funkcí `ctlClock` přepsáním nadřazených metod a přidáním nových metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="58426-188">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

 <span data-ttu-id="58426-189">Prvním krokem při vytváření zděděného ovládacího prvku je jeho odvození od jeho nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="58426-189">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="58426-190">Tato akce vytvoří nový ovládací prvek, který obsahuje všechny vlastnosti, metody a grafické charakteristiky nadřazeného ovládacího prvku, ale může také sloužit jako základ pro přidání nových nebo upravených funkcí.</span><span class="sxs-lookup"><span data-stu-id="58426-190">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="58426-191">Vytvoření zděděného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="58426-191">To create the inherited control</span></span>

1. <span data-ttu-id="58426-192">V Průzkumník řešení klikněte pravým tlačítkem myši na **ctlClockLib**, přejděte na **Přidat**a pak klikněte na **uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="58426-192">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="58426-193">**Přidat novou položku** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="58426-193">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="58426-194">Vyberte šablonu **zděděného uživatelského ovládacího prvku** .</span><span class="sxs-lookup"><span data-stu-id="58426-194">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="58426-195">Do pole **název** zadejte `ctlAlarmClock.vb`a pak klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="58426-195">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>

     <span data-ttu-id="58426-196">Zobrazí se dialogové okno **Výběr dědičnosti** .</span><span class="sxs-lookup"><span data-stu-id="58426-196">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="58426-197">V části **název součásti**poklikejte na **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="58426-197">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="58426-198">V Průzkumník řešení Procházet aktuální projekty.</span><span class="sxs-lookup"><span data-stu-id="58426-198">In Solution Explorer, browse through the current projects.</span></span>

    > [!NOTE]
    > <span data-ttu-id="58426-199">Do aktuálního projektu byl přidán soubor s názvem **ctlAlarmClock. vb** .</span><span class="sxs-lookup"><span data-stu-id="58426-199">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>

### <a name="adding-the-alarm-properties"></a><span data-ttu-id="58426-200">Přidání vlastností alarmu</span><span class="sxs-lookup"><span data-stu-id="58426-200">Adding the Alarm Properties</span></span>
 <span data-ttu-id="58426-201">Vlastnosti jsou přidány do zděděného ovládacího prvku stejným způsobem jako přidaným do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="58426-201">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="58426-202">Nyní použijete syntaxi deklarace vlastností k přidání dvou vlastností do ovládacího prvku: `AlarmTime`, který bude uchovávat hodnotu data a času, kdy má alarm přejít, a `AlarmSet`, který bude označovat, zda je alarm nastaven.</span><span class="sxs-lookup"><span data-stu-id="58426-202">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="58426-203">Přidání vlastností do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="58426-203">To add properties to your composite control</span></span>

1. <span data-ttu-id="58426-204">V Průzkumník řešení klikněte pravým tlačítkem na **ctlAlarmClock**a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="58426-204">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="58426-205">Vyhledejte deklaraci třídy pro ovládací prvek ctlAlarmClock, který se zobrazí `Public Class ctlAlarmClock`jako.</span><span class="sxs-lookup"><span data-stu-id="58426-205">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="58426-206">V deklaraci třídy vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="58426-206">In the class declaration, insert the following code.</span></span>

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

### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="58426-207">Přidání do grafického rozhraní ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="58426-207">Adding to the Graphical Interface of the Control</span></span>
 <span data-ttu-id="58426-208">Zděděný ovládací prvek má vizuální rozhraní, které je identické s ovládacím prvkem, ze kterého dědí.</span><span class="sxs-lookup"><span data-stu-id="58426-208">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="58426-209">Má stejné ovládací prvky jako svůj nadřazený ovládací prvek, ale vlastnosti ovládacích prvků nebudou k dispozici, pokud nebyly výslovně zpřístupněny.</span><span class="sxs-lookup"><span data-stu-id="58426-209">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="58426-210">Můžete přidat do grafického rozhraní zděděného složeného ovládacího prvku stejným způsobem, jako byste přidali do jakéhokoli složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="58426-210">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="58426-211">Pokud chcete pokračovat v přidávání do vizuálního rozhraní pro budíky, přidejte ovládací prvek popisek, který bude při zvukovém alarmu blikat.</span><span class="sxs-lookup"><span data-stu-id="58426-211">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="58426-212">Přidání ovládacího prvku popisek</span><span class="sxs-lookup"><span data-stu-id="58426-212">To add the label control</span></span>

1. <span data-ttu-id="58426-213">V Průzkumník řešení klikněte pravým tlačítkem myši na **ctlAlarmClock**a pak klikněte na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="58426-213">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>

     <span data-ttu-id="58426-214">Návrhář pro `ctlAlarmClock` se otevře v hlavním okně.</span><span class="sxs-lookup"><span data-stu-id="58426-214">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="58426-215">Klikněte `lblDisplay` na tlačítko (zobrazená část ovládacího prvku) a zobrazte okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="58426-215">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="58426-216">Všechny vlastnosti jsou zobrazeny šedě.</span><span class="sxs-lookup"><span data-stu-id="58426-216">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="58426-217">To znamená, že tyto vlastnosti jsou nativní `lblDisplay` a nelze je upravovat nebo k nim nelze přicházet v okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="58426-217">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="58426-218">Ve výchozím nastavení jsou `Private`ovládací prvky obsažené ve složeném ovládacím prvku a jejich vlastnosti přístupné žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="58426-218">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="58426-219">Pokud chcete, aby následující uživatelé složeného ovládacího prvku měli přístup k vnitřním ovládacím prvkům, deklarujte `Public` je `Protected`jako nebo.</span><span class="sxs-lookup"><span data-stu-id="58426-219">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="58426-220">To vám umožní nastavit a upravit vlastnosti ovládacích prvků obsažených v rámci složeného ovládacího prvku pomocí příslušného kódu.</span><span class="sxs-lookup"><span data-stu-id="58426-220">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="58426-221"><xref:System.Windows.Forms.Label> Přidejte ovládací prvek do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="58426-221">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="58426-222">Pomocí myši přetáhněte <xref:System.Windows.Forms.Label> ovládací prvek hned pod zobrazeným polem.</span><span class="sxs-lookup"><span data-stu-id="58426-222">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="58426-223">V okno Vlastnosti nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="58426-223">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="58426-224">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="58426-224">Property</span></span>|<span data-ttu-id="58426-225">Nastavení</span><span class="sxs-lookup"><span data-stu-id="58426-225">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="58426-226">**Název**</span><span class="sxs-lookup"><span data-stu-id="58426-226">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="58426-227">**Text**</span><span class="sxs-lookup"><span data-stu-id="58426-227">**Text**</span></span>|<span data-ttu-id="58426-228">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="58426-228">**Alarm!**</span></span>|
    |<span data-ttu-id="58426-229">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="58426-229">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="58426-230">**Zobrazeny**</span><span class="sxs-lookup"><span data-stu-id="58426-230">**Visible**</span></span>|`False`|

### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="58426-231">Přidání funkce alarmu</span><span class="sxs-lookup"><span data-stu-id="58426-231">Adding the Alarm Functionality</span></span>
 <span data-ttu-id="58426-232">V předchozích postupech jste přidali vlastnosti a ovládací prvek, který umožní funkci alarmu ve složeném ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="58426-232">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="58426-233">V tomto postupu přidáte kód, který bude porovnávat aktuální čas s časem alarmu, a pokud jsou stejné, budete chtít zvuk a přehrát alarm.</span><span class="sxs-lookup"><span data-stu-id="58426-233">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="58426-234">Tím, že `ctlClock` `ctlClock`přepíšete `Timer1_Tick` metodu a přidáte do ní další kód, rozšíříte možnost azachováte`ctlAlarmClock` všechny podstatné funkce.</span><span class="sxs-lookup"><span data-stu-id="58426-234">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="58426-235">Přepsání metody Timer1_Tick pro ctlClock</span><span class="sxs-lookup"><span data-stu-id="58426-235">To override the Timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="58426-236">V Průzkumník řešení klikněte pravým tlačítkem na **ctlAlarmClock. vb**a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="58426-236">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>

2. <span data-ttu-id="58426-237">`Private blnAlarmSet As Boolean` Vyhledejte příkaz.</span><span class="sxs-lookup"><span data-stu-id="58426-237">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="58426-238">Hned pod ním přidejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="58426-238">Immediately beneath it, add the following statement.</span></span>

    ```vb
    Dim blnColorTicker as Boolean
    ```

3. <span data-ttu-id="58426-239">`End Class` Vyhledejte příkaz v dolní části stránky.</span><span class="sxs-lookup"><span data-stu-id="58426-239">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="58426-240">Těsně před `End Class` příkazem přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="58426-240">Just before the `End Class` statement, add the following code.</span></span>

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

     <span data-ttu-id="58426-241">Přidání tohoto kódu dosahuje několika úloh.</span><span class="sxs-lookup"><span data-stu-id="58426-241">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="58426-242">`Overrides` Příkaz nasměruje ovládací prvek na použití této metody místo metody, která byla zděděna ze základního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="58426-242">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="58426-243">Při volání této metody volá metodu, kterou Přepisuje, vyvoláním `MyBase.Timer1_Tick` příkazu, čímž se zajistí, že všechny funkce zahrnuté v původním ovládacím prvku budou v tomto ovládacím prvku reprodukovány.</span><span class="sxs-lookup"><span data-stu-id="58426-243">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="58426-244">Potom spustí další kód, který bude začlenit funkci alarmu.</span><span class="sxs-lookup"><span data-stu-id="58426-244">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="58426-245">Pokud dojde k alarmu, zobrazí se ovládací prvek popisku, který se bude objevovat zvukovým signálem.</span><span class="sxs-lookup"><span data-stu-id="58426-245">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>

    > [!NOTE]
    > <span data-ttu-id="58426-246">Vzhledem k tomu, že přepisujete zděděnou obslužnou rutinu události, nemusíte zadávat událost `Handles` s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="58426-246">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="58426-247">Událost je již zapojena.</span><span class="sxs-lookup"><span data-stu-id="58426-247">The event is already hooked up.</span></span> <span data-ttu-id="58426-248">Vše, co přepisujete, je implementace obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="58426-248">All you are overriding is the implementation of the handler.</span></span>

     <span data-ttu-id="58426-249">Ovládací prvek hodiny budíku je skoro kompletní.</span><span class="sxs-lookup"><span data-stu-id="58426-249">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="58426-250">Jediná věc, kterou zbývá, je implementovat způsob, jak ho vypnout.</span><span class="sxs-lookup"><span data-stu-id="58426-250">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="58426-251">K tomu je třeba přidat kód do `lblAlarm_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="58426-251">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="58426-252">Implementace metody shutoff</span><span class="sxs-lookup"><span data-stu-id="58426-252">To implement the shutoff method</span></span>

1. <span data-ttu-id="58426-253">V Průzkumník řešení klikněte pravým tlačítkem myši na **ctlAlarmClock. vb**a potom klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="58426-253">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="58426-254">V Návrháři poklikejte na **lblAlarm**.</span><span class="sxs-lookup"><span data-stu-id="58426-254">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="58426-255">Otevře se **Editor kódu** na `Private Sub lblAlarm_Click` řádku.</span><span class="sxs-lookup"><span data-stu-id="58426-255">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>

3. <span data-ttu-id="58426-256">Upravte tuto metodu tak, aby vypadala jako následující kód.</span><span class="sxs-lookup"><span data-stu-id="58426-256">Modify this method so that it resembles the following code.</span></span>

    ```vb
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _
     System.EventArgs) Handles lblAlarm.Click
        ' Turns off the alarm.
        AlarmSet = False
        ' Hides the flashing label.
        lblAlarm.Visible = False
    End Sub
    ```

4. <span data-ttu-id="58426-257">V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="58426-257">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="58426-258">Použití zděděného ovládacího prvku na formuláři</span><span class="sxs-lookup"><span data-stu-id="58426-258">Using the Inherited Control on a Form</span></span>
 <span data-ttu-id="58426-259">Zděděný ovládací prvek lze otestovat stejným způsobem jako ovládací prvek `ctlClock`základní třídy: Stisknutím klávesy F5 Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="58426-259">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="58426-260">Další informace najdete v tématu [jak: Otestuje chování prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)v době běhu.</span><span class="sxs-lookup"><span data-stu-id="58426-260">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

 <span data-ttu-id="58426-261">Chcete-li ovládací prvek použít, budete ho muset hostovat na formuláři.</span><span class="sxs-lookup"><span data-stu-id="58426-261">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="58426-262">Stejně jako u standardního složeného ovládacího prvku nemůže zděděný složený ovládací prvek samostatně a musí být hostovaný ve formuláři nebo jiném kontejneru.</span><span class="sxs-lookup"><span data-stu-id="58426-262">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="58426-263">Vzhledem `ctlAlarmClock` k tomu, že má větší hloubku funkčnosti, je nutné k otestování dalšího kódu.</span><span class="sxs-lookup"><span data-stu-id="58426-263">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="58426-264">V tomto postupu napíšete jednoduchý program, který bude testovat funkčnost `ctlAlarmClock`nástroje.</span><span class="sxs-lookup"><span data-stu-id="58426-264">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="58426-265">Napíšete kód pro nastavení a zobrazení `AlarmTime` `ctlAlarmClock`vlastnosti a otestujete své své vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="58426-265">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="58426-266">Sestavení a přidání ovládacího prvku do formuláře testu</span><span class="sxs-lookup"><span data-stu-id="58426-266">To build and add your control to a test form</span></span>

1. <span data-ttu-id="58426-267">V Průzkumník řešení klikněte pravým tlačítkem na **ctlClockLib**a pak klikněte na **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="58426-267">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="58426-268">V nabídce **soubor** přejděte na příkaz **Přidat**a poté klikněte na možnost **Nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="58426-268">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>

3. <span data-ttu-id="58426-269">Přidejte do řešení nový projekt **aplikace pro Windows** a pojmenujte ho `Test`.</span><span class="sxs-lookup"><span data-stu-id="58426-269">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>

     <span data-ttu-id="58426-270">**Testovací** projekt je přidán do Průzkumník řešení.</span><span class="sxs-lookup"><span data-stu-id="58426-270">The **Test** project is added to Solution Explorer.</span></span>

4. <span data-ttu-id="58426-271">V Průzkumník řešení klikněte pravým tlačítkem myši `Test` na uzel projektu a potom klikněte na tlačítko **Přidat odkaz** . zobrazí se dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="58426-271">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="58426-272">Klikněte na kartu s označením **projekty**.</span><span class="sxs-lookup"><span data-stu-id="58426-272">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="58426-273">Projekt **ctlClockLib** bude uveden v části **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="58426-273">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="58426-274">Dvojím kliknutím na **ctlClockLib** přidejte odkaz na testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="58426-274">Double-click **ctlClockLib** to add the reference to the test project.</span></span>

6. <span data-ttu-id="58426-275">V Průzkumník řešení klikněte pravým tlačítkem na **test**a pak klikněte na **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="58426-275">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>

7. <span data-ttu-id="58426-276">V **sadě nástrojů**rozbalte uzel **součásti ctlClockLib** .</span><span class="sxs-lookup"><span data-stu-id="58426-276">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

8. <span data-ttu-id="58426-277">Dvojím kliknutím na **ctlAlarmClock** přidejte instanci `ctlAlarmClock` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="58426-277">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>

9. <span data-ttu-id="58426-278">V **sadě nástrojů**Najděte a dvakrát klikněte na **DateTimePicker** a přidejte <xref:System.Windows.Forms.DateTimePicker> ovládací prvek do <xref:System.Windows.Forms.Label> formuláře a pak přidejte ovládací prvek dvojitým kliknutím na **popisek**.</span><span class="sxs-lookup"><span data-stu-id="58426-278">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

10. <span data-ttu-id="58426-279">Pomocí myši umístěte ovládací prvky na vhodné místo na formuláři.</span><span class="sxs-lookup"><span data-stu-id="58426-279">Use the mouse to position the controls in a convenient place on the form.</span></span>

11. <span data-ttu-id="58426-280">Následujícím způsobem nastavte vlastnosti těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="58426-280">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="58426-281">Control</span><span class="sxs-lookup"><span data-stu-id="58426-281">Control</span></span>|<span data-ttu-id="58426-282">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="58426-282">Property</span></span>|<span data-ttu-id="58426-283">Value</span><span class="sxs-lookup"><span data-stu-id="58426-283">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="58426-284">**Text**</span><span class="sxs-lookup"><span data-stu-id="58426-284">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="58426-285">**Název**</span><span class="sxs-lookup"><span data-stu-id="58426-285">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="58426-286">**Název**</span><span class="sxs-lookup"><span data-stu-id="58426-286">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="58426-287">**Formátovat**</span><span class="sxs-lookup"><span data-stu-id="58426-287">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

12. <span data-ttu-id="58426-288">V Návrháři poklikejte na **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="58426-288">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="58426-289">Otevře`Private Sub dtpTest_ValueChanged`se **Editor kódu** .</span><span class="sxs-lookup"><span data-stu-id="58426-289">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>

13. <span data-ttu-id="58426-290">Upravte kód tak, aby vypadal takto:</span><span class="sxs-lookup"><span data-stu-id="58426-290">Modify the code so that it resembles the following.</span></span>

    ```vb
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles dtpTest.ValueChanged
        ctlAlarmClock1.AlarmTime = dtpTest.Value
        ctlAlarmClock1.AlarmSet = True
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _
            "hh:mm")
    End Sub
    ```

14. <span data-ttu-id="58426-291">V Průzkumník řešení klikněte pravým tlačítkem na **test**a pak klikněte na **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="58426-291">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

15. <span data-ttu-id="58426-292">Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="58426-292">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="58426-293">Spustí se testovací program.</span><span class="sxs-lookup"><span data-stu-id="58426-293">The test program starts.</span></span> <span data-ttu-id="58426-294">Všimněte si, že aktuální čas je aktualizován v `ctlAlarmClock` ovládacím prvku a že počáteční čas je zobrazen <xref:System.Windows.Forms.DateTimePicker> v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="58426-294">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

16. <span data-ttu-id="58426-295">Klikněte na <xref:System.Windows.Forms.DateTimePicker> místo, kde se zobrazují minuty hodiny.</span><span class="sxs-lookup"><span data-stu-id="58426-295">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

17. <span data-ttu-id="58426-296">Pomocí klávesnice nastavte hodnotu minuty, která je 1 minutou větší než aktuální čas zobrazený v `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="58426-296">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="58426-297">Čas pro nastavení alarmu je zobrazen v `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="58426-297">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="58426-298">Počkejte, až zobrazený čas dorazí na čas nastavení alarmu.</span><span class="sxs-lookup"><span data-stu-id="58426-298">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="58426-299">Když zobrazený čas dosáhne doby, po kterou je nastavené alarmu, bude zvukový signál zvuk `lblAlarm` a bude blikat.</span><span class="sxs-lookup"><span data-stu-id="58426-299">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>

18. <span data-ttu-id="58426-300">Vypněte alarm kliknutím na tlačítko `lblAlarm`.</span><span class="sxs-lookup"><span data-stu-id="58426-300">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="58426-301">Nyní můžete resetovat alarm.</span><span class="sxs-lookup"><span data-stu-id="58426-301">You may now reset the alarm.</span></span>

     <span data-ttu-id="58426-302">Tento návod pokrývá řadu klíčových konceptů.</span><span class="sxs-lookup"><span data-stu-id="58426-302">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="58426-303">Naučili jste se vytvořit složený ovládací prvek kombinováním ovládacích prvků a součástí do složeného kontejneru ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="58426-303">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="58426-304">Seznámili jste se s přidáním vlastností do ovládacího prvku a při psaní kódu pro implementaci vlastních funkcí.</span><span class="sxs-lookup"><span data-stu-id="58426-304">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="58426-305">V poslední části jste se dozvěděli o rozšíření funkcí daného složeného ovládacího prvku prostřednictvím dědičnosti a ke změně funkčnosti metod hostitele přepsáním těchto metod.</span><span class="sxs-lookup"><span data-stu-id="58426-305">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="58426-306">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58426-306">See also</span></span>

- [<span data-ttu-id="58426-307">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="58426-307">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="58426-308">Postupy: Vytváření složených ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="58426-308">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- [<span data-ttu-id="58426-309">Postupy: Zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="58426-309">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
