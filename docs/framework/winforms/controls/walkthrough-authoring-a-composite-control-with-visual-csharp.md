---
title: 'Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#'
ms.date: 03/30/2017
dev_langs:
- CSharp
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c1d9be77550b1255a24120c68f20d25640e0ebdf
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460627"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a><span data-ttu-id="e915a-102">Návod: Vytvoření složeného ovládacího prvku pomocí jazyka C\#</span><span class="sxs-lookup"><span data-stu-id="e915a-102">Walkthrough: Author a Composite Control with C\#</span></span>

<span data-ttu-id="e915a-103">Složené ovládací prvky poskytují prostředky, pomocí kterých lze vytvořit a znovu použít vlastní grafická rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e915a-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="e915a-104">Složený ovládací prvek je v podstatě součástí vizuální reprezentace.</span><span class="sxs-lookup"><span data-stu-id="e915a-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="e915a-105">V takovém případě se může skládat z jednoho nebo více model Windows Forms ovládacích prvků, komponent nebo bloků kódu, které mohou rozšiřování funkcí pomocí ověření vstupu uživatele, změny vlastností zobrazení nebo provádění jiných úloh vyžadovaných autorem.</span><span class="sxs-lookup"><span data-stu-id="e915a-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="e915a-106">Složené ovládací prvky lze umístit na model Windows Forms stejným způsobem jako jiné ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e915a-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="e915a-107">V první části tohoto návodu vytvoříte jednoduchý složený ovládací prvek s názvem `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="e915a-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="e915a-108">V druhé části návodu rozšíříte funkci `ctlClock` prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="e915a-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="e915a-109">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="e915a-109">Create the Project</span></span>

<span data-ttu-id="e915a-110">Při vytváření nového projektu zadáte jeho název pro nastavení kořenového oboru názvů, název sestavení a název projektu a zajistěte, aby byla výchozí komponenta ve správném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e915a-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="e915a-111">Vytvoření knihovny ovládacích prvků ctlClockLib a ovládacího prvku ctlClock</span><span class="sxs-lookup"><span data-stu-id="e915a-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="e915a-112">V aplikaci Visual Studio vytvořte nový projekt **knihovny ovládacích prvků model Windows Forms** a pojmenujte jej **ctlClockLib**.</span><span class="sxs-lookup"><span data-stu-id="e915a-112">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ctlClockLib**.</span></span>

     <span data-ttu-id="e915a-113">Název projektu, `ctlClockLib`, je ve výchozím nastavení přiřazen také kořenovému oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e915a-113">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="e915a-114">Kořenový obor názvů slouží k získání názvů komponent v sestavení.</span><span class="sxs-lookup"><span data-stu-id="e915a-114">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="e915a-115">Například pokud dvě sestavení poskytují komponenty s názvem `ctlClock`, můžete určit `ctlClock` komponentu pomocí `ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="e915a-115">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

2. <span data-ttu-id="e915a-116">V **Průzkumník řešení**klikněte pravým tlačítkem na **UserControl1.cs**a pak klikněte na **Přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="e915a-116">In **Solution Explorer**, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="e915a-117">Změňte název souboru na `ctlClock.cs`.</span><span class="sxs-lookup"><span data-stu-id="e915a-117">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="e915a-118">Pokud se zobrazí dotaz, zda chcete přejmenovat všechny odkazy na prvek kódu "UserControl1", klikněte na tlačítko **Ano** .</span><span class="sxs-lookup"><span data-stu-id="e915a-118">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="e915a-119">Ve výchozím nastavení dědí složený ovládací prvek z <xref:System.Windows.Forms.UserControl> třídy poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="e915a-119">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="e915a-120">Třída <xref:System.Windows.Forms.UserControl> poskytuje funkce vyžadované všemi složenými ovládacími prvky a implementuje standardní metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e915a-120">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

