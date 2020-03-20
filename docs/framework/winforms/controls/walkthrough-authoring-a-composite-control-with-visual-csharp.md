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
ms.openlocfilehash: 3ad9aad026a1a6a1266845736d7651db77fd5d5c
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546721"
---
# <a name="walkthrough-author-a-composite-control-with-c"></a><span data-ttu-id="c329f-102">Návod: Vytvoření složeného ovládacího prvku pomocí c\#</span><span class="sxs-lookup"><span data-stu-id="c329f-102">Walkthrough: Author a Composite Control with C\#</span></span>

<span data-ttu-id="c329f-103">Složené ovládací prvky poskytují prostředky, kterými lze vytvořit a znovu použít vlastní grafická rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c329f-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="c329f-104">Složený ovládací prvek je v podstatě součást s vizuální reprezentací.</span><span class="sxs-lookup"><span data-stu-id="c329f-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="c329f-105">Jako takový může sestávat z jednoho nebo více ovládacích prvků, součástí nebo bloků kódu ve formulářích Systému Windows, které mohou rozšířit funkce ověřením vstupu uživatele, úpravou vlastností zobrazení nebo provedením dalších úloh vyžadovaných autorem.</span><span class="sxs-lookup"><span data-stu-id="c329f-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="c329f-106">Složené ovládací prvky lze umístit do formulářů Windows stejným způsobem jako ostatní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c329f-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="c329f-107">V první části tohoto návodu vytvoříte jednoduchý `ctlClock`složený ovládací prvek s názvem .</span><span class="sxs-lookup"><span data-stu-id="c329f-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="c329f-108">V druhé části návodu rozšířit funkce prostřednictvím `ctlClock` dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="c329f-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="c329f-109">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="c329f-109">Create the Project</span></span>

<span data-ttu-id="c329f-110">Při vytváření nového projektu zadáte jeho název, chcete-li nastavit kořenový obor názvů, název sestavení a název projektu a zajistit, aby výchozí součást byla ve správném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c329f-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="c329f-111">Vytvoření knihovny ovládacích prvku ctlClockLib a ovládacího prvku ctlClock</span><span class="sxs-lookup"><span data-stu-id="c329f-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="c329f-112">V sadě Visual Studio vytvořte nový projekt **knihovny windows forms control** a pojmenujte jej **ctlClockLib**.</span><span class="sxs-lookup"><span data-stu-id="c329f-112">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ctlClockLib**.</span></span>

     <span data-ttu-id="c329f-113">Název projektu `ctlClockLib`, je také přiřazen kořenovému oboru názvů ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c329f-113">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="c329f-114">Kořenový obor názvů se používá ke kvalifikaci názvů součástí v sestavě.</span><span class="sxs-lookup"><span data-stu-id="c329f-114">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="c329f-115">Pokud například dvě sestavy poskytují `ctlClock`součásti s `ctlClock` názvem , můžete určit součást pomocí`ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="c329f-115">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

2. <span data-ttu-id="c329f-116">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **UserControl1.cs**a potom klepněte na příkaz **Přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="c329f-116">In **Solution Explorer**, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="c329f-117">Změňte název `ctlClock.cs`souboru na .</span><span class="sxs-lookup"><span data-stu-id="c329f-117">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="c329f-118">Klepněte na tlačítko **Ano,** když budete dotázáni, zda chcete přejmenovat všechny odkazy na prvek kódu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="c329f-118">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    > <span data-ttu-id="c329f-119">Ve výchozím nastavení zdědí <xref:System.Windows.Forms.UserControl> složený ovládací prvek z třídy poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="c329f-119">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="c329f-120">Třída <xref:System.Windows.Forms.UserControl> poskytuje funkce vyžadované všemi složenými ovládacími prvky a implementuje standardní metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c329f-120">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

3. <span data-ttu-id="c329f-121">V nabídce **Soubor** kliknutím na **Uložit vše** projekt uložte.</span><span class="sxs-lookup"><span data-stu-id="c329f-121">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="c329f-122">Přidání ovládacích prvků a součástí systému Windows do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c329f-122">Add Windows Controls and Components to the Composite Control</span></span>

