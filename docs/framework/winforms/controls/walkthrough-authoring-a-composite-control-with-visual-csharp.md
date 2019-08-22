---
title: 'Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: 12b506e859579a0755c2e9842e792c59968c94a8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666756"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a><span data-ttu-id="ba9ef-102">Návod: Vytváření složeného ovládacího prvku pomocí Visual C\#</span><span class="sxs-lookup"><span data-stu-id="ba9ef-102">Walkthrough: Authoring a Composite Control with Visual C\#</span></span>

<span data-ttu-id="ba9ef-103">Složené ovládací prvky poskytují prostředky, pomocí kterých lze vytvořit a znovu použít vlastní grafická rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="ba9ef-104">Složený ovládací prvek je v podstatě součástí vizuální reprezentace.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="ba9ef-105">V takovém případě se může skládat z jednoho nebo více model Windows Forms ovládacích prvků, komponent nebo bloků kódu, které mohou rozšiřování funkcí pomocí ověření vstupu uživatele, změny vlastností zobrazení nebo provádění jiných úloh vyžadovaných autorem.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="ba9ef-106">Složené ovládací prvky lze umístit na model Windows Forms stejným způsobem jako jiné ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="ba9ef-107">V první části tohoto návodu vytvoříte jednoduchý složený ovládací prvek s názvem `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="ba9ef-108">V druhé části návodu rozšíříte funkce `ctlClock` nástroje prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="ba9ef-109">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="ba9ef-109">Creating the Project</span></span>

<span data-ttu-id="ba9ef-110">Při vytváření nového projektu zadáte jeho název pro nastavení kořenového oboru názvů, název sestavení a název projektu a zajistěte, aby byla výchozí komponenta ve správném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="ba9ef-111">Vytvoření knihovny ovládacích prvků ctlClockLib a ovládacího prvku ctlClock</span><span class="sxs-lookup"><span data-stu-id="ba9ef-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="ba9ef-112">V nabídce **soubor** přejděte na příkaz **Nový**a kliknutím na položku **projekt** otevřete dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="ba9ef-112">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="ba9ef-113">V seznamu C# vizuálních projektů vyberte šablonu projektu **Knihovna ovládacích prvků model Windows Forms** , do pole `ctlClockLib` **název** zadejte a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-113">From the list of Visual C# projects, select the **Windows Forms Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>

     <span data-ttu-id="ba9ef-114">Název projektu, `ctlClockLib`, je ve výchozím nastavení přiřazen ke kořenovému oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-114">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="ba9ef-115">Kořenový obor názvů slouží k získání názvů komponent v sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-115">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="ba9ef-116">Například pokud dvě sestavení poskytují komponenty s názvem `ctlClock`, můžete určit svou `ctlClock` komponentu pomocí`ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="ba9ef-116">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

3. <span data-ttu-id="ba9ef-117">V Průzkumník řešení klikněte pravým tlačítkem na **UserControl1.cs**a pak klikněte na **Přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-117">In Solution Explorer, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="ba9ef-118">Změňte název souboru na `ctlClock.cs`.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-118">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="ba9ef-119">Pokud se zobrazí dotaz, zda chcete přejmenovat všechny odkazy na prvek kódu "UserControl1", klikněte na tlačítko **Ano** .</span><span class="sxs-lookup"><span data-stu-id="ba9ef-119">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="ba9ef-120">Ve výchozím nastavení dědí složený ovládací prvek ze <xref:System.Windows.Forms.UserControl> třídy poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-120">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="ba9ef-121"><xref:System.Windows.Forms.UserControl> Třída poskytuje funkce vyžadované všemi složenými ovládacími prvky a implementuje standardní metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-121">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