3. <span data-ttu-id="e915a-121">V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="e915a-121">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="e915a-122">Přidat ovládací prvky a součásti systému Windows do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e915a-122">Add Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="e915a-123">Vizuální rozhraní je podstatnou součástí složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e915a-123">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="e915a-124">Toto vizuální rozhraní je implementováno přidáním jednoho nebo více ovládacích prvků Windows na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="e915a-124">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="e915a-125">V následující ukázce zahrnete ovládací prvky Windows do složeného ovládacího prvku a napíšete kód pro implementaci funkcí.</span><span class="sxs-lookup"><span data-stu-id="e915a-125">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="e915a-126">Přidání popisku a časovače do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e915a-126">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="e915a-127">V **Průzkumník řešení**klikněte pravým tlačítkem na **ctlClock.cs**a potom klikněte na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e915a-127">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="e915a-128">V sadě **nástrojů**rozbalte uzel **běžné ovládací prvky** a dvakrát klikněte na položku **popisek**.</span><span class="sxs-lookup"><span data-stu-id="e915a-128">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="e915a-129">Ovládací prvek <xref:System.Windows.Forms.Label> s názvem `label1` je přidán k ovládacímu prvku na návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="e915a-129">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="e915a-130">V návrháři klikněte na možnost **Label1**.</span><span class="sxs-lookup"><span data-stu-id="e915a-130">In the designer, click **label1**.</span></span> <span data-ttu-id="e915a-131">V okno Vlastnosti nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e915a-131">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="e915a-132">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e915a-132">Property</span></span>|<span data-ttu-id="e915a-133">Změnit na</span><span class="sxs-lookup"><span data-stu-id="e915a-133">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="e915a-134">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e915a-134">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="e915a-135">**Text**</span><span class="sxs-lookup"><span data-stu-id="e915a-135">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="e915a-136">**Textu**</span><span class="sxs-lookup"><span data-stu-id="e915a-136">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="e915a-137">**Font. Size**</span><span class="sxs-lookup"><span data-stu-id="e915a-137">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="e915a-138">V sadě **nástrojů**rozbalte uzel **komponenty** a dvakrát klikněte na položku **časovač**.</span><span class="sxs-lookup"><span data-stu-id="e915a-138">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="e915a-139">Vzhledem k tomu, že <xref:System.Windows.Forms.Timer> je komponenta, nemá v době běhu žádná vizuální reprezentace.</span><span class="sxs-lookup"><span data-stu-id="e915a-139">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="e915a-140">Proto se nezobrazí s ovládacími prvky na návrhové ploše, ale spíše v **Návrháři komponent** (zásobník na spodní straně návrhové plochy).</span><span class="sxs-lookup"><span data-stu-id="e915a-140">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="e915a-141">V **Návrháři komponent**klikněte na **Timer1**a pak nastavte vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> na `1000` a vlastnost <xref:System.Windows.Forms.Timer.Enabled%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="e915a-141">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="e915a-142">Vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> řídí frekvenci, se kterou <xref:System.Windows.Forms.Timer> komponenta se zaškrtne.</span><span class="sxs-lookup"><span data-stu-id="e915a-142">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="e915a-143">Pokaždé, když `timer1`, spustí kód v události `timer1_Tick`.</span><span class="sxs-lookup"><span data-stu-id="e915a-143">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="e915a-144">Interval představuje počet milisekund mezi takty.</span><span class="sxs-lookup"><span data-stu-id="e915a-144">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="e915a-145">V **Návrháři komponent**poklikejte na **Timer1** a přejděte na událost `timer1_Tick` pro `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="e915a-145">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="e915a-146">Upravte kód tak, aby vypadal jako následující ukázka kódu.</span><span class="sxs-lookup"><span data-stu-id="e915a-146">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="e915a-147">Nezapomeňte změnit modifikátor přístupu z `private` na `protected`.</span><span class="sxs-lookup"><span data-stu-id="e915a-147">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="e915a-148">Tento kód způsobí, že se aktuální čas zobrazí v `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="e915a-148">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="e915a-149">Vzhledem k tomu, že interval `timer1` byl nastaven na hodnotu `1000`, bude tato událost provedena každých tisíc milisekund, čímž se aktualizuje aktuální čas každou sekundu.</span><span class="sxs-lookup"><span data-stu-id="e915a-149">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="e915a-150">Upravte metodu, kterou chcete přepsat pomocí klíčového slova `virtual`.</span><span class="sxs-lookup"><span data-stu-id="e915a-150">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="e915a-151">Další informace najdete v části "dědění z uživatelského ovládacího prvku" níže.</span><span class="sxs-lookup"><span data-stu-id="e915a-151">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="e915a-152">V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="e915a-152">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-properties-to-the-composite-control"></a><span data-ttu-id="e915a-153">Přidat vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e915a-153">Add Properties to the Composite Control</span></span>