<span data-ttu-id="c329f-123">Vizuální rozhraní je nezbytnou součástí vašeho kompozitního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c329f-123">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="c329f-124">Toto vizuální rozhraní je implementováno přidáním jednoho nebo více ovládacích prvků systému Windows na povrch návrháře.</span><span class="sxs-lookup"><span data-stu-id="c329f-124">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="c329f-125">V následující ukázce začleníte ovládací prvky systému Windows do složeného ovládacího prvku a napíšete kód pro implementaci funkcí.</span><span class="sxs-lookup"><span data-stu-id="c329f-125">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="c329f-126">Přidání popisku a časovače do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c329f-126">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="c329f-127">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **ctlClock.cs**a potom klepněte na příkaz **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="c329f-127">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="c329f-128">V **panelu nástrojů**rozbalte uzel **Běžné ovládací prvky** a poklepejte na **popisek**.</span><span class="sxs-lookup"><span data-stu-id="c329f-128">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="c329f-129">Ovládací <xref:System.Windows.Forms.Label> prvek `label1` s názvem je přidán do ovládacího prvku na povrchu návrháře.</span><span class="sxs-lookup"><span data-stu-id="c329f-129">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="c329f-130">V návrháři klepněte na **popisek1**.</span><span class="sxs-lookup"><span data-stu-id="c329f-130">In the designer, click **label1**.</span></span> <span data-ttu-id="c329f-131">V okně Vlastnosti nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c329f-131">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="c329f-132">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c329f-132">Property</span></span>|<span data-ttu-id="c329f-133">Změňte na</span><span class="sxs-lookup"><span data-stu-id="c329f-133">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="c329f-134">**Název**</span><span class="sxs-lookup"><span data-stu-id="c329f-134">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="c329f-135">**Text**</span><span class="sxs-lookup"><span data-stu-id="c329f-135">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="c329f-136">**Textalign**</span><span class="sxs-lookup"><span data-stu-id="c329f-136">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="c329f-137">**Písmo.Velikost**</span><span class="sxs-lookup"><span data-stu-id="c329f-137">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="c329f-138">V **panelu nástrojů**rozbalte uzel **Součásti** a poklepejte na **tlačítko Časovač**.</span><span class="sxs-lookup"><span data-stu-id="c329f-138">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="c329f-139">Vzhledem <xref:System.Windows.Forms.Timer> k tomu, že a je součást, nemá žádné vizuální reprezentace za běhu.</span><span class="sxs-lookup"><span data-stu-id="c329f-139">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="c329f-140">Proto se nezobrazí s ovládacími prvky na povrchu návrháře, ale spíše v **Návrhář komponent** (zásobník v dolní části povrchu návrháře).</span><span class="sxs-lookup"><span data-stu-id="c329f-140">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="c329f-141">V **Návrháři komponent**klepněte na **tlačítko timer1** <xref:System.Windows.Forms.Timer.Enabled%2A> a `true`nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `1000` a vlastnost na .</span><span class="sxs-lookup"><span data-stu-id="c329f-141">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>

     <span data-ttu-id="c329f-142">Vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> určuje frekvenci, s <xref:System.Windows.Forms.Timer> jakou komponenta značky.</span><span class="sxs-lookup"><span data-stu-id="c329f-142">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="c329f-143">Pokaždé, `timer1` když zaškrtne, spustí `timer1_Tick` kód v události.</span><span class="sxs-lookup"><span data-stu-id="c329f-143">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="c329f-144">Interval představuje počet milisekund mezi značkami.</span><span class="sxs-lookup"><span data-stu-id="c329f-144">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="c329f-145">V **Návrháři komponent**poklepáním **na timer1** přejděte na `timer1_Tick` událost pro . `ctlClock`</span><span class="sxs-lookup"><span data-stu-id="c329f-145">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="c329f-146">Upravte kód tak, aby se podobal následující ukázce kódu.</span><span class="sxs-lookup"><span data-stu-id="c329f-146">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="c329f-147">Nezapomeňte změnit modifikátor `private` přístupu z na `protected`.</span><span class="sxs-lookup"><span data-stu-id="c329f-147">Be sure to change the access modifier from `private` to `protected`.</span></span>

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     <span data-ttu-id="c329f-148">Tento kód způsobí, že aktuální `lblDisplay`čas se zobrazí v .</span><span class="sxs-lookup"><span data-stu-id="c329f-148">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="c329f-149">Vzhledem k `timer1` tomu, `1000`že interval byl nastaven na , bude tato událost nastat každých tisíc milisekund, tedy aktualizace aktuální čas každou sekundu.</span><span class="sxs-lookup"><span data-stu-id="c329f-149">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="c329f-150">Upravte metodu tak, aby `virtual` byla overridable s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="c329f-150">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="c329f-151">Další informace naleznete v části "Dědění z uživatelského ovládacího prvku" níže.</span><span class="sxs-lookup"><span data-stu-id="c329f-151">For more information, see the  "Inheriting from a User Control" section below.</span></span>

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. <span data-ttu-id="c329f-152">V nabídce **Soubor** kliknutím na **Uložit vše** projekt uložte.</span><span class="sxs-lookup"><span data-stu-id="c329f-152">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="add-properties-to-the-composite-control"></a><span data-ttu-id="c329f-153">Přidání vlastností do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c329f-153">Add Properties to the Composite Control</span></span>