4. <span data-ttu-id="ba9ef-122">V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-122">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="ba9ef-123">Přidávání ovládacích prvků a součástí systému Windows do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ba9ef-123">Adding Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="ba9ef-124">Vizuální rozhraní je podstatnou součástí složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-124">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="ba9ef-125">Toto vizuální rozhraní je implementováno přidáním jednoho nebo více ovládacích prvků Windows na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-125">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="ba9ef-126">V následující ukázce zahrnete ovládací prvky Windows do složeného ovládacího prvku a napíšete kód pro implementaci funkcí.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-126">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="ba9ef-127">Přidání popisku a časovače do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ba9ef-127">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="ba9ef-128">V Průzkumník řešení klikněte pravým tlačítkem na **ctlClock.cs**a potom klikněte na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-128">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="ba9ef-129">V sadě **nástrojů**rozbalte uzel **běžné ovládací prvky** a dvakrát klikněte na položku **popisek**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-129">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="ba9ef-130">Ovládací prvek s `label1` názvem je přidán k ovládacímu prvku na návrhové ploše. <xref:System.Windows.Forms.Label></span><span class="sxs-lookup"><span data-stu-id="ba9ef-130">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="ba9ef-131">V návrháři klikněte na možnost **Label1**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-131">In the designer, click **label1**.</span></span> <span data-ttu-id="ba9ef-132">V okno Vlastnosti nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-132">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="ba9ef-133">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ba9ef-133">Property</span></span>|<span data-ttu-id="ba9ef-134">Změnit na</span><span class="sxs-lookup"><span data-stu-id="ba9ef-134">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="ba9ef-135">**Název**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-135">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="ba9ef-136">**Text**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-136">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="ba9ef-137">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-137">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="ba9ef-138">**Font. Size**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-138">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="ba9ef-139">V sadě **nástrojů**rozbalte uzel **komponenty** a dvakrát klikněte na položku **časovač**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-139">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="ba9ef-140">Vzhledem k <xref:System.Windows.Forms.Timer> tomu, že se jedná o komponentu, nemá v době běhu žádná vizuální reprezentace.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-140">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="ba9ef-141">Proto se nezobrazí s ovládacími prvky na návrhové ploše, ale spíše v **Návrháři komponent** (zásobník na spodní straně návrhové plochy).</span><span class="sxs-lookup"><span data-stu-id="ba9ef-141">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="ba9ef-142">V **Návrháři komponent**klikněte na **Timer1**a <xref:System.Windows.Forms.Timer.Interval%2A> pak nastavte `true`vlastnost na `1000`. <xref:System.Windows.Forms.Timer.Enabled%2A></span><span class="sxs-lookup"><span data-stu-id="ba9ef-142">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="ba9ef-143">Vlastnost určuje četnost, se kterou se <xref:System.Windows.Forms.Timer> komponenta zaškrtne. <xref:System.Windows.Forms.Timer.Interval%2A></span><span class="sxs-lookup"><span data-stu-id="ba9ef-143">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="ba9ef-144">Každé časové `timer1` impulsy spustí kód `timer1_Tick` v události.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-144">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="ba9ef-145">Interval představuje počet milisekund mezi takty.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-145">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="ba9ef-146">V **Návrháři komponent**poklikejte na **Timer1** a `timer1_Tick` přejděte na událost pro `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-146">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="ba9ef-147">Upravte kód tak, aby vypadal jako následující ukázka kódu.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-147">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="ba9ef-148">Nezapomeňte změnit modifikátor přístupu z `private` na. `protected`</span><span class="sxs-lookup"><span data-stu-id="ba9ef-148">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="ba9ef-149">Tento kód způsobí, že bude aktuální čas zobrazen v `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-149">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="ba9ef-150">Vzhledem k tomu, `timer1` že interval byl `1000`nastaven na hodnotu, bude tato událost provedena každých tisíc milisekund, čímž se aktualizuje aktuální čas každou sekundu.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-150">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="ba9ef-151">Upravte metodu, kterou chcete přepsat pomocí `virtual` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-151">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="ba9ef-152">Další informace najdete v části "dědění z uživatelského ovládacího prvku" níže.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-152">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="ba9ef-153">V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-153">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="ba9ef-154">Přidání vlastností do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ba9ef-154">Adding Properties to the Composite Control</span></span>