<span data-ttu-id="e915a-154">Ovládací prvek hodiny nyní zapouzdřuje ovládací prvek <xref:System.Windows.Forms.Label> a <xref:System.Windows.Forms.Timer> komponentu, z nichž každá má vlastní sadu vlastních vlastností.</span><span class="sxs-lookup"><span data-stu-id="e915a-154">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="e915a-155">Přestože jednotlivé vlastnosti těchto ovládacích prvků nebudou k dispozici pro následné uživatele vašeho ovládacího prvku, můžete vytvořit a vystavit vlastní vlastnosti zápisem příslušných bloků kódu.</span><span class="sxs-lookup"><span data-stu-id="e915a-155">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="e915a-156">V následujícím postupu přidáte vlastnosti ovládacího prvku, který uživateli umožňuje změnit barvu pozadí a textu.</span><span class="sxs-lookup"><span data-stu-id="e915a-156">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="e915a-157">Přidání vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e915a-157">To add a property to your composite control</span></span>

1. <span data-ttu-id="e915a-158">V **Průzkumník řešení**klikněte pravým tlačítkem na **ctlClock.cs**a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="e915a-158">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="e915a-159">Otevře se **Editor kódu** pro váš ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="e915a-159">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="e915a-160">Vyhledejte příkaz `public partial class ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="e915a-160">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="e915a-161">Pod levou složenou závorku (`{)`zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e915a-161">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="e915a-162">Tyto příkazy vytvoří soukromé proměnné, které použijete k uložení hodnot pro vlastnosti, které se chystáte vytvořit.</span><span class="sxs-lookup"><span data-stu-id="e915a-162">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="e915a-163">Zadejte nebo vložte následující kód pod deklaracemi proměnných z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="e915a-163">Enter or paste the following code beneath the variable declarations from step 2.</span></span>

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

     <span data-ttu-id="e915a-164">Předchozí kód zpřístupňuje dvě vlastní vlastnosti, `ClockForeColor` a `ClockBackColor`, k dispozici dalším uživatelům tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e915a-164">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="e915a-165">Příkazy `get` a `set` poskytují úložiště a načtení hodnoty vlastnosti a také kód pro implementaci funkcí vhodných pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e915a-165">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="e915a-166">V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="e915a-166">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="e915a-167">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e915a-167">Test the Control</span></span>

<span data-ttu-id="e915a-168">Ovládací prvky nejsou samostatné aplikace; musí být hostovány v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e915a-168">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="e915a-169">Otestujte chování ovládacího prvku za běhu a využijte jeho vlastnosti pomocí **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="e915a-169">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="e915a-170">Další informace naleznete v tématu [How to: test runtime Behavior prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="e915a-170">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="e915a-171">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e915a-171">To test your control</span></span>

1. <span data-ttu-id="e915a-172">Stisknutím klávesy **F5** Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="e915a-172">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="e915a-173">V mřížce vlastností kontejneru testu Najděte vlastnost `ClockBackColor` a potom vyberte vlastnost, která zobrazí paletu barev.</span><span class="sxs-lookup"><span data-stu-id="e915a-173">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="e915a-174">Vyberte barvu kliknutím na ni.</span><span class="sxs-lookup"><span data-stu-id="e915a-174">Choose a color by clicking it.</span></span>

   <span data-ttu-id="e915a-175">Barva pozadí ovládacího prvku se změní na barvu, kterou jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="e915a-175">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="e915a-176">Pomocí podobné posloupnosti událostí ověřte, zda vlastnost `ClockForeColor` pracuje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="e915a-176">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

   <span data-ttu-id="e915a-177">V této části a předchozích částech jste viděli, jak mohou být komponenty a ovládací prvky systému Windows kombinovány s kódem a balíčkem, aby poskytovaly vlastní funkce ve formě složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e915a-177">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="e915a-178">Naučili jste se vystavit vlastnosti ve složeném ovládacím prvku a jak otestovat ovládací prvek po jeho dokončení.</span><span class="sxs-lookup"><span data-stu-id="e915a-178">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="e915a-179">V další části se dozvíte, jak vytvořit zděděný složený ovládací prvek pomocí `ctlClock` jako základu.</span><span class="sxs-lookup"><span data-stu-id="e915a-179">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inherit-from-a-composite-control"></a><span data-ttu-id="e915a-180">Zdědit ze složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e915a-180">Inherit from a Composite Control</span></span>

<span data-ttu-id="e915a-181">V předchozích částech jste zjistili, jak zkombinovat ovládací prvky, komponenty a kód Windows do opakovaně použitelných složených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e915a-181">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="e915a-182">Složený ovládací prvek se teď dá použít jako základ, na kterém můžou být sestavené další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e915a-182">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="e915a-183">Proces odvození třídy ze základní třídy se nazývá *Dědičnost*.</span><span class="sxs-lookup"><span data-stu-id="e915a-183">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="e915a-184">V této části vytvoříte složený ovládací prvek s názvem `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="e915a-184">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="e915a-185">Tento ovládací prvek bude odvozen z jeho nadřazeného ovládacího prvku `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="e915a-185">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="e915a-186">Naučíte se rozšíření funkcí `ctlClock` přepsáním nadřazených metod a přidáním nových metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="e915a-186">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="e915a-187">Prvním krokem při vytváření zděděného ovládacího prvku je jeho odvození od jeho nadřazené položky.</span><span class="sxs-lookup"><span data-stu-id="e915a-187">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="e915a-188">Tato akce vytvoří nový ovládací prvek, který obsahuje všechny vlastnosti, metody a grafické charakteristiky nadřazeného ovládacího prvku, ale může také sloužit jako základ pro přidání nových nebo upravených funkcí.</span><span class="sxs-lookup"><span data-stu-id="e915a-188">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="e915a-189">Vytvoření zděděného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e915a-189">To create the inherited control</span></span>

1. <span data-ttu-id="e915a-190">V **Průzkumník řešení**klikněte pravým tlačítkem myši na **ctlClockLib**, přejděte na **Přidat**a pak klikněte na **uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="e915a-190">In **Solution Explorer**, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="e915a-191">Otevře se dialogové okno **Přidat novou položku** .</span><span class="sxs-lookup"><span data-stu-id="e915a-191">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="e915a-192">Vyberte šablonu **zděděného uživatelského ovládacího prvku** .</span><span class="sxs-lookup"><span data-stu-id="e915a-192">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="e915a-193">Do pole **název** zadejte `ctlAlarmClock.cs`a pak klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="e915a-193">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="e915a-194">Zobrazí se dialogové okno **Výběr dědičnosti** .</span><span class="sxs-lookup"><span data-stu-id="e915a-194">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="e915a-195">V části **název součásti**poklikejte na **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="e915a-195">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="e915a-196">V **Průzkumník řešení**Procházet aktuální projekty.</span><span class="sxs-lookup"><span data-stu-id="e915a-196">In **Solution Explorer**, browse through the current projects.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e915a-197">Do aktuálního projektu byl přidán soubor s názvem **ctlAlarmClock.cs** .</span><span class="sxs-lookup"><span data-stu-id="e915a-197">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="add-the-alarm-properties"></a><span data-ttu-id="e915a-198">Přidání vlastností alarmu</span><span class="sxs-lookup"><span data-stu-id="e915a-198">Add the Alarm Properties</span></span>

<span data-ttu-id="e915a-199">Vlastnosti jsou přidány do zděděného ovládacího prvku stejným způsobem jako přidaným do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e915a-199">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="e915a-200">Nyní použijete syntaxi deklarace vlastností k přidání dvou vlastností do ovládacího prvku: `AlarmTime`, který uloží hodnotu data a času, kdy má alarm přejít, a `AlarmSet`, který označuje, zda je alarm nastaven.</span><span class="sxs-lookup"><span data-stu-id="e915a-200">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="e915a-201">Přidání vlastností do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e915a-201">To add properties to your composite control</span></span>

1. <span data-ttu-id="e915a-202">V **Průzkumník řešení**klikněte pravým tlačítkem na **ctlAlarmClock**a pak klikněte na **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="e915a-202">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="e915a-203">Vyhledejte příkaz `public class`.</span><span class="sxs-lookup"><span data-stu-id="e915a-203">Locate the `public class` statement.</span></span> <span data-ttu-id="e915a-204">Všimněte si, že ovládací prvek dědí z `ctlClockLib.ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="e915a-204">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="e915a-205">Pod levou složenou závorku (příkaz`{)` zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e915a-205">Beneath the opening brace (`{)` statement, type the following code.</span></span>

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

### <a name="add-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="e915a-206">Přidat do grafického rozhraní ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e915a-206">Add to the Graphical Interface of the Control</span></span>

<span data-ttu-id="e915a-207">Zděděný ovládací prvek má vizuální rozhraní, které je identické s ovládacím prvkem, ze kterého dědí.</span><span class="sxs-lookup"><span data-stu-id="e915a-207">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="e915a-208">Má stejné ovládací prvky jako svůj nadřazený ovládací prvek, ale vlastnosti ovládacích prvků nebudou k dispozici, pokud nebyly výslovně zpřístupněny.</span><span class="sxs-lookup"><span data-stu-id="e915a-208">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="e915a-209">Můžete přidat do grafického rozhraní zděděného složeného ovládacího prvku stejným způsobem, jako byste přidali do jakéhokoli složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e915a-209">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="e915a-210">Pokud chcete pokračovat v přidávání do vizuálního rozhraní pro budíky, přidejte ovládací prvek popisek, který bude při zvukovém alarmu blikat.</span><span class="sxs-lookup"><span data-stu-id="e915a-210">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="e915a-211">Přidání ovládacího prvku popisek</span><span class="sxs-lookup"><span data-stu-id="e915a-211">To add the label control</span></span>

1. <span data-ttu-id="e915a-212">V **Průzkumník řešení**klikněte pravým tlačítkem na **ctlAlarmClock**a potom klikněte na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e915a-212">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="e915a-213">V hlavním okně se otevře Návrhář pro `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="e915a-213">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="e915a-214">Klikněte na zobrazenou část ovládacího prvku a zobrazte okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e915a-214">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e915a-215">Všechny vlastnosti jsou zobrazeny šedě.</span><span class="sxs-lookup"><span data-stu-id="e915a-215">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="e915a-216">To značí, že tyto vlastnosti jsou nativní pro `lblDisplay` a nelze je upravit nebo použít v okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e915a-216">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="e915a-217">Ve výchozím nastavení jsou ovládací prvky obsažené ve složeném ovládacím prvku `private`a jejich vlastnosti nejsou přístupné žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="e915a-217">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e915a-218">Pokud chcete, aby následující uživatelé složeného ovládacího prvku měli přístup k vnitřním ovládacím prvkům, deklarujte je jako `public` nebo `protected`.</span><span class="sxs-lookup"><span data-stu-id="e915a-218">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="e915a-219">To vám umožní nastavit a upravit vlastnosti ovládacích prvků obsažených v rámci složeného ovládacího prvku pomocí příslušného kódu.</span><span class="sxs-lookup"><span data-stu-id="e915a-219">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="e915a-220">Přidejte ovládací prvek <xref:System.Windows.Forms.Label> do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e915a-220">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="e915a-221">Pomocí myši přetáhněte ovládací prvek <xref:System.Windows.Forms.Label> hned pod pole zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e915a-221">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="e915a-222">V okno Vlastnosti nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e915a-222">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="e915a-223">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e915a-223">Property</span></span>|<span data-ttu-id="e915a-224">Nastavením</span><span class="sxs-lookup"><span data-stu-id="e915a-224">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="e915a-225">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e915a-225">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="e915a-226">**Text**</span><span class="sxs-lookup"><span data-stu-id="e915a-226">**Text**</span></span>|<span data-ttu-id="e915a-227">**Požární!**</span><span class="sxs-lookup"><span data-stu-id="e915a-227">**Alarm!**</span></span>|
    |<span data-ttu-id="e915a-228">**Textu**</span><span class="sxs-lookup"><span data-stu-id="e915a-228">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="e915a-229">**Zobrazeny**</span><span class="sxs-lookup"><span data-stu-id="e915a-229">**Visible**</span></span>|`false`|

### <a name="add-the-alarm-functionality"></a><span data-ttu-id="e915a-230">Přidání funkce alarm</span><span class="sxs-lookup"><span data-stu-id="e915a-230">Add the Alarm Functionality</span></span>

<span data-ttu-id="e915a-231">V předchozích postupech jste přidali vlastnosti a ovládací prvek, který umožní funkci alarmu ve složeném ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="e915a-231">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="e915a-232">V tomto postupu přidáte kód, který bude porovnávat aktuální čas s časem alarmu, a pokud se jedná o stejnou dobu, aby se pomohlo zablikat alarm.</span><span class="sxs-lookup"><span data-stu-id="e915a-232">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="e915a-233">Přepsáním metody `timer1_Tick` `ctlClock` a přidáním dalšího kódu do něj rozšíříte schopnost `ctlAlarmClock` a zároveň zachováte všechny podstatné funkce `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="e915a-233">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="e915a-234">Přepsání metody timer1_Tick pro ctlClock</span><span class="sxs-lookup"><span data-stu-id="e915a-234">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="e915a-235">V **editoru kódu**vyhledejte příkaz `private bool blnAlarmSet;`.</span><span class="sxs-lookup"><span data-stu-id="e915a-235">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="e915a-236">Hned pod ním přidejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e915a-236">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="e915a-237">V **editoru kódu**vyhledejte pravou složenou závorku (`})` na konci třídy.</span><span class="sxs-lookup"><span data-stu-id="e915a-237">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="e915a-238">Těsně před složenou závorku přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e915a-238">Just before the brace, add the following code.</span></span>

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

     <span data-ttu-id="e915a-239">Přidání tohoto kódu dosahuje několika úloh.</span><span class="sxs-lookup"><span data-stu-id="e915a-239">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="e915a-240">Příkaz `override` přesměruje ovládací prvek na použití této metody místo metody, která byla zděděna ze základního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e915a-240">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="e915a-241">Při volání této metody volá metodu, kterou Přepisuje, vyvoláním příkazu `base.timer1_Tick`, aby se zajistilo, že všechny funkce zahrnuté v původním ovládacím prvku budou v tomto ovládacím prvku reprodukovány.</span><span class="sxs-lookup"><span data-stu-id="e915a-241">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="e915a-242">Potom spustí další kód, který bude začlenit funkci alarmu.</span><span class="sxs-lookup"><span data-stu-id="e915a-242">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="e915a-243">Pokud dojde k alarmu, zobrazí se ovládací prvek popisku, který bude blikat.</span><span class="sxs-lookup"><span data-stu-id="e915a-243">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="e915a-244">Ovládací prvek hodiny budíku je skoro kompletní.</span><span class="sxs-lookup"><span data-stu-id="e915a-244">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="e915a-245">Jediná věc, kterou zbývá, je implementovat způsob, jak ho vypnout.</span><span class="sxs-lookup"><span data-stu-id="e915a-245">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="e915a-246">K tomu je třeba přidat kód do metody `lblAlarm_Click`.</span><span class="sxs-lookup"><span data-stu-id="e915a-246">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="e915a-247">Implementace metody shutoff</span><span class="sxs-lookup"><span data-stu-id="e915a-247">To implement the shutoff method</span></span>

1. <span data-ttu-id="e915a-248">V **Průzkumník řešení**klikněte pravým tlačítkem na **ctlAlarmClock.cs**a potom klikněte na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e915a-248">In **Solution Explorer**, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="e915a-249">Otevře se Návrhář.</span><span class="sxs-lookup"><span data-stu-id="e915a-249">The designer opens.</span></span>

2. <span data-ttu-id="e915a-250">Přidejte k ovládacímu prvku tlačítko.</span><span class="sxs-lookup"><span data-stu-id="e915a-250">Add a button to the control.</span></span> <span data-ttu-id="e915a-251">Nastavte vlastnosti tlačítka následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e915a-251">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="e915a-252">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e915a-252">Property</span></span>|<span data-ttu-id="e915a-253">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e915a-253">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="e915a-254">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e915a-254">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="e915a-255">**Text**</span><span class="sxs-lookup"><span data-stu-id="e915a-255">**Text**</span></span>|<span data-ttu-id="e915a-256">**Zakázat alarm**</span><span class="sxs-lookup"><span data-stu-id="e915a-256">**Disable Alarm**</span></span>|

3. <span data-ttu-id="e915a-257">V Návrháři poklikejte na **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="e915a-257">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="e915a-258">Otevře se **Editor kódu** na `private void btnAlarmOff_Click` řádek.</span><span class="sxs-lookup"><span data-stu-id="e915a-258">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="e915a-259">Upravte tuto metodu tak, aby vypadala jako následující kód.</span><span class="sxs-lookup"><span data-stu-id="e915a-259">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="e915a-260">V nabídce **soubor** klikněte na **Uložit vše** a uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="e915a-260">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="use-the-inherited-control-on-a-form"></a><span data-ttu-id="e915a-261">Použití zděděného ovládacího prvku na formuláři</span><span class="sxs-lookup"><span data-stu-id="e915a-261">Use the Inherited Control on a Form</span></span>

<span data-ttu-id="e915a-262">Zděděný ovládací prvek lze otestovat stejným způsobem jako ovládací prvek základní třídy, `ctlClock`: stisknutím klávesy **F5** sestavíte projekt a spustíte ovládací prvek v **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="e915a-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="e915a-263">Další informace naleznete v tématu [How to: test runtime Behavior prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="e915a-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="e915a-264">Chcete-li ovládací prvek použít, budete ho muset hostovat na formuláři.</span><span class="sxs-lookup"><span data-stu-id="e915a-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="e915a-265">Stejně jako u standardního složeného ovládacího prvku nemůže zděděný složený ovládací prvek samostatně a musí být hostovaný ve formuláři nebo jiném kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e915a-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="e915a-266">Vzhledem k tomu, že `ctlAlarmClock` má větší hloubku funkčnosti, je nutné k otestování dalšího kódu.</span><span class="sxs-lookup"><span data-stu-id="e915a-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="e915a-267">V tomto postupu napíšete jednoduchý program, který bude testovat funkčnost `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="e915a-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="e915a-268">Napíšete kód pro nastavení a zobrazení `AlarmTime` vlastnosti `ctlAlarmClock`a otestujete jeho své vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="e915a-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="e915a-269">Sestavení a přidání ovládacího prvku do formuláře testu</span><span class="sxs-lookup"><span data-stu-id="e915a-269">To build and add your control to a test form</span></span>

