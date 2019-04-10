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
ms.openlocfilehash: 67fecb95ea373e88e5428251151cc30bfeb580a6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321029"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a><span data-ttu-id="dbf63-102">Návod: Vytvoření složeného ovládacího prvku pomocí Visual C\#</span><span class="sxs-lookup"><span data-stu-id="dbf63-102">Walkthrough: Authoring a Composite Control with Visual C\#</span></span>
<span data-ttu-id="dbf63-103">Složené ovládací prvky poskytují způsob, kterým lze vytvořit vlastní grafické rozhraní a znovu použít.</span><span class="sxs-lookup"><span data-stu-id="dbf63-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="dbf63-104">Složený ovládací prvek je v podstatě komponent pomocí vizuální reprezentace.</span><span class="sxs-lookup"><span data-stu-id="dbf63-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="dbf63-105">V důsledku toho může obsahovat jeden nebo více Windows Forms ovládací prvky, komponenty nebo bloky kódu, který můžete rozšířit funkce ověřování uživatelského vstupu, změnou zobrazení vlastností nebo provádění jiných úloh vyžaduje autorem.</span><span class="sxs-lookup"><span data-stu-id="dbf63-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="dbf63-106">Složené ovládací prvky mohou být umístěny ve Windows Forms stejným způsobem jako ostatní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="dbf63-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="dbf63-107">V první části tohoto návodu vytvoříte jednoduchou složeného ovládacího prvku volá `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="dbf63-108">V druhé části tohoto průvodce, které rozšiřují funkce nástroje `ctlClock` prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="dbf63-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbf63-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="dbf63-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="dbf63-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="dbf63-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="dbf63-111">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="dbf63-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="dbf63-112">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="dbf63-112">Creating the Project</span></span>  
 <span data-ttu-id="dbf63-113">Když vytvoříte nový projekt, zadejte její název na nastavit kořenový obor názvů, název sestavení a název projektu a ujistěte se, že součást výchozí bude v správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="dbf63-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="dbf63-114">Chcete-li vytvořit ctlClockLib Knihovna ovládacích prvků a ovládací prvek ctlClock</span><span class="sxs-lookup"><span data-stu-id="dbf63-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1. <span data-ttu-id="dbf63-115">Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu** otevřete **nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="dbf63-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="dbf63-116">V seznamu Projekty Visual C#, vyberte **Knihovna ovládacích prvků Windows Forms** šablony projektu, typ `ctlClockLib` v **název** pole a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-116">From the list of Visual C# projects, select the **Windows Forms Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="dbf63-117">Název projektu `ctlClockLib`, je také přiřazený k oboru názvů root ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="dbf63-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="dbf63-118">Kořenový obor názvů se používá k určení názvů součástí sestavení.</span><span class="sxs-lookup"><span data-stu-id="dbf63-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="dbf63-119">Například, pokud se dvě sestavení poskytují komponenty s názvem `ctlClock`, můžete zadat vaše `ctlClock` pomocí komponenty</span><span class="sxs-lookup"><span data-stu-id="dbf63-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using</span></span> `ctlClockLib.ctlClock.`  
  
3. <span data-ttu-id="dbf63-120">V Průzkumníku řešení klikněte pravým tlačítkem na **UserControl1.cs**a potom klikněte na tlačítko **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-120">In Solution Explorer, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="dbf63-121">Změňte název souboru, aby `ctlClock.cs`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-121">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="dbf63-122">Klikněte na tlačítko **Ano** tlačítko, pokud budete vyzváni, pokud chcete přejmenovat všechny odkazy na prvek kódu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="dbf63-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dbf63-123">Ve výchozím nastavení, zdědí složeného ovládacího prvku <xref:System.Windows.Forms.UserControl> třídy poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="dbf63-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="dbf63-124"><xref:System.Windows.Forms.UserControl> Třída poskytuje funkce vyžadované všech složených ovládacích prvků a implementuje standardní metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dbf63-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4. <span data-ttu-id="dbf63-125">Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** chcete projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="dbf63-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="dbf63-126">Přidání Windows ovládacích prvků a komponent do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="dbf63-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="dbf63-127">Vizuální rozhraní je zásadní součástí složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dbf63-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="dbf63-128">Tento vizuální rozhraní je implementováno přidání jednoho nebo více ovládacích prvků Windows na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="dbf63-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="dbf63-129">V následující ukázce se začlenit ovládacích prvků Windows do složeného ovládacího prvku a napsat kód k implementaci funkcionality.</span><span class="sxs-lookup"><span data-stu-id="dbf63-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="dbf63-130">Přidejte popisek a časovač do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="dbf63-130">To add a Label and a Timer to your composite control</span></span>  
  
1. <span data-ttu-id="dbf63-131">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClock.cs**a potom klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-131">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>  
  
2. <span data-ttu-id="dbf63-132">V **nástrojů**, rozbalte **běžné ovládací prvky** uzel a poté dvojitým kliknutím **popisek**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-132">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="dbf63-133">A <xref:System.Windows.Forms.Label> ovládací prvek s názvem `label1` se přidá do vašeho ovládacího prvku na návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="dbf63-133">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>  
  
3. <span data-ttu-id="dbf63-134">V návrháři, klikněte na tlačítko **label1**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-134">In the designer, click **label1**.</span></span> <span data-ttu-id="dbf63-135">V okně Vlastnosti nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dbf63-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="dbf63-136">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="dbf63-136">Property</span></span>|<span data-ttu-id="dbf63-137">Změňte na</span><span class="sxs-lookup"><span data-stu-id="dbf63-137">Change to</span></span>|  
    |--------------|---------------|  
    |**<span data-ttu-id="dbf63-138">Name</span><span class="sxs-lookup"><span data-stu-id="dbf63-138">Name</span></span>**|`lblDisplay`|  
    |**<span data-ttu-id="dbf63-139">Text</span><span class="sxs-lookup"><span data-stu-id="dbf63-139">Text</span></span>**|`(blank space)`|  
    |**<span data-ttu-id="dbf63-140">TextAlign</span><span class="sxs-lookup"><span data-stu-id="dbf63-140">TextAlign</span></span>**|`MiddleCenter`|  
    |**<span data-ttu-id="dbf63-141">Font.Size</span><span class="sxs-lookup"><span data-stu-id="dbf63-141">Font.Size</span></span>**|`14`|  
  
4. <span data-ttu-id="dbf63-142">V **nástrojů**, rozbalte **součásti** uzel a poté dvojitým kliknutím **časovače**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="dbf63-143">Protože <xref:System.Windows.Forms.Timer> je komponenta, nemá žádný vizuální reprezentace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="dbf63-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="dbf63-144">Proto není zobrazen s ovládacími prvky na návrhové ploše, ale spíše v **návrháře komponent** (na hlavním panelu v dolní části na plochu návrháře).</span><span class="sxs-lookup"><span data-stu-id="dbf63-144">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>  
  
5. <span data-ttu-id="dbf63-145">V **návrháře komponent**, klikněte na tlačítko **timer1**a pak nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `1000` a <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-145">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="dbf63-146"><xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost řídí frekvenci, se kterým <xref:System.Windows.Forms.Timer> komponenty značky.</span><span class="sxs-lookup"><span data-stu-id="dbf63-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="dbf63-147">Pokaždé, když `timer1` tiků, spustí kód, který `timer1_Tick` událostí.</span><span class="sxs-lookup"><span data-stu-id="dbf63-147">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="dbf63-148">Interval představuje počet milisekund mezi značkami.</span><span class="sxs-lookup"><span data-stu-id="dbf63-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6. <span data-ttu-id="dbf63-149">V **návrháře komponent**, dvakrát klikněte na panel **timer1** přejděte `timer1_Tick` událost pro `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-149">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>  
  