<span data-ttu-id="ba9ef-155">Ovládací prvek hodiny nyní zapouzdřuje <xref:System.Windows.Forms.Label> ovládací prvek <xref:System.Windows.Forms.Timer> a komponentu, z nichž každá má svou vlastní sadu vlastností.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-155">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="ba9ef-156">Přestože jednotlivé vlastnosti těchto ovládacích prvků nebudou k dispozici pro následné uživatele vašeho ovládacího prvku, můžete vytvořit a vystavit vlastní vlastnosti zápisem příslušných bloků kódu.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-156">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="ba9ef-157">V následujícím postupu přidáte vlastnosti ovládacího prvku, který uživateli umožňuje změnit barvu pozadí a textu.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-157">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="ba9ef-158">Přidání vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ba9ef-158">To add a property to your composite control</span></span>

1. <span data-ttu-id="ba9ef-159">V Průzkumník řešení klikněte pravým tlačítkem na **ctlClock.cs**a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-159">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="ba9ef-160">Otevře se **Editor kódu** pro váš ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-160">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="ba9ef-161">`public partial class ctlClock` Vyhledejte příkaz.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-161">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="ba9ef-162">Pod levou složenou závorku`{)`(zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-162">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="ba9ef-163">Tyto příkazy vytvoří soukromé proměnné, které použijete k uložení hodnot pro vlastnosti, které se chystáte vytvořit.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-163">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="ba9ef-164">Zadejte následující kód pod deklaracemi proměnných z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-164">Type the following code beneath the variable declarations from step 2.</span></span>

    ```csharp
    // Declares the name and type of the property.
    public Color ClockBackColor
    {
        // Retrieves the value of the private variable colBColor.
        get
        {
            return colBColor;
        }
        // Stores the selected value in the private variable colBColor, and
        // updates the background color of the label control lblDisplay.
        set
        {
            colBColor = value;
            lblDisplay.BackColor = colBColor;
        }
    }
    // Provides a similar set of instructions for the foreground color.
    public Color ClockForeColor
    {
        get
        {
            return colFColor;
        }
        set
        {
            colFColor = value;
            lblDisplay.ForeColor = colFColor;
        }
    }
    ```

     <span data-ttu-id="ba9ef-165">Předchozí kód zpřístupňuje dvě vlastní vlastnosti `ClockForeColor` a `ClockBackColor`, které jsou k dispozici dalším uživatelům tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-165">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="ba9ef-166">Příkazy `get` a`set` poskytují úložiště a načtení hodnoty vlastnosti a také kód pro implementaci funkcí vhodných pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-166">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="ba9ef-167">V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-167">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="testing-the-control"></a><span data-ttu-id="ba9ef-168">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ba9ef-168">Testing the Control</span></span>