1. <span data-ttu-id="e915a-270">V **Průzkumník řešení**klikněte pravým tlačítkem na **ctlClockLib**a pak klikněte na **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="e915a-270">In **Solution Explorer**, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="e915a-271">Přidejte do řešení nový projekt **aplikace pro Windows** a pojmenujte ho **test**.</span><span class="sxs-lookup"><span data-stu-id="e915a-271">Add a new **Windows Application** project to the solution, and name it **Test**.</span></span>

3. <span data-ttu-id="e915a-272">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** pro projekt testů.</span><span class="sxs-lookup"><span data-stu-id="e915a-272">In **Solution Explorer**, right-click the **References** node for your test project.</span></span> <span data-ttu-id="e915a-273">Kliknutím na tlačítko **Přidat odkaz** zobrazíte dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="e915a-273">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="e915a-274">Klikněte na kartu s označením **projekty**.</span><span class="sxs-lookup"><span data-stu-id="e915a-274">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="e915a-275">Váš `ctlClockLib` projekt bude uveden v části **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="e915a-275">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="e915a-276">Dvojím kliknutím na projekt přidejte odkaz na testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="e915a-276">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="e915a-277">V **Průzkumník řešení**klikněte pravým tlačítkem na **test**a pak klikněte na **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="e915a-277">In **Solution Explorer**, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="e915a-278">V **sadě nástrojů**rozbalte uzel **součásti ctlClockLib** .</span><span class="sxs-lookup"><span data-stu-id="e915a-278">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="e915a-279">Dvojím kliknutím na **ctlAlarmClock** přidáte kopii `ctlAlarmClock` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="e915a-279">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="e915a-280">Na **panelu nástrojů**vyhledejte **DateTimePicker** a dvakrát klikněte na položku a přidejte ovládací prvek <xref:System.Windows.Forms.DateTimePicker> do formuláře a poté přidejte ovládací prvek <xref:System.Windows.Forms.Label> dvojitým kliknutím na položku **Label**.</span><span class="sxs-lookup"><span data-stu-id="e915a-280">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="e915a-281">Pomocí myši umístěte ovládací prvky na vhodné místo na formuláři.</span><span class="sxs-lookup"><span data-stu-id="e915a-281">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="e915a-282">Následujícím způsobem nastavte vlastnosti těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e915a-282">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="e915a-283">Control</span><span class="sxs-lookup"><span data-stu-id="e915a-283">Control</span></span>|<span data-ttu-id="e915a-284">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e915a-284">Property</span></span>|<span data-ttu-id="e915a-285">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e915a-285">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="e915a-286">**Text**</span><span class="sxs-lookup"><span data-stu-id="e915a-286">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="e915a-287">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e915a-287">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="e915a-288">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e915a-288">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="e915a-289">**Formátovat**</span><span class="sxs-lookup"><span data-stu-id="e915a-289">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="e915a-290">V Návrháři poklikejte na **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="e915a-290">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="e915a-291">Otevře se **Editor kódu** pro `private void dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="e915a-291">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="e915a-292">Upravte kód tak, aby vypadal takto:</span><span class="sxs-lookup"><span data-stu-id="e915a-292">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="e915a-293">V **Průzkumník řešení**klikněte pravým tlačítkem na **test**a pak klikněte na **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="e915a-293">In **Solution Explorer**, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="e915a-294">V nabídce **ladit** klikněte na **Spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="e915a-294">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="e915a-295">Spustí se testovací program.</span><span class="sxs-lookup"><span data-stu-id="e915a-295">The test program starts.</span></span> <span data-ttu-id="e915a-296">Všimněte si, že aktuální čas je aktualizován v ovládacím prvku `ctlAlarmClock` a že počáteční čas je zobrazen v ovládacím prvku <xref:System.Windows.Forms.DateTimePicker>.</span><span class="sxs-lookup"><span data-stu-id="e915a-296">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="e915a-297">Klikněte na <xref:System.Windows.Forms.DateTimePicker>, kde se zobrazí minuty z hodiny.</span><span class="sxs-lookup"><span data-stu-id="e915a-297">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="e915a-298">Pomocí klávesnice nastavte hodnotu minuty, která je o jednu minutu větší než aktuální čas zobrazený `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="e915a-298">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="e915a-299">Čas nastavení alarmu se zobrazí v `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="e915a-299">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="e915a-300">Počkejte, až zobrazený čas dorazí na čas nastavení alarmu.</span><span class="sxs-lookup"><span data-stu-id="e915a-300">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="e915a-301">Když zobrazený čas dosáhne doby, na kterou je nastavené alarm, `lblAlarm` bude blikat.</span><span class="sxs-lookup"><span data-stu-id="e915a-301">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="e915a-302">Vypněte alarm kliknutím na `btnAlarmOff`.</span><span class="sxs-lookup"><span data-stu-id="e915a-302">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="e915a-303">Nyní můžete resetovat alarm.</span><span class="sxs-lookup"><span data-stu-id="e915a-303">You may now reset the alarm.</span></span>

<span data-ttu-id="e915a-304">Tento článek pojednává o řadě klíčových konceptů.</span><span class="sxs-lookup"><span data-stu-id="e915a-304">This article has covered a number of key concepts.</span></span> <span data-ttu-id="e915a-305">Naučili jste se vytvořit složený ovládací prvek kombinováním ovládacích prvků a součástí do složeného kontejneru ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e915a-305">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="e915a-306">Seznámili jste se s přidáním vlastností do ovládacího prvku a při psaní kódu pro implementaci vlastních funkcí.</span><span class="sxs-lookup"><span data-stu-id="e915a-306">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="e915a-307">V poslední části jste se dozvěděli o rozšíření funkcí daného složeného ovládacího prvku prostřednictvím dědičnosti a ke změně funkčnosti metod hostitele přepsáním těchto metod.</span><span class="sxs-lookup"><span data-stu-id="e915a-307">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="e915a-308">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e915a-308">See also</span></span>

- [<span data-ttu-id="e915a-309">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e915a-309">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="e915a-310">Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="e915a-310">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="e915a-311">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="e915a-311">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