7. <span data-ttu-id="dbf63-150">Upravte kód tak, aby vypadá podobně jako následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="dbf63-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="dbf63-151">Nezapomeňte změnit modifikátor přístupu z `private` k `protected`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-151">Be sure to change the access modifier from `private` to `protected`.</span></span>  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     <span data-ttu-id="dbf63-152">Tento kód způsobí, že aktuální čas v `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="dbf63-153">Protože interval `timer1` byl nastaven na `1000`, dojde k této události každých tisíců milisekund, tedy aktualizuje aktuální čas každou sekundu.</span><span class="sxs-lookup"><span data-stu-id="dbf63-153">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8. <span data-ttu-id="dbf63-154">Upravte metodu k možné overridable s `virtual` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="dbf63-154">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="dbf63-155">Další informace naleznete v části "Dědění z uživatelského ovládacího prvku" níže.</span><span class="sxs-lookup"><span data-stu-id="dbf63-155">For more information, see the  "Inheriting from a User Control" section below.</span></span>  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. <span data-ttu-id="dbf63-156">Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** chcete projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="dbf63-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="dbf63-157">Přidání vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="dbf63-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="dbf63-158">Ovládací prvek hodiny nyní zapouzdřuje <xref:System.Windows.Forms.Label> ovládacího prvku a <xref:System.Windows.Forms.Timer> komponenty, každý s vlastní sadou vlastní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dbf63-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="dbf63-159">I když jednotlivé vlastnosti těchto ovládacích prvků nebudou přístupné uživatelům následné ovládacího prvku, můžete vytvořit a vystavit vlastní vlastnosti napsáním příslušné bloky kódu.</span><span class="sxs-lookup"><span data-stu-id="dbf63-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="dbf63-160">V následujícím postupu přidejte vlastnosti do ovládacího prvku, který uživateli umožňuje změnit barvu pozadí a textu.</span><span class="sxs-lookup"><span data-stu-id="dbf63-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="dbf63-161">Přidání vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="dbf63-161">To add a property to your composite control</span></span>  
  
1. <span data-ttu-id="dbf63-162">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClock.cs**a potom klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-162">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="dbf63-163">**Editor kódu** pro vaše ovládací prvek se otevře.</span><span class="sxs-lookup"><span data-stu-id="dbf63-163">The **Code Editor** for your control opens.</span></span>  
  
2. <span data-ttu-id="dbf63-164">Vyhledejte `public partial class ctlClock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="dbf63-164">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="dbf63-165">Pod levou složenou závorku (`{)`, zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="dbf63-165">Beneath the opening brace (`{)`, type the following code.</span></span>  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     <span data-ttu-id="dbf63-166">Tyto příkazy vytvořit soukromé proměnné, které budete používat k ukládání hodnot pro vlastnosti, které se chystáte vytvořit.</span><span class="sxs-lookup"><span data-stu-id="dbf63-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3. <span data-ttu-id="dbf63-167">Zadejte následující kód pod deklarace proměnných z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="dbf63-167">Type the following code beneath the variable declarations from step 2.</span></span>  
  
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
  
     <span data-ttu-id="dbf63-168">Předchozí kód provede dvě vlastní vlastnosti `ClockForeColor` a `ClockBackColor`, která je dostupná uživatelům následné tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dbf63-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="dbf63-169">`get` a `set` příkazy zajišťují pro ukládání a načítání hodnoty vlastnosti, jakož i kód k implementaci funkcionality odpovídající vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dbf63-169">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4. <span data-ttu-id="dbf63-170">Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** chcete projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="dbf63-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="dbf63-171">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="dbf63-171">Testing the Control</span></span>  
 <span data-ttu-id="dbf63-172">Ovládací prvky nejsou samostatné aplikace; musí být uložen v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="dbf63-172">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="dbf63-173">Chování ovládacího prvku za běhu testu přestal pracovat a s jeho vlastnosti **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="dbf63-174">Další informace najdete v tématu [jak: Testování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="dbf63-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="dbf63-175">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="dbf63-175">To test your control</span></span>  
  
1. <span data-ttu-id="dbf63-176">Stisknutím klávesy F5 sestavte projekt a spusťte váš ovládací prvek **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2. <span data-ttu-id="dbf63-177">V mřížce vlastností kontejner testu, vyhledejte `ClockBackColor` vlastnost a potom vyberte vlastnost pro zobrazení palety barev.</span><span class="sxs-lookup"><span data-stu-id="dbf63-177">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>  
  
3. <span data-ttu-id="dbf63-178">Kliknutím zvolte barvu.</span><span class="sxs-lookup"><span data-stu-id="dbf63-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="dbf63-179">Barva pozadí ovládacího prvku změní barvu, kterou jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="dbf63-179">The background color of your control changes to the color you selected.</span></span>  
  
4. <span data-ttu-id="dbf63-180">Ověřte, že pomocí podobně jako posloupnost událostí `ClockForeColor` vlastnost funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="dbf63-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
     <span data-ttu-id="dbf63-181">V této části a v předchozích částech, jste viděli, jak mohou být kombinovány komponent a ovládacích prvků Windows s kódem a balení poskytují vlastní funkce v podobě složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dbf63-181">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="dbf63-182">Naučili jste se vystavení vlastností v složeného ovládacího prvku a po dokončení testování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dbf63-182">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="dbf63-183">V další části se dozvíte, jak vytvořit objekt zděděné složeného ovládacího prvku pomocí `ctlClock` jako základ.</span><span class="sxs-lookup"><span data-stu-id="dbf63-183">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="dbf63-184">Dědění z složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="dbf63-184">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="dbf63-185">V předchozích částech jste zjistili, jak zkombinovat ovládací prvky, komponenty a kódu Windows do opakovaně použitelného složených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="dbf63-185">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="dbf63-186">Složený ovládací prvek je nyní možné jako základ, na kterém je možné sestavovat další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="dbf63-186">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="dbf63-187">Proces odvození třídy ze základní třídy se nazývá *dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="dbf63-187">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="dbf63-188">V této části vytvoříte složeného ovládacího prvku volá `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-188">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="dbf63-189">Tento ovládací prvek bude odvozený z jeho nadřazenému ovládacímu prvku `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-189">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="dbf63-190">Se dozvíte, jak rozšířit funkce `ctlClock` nadřazené metody přepsání a přidáním nových metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="dbf63-190">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="dbf63-191">Prvním krokem při vytváření zděděný ovládací prvek je odvozen od svého nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="dbf63-191">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="dbf63-192">Tato akce vytvoří nový ovládací prvek, který má všechny vlastnosti, metody a grafické vlastnosti nadřazeného ovládacího prvku, ale mohou chovat i jako základ pro přidání nové nebo upravené funkce.</span><span class="sxs-lookup"><span data-stu-id="dbf63-192">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="dbf63-193">Chcete-li vytvořit zděděný ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="dbf63-193">To create the inherited control</span></span>  
  
1. <span data-ttu-id="dbf63-194">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClockLib**, přejděte na **přidat**a potom klikněte na tlačítko **uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-194">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="dbf63-195">**Přidat novou položku** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="dbf63-195">The **Add New Item** dialog box opens.</span></span>  
  
2. <span data-ttu-id="dbf63-196">Vyberte **zděděné uživatelský ovládací prvek** šablony.</span><span class="sxs-lookup"><span data-stu-id="dbf63-196">Select the **Inherited User Control** template.</span></span>  
  
3. <span data-ttu-id="dbf63-197">V **název** zadejte `ctlAlarmClock.cs`a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-197">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="dbf63-198">**Výběr dědičnosti** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="dbf63-198">The **Inheritance Picker** dialog box appears.</span></span>  
  
4. <span data-ttu-id="dbf63-199">V části **název komponenty**, dvakrát klikněte na panel **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-199">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5. <span data-ttu-id="dbf63-200">V Průzkumníku řešení projděte si aktuální projekty.</span><span class="sxs-lookup"><span data-stu-id="dbf63-200">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dbf63-201">Soubor s názvem **ctlAlarmClock.cs** byl přidán do aktuálního projektu.</span><span class="sxs-lookup"><span data-stu-id="dbf63-201">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="dbf63-202">Přidání vlastností upozornění</span><span class="sxs-lookup"><span data-stu-id="dbf63-202">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="dbf63-203">Vlastnosti jsou přidány do zděděný ovládací prvek stejným způsobem, které se přidají do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dbf63-203">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="dbf63-204">Teď použijete syntaxi deklarace vlastností přidat dvě vlastnosti do ovládacího prvku: `AlarmTime`, která bude uchovávat hodnotu Datum a čas vypnutí, a `AlarmSet`, která indikuje, jestli je nastavit alarm.</span><span class="sxs-lookup"><span data-stu-id="dbf63-204">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="dbf63-205">Přidání vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="dbf63-205">To add properties to your composite control</span></span>  
  
1. <span data-ttu-id="dbf63-206">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock**a potom klikněte na tlačítko **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-206">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2. <span data-ttu-id="dbf63-207">Vyhledejte `public class` příkazu.</span><span class="sxs-lookup"><span data-stu-id="dbf63-207">Locate the `public class` statement.</span></span> <span data-ttu-id="dbf63-208">Všimněte si, že ovládací prvek dědí z `ctlClockLib.ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-208">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="dbf63-209">Pod levou složenou závorku (`{)` příkazu, zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="dbf63-209">Beneath the opening brace (`{)` statement, type the following code.</span></span>  
  
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
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="dbf63-210">Přidávání do rozhraní grafického ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="dbf63-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="dbf63-211">Zděděný ovládací prvek má grafické rozhraní, který je stejný jako ovládací prvek, který dědí z.</span><span class="sxs-lookup"><span data-stu-id="dbf63-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="dbf63-212">Má stejné základní ovládací prvky jako jeho nadřazený ovládací prvek, ale vlastností základních ovládacích prvků nebude k dispozici, pokud výslovně vystavený.</span><span class="sxs-lookup"><span data-stu-id="dbf63-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="dbf63-213">Můžete přidat grafické rozhraní zděděných složeného ovládacího prvku stejným způsobem jako můžete přidat do jakékoli složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dbf63-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="dbf63-214">Pokračujte v přidávání do vašeho budíku vizuální rozhraní, přidejte ovládací prvek popisku, který bude flash, když je zvukově alarm.</span><span class="sxs-lookup"><span data-stu-id="dbf63-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="dbf63-215">Chcete-li přidat ovládací prvek popisek</span><span class="sxs-lookup"><span data-stu-id="dbf63-215">To add the label control</span></span>  
  
1. <span data-ttu-id="dbf63-216">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock**a potom klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-216">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="dbf63-217">Návrhář pro `ctlAlarmClock` otevře v hlavním okně.</span><span class="sxs-lookup"><span data-stu-id="dbf63-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2. <span data-ttu-id="dbf63-218">Klikněte na část zobrazení ovládacího prvku a zobrazte v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dbf63-218">Click the display portion of the control, and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dbf63-219">Když se zobrazí všechny vlastnosti, jsou neaktivní.</span><span class="sxs-lookup"><span data-stu-id="dbf63-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="dbf63-220">To znamená, že tyto vlastnosti jsou pro nativní `lblDisplay` a nelze změnit ani získat přístup v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dbf63-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="dbf63-221">Ve výchozím nastavení, ovládacích prvcích obsažených složeného ovládacího prvku jsou `private`, a jejich vlastnosti nejsou dostupné žádné prostředky.</span><span class="sxs-lookup"><span data-stu-id="dbf63-221">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dbf63-222">Pokud chcete mít přístup k jeho interní kontrolní mechanismy následné uživatelé složeného ovládacího prvku, je jako deklarovat `public` nebo `protected`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="dbf63-223">To vám umožní nastavit a změnit vlastnosti ovládacích prvků uvnitř složeného ovládacího prvku pomocí odpovídající kód.</span><span class="sxs-lookup"><span data-stu-id="dbf63-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3. <span data-ttu-id="dbf63-224">Přidat <xref:System.Windows.Forms.Label> ovládacího prvku do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dbf63-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4. <span data-ttu-id="dbf63-225">Pomocí myši přetáhnout <xref:System.Windows.Forms.Label> ovládací prvek bezprostředně pod rozevíracím seznamu zobrazit.</span><span class="sxs-lookup"><span data-stu-id="dbf63-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="dbf63-226">V okně Vlastnosti nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dbf63-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="dbf63-227">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="dbf63-227">Property</span></span>|<span data-ttu-id="dbf63-228">Nastavení</span><span class="sxs-lookup"><span data-stu-id="dbf63-228">Setting</span></span>|  
    |--------------|-------------|  
    |**<span data-ttu-id="dbf63-229">Name</span><span class="sxs-lookup"><span data-stu-id="dbf63-229">Name</span></span>**|`lblAlarm`|  
    |**<span data-ttu-id="dbf63-230">Text</span><span class="sxs-lookup"><span data-stu-id="dbf63-230">Text</span></span>**|**<span data-ttu-id="dbf63-231">Upozornění!</span><span class="sxs-lookup"><span data-stu-id="dbf63-231">Alarm!</span></span>**|  
    |**<span data-ttu-id="dbf63-232">TextAlign</span><span class="sxs-lookup"><span data-stu-id="dbf63-232">TextAlign</span></span>**|`MiddleCenter`|  
    |**<span data-ttu-id="dbf63-233">Viditelné</span><span class="sxs-lookup"><span data-stu-id="dbf63-233">Visible</span></span>**|`false`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="dbf63-234">Přidání funkce upozornění</span><span class="sxs-lookup"><span data-stu-id="dbf63-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="dbf63-235">V předchozích postupů jste přidali, vlastností a ovládací prvek, který vám umožní alarmů funkcí do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dbf63-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="dbf63-236">V tomto postupu přidáte kód, který porovná aktuální čas na čas alarmu, a pokud se shodují, na flash alarm.</span><span class="sxs-lookup"><span data-stu-id="dbf63-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="dbf63-237">Přepsáním `timer1_Tick` metoda `ctlClock` a do ní přidáte další kód, budou rozšíření možností objektu `ctlAlarmClock` při zachování všech funkcí inherentní `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-237">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="dbf63-238">Chcete-li přepsat metodu timer1_Tick ctlClock</span><span class="sxs-lookup"><span data-stu-id="dbf63-238">To override the timer1_Tick method of ctlClock</span></span>  
  
1. <span data-ttu-id="dbf63-239">V **Editor kódu**, vyhledejte `private bool blnAlarmSet;` příkazu.</span><span class="sxs-lookup"><span data-stu-id="dbf63-239">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="dbf63-240">Bezprostředně pod něj přidejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="dbf63-240">Immediately beneath it, add the following statement.</span></span>  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2. <span data-ttu-id="dbf63-241">V **Editor kódu**, vyhledejte pravou složenou závorku (`})` na konci třídy.</span><span class="sxs-lookup"><span data-stu-id="dbf63-241">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="dbf63-242">Těsně před složenou závorku přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="dbf63-242">Just before the brace, add the following code.</span></span>  
  
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
  
     <span data-ttu-id="dbf63-243">Tento kód provede několik úloh.</span><span class="sxs-lookup"><span data-stu-id="dbf63-243">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="dbf63-244">`override` Příkaz přesměruje ovládacího prvku, aby používali tuto metodu místo metody, která se dědí ze základního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dbf63-244">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="dbf63-245">Když tato metoda je volána, volá metodu přepíše vyvoláním `base.timer1_Tick` příkaz zajistí, že všechny funkce součástí původního ovládacího prvku je uveden v tomto ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="dbf63-245">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="dbf63-246">Pak spustí další kód začlenit funkce alarm.</span><span class="sxs-lookup"><span data-stu-id="dbf63-246">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="dbf63-247">Blikající ovládací prvek popisku se zobrazí při výskytu varování.</span><span class="sxs-lookup"><span data-stu-id="dbf63-247">A flashing label control will appear when the alarm occurs.</span></span>  
  
     <span data-ttu-id="dbf63-248">Ovládací prvek budíku je skoro hotová.</span><span class="sxs-lookup"><span data-stu-id="dbf63-248">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="dbf63-249">Jediné, co, která zůstává je implementace způsob, jak ji vypnout.</span><span class="sxs-lookup"><span data-stu-id="dbf63-249">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="dbf63-250">K tomu přidáte kód, který `lblAlarm_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="dbf63-250">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="dbf63-251">K implementaci přístupnými – metoda</span><span class="sxs-lookup"><span data-stu-id="dbf63-251">To implement the shutoff method</span></span>  
  
1. <span data-ttu-id="dbf63-252">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock.cs**a potom klikněte na tlačítko **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-252">In Solution Explorer, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="dbf63-253">Otevře se Návrhář.</span><span class="sxs-lookup"><span data-stu-id="dbf63-253">The designer opens.</span></span>  
  
2. <span data-ttu-id="dbf63-254">Přidání tlačítka pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="dbf63-254">Add a button to the control.</span></span> <span data-ttu-id="dbf63-255">Vlastnosti tlačítka nastavte následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="dbf63-255">Set the properties of the button as follows.</span></span>  
  
    |<span data-ttu-id="dbf63-256">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="dbf63-256">Property</span></span>|<span data-ttu-id="dbf63-257">Hodnota</span><span class="sxs-lookup"><span data-stu-id="dbf63-257">Value</span></span>|  
    |--------------|-----------|  
    |**<span data-ttu-id="dbf63-258">Name</span><span class="sxs-lookup"><span data-stu-id="dbf63-258">Name</span></span>**|`btnAlarmOff`|  
    |**<span data-ttu-id="dbf63-259">Text</span><span class="sxs-lookup"><span data-stu-id="dbf63-259">Text</span></span>**|**<span data-ttu-id="dbf63-260">Zakázat upozornění</span><span class="sxs-lookup"><span data-stu-id="dbf63-260">Disable Alarm</span></span>**|  
  
3. <span data-ttu-id="dbf63-261">V Návrháři dvakrát klikněte na panel **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-261">In the designer, double-click **btnAlarmOff**.</span></span>  
  
     <span data-ttu-id="dbf63-262">**Editor kódu** se otevře `private void btnAlarmOff_Click` řádku.</span><span class="sxs-lookup"><span data-stu-id="dbf63-262">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>  
  
4. <span data-ttu-id="dbf63-263">Upravte tuto metodu tak, aby vypadá podobně jako následující kód.</span><span class="sxs-lookup"><span data-stu-id="dbf63-263">Modify this method so that it resembles the following code.</span></span>  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5. <span data-ttu-id="dbf63-264">Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** chcete projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="dbf63-264">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="dbf63-265">Pomocí zděděný ovládací prvek ve formuláři</span><span class="sxs-lookup"><span data-stu-id="dbf63-265">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="dbf63-266">Zděděný ovládací prvek můžete otestovat stejným způsobem můžete otestovat základní třídy ovládacího prvku, `ctlClock`: Stisknutím klávesy F5 sestavte projekt a spusťte váš ovládací prvek **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-266">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="dbf63-267">Další informace najdete v tématu [jak: Testování běhového chování UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="dbf63-267">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="dbf63-268">Vložit ovládací prvek používat, musíte ho hostovat ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="dbf63-268">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="dbf63-269">Stejně jako u standardní složeného ovládacího prvku, zděděné složený ovládací prvek nemůže zůstat sama a musí být hostovaný ve formuláři nebo jiném kontejneru.</span><span class="sxs-lookup"><span data-stu-id="dbf63-269">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="dbf63-270">Protože `ctlAlarmClock` větší hloubky funkce, je potřeba ji otestovat další kód.</span><span class="sxs-lookup"><span data-stu-id="dbf63-270">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="dbf63-271">V tomto postupu budete psát jednoduchý program k otestování funkce `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-271">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="dbf63-272">Budete psát kód pro nastavení a zobrazení `AlarmTime` vlastnost `ctlAlarmClock`a testovat své vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="dbf63-272">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="dbf63-273">K vytvoření a přidání ovládacího prvku na formulář testu</span><span class="sxs-lookup"><span data-stu-id="dbf63-273">To build and add your control to a test form</span></span>  
  
1. <span data-ttu-id="dbf63-274">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClockLib**a potom klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-274">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2. <span data-ttu-id="dbf63-275">Přidat nový **aplikace Windows** projektu do řešení a pojmenujte ho `Test`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-275">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
3. <span data-ttu-id="dbf63-276">V Průzkumníku řešení klikněte pravým tlačítkem myši **odkazy** uzel pro testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="dbf63-276">In Solution Explorer, right-click the **References** node for your test project.</span></span> <span data-ttu-id="dbf63-277">Klikněte na tlačítko **přidat odkaz** zobrazíte **přidat odkaz** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="dbf63-277">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="dbf63-278">Klikněte na kartu **projekty**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-278">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="dbf63-279">Vaše `ctlClockLib` projektu budou uvedené v části **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-279">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="dbf63-280">Dvakrát klikněte na projekt tak, aby do testovacího projektu přidejte odkaz.</span><span class="sxs-lookup"><span data-stu-id="dbf63-280">Double-click the project to add the reference to the test project.</span></span>  
  
4. <span data-ttu-id="dbf63-281">V Průzkumníku řešení klikněte pravým tlačítkem na **testovací**a potom klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-281">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
5. <span data-ttu-id="dbf63-282">V **nástrojů**, rozbalte **ctlClockLib součásti** uzlu.</span><span class="sxs-lookup"><span data-stu-id="dbf63-282">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
6. <span data-ttu-id="dbf63-283">Dvakrát klikněte na panel **ctlAlarmClock** přidat kopii `ctlAlarmClock` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="dbf63-283">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>  
  
7. <span data-ttu-id="dbf63-284">V **nástrojů**, vyhledejte a dvakrát klikněte na panel **ovládacího prvku DateTimePicker** přidat <xref:System.Windows.Forms.DateTimePicker> ovládací prvek do formuláře a poté přidejte <xref:System.Windows.Forms.Label> ovládací prvek dvojitým kliknutím **popisek**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-284">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
8. <span data-ttu-id="dbf63-285">Pokud chcete umístit ovládací prvky v místě na formuláři pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="dbf63-285">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
9. <span data-ttu-id="dbf63-286">Následujícím způsobem nastavte vlastnosti těchto ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="dbf63-286">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="dbf63-287">Control</span><span class="sxs-lookup"><span data-stu-id="dbf63-287">Control</span></span>|<span data-ttu-id="dbf63-288">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="dbf63-288">Property</span></span>|<span data-ttu-id="dbf63-289">Hodnota</span><span class="sxs-lookup"><span data-stu-id="dbf63-289">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|**<span data-ttu-id="dbf63-290">Text</span><span class="sxs-lookup"><span data-stu-id="dbf63-290">Text</span></span>**|`(blank space)`|  
    ||**<span data-ttu-id="dbf63-291">Name</span><span class="sxs-lookup"><span data-stu-id="dbf63-291">Name</span></span>**|`lblTest`|  
    |`dateTimePicker1`|**<span data-ttu-id="dbf63-292">Name</span><span class="sxs-lookup"><span data-stu-id="dbf63-292">Name</span></span>**|`dtpTest`|  
    ||**<span data-ttu-id="dbf63-293">Formát</span><span class="sxs-lookup"><span data-stu-id="dbf63-293">Format</span></span>**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. <span data-ttu-id="dbf63-294">V Návrháři dvakrát klikněte na panel **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-294">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="dbf63-295">**Editor kódu** otevře `private void dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-295">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>  
  
11. <span data-ttu-id="dbf63-296">Upravte kód tak, aby se podobá následující.</span><span class="sxs-lookup"><span data-stu-id="dbf63-296">Modify the code so that it resembles the following.</span></span>  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. <span data-ttu-id="dbf63-297">V Průzkumníku řešení klikněte pravým tlačítkem na **testovací**a potom klikněte na tlačítko **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-297">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
13. <span data-ttu-id="dbf63-298">Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="dbf63-298">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="dbf63-299">Testovací program spustí.</span><span class="sxs-lookup"><span data-stu-id="dbf63-299">The test program starts.</span></span> <span data-ttu-id="dbf63-300">Všimněte si, že aktuální čas je aktualizace v `ctlAlarmClock` ovládacího prvku a, počáteční čas je zobrazena ve <xref:System.Windows.Forms.DateTimePicker> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dbf63-300">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
14. <span data-ttu-id="dbf63-301">Klikněte na tlačítko <xref:System.Windows.Forms.DateTimePicker> ve kterém se zobrazují minuty v hodině.</span><span class="sxs-lookup"><span data-stu-id="dbf63-301">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
15. <span data-ttu-id="dbf63-302">Pomocí klávesnice, nastavte hodnotu minut, který je větší než aktuální čas zobrazí jednu minutu `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-302">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="dbf63-303">Čas potřebný pro nastavení upozornění se zobrazí v `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-303">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="dbf63-304">Počkejte zobrazeném čase k nastavení doby alarm.</span><span class="sxs-lookup"><span data-stu-id="dbf63-304">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="dbf63-305">Čas, ke kterému je nastavit alarm, dosáhne zobrazeném čase `lblAlarm` bude flash.</span><span class="sxs-lookup"><span data-stu-id="dbf63-305">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>  
  
16. <span data-ttu-id="dbf63-306">Vypnout alarmu, kliknutím na `btnAlarmOff`.</span><span class="sxs-lookup"><span data-stu-id="dbf63-306">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="dbf63-307">Nyní může resetovat alarm.</span><span class="sxs-lookup"><span data-stu-id="dbf63-307">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="dbf63-308">Tento názorný postup zahrnují několik klíčových konceptů.</span><span class="sxs-lookup"><span data-stu-id="dbf63-308">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="dbf63-309">Naučili jste se vytvoření složeného ovládacího prvku kombinací ovládacích prvků a komponent do složeného ovládacího prvku kontejneru.</span><span class="sxs-lookup"><span data-stu-id="dbf63-309">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="dbf63-310">Jste se naučili přidání vlastnosti do ovládacího prvku a napsat kód k implementaci vlastních funkcí.</span><span class="sxs-lookup"><span data-stu-id="dbf63-310">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="dbf63-311">V předchozí části jste se dozvěděli k rozšíření funkčnosti dané složeného ovládacího prvku prostřednictvím dědičnosti a změnit funkci metody hostitele tak, že přepíšete tyto metody.</span><span class="sxs-lookup"><span data-stu-id="dbf63-311">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbf63-312">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dbf63-312">See also</span></span>

- [<span data-ttu-id="dbf63-313">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="dbf63-313">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="dbf63-314">Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="dbf63-314">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="dbf63-315">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="dbf63-315">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