<span data-ttu-id="ba9ef-169">Ovládací prvky nejsou samostatné aplikace; musí být hostovány v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-169">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="ba9ef-170">Otestujte chování ovládacího prvku za běhu a využijte jeho vlastnosti pomocí **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-170">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="ba9ef-171">Další informace najdete v tématu [jak: Otestuje chování prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-171">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="ba9ef-172">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ba9ef-172">To test your control</span></span>

1. <span data-ttu-id="ba9ef-173">Stisknutím klávesy F5 Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-173">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="ba9ef-174">V mřížce vlastností kontejneru testů vyhledejte `ClockBackColor` vlastnost a potom vyberte vlastnost, která zobrazí paletu barev.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-174">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="ba9ef-175">Vyberte barvu kliknutím na ni.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-175">Choose a color by clicking it.</span></span>

     <span data-ttu-id="ba9ef-176">Barva pozadí ovládacího prvku se změní na barvu, kterou jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-176">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="ba9ef-177">Pomocí podobné posloupnosti událostí ověřte, zda `ClockForeColor` vlastnost pracuje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-177">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

     <span data-ttu-id="ba9ef-178">V této části a předchozích částech jste viděli, jak mohou být komponenty a ovládací prvky systému Windows kombinovány s kódem a balíčkem, aby poskytovaly vlastní funkce ve formě složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-178">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="ba9ef-179">Naučili jste se vystavit vlastnosti ve složeném ovládacím prvku a jak otestovat ovládací prvek po jeho dokončení.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-179">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="ba9ef-180">V další části se dozvíte, jak vytvořit zděděný složený ovládací prvek pomocí `ctlClock` jako základu.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-180">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="ba9ef-181">Dědění ze složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ba9ef-181">Inheriting from a Composite Control</span></span>

<span data-ttu-id="ba9ef-182">V předchozích částech jste zjistili, jak zkombinovat ovládací prvky, komponenty a kód Windows do opakovaně použitelných složených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-182">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="ba9ef-183">Složený ovládací prvek se teď dá použít jako základ, na kterém můžou být sestavené další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-183">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="ba9ef-184">Proces odvození třídy ze základní třídy se nazývá *Dědičnost*.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-184">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="ba9ef-185">V této části vytvoříte složený ovládací prvek, který se nazývá `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-185">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="ba9ef-186">Tento ovládací prvek bude odvozen z jeho nadřazeného ovládacího prvku `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-186">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="ba9ef-187">Naučíte se rozšíření funkcí `ctlClock` přepsáním nadřazených metod a přidáním nových metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-187">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="ba9ef-188">Prvním krokem při vytváření zděděného ovládacího prvku je jeho odvození od jeho nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-188">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="ba9ef-189">Tato akce vytvoří nový ovládací prvek, který obsahuje všechny vlastnosti, metody a grafické charakteristiky nadřazeného ovládacího prvku, ale může také sloužit jako základ pro přidání nových nebo upravených funkcí.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-189">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="ba9ef-190">Vytvoření zděděného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ba9ef-190">To create the inherited control</span></span>

1. <span data-ttu-id="ba9ef-191">V Průzkumník řešení klikněte pravým tlačítkem myši na **ctlClockLib**, přejděte na **Přidat**a pak klikněte na **uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-191">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="ba9ef-192">**Přidat novou položku** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-192">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="ba9ef-193">Vyberte šablonu **zděděného uživatelského ovládacího prvku** .</span><span class="sxs-lookup"><span data-stu-id="ba9ef-193">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="ba9ef-194">Do pole **název** zadejte `ctlAlarmClock.cs`a pak klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-194">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="ba9ef-195">Zobrazí se dialogové okno **Výběr dědičnosti** .</span><span class="sxs-lookup"><span data-stu-id="ba9ef-195">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="ba9ef-196">V části **název součásti**poklikejte na **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-196">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="ba9ef-197">V Průzkumník řešení Procházet aktuální projekty.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-197">In Solution Explorer, browse through the current projects.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="ba9ef-198">Do aktuálního projektu byl přidán soubor s názvem **ctlAlarmClock.cs** .</span><span class="sxs-lookup"><span data-stu-id="ba9ef-198">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="adding-the-alarm-properties"></a><span data-ttu-id="ba9ef-199">Přidání vlastností alarmu</span><span class="sxs-lookup"><span data-stu-id="ba9ef-199">Adding the Alarm Properties</span></span>

<span data-ttu-id="ba9ef-200">Vlastnosti jsou přidány do zděděného ovládacího prvku stejným způsobem jako přidaným do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-200">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="ba9ef-201">Nyní použijete syntaxi deklarace vlastností k přidání dvou vlastností do ovládacího prvku: `AlarmTime`, který bude uchovávat hodnotu data a času, kdy má alarm přejít, a `AlarmSet`, který bude označovat, zda je alarm nastaven.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-201">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="ba9ef-202">Přidání vlastností do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ba9ef-202">To add properties to your composite control</span></span>

1. <span data-ttu-id="ba9ef-203">V Průzkumník řešení klikněte pravým tlačítkem na **ctlAlarmClock**a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-203">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="ba9ef-204">`public class` Vyhledejte příkaz.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-204">Locate the `public class` statement.</span></span> <span data-ttu-id="ba9ef-205">Všimněte si, že ovládací prvek `ctlClockLib.ctlClock`dědí z.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-205">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="ba9ef-206">Pod levou složenou závorku`{)` (příkaz zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-206">Beneath the opening brace (`{)` statement, type the following code.</span></span>

    ```csharp
    private DateTime dteAlarmTime;
    private bool blnAlarmSet;
    // These properties will be declared as public to allow future
    // developers to access them.
    public DateTime AlarmTime
    {
        get
        {
            return dteAlarmTime;
        }
        set
        {
            dteAlarmTime = value;
        }
    }
    public bool AlarmSet
    {
        get
        {
            return blnAlarmSet;
        }
        set
        {
            blnAlarmSet = value;
        }
    }
    ```

### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="ba9ef-207">Přidání do grafického rozhraní ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ba9ef-207">Adding to the Graphical Interface of the Control</span></span>

<span data-ttu-id="ba9ef-208">Zděděný ovládací prvek má vizuální rozhraní, které je identické s ovládacím prvkem, ze kterého dědí.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-208">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="ba9ef-209">Má stejné ovládací prvky jako svůj nadřazený ovládací prvek, ale vlastnosti ovládacích prvků nebudou k dispozici, pokud nebyly výslovně zpřístupněny.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-209">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="ba9ef-210">Můžete přidat do grafického rozhraní zděděného složeného ovládacího prvku stejným způsobem, jako byste přidali do jakéhokoli složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-210">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="ba9ef-211">Pokud chcete pokračovat v přidávání do vizuálního rozhraní pro budíky, přidejte ovládací prvek popisek, který bude při zvukovém alarmu blikat.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-211">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="ba9ef-212">Přidání ovládacího prvku popisek</span><span class="sxs-lookup"><span data-stu-id="ba9ef-212">To add the label control</span></span>

1. <span data-ttu-id="ba9ef-213">V Průzkumník řešení klikněte pravým tlačítkem na **ctlAlarmClock**a potom klikněte na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-213">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="ba9ef-214">Návrhář pro `ctlAlarmClock` se otevře v hlavním okně.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-214">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="ba9ef-215">Klikněte na zobrazenou část ovládacího prvku a zobrazte okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-215">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ba9ef-216">Všechny vlastnosti jsou zobrazeny šedě.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-216">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="ba9ef-217">To znamená, že tyto vlastnosti jsou nativní `lblDisplay` a nelze je upravovat nebo k nim nelze přicházet v okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-217">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="ba9ef-218">Ve výchozím nastavení jsou `private`ovládací prvky obsažené ve složeném ovládacím prvku a jejich vlastnosti přístupné žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-218">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ba9ef-219">Pokud chcete, aby následující uživatelé složeného ovládacího prvku měli přístup k vnitřním ovládacím prvkům, deklarujte `public` je `protected`jako nebo.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-219">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="ba9ef-220">To vám umožní nastavit a upravit vlastnosti ovládacích prvků obsažených v rámci složeného ovládacího prvku pomocí příslušného kódu.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-220">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="ba9ef-221"><xref:System.Windows.Forms.Label> Přidejte ovládací prvek do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-221">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="ba9ef-222">Pomocí myši přetáhněte <xref:System.Windows.Forms.Label> ovládací prvek hned pod zobrazeným polem.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-222">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="ba9ef-223">V okno Vlastnosti nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-223">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="ba9ef-224">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ba9ef-224">Property</span></span>|<span data-ttu-id="ba9ef-225">Nastavení</span><span class="sxs-lookup"><span data-stu-id="ba9ef-225">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="ba9ef-226">**Název**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-226">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="ba9ef-227">**Text**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-227">**Text**</span></span>|<span data-ttu-id="ba9ef-228">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-228">**Alarm!**</span></span>|
    |<span data-ttu-id="ba9ef-229">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-229">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="ba9ef-230">**Zobrazeny**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-230">**Visible**</span></span>|`false`|

### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="ba9ef-231">Přidání funkce alarmu</span><span class="sxs-lookup"><span data-stu-id="ba9ef-231">Adding the Alarm Functionality</span></span>

<span data-ttu-id="ba9ef-232">V předchozích postupech jste přidali vlastnosti a ovládací prvek, který umožní funkci alarmu ve složeném ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-232">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="ba9ef-233">V tomto postupu přidáte kód, který bude porovnávat aktuální čas s časem alarmu, a pokud se jedná o stejnou dobu, aby se pomohlo zablikat alarm.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-233">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="ba9ef-234">Tím, že `ctlClock` `ctlClock`přepíšete `timer1_Tick` metodu a přidáte do ní další kód, rozšíříte možnost azachováte`ctlAlarmClock` všechny podstatné funkce.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-234">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="ba9ef-235">Přepsání metody timer1_Tick pro ctlClock</span><span class="sxs-lookup"><span data-stu-id="ba9ef-235">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="ba9ef-236">V **editoru kódu**vyhledejte `private bool blnAlarmSet;` příkaz.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-236">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="ba9ef-237">Hned pod ním přidejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-237">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="ba9ef-238">V **editoru kódu**vyhledejte pravou složenou závorku (`})` na konci třídy.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-238">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="ba9ef-239">Těsně před složenou závorku přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-239">Just before the brace, add the following code.</span></span>

    ```csharp
    protected override void timer1_Tick(object sender, System.EventArgs e)
    {
        // Calls the Timer1_Tick method of ctlClock.
        base.timer1_Tick(sender, e);
        // Checks to see if the alarm is set.
        if (AlarmSet == false)
            return;
        else
            // If the date, hour, and minute of the alarm time are the same as
            // the current time, flash an alarm.
        {
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)
            {
                // Sets lblAlarmVisible to true, and changes the background color based on
                // the value of blnColorTicker. The background color of the label
                // will flash once per tick of the clock.
                lblAlarm.Visible = true;
                if (blnColorTicker == false)
                {
                    lblAlarm.BackColor = Color.Red;
                    blnColorTicker = true;
                }
                else
                {
                    lblAlarm.BackColor = Color.Blue;
                    blnColorTicker = false;
                }
            }
            else
            {
                // Once the alarm has sounded for a minute, the label is made
                // invisible again.
                lblAlarm.Visible = false;
            }
        }
    }
    ```

     <span data-ttu-id="ba9ef-240">Přidání tohoto kódu dosahuje několika úloh.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-240">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="ba9ef-241">`override` Příkaz nasměruje ovládací prvek na použití této metody místo metody, která byla zděděna ze základního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-241">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="ba9ef-242">Při volání této metody volá metodu, kterou Přepisuje, vyvoláním `base.timer1_Tick` příkazu, čímž se zajistí, že všechny funkce zahrnuté v původním ovládacím prvku budou v tomto ovládacím prvku reprodukovány.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-242">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="ba9ef-243">Potom spustí další kód, který bude začlenit funkci alarmu.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-243">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="ba9ef-244">Pokud dojde k alarmu, zobrazí se ovládací prvek popisku, který bude blikat.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-244">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="ba9ef-245">Ovládací prvek hodiny budíku je skoro kompletní.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-245">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="ba9ef-246">Jediná věc, kterou zbývá, je implementovat způsob, jak ho vypnout.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-246">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="ba9ef-247">K tomu je třeba přidat kód do `lblAlarm_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-247">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="ba9ef-248">Implementace metody shutoff</span><span class="sxs-lookup"><span data-stu-id="ba9ef-248">To implement the shutoff method</span></span>