<span data-ttu-id="c329f-154">Ovládací prvek hodiny nyní zapouzdřuje <xref:System.Windows.Forms.Label> ovládací prvek a <xref:System.Windows.Forms.Timer> součást, každý s vlastní sadou vlastních vlastností.</span><span class="sxs-lookup"><span data-stu-id="c329f-154">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="c329f-155">Zatímco jednotlivé vlastnosti těchto ovládacích prvků nebudou přístupné pro následné uživatele ovládacího prvku, můžete vytvořit a vystavit vlastní vlastnosti napsáním příslušné bloky kódu.</span><span class="sxs-lookup"><span data-stu-id="c329f-155">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="c329f-156">V následujícím postupu přidáte do ovládacího prvku vlastnosti, které uživateli umožní změnit barvu pozadí a textu.</span><span class="sxs-lookup"><span data-stu-id="c329f-156">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="c329f-157">Přidání vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c329f-157">To add a property to your composite control</span></span>

1. <span data-ttu-id="c329f-158">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **ctlClock.cs**a potom klepněte na příkaz **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="c329f-158">In **Solution Explorer**, right-click **ctlClock.cs**, and then click **View Code**.</span></span>

     <span data-ttu-id="c329f-159">Otevře se **Editor kódu** pro váš ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c329f-159">The **Code Editor** for your control opens.</span></span>