1. <span data-ttu-id="ba9ef-249">V Průzkumník řešení klikněte pravým tlačítkem na **ctlAlarmClock.cs**a potom klikněte na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-249">In Solution Explorer, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="ba9ef-250">Otevře se Návrhář.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-250">The designer opens.</span></span>

2. <span data-ttu-id="ba9ef-251">Přidejte k ovládacímu prvku tlačítko.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-251">Add a button to the control.</span></span> <span data-ttu-id="ba9ef-252">Nastavte vlastnosti tlačítka následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-252">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="ba9ef-253">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ba9ef-253">Property</span></span>|<span data-ttu-id="ba9ef-254">Value</span><span class="sxs-lookup"><span data-stu-id="ba9ef-254">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="ba9ef-255">**Název**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-255">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="ba9ef-256">**Text**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-256">**Text**</span></span>|<span data-ttu-id="ba9ef-257">**Zakázat alarm**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-257">**Disable Alarm**</span></span>|

3. <span data-ttu-id="ba9ef-258">V Návrháři poklikejte na **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-258">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="ba9ef-259">Otevře se **Editor kódu** na `private void btnAlarmOff_Click` řádku.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-259">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="ba9ef-260">Upravte tuto metodu tak, aby vypadala jako následující kód.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-260">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="ba9ef-261">V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-261">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="ba9ef-262">Použití zděděného ovládacího prvku na formuláři</span><span class="sxs-lookup"><span data-stu-id="ba9ef-262">Using the Inherited Control on a Form</span></span>

<span data-ttu-id="ba9ef-263">Zděděný ovládací prvek lze otestovat stejným způsobem jako ovládací prvek `ctlClock`základní třídy: Stisknutím klávesy F5 Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-263">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="ba9ef-264">Další informace najdete v tématu [jak: Otestuje chování prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-264">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="ba9ef-265">Chcete-li ovládací prvek použít, budete ho muset hostovat na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-265">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="ba9ef-266">Stejně jako u standardního složeného ovládacího prvku nemůže zděděný složený ovládací prvek samostatně a musí být hostovaný ve formuláři nebo jiném kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-266">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="ba9ef-267">Vzhledem `ctlAlarmClock` k tomu, že má větší hloubku funkčnosti, je nutné k otestování dalšího kódu.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-267">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="ba9ef-268">V tomto postupu napíšete jednoduchý program, který bude testovat funkčnost `ctlAlarmClock`nástroje.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-268">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="ba9ef-269">Napíšete kód pro nastavení a zobrazení `AlarmTime` `ctlAlarmClock`vlastnosti a otestujete své své vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-269">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="ba9ef-270">Sestavení a přidání ovládacího prvku do formuláře testu</span><span class="sxs-lookup"><span data-stu-id="ba9ef-270">To build and add your control to a test form</span></span>