2. <span data-ttu-id="c329f-160">Vyhledejte `public partial class ctlClock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="c329f-160">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="c329f-161">Pod otevírací složenou`{)`závorku ( zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="c329f-161">Beneath the opening brace (`{)`, type the following code.</span></span>

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     <span data-ttu-id="c329f-162">Tyto příkazy vytvořit soukromé proměnné, které budete používat k uložení hodnoty pro vlastnosti, které se chystáte vytvořit.</span><span class="sxs-lookup"><span data-stu-id="c329f-162">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="c329f-163">Zadejte nebo vložte následující kód pod deklarace proměnných z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="c329f-163">Enter or paste the following code beneath the variable declarations from step 2.</span></span>

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

     <span data-ttu-id="c329f-164">Předchozí kód zpřístupní dvě `ClockForeColor` `ClockBackColor`vlastní vlastnosti a , k dispozici pro následné uživatele tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c329f-164">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="c329f-165">`get` Příkazy `set` a poskytují úložiště a načítání hodnoty vlastnosti, stejně jako kód pro implementaci funkce vhodné pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c329f-165">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="c329f-166">V nabídce **Soubor** kliknutím na **Uložit vše** projekt uložte.</span><span class="sxs-lookup"><span data-stu-id="c329f-166">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="c329f-167">Otestujte ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="c329f-167">Test the Control</span></span>

<span data-ttu-id="c329f-168">Ovládací prvky nejsou samostatné aplikace; musí být umístěny v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c329f-168">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="c329f-169">Otestujte chování ovládacího prvku za běhu a jeho vlastnosti můžete používat pomocí **testovacího kontejneru UserControl**.</span><span class="sxs-lookup"><span data-stu-id="c329f-169">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="c329f-170">Další informace naleznete v [tématu How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="c329f-170">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="c329f-171">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c329f-171">To test your control</span></span>

1. <span data-ttu-id="c329f-172">Stisknutím **klávesy F5** vytvořte projekt a spusťte ovládací prvek v **testovacím kontejneru UserControl**.</span><span class="sxs-lookup"><span data-stu-id="c329f-172">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="c329f-173">V mřížce vlastností testovacího kontejneru vyhledejte `ClockBackColor` vlastnost a pak vyberte vlastnost, která zobrazí paletu barev.</span><span class="sxs-lookup"><span data-stu-id="c329f-173">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>

3. <span data-ttu-id="c329f-174">Kliknutím zvolte barvu.</span><span class="sxs-lookup"><span data-stu-id="c329f-174">Choose a color by clicking it.</span></span>

   <span data-ttu-id="c329f-175">Barva pozadí ovládacího prvku se změní na vybranou barvu.</span><span class="sxs-lookup"><span data-stu-id="c329f-175">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="c329f-176">Použijte podobnou posloupnost událostí `ClockForeColor` k ověření, že vlastnost funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="c329f-176">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

   <span data-ttu-id="c329f-177">V této části a v předchozích částech jste viděli, jak lze součásti a ovládací prvky systému Windows kombinovat s kódem a balením a poskytovat vlastní funkce ve formě složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c329f-177">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="c329f-178">Naučili jste se vystavit vlastnosti v složené ovládací prvek a jak otestovat ovládací prvek po dokončení.</span><span class="sxs-lookup"><span data-stu-id="c329f-178">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="c329f-179">V další části se dozvíte, jak vytvořit `ctlClock` zděděný složený ovládací prvek pomocí jako základ.</span><span class="sxs-lookup"><span data-stu-id="c329f-179">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inherit-from-a-composite-control"></a><span data-ttu-id="c329f-180">Dědit z složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c329f-180">Inherit from a Composite Control</span></span>

<span data-ttu-id="c329f-181">V předchozích částech jste se naučili kombinovat ovládací prvky systému Windows, součásti a kód do opakovaně použitelných složených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="c329f-181">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="c329f-182">Složený ovládací prvek lze nyní použít jako základ, na kterém lze sestavit další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c329f-182">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="c329f-183">Proces odvození třídy ze základní třídy se nazývá *dědičnost*.</span><span class="sxs-lookup"><span data-stu-id="c329f-183">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="c329f-184">V této části vytvoříte složený `ctlAlarmClock`ovládací prvek s názvem .</span><span class="sxs-lookup"><span data-stu-id="c329f-184">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="c329f-185">Tento ovládací prvek bude odvozen z `ctlClock`nadřazeného ovládacího prvku .</span><span class="sxs-lookup"><span data-stu-id="c329f-185">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="c329f-186">Naučíte se rozšířit funkce `ctlClock` přepsáním nadřazených metod a přidáním nových metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="c329f-186">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

<span data-ttu-id="c329f-187">Prvním krokem při vytváření zděděného ovládacího prvku je jeho odvození z nadřazeného prvku.</span><span class="sxs-lookup"><span data-stu-id="c329f-187">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="c329f-188">Tato akce vytvoří nový ovládací prvek, který má všechny vlastnosti, metody a grafické charakteristiky nadřazeného ovládacího prvku, ale může také sloužit jako základ pro přidání nové nebo upravené funkce.</span><span class="sxs-lookup"><span data-stu-id="c329f-188">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="c329f-189">Vytvoření zděděného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c329f-189">To create the inherited control</span></span>

1. <span data-ttu-id="c329f-190">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **položku ctlClockLib**, přejděte na **tlačítko Přidat**a klepněte na příkaz Uživatelské **řízení**.</span><span class="sxs-lookup"><span data-stu-id="c329f-190">In **Solution Explorer**, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="c329f-191">Otevře se dialogové okno **Přidat novou položku.**</span><span class="sxs-lookup"><span data-stu-id="c329f-191">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="c329f-192">Vyberte šablonu **Zděděný uživatelský ovládací prvek.**</span><span class="sxs-lookup"><span data-stu-id="c329f-192">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="c329f-193">Do pole **Název** `ctlAlarmClock.cs`zadejte a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="c329f-193">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>

     <span data-ttu-id="c329f-194">Zobrazí se dialogové okno **Výběr dědičnosti.**</span><span class="sxs-lookup"><span data-stu-id="c329f-194">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="c329f-195">V **části Název součásti**poklepejte na **položku ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="c329f-195">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="c329f-196">V **Průzkumníku řešení**projděte aktuální projekty.</span><span class="sxs-lookup"><span data-stu-id="c329f-196">In **Solution Explorer**, browse through the current projects.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c329f-197">Do aktuálního projektu byl přidán soubor s názvem **ctlAlarmClock.cs.**</span><span class="sxs-lookup"><span data-stu-id="c329f-197">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>

### <a name="add-the-alarm-properties"></a><span data-ttu-id="c329f-198">Přidání vlastností alarmu</span><span class="sxs-lookup"><span data-stu-id="c329f-198">Add the Alarm Properties</span></span>

<span data-ttu-id="c329f-199">Vlastnosti jsou přidány do zděděného ovládacího prvku stejným způsobem, jakým jsou přidány do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c329f-199">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="c329f-200">Nyní použijete syntaxi deklarace vlastnosti k `AlarmTime`přidání dvou vlastností do ovládacího prvku: , který `AlarmSet`uloží hodnotu data a času, kdy má alarm zhasnout, a , která bude označovat, zda je budík nastaven.</span><span class="sxs-lookup"><span data-stu-id="c329f-200">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="c329f-201">Přidání vlastností do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c329f-201">To add properties to your composite control</span></span>

1. <span data-ttu-id="c329f-202">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **příkaz ctlAlarmClock**a potom klepněte na příkaz **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="c329f-202">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="c329f-203">Vyhledejte `public class` příkaz.</span><span class="sxs-lookup"><span data-stu-id="c329f-203">Locate the `public class` statement.</span></span> <span data-ttu-id="c329f-204">Všimněte si, že `ctlClockLib.ctlClock`ovládací prvek dědí z .</span><span class="sxs-lookup"><span data-stu-id="c329f-204">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="c329f-205">Pod otevírací složenou`{)` závorku ( příkaz zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="c329f-205">Beneath the opening brace (`{)` statement, type the following code.</span></span>

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

### <a name="add-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="c329f-206">Přidat do grafického rozhraní ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c329f-206">Add to the Graphical Interface of the Control</span></span>

<span data-ttu-id="c329f-207">Zděděný ovládací prvek má vizuální rozhraní, které je shodné s ovládacím prvkem, který dědí z.</span><span class="sxs-lookup"><span data-stu-id="c329f-207">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="c329f-208">Má stejné základní ovládací prvky jako jeho nadřazený ovládací prvek, ale vlastnosti základní ovládací prvky nebudou k dispozici, pokud nebyly konkrétně vystaveny.</span><span class="sxs-lookup"><span data-stu-id="c329f-208">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="c329f-209">Do grafického rozhraní zděděného složeného ovládacího prvku můžete přidat stejným způsobem, jako byste jej přidali do libovolného složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c329f-209">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="c329f-210">Chcete-li pokračovat v přidávání do vizuálního rozhraní budíku, přidáte ovládací prvek štítku, který bude blikat, když budík zazní.</span><span class="sxs-lookup"><span data-stu-id="c329f-210">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="c329f-211">Přidání ovládacího prvku popisek</span><span class="sxs-lookup"><span data-stu-id="c329f-211">To add the label control</span></span>

1. <span data-ttu-id="c329f-212">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **příkaz ctlAlarmClock**a potom klepněte na příkaz **Zobrazit návrháře**.</span><span class="sxs-lookup"><span data-stu-id="c329f-212">In **Solution Explorer**, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>

     <span data-ttu-id="c329f-213">Návrhář pro `ctlAlarmClock` otevírá v hlavním okně.</span><span class="sxs-lookup"><span data-stu-id="c329f-213">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="c329f-214">Klepněte na zobrazovanou část ovládacího prvku a zobrazte okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c329f-214">Click the display portion of the control, and view the Properties window.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c329f-215">Zatímco jsou zobrazeny všechny vlastnosti, jsou ztlumené.</span><span class="sxs-lookup"><span data-stu-id="c329f-215">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="c329f-216">To znamená, že tyto `lblDisplay` vlastnosti jsou nativní pro a nelze změnit nebo přistupovat v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c329f-216">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="c329f-217">Ve výchozím nastavení jsou `private`ovládací prvky obsažené ve složeném ovládacím prvku a jejich vlastnosti nejsou žádným způsobem přístupné.</span><span class="sxs-lookup"><span data-stu-id="c329f-217">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c329f-218">Pokud chcete, aby další uživatelé složeného ovládacího prvku `public` měli `protected`přístup k jeho vnitřním ovládacím prvkům, deklarujte je jako nebo .</span><span class="sxs-lookup"><span data-stu-id="c329f-218">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="c329f-219">To vám umožní nastavit a upravit vlastnosti ovládacích prvků obsažených v složeném ovládacím prvku pomocí příslušného kódu.</span><span class="sxs-lookup"><span data-stu-id="c329f-219">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="c329f-220">Přidejte <xref:System.Windows.Forms.Label> ovládací prvek do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c329f-220">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="c329f-221">Pomocí myši přetáhněte <xref:System.Windows.Forms.Label> ovládací prvek bezprostředně pod pole displeje.</span><span class="sxs-lookup"><span data-stu-id="c329f-221">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="c329f-222">V okně Vlastnosti nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c329f-222">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="c329f-223">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c329f-223">Property</span></span>|<span data-ttu-id="c329f-224">Nastavení</span><span class="sxs-lookup"><span data-stu-id="c329f-224">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="c329f-225">**Název**</span><span class="sxs-lookup"><span data-stu-id="c329f-225">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="c329f-226">**Text**</span><span class="sxs-lookup"><span data-stu-id="c329f-226">**Text**</span></span>|<span data-ttu-id="c329f-227">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="c329f-227">**Alarm!**</span></span>|
    |<span data-ttu-id="c329f-228">**Textalign**</span><span class="sxs-lookup"><span data-stu-id="c329f-228">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="c329f-229">**Visible**</span><span class="sxs-lookup"><span data-stu-id="c329f-229">**Visible**</span></span>|`false`|

### <a name="add-the-alarm-functionality"></a><span data-ttu-id="c329f-230">Přidání funkce alarmu</span><span class="sxs-lookup"><span data-stu-id="c329f-230">Add the Alarm Functionality</span></span>

<span data-ttu-id="c329f-231">V předchozích postupech jste přidali vlastnosti a ovládací prvek, který umožní funkce alarmu ve složeném ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="c329f-231">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="c329f-232">V tomto postupu přidáte kód pro porovnání aktuálního času s časem alarmu a pokud jsou stejné, pro blikání alarmu.</span><span class="sxs-lookup"><span data-stu-id="c329f-232">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="c329f-233">Přepsáním `timer1_Tick` metody `ctlClock` a přidáním dalšího kódu do něj `ctlAlarmClock` rozšíříte možnost i zachování `ctlClock`všech vlastních funkcí aplikace .</span><span class="sxs-lookup"><span data-stu-id="c329f-233">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="c329f-234">Chcete-li přepsat timer1_Tick metodu ctlClock</span><span class="sxs-lookup"><span data-stu-id="c329f-234">To override the timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="c329f-235">V **Editoru kódu** `private bool blnAlarmSet;` vyhledejte příkaz.</span><span class="sxs-lookup"><span data-stu-id="c329f-235">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="c329f-236">Okamžitě pod něj přidejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="c329f-236">Immediately beneath it, add the following statement.</span></span>

    ```csharp
    private bool blnColorTicker;
    ```

2. <span data-ttu-id="c329f-237">V **Editoru kódu**vyhledejte`})` uzavírací složenou závorku ( na konci třídy.</span><span class="sxs-lookup"><span data-stu-id="c329f-237">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="c329f-238">Těsně před složenou závorku přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="c329f-238">Just before the brace, add the following code.</span></span>

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

     <span data-ttu-id="c329f-239">Přidání tohoto kódu provádí několik úkolů.</span><span class="sxs-lookup"><span data-stu-id="c329f-239">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="c329f-240">Příkaz `override` řídí ovládací prvek použít tuto metodu namísto metody, která byla zděděna ze základního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c329f-240">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="c329f-241">Při volání této metody volá metodu, kterou přepíše `base.timer1_Tick` vyvoláním příkazu, zajištěním, že všechny funkce obsažené v původním ovládacím prvku jsou reprodukovány v tomto ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="c329f-241">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="c329f-242">Potom spustí další kód začlenit funkce alarmu.</span><span class="sxs-lookup"><span data-stu-id="c329f-242">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="c329f-243">Když dojde k poplachu, zobrazí se blikající ovládací prvek štítku.</span><span class="sxs-lookup"><span data-stu-id="c329f-243">A flashing label control will appear when the alarm occurs.</span></span>

     <span data-ttu-id="c329f-244">Ovládání budíku je téměř dokončeno.</span><span class="sxs-lookup"><span data-stu-id="c329f-244">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="c329f-245">Jediná věc, která zůstává, je implementovat způsob, jak ji vypnout.</span><span class="sxs-lookup"><span data-stu-id="c329f-245">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="c329f-246">Chcete-li to provést, přidáte `lblAlarm_Click` kód k metodě.</span><span class="sxs-lookup"><span data-stu-id="c329f-246">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="c329f-247">Implementace metody vypnutí</span><span class="sxs-lookup"><span data-stu-id="c329f-247">To implement the shutoff method</span></span>

1. <span data-ttu-id="c329f-248">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **ctlAlarmClock.cs**a potom klepněte na příkaz **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="c329f-248">In **Solution Explorer**, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>

     <span data-ttu-id="c329f-249">Návrhář otevře.</span><span class="sxs-lookup"><span data-stu-id="c329f-249">The designer opens.</span></span>

2. <span data-ttu-id="c329f-250">Přidejte tlačítko do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c329f-250">Add a button to the control.</span></span> <span data-ttu-id="c329f-251">Nastavte vlastnosti tlačítka následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="c329f-251">Set the properties of the button as follows.</span></span>

    |<span data-ttu-id="c329f-252">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c329f-252">Property</span></span>|<span data-ttu-id="c329f-253">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c329f-253">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="c329f-254">**Název**</span><span class="sxs-lookup"><span data-stu-id="c329f-254">**Name**</span></span>|`btnAlarmOff`|
    |<span data-ttu-id="c329f-255">**Text**</span><span class="sxs-lookup"><span data-stu-id="c329f-255">**Text**</span></span>|<span data-ttu-id="c329f-256">**Zakázat alarm**</span><span class="sxs-lookup"><span data-stu-id="c329f-256">**Disable Alarm**</span></span>|

3. <span data-ttu-id="c329f-257">V návrháři poklepejte na **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="c329f-257">In the designer, double-click **btnAlarmOff**.</span></span>

     <span data-ttu-id="c329f-258">**Editor kódu** se `private void btnAlarmOff_Click` otevře na řádku.</span><span class="sxs-lookup"><span data-stu-id="c329f-258">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>

4. <span data-ttu-id="c329f-259">Upravte tuto metodu tak, aby se podobala následujícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="c329f-259">Modify this method so that it resembles the following code.</span></span>

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. <span data-ttu-id="c329f-260">V nabídce **Soubor** kliknutím na **Uložit vše** projekt uložte.</span><span class="sxs-lookup"><span data-stu-id="c329f-260">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="use-the-inherited-control-on-a-form"></a><span data-ttu-id="c329f-261">Použití zděděného ovládacího prvku ve formuláři</span><span class="sxs-lookup"><span data-stu-id="c329f-261">Use the Inherited Control on a Form</span></span>

<span data-ttu-id="c329f-262">Zděděný ovládací prvek můžete otestovat stejným způsobem, `ctlClock`jakým jste testovali ovládací prvek základní třídy: Stisknutím **klávesy F5** vytvořte projekt a spusťte ovládací prvek v **testovacím kontejneru UserControl**.</span><span class="sxs-lookup"><span data-stu-id="c329f-262">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="c329f-263">Další informace naleznete v [tématu How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="c329f-263">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="c329f-264">Chcete-li ovládací prvek použít, budete jej muset hostovat ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="c329f-264">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="c329f-265">Stejně jako u standardního složeného ovládacího prvku zděděný složený ovládací prvek nemůže samostatně a musí být hostován ve formuláři nebo jiném kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c329f-265">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="c329f-266">Vzhledem k tomu, `ctlAlarmClock` že má větší hloubku funkčnosti, další kód je nutné otestovat.</span><span class="sxs-lookup"><span data-stu-id="c329f-266">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="c329f-267">V tomto postupu napíšete jednoduchý program pro `ctlAlarmClock`testování funkčnosti aplikace .</span><span class="sxs-lookup"><span data-stu-id="c329f-267">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="c329f-268">Napíšete kód pro nastavení `AlarmTime` a `ctlAlarmClock`zobrazení vlastnosti aplikace a otestujete jeho vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="c329f-268">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="c329f-269">Vytvoření a přidání ovládacího prvku do testovacího formuláře</span><span class="sxs-lookup"><span data-stu-id="c329f-269">To build and add your control to a test form</span></span>

1. <span data-ttu-id="c329f-270">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **příkaz ctlClockLib**a potom klepněte na příkaz **Sestavit**.</span><span class="sxs-lookup"><span data-stu-id="c329f-270">In **Solution Explorer**, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="c329f-271">Přidejte do řešení nový projekt **aplikace Windows Forms Application** a pojmenujte jej **Test**.</span><span class="sxs-lookup"><span data-stu-id="c329f-271">Add a new **Windows Forms Application** project to the solution, and name it **Test**.</span></span>

3. <span data-ttu-id="c329f-272">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Reference** pro testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="c329f-272">In **Solution Explorer**, right-click the **References** node for your test project.</span></span> <span data-ttu-id="c329f-273">Kliknutím na **Přidat odkaz** zobrazíte dialogové okno **Přidat odkaz.**</span><span class="sxs-lookup"><span data-stu-id="c329f-273">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="c329f-274">Klikněte na kartu s názvem **Projekty**.</span><span class="sxs-lookup"><span data-stu-id="c329f-274">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="c329f-275">Projekt `ctlClockLib` bude uveden v části **Název projektu**.</span><span class="sxs-lookup"><span data-stu-id="c329f-275">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="c329f-276">Poklepáním na projekt přidejte odkaz na testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="c329f-276">Double-click the project to add the reference to the test project.</span></span>

4. <span data-ttu-id="c329f-277">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **tlačítko Testovat**a potom klepněte na příkaz **Sestavit**.</span><span class="sxs-lookup"><span data-stu-id="c329f-277">In **Solution Explorer**, right-click **Test**, and then click **Build**.</span></span>

5. <span data-ttu-id="c329f-278">V **panelu nástrojů**rozbalte uzel **komponenty ctlClockLib.**</span><span class="sxs-lookup"><span data-stu-id="c329f-278">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

6. <span data-ttu-id="c329f-279">Poklepáním na **ctlAlarmClock** přidejte kopii `ctlAlarmClock` formuláře.</span><span class="sxs-lookup"><span data-stu-id="c329f-279">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>

7. <span data-ttu-id="c329f-280">V **panelu nástrojů**vyhledejte a poklepejte na <xref:System.Windows.Forms.DateTimePicker> <xref:System.Windows.Forms.Label> **položku DateTimePicker,** chcete-li do formuláře přidat ovládací prvek, a potom přidejte ovládací prvek poklepáním na **popisek**.</span><span class="sxs-lookup"><span data-stu-id="c329f-280">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

8. <span data-ttu-id="c329f-281">Pomocí myši umístěte ovládací prvky na vhodné místo ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="c329f-281">Use the mouse to position the controls in a convenient place on the form.</span></span>

9. <span data-ttu-id="c329f-282">Nastavte vlastnosti těchto ovládacích prvků následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="c329f-282">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="c329f-283">Řízení</span><span class="sxs-lookup"><span data-stu-id="c329f-283">Control</span></span>|<span data-ttu-id="c329f-284">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c329f-284">Property</span></span>|<span data-ttu-id="c329f-285">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c329f-285">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="c329f-286">**Text**</span><span class="sxs-lookup"><span data-stu-id="c329f-286">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="c329f-287">**Název**</span><span class="sxs-lookup"><span data-stu-id="c329f-287">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="c329f-288">**Název**</span><span class="sxs-lookup"><span data-stu-id="c329f-288">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="c329f-289">**Formát**</span><span class="sxs-lookup"><span data-stu-id="c329f-289">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. <span data-ttu-id="c329f-290">V návrháři poklepejte na **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="c329f-290">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="c329f-291">**Editor kódu** se `private void dtpTest_ValueChanged`otevře do aplikace .</span><span class="sxs-lookup"><span data-stu-id="c329f-291">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>

11. <span data-ttu-id="c329f-292">Upravte kód tak, aby se podobal následujícím.</span><span class="sxs-lookup"><span data-stu-id="c329f-292">Modify the code so that it resembles the following.</span></span>

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. <span data-ttu-id="c329f-293">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na **tlačítko Testovat**a potom klepněte na příkaz Nastavit jako **počáteční projekt**.</span><span class="sxs-lookup"><span data-stu-id="c329f-293">In **Solution Explorer**, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

13. <span data-ttu-id="c329f-294">V nabídce **Ladit** klikněte na **Spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="c329f-294">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="c329f-295">Spustí se testovací program.</span><span class="sxs-lookup"><span data-stu-id="c329f-295">The test program starts.</span></span> <span data-ttu-id="c329f-296">Všimněte si, že aktuální `ctlAlarmClock` čas je aktualizován v ovládacím <xref:System.Windows.Forms.DateTimePicker> prvku a že počáteční čas je zobrazen v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="c329f-296">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

14. <span data-ttu-id="c329f-297">Klikněte <xref:System.Windows.Forms.DateTimePicker> na místo, kde se zobrazí minuty hodiny.</span><span class="sxs-lookup"><span data-stu-id="c329f-297">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

15. <span data-ttu-id="c329f-298">Pomocí klávesnice nastavte hodnotu pro minuty, která je o `ctlAlarmClock`jednu minutu větší než aktuální čas zobrazený aplikacem .</span><span class="sxs-lookup"><span data-stu-id="c329f-298">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="c329f-299">Čas nastavení alarmu je `lblTest`zobrazen v .</span><span class="sxs-lookup"><span data-stu-id="c329f-299">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="c329f-300">Počkejte, až zobrazený čas dosáhne doby nastavení alarmu.</span><span class="sxs-lookup"><span data-stu-id="c329f-300">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="c329f-301">Když zobrazený čas dosáhne času, na který je `lblAlarm` budík nastaven, bude blikat.</span><span class="sxs-lookup"><span data-stu-id="c329f-301">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>

16. <span data-ttu-id="c329f-302">Vypněte budík `btnAlarmOff`kliknutím na tlačítko .</span><span class="sxs-lookup"><span data-stu-id="c329f-302">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="c329f-303">Nyní můžete resetovat alarm.</span><span class="sxs-lookup"><span data-stu-id="c329f-303">You may now reset the alarm.</span></span>

<span data-ttu-id="c329f-304">Tento článek se vztahuje na řadu klíčových pojmů.</span><span class="sxs-lookup"><span data-stu-id="c329f-304">This article has covered a number of key concepts.</span></span> <span data-ttu-id="c329f-305">Naučili jste se vytvořit složený ovládací prvek kombinací ovládacích prvků a součástí do kontejneru složených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="c329f-305">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="c329f-306">Naučili jste se přidat vlastnosti do ovládacího prvku a napsat kód pro implementaci vlastních funkcí.</span><span class="sxs-lookup"><span data-stu-id="c329f-306">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="c329f-307">V poslední části jste se naučili rozšířit funkce daného složeného ovládacího prvku prostřednictvím dědičnosti a změnit funkce hostitelských metod přepsáním těchto metod.</span><span class="sxs-lookup"><span data-stu-id="c329f-307">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="c329f-308">Viz také</span><span class="sxs-lookup"><span data-stu-id="c329f-308">See also</span></span>

- [<span data-ttu-id="c329f-309">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="c329f-309">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="c329f-310">Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="c329f-310">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="c329f-311">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="c329f-311">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