1. <span data-ttu-id="ba9ef-271">V Průzkumník řešení klikněte pravým tlačítkem na **ctlClockLib**a pak klikněte na **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-271">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="ba9ef-272">Přidejte do řešení nový projekt **aplikace pro Windows** a pojmenujte ho `Test`.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-272">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>

3. <span data-ttu-id="ba9ef-273">V Průzkumník řešení klikněte pravým tlačítkem myši na uzel **odkazy** pro projekt testů.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-273">In Solution Explorer, right-click the **References** node for your test project.</span></span> <span data-ttu-id="ba9ef-274">Kliknutím na tlačítko **Přidat odkaz** zobrazíte dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="ba9ef-274">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="ba9ef-275">Klikněte na kartu s označením **projekty**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-275">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="ba9ef-276">Projekt bude uveden v části **název projektu.** `ctlClockLib`</span><span class="sxs-lookup"><span data-stu-id="ba9ef-276">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="ba9ef-277">Dvojím kliknutím na projekt přidejte odkaz na testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-277">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="ba9ef-278">V Průzkumník řešení klikněte pravým tlačítkem na **test**a pak klikněte na **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-278">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="ba9ef-279">V **sadě nástrojů**rozbalte uzel **součásti ctlClockLib** .</span><span class="sxs-lookup"><span data-stu-id="ba9ef-279">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="ba9ef-280">Dvojím kliknutím na **ctlAlarmClock** přidáte kopii `ctlAlarmClock` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-280">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="ba9ef-281">V **sadě nástrojů**Najděte a dvakrát klikněte na **DateTimePicker** a přidejte <xref:System.Windows.Forms.DateTimePicker> ovládací prvek do <xref:System.Windows.Forms.Label> formuláře a pak přidejte ovládací prvek dvojitým kliknutím na **popisek**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-281">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="ba9ef-282">Pomocí myši umístěte ovládací prvky na vhodné místo na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-282">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="ba9ef-283">Následujícím způsobem nastavte vlastnosti těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-283">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="ba9ef-284">Control</span><span class="sxs-lookup"><span data-stu-id="ba9ef-284">Control</span></span>|<span data-ttu-id="ba9ef-285">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ba9ef-285">Property</span></span>|<span data-ttu-id="ba9ef-286">Value</span><span class="sxs-lookup"><span data-stu-id="ba9ef-286">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="ba9ef-287">**Text**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-287">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="ba9ef-288">**Název**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-288">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="ba9ef-289">**Název**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-289">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="ba9ef-290">**Formátovat**</span><span class="sxs-lookup"><span data-stu-id="ba9ef-290">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="ba9ef-291">V Návrháři poklikejte na **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-291">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="ba9ef-292">Otevře`private void dtpTest_ValueChanged`se **Editor kódu** .</span><span class="sxs-lookup"><span data-stu-id="ba9ef-292">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="ba9ef-293">Upravte kód tak, aby vypadal takto:</span><span class="sxs-lookup"><span data-stu-id="ba9ef-293">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="ba9ef-294">V Průzkumník řešení klikněte pravým tlačítkem na **test**a pak klikněte na **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-294">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="ba9ef-295">Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-295">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="ba9ef-296">Spustí se testovací program.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-296">The test program starts.</span></span> <span data-ttu-id="ba9ef-297">Všimněte si, že aktuální čas je aktualizován v `ctlAlarmClock` ovládacím prvku a že počáteční čas je zobrazen <xref:System.Windows.Forms.DateTimePicker> v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-297">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="ba9ef-298">Klikněte na <xref:System.Windows.Forms.DateTimePicker> místo, kde se zobrazují minuty hodiny.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-298">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="ba9ef-299">Pomocí klávesnice nastavte hodnotu minuty, která je 1 minutou větší než aktuální čas zobrazený v `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-299">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="ba9ef-300">Čas pro nastavení alarmu je zobrazen v `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-300">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="ba9ef-301">Počkejte, až zobrazený čas dorazí na čas nastavení alarmu.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-301">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="ba9ef-302">Když zobrazená doba dosáhne doby, na kterou je nastavené alarm, `lblAlarm` bude blikat.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-302">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="ba9ef-303">Vypněte alarm kliknutím na tlačítko `btnAlarmOff`.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-303">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="ba9ef-304">Nyní můžete resetovat alarm.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-304">You may now reset the alarm.</span></span>

     <span data-ttu-id="ba9ef-305">Tento návod pokrývá řadu klíčových konceptů.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-305">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="ba9ef-306">Naučili jste se vytvořit složený ovládací prvek kombinováním ovládacích prvků a součástí do složeného kontejneru ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-306">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="ba9ef-307">Seznámili jste se s přidáním vlastností do ovládacího prvku a při psaní kódu pro implementaci vlastních funkcí.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-307">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="ba9ef-308">V poslední části jste se dozvěděli o rozšíření funkcí daného složeného ovládacího prvku prostřednictvím dědičnosti a ke změně funkčnosti metod hostitele přepsáním těchto metod.</span><span class="sxs-lookup"><span data-stu-id="ba9ef-308">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba9ef-309">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba9ef-309">See also</span></span>

- [<span data-ttu-id="ba9ef-310">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="ba9ef-310">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="ba9ef-311">Postupy: Zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="ba9ef-311">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="ba9ef-312">Návod: Dědění z ovládacího prvku model Windows Forms pomocí vizuáluC#</span><span class="sxs-lookup"><span data-stu-id="ba9ef-312">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
