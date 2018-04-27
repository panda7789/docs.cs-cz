---
title: 'Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c88a9b4786fd544d175243fedb56b5071c8990f6
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a><span data-ttu-id="e108a-102">Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="e108a-102">Walkthrough: Authoring a Composite Control with Visual C#</span></span> #
<span data-ttu-id="e108a-103">Složené ovládací prvky poskytují prostředky, pomocí kterého lze vytvořit vlastní grafické rozhraní a znovu použít.</span><span class="sxs-lookup"><span data-stu-id="e108a-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="e108a-104">Složeného ovládacího prvku je v podstatě součást s vizuální reprezentace.</span><span class="sxs-lookup"><span data-stu-id="e108a-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="e108a-105">Takto může obsahovat jeden nebo více Windows Forms – ovládací prvky, komponenty nebo bloky kódu, který můžete rozšířit funkce ověřování uživatelského vstupu, změnou vlastností zobrazení nebo provádění jiných úloh vyžaduje autorem.</span><span class="sxs-lookup"><span data-stu-id="e108a-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="e108a-106">Složené ovládací prvky můžete umístit v rozhraní Windows Forms stejným způsobem jako další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e108a-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="e108a-107">V první části tohoto návodu, vytvořte jednoduché složeného ovládacího prvku názvem `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="e108a-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="e108a-108">V druhé části tohoto průvodce, můžete rozšířit funkce `ctlClock` prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="e108a-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e108a-109">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="e108a-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e108a-110">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="e108a-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e108a-111">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="e108a-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="e108a-112">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="e108a-112">Creating the Project</span></span>  
 <span data-ttu-id="e108a-113">Když vytvoříte nový projekt, je třeba zadat jeho název nastavení kořenového oboru názvů, název sestavení a název projektu a ujistěte se, že komponentu výchozí bude ve správném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e108a-113">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="e108a-114">K vytvoření knihovny řízení ctlClockLib a ctlClock ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="e108a-114">To create the ctlClockLib control library and the ctlClock control</span></span>  
  
1.  <span data-ttu-id="e108a-115">Na **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **projektu** otevřete **nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e108a-115">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="e108a-116">Ze seznamu Projekty Visual C#, vyberte **knihovny ovládacích prvků Windows Forms** šablona projektu, typ `ctlClockLib` v **název** pole a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="e108a-116">From the list of Visual C# projects, select the **Windows Forms Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e108a-117">Název projektu `ctlClockLib`, je také přiřazený k oboru názvů root ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e108a-117">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="e108a-118">Kořenový obor názvů se použijí pro kvalifikaci názvy součásti v sestavení.</span><span class="sxs-lookup"><span data-stu-id="e108a-118">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="e108a-119">Například, pokud dvě sestavení poskytují komponenty s názvem `ctlClock`, můžete zadat vaše `ctlClock` pomocí součásti `ctlClockLib.ctlClock.`</span><span class="sxs-lookup"><span data-stu-id="e108a-119">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>  
  
3.  <span data-ttu-id="e108a-120">V Průzkumníku řešení klikněte pravým tlačítkem na **UserControl1.cs**a potom klikněte na **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="e108a-120">In Solution Explorer, right-click **UserControl1.cs**, and then click **Rename**.</span></span> <span data-ttu-id="e108a-121">Změňte název souboru `ctlClock.cs`.</span><span class="sxs-lookup"><span data-stu-id="e108a-121">Change the file name to `ctlClock.cs`.</span></span> <span data-ttu-id="e108a-122">Klikněte **Ano** tlačítko po zobrazení dotazu, pokud chcete přejmenovat všechny odkazy na tento element kódu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="e108a-122">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e108a-123">Ve výchozím nastavení, zdědí složeného ovládacího prvku <xref:System.Windows.Forms.UserControl> třída poskytuje systém.</span><span class="sxs-lookup"><span data-stu-id="e108a-123">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="e108a-124"><xref:System.Windows.Forms.UserControl> Třída poskytuje funkce, které vyžadují všechny složené ovládací prvky a implementuje standardní metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e108a-124">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>  
  
4.  <span data-ttu-id="e108a-125">Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** k uložení projektu.</span><span class="sxs-lookup"><span data-stu-id="e108a-125">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="e108a-126">Přidání Windows ovládací prvky a součásti složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e108a-126">Adding Windows Controls and Components to the Composite Control</span></span>  
 <span data-ttu-id="e108a-127">Vizuální rozhraní je zásadní součástí vaší složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-127">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="e108a-128">Toto visual rozhraní je implementováno modulem přidání jednoho nebo více ovládacích prvků Windows na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="e108a-128">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="e108a-129">V následující ukázce se ovládací prvky Windows začlenit do vaší složeného ovládacího prvku a napsat kód pro implementaci funkcí.</span><span class="sxs-lookup"><span data-stu-id="e108a-129">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="e108a-130">Přidat k vaší složeného ovládacího prvku popisek a časovač</span><span class="sxs-lookup"><span data-stu-id="e108a-130">To add a Label and a Timer to your composite control</span></span>  
  
1.  <span data-ttu-id="e108a-131">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClock.cs**a potom klikněte na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e108a-131">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="e108a-132">V **sada nástrojů**, rozbalte **běžné ovládací prvky** uzel a poté dvojitým kliknutím **popisek**.</span><span class="sxs-lookup"><span data-stu-id="e108a-132">In the **Toolbox**, expand the **Common Controls** node, and then double-click **Label**.</span></span>  
  
     <span data-ttu-id="e108a-133">A <xref:System.Windows.Forms.Label> ovládací prvek s názvem `label1` se přidá do vašeho ovládacího prvku na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="e108a-133">A <xref:System.Windows.Forms.Label> control named `label1` is added to your control on the designer surface.</span></span>  
  
3.  <span data-ttu-id="e108a-134">V návrháři, klikněte na tlačítko **label1**.</span><span class="sxs-lookup"><span data-stu-id="e108a-134">In the designer, click **label1**.</span></span> <span data-ttu-id="e108a-135">V okně vlastností nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e108a-135">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="e108a-136">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e108a-136">Property</span></span>|<span data-ttu-id="e108a-137">Změňte na</span><span class="sxs-lookup"><span data-stu-id="e108a-137">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="e108a-138">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e108a-138">**Name**</span></span>|`lblDisplay`|  
    |<span data-ttu-id="e108a-139">**Text**</span><span class="sxs-lookup"><span data-stu-id="e108a-139">**Text**</span></span>|`(blank space)`|  
    |<span data-ttu-id="e108a-140">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="e108a-140">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="e108a-141">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="e108a-141">**Font.Size**</span></span>|`14`|  
  
4.  <span data-ttu-id="e108a-142">V **sada nástrojů**, rozbalte **součásti** uzel a poté dvojitým kliknutím **časovače**.</span><span class="sxs-lookup"><span data-stu-id="e108a-142">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>  
  
     <span data-ttu-id="e108a-143">Protože <xref:System.Windows.Forms.Timer> je komponenta, nemá žádné vizuální znázornění za běhu.</span><span class="sxs-lookup"><span data-stu-id="e108a-143">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="e108a-144">Proto ho pomocí ovládacích prvků na plochu návrháře, ale spíše v nezobrazí **Návrháři součástí** (panelu v dolní části plochu návrháře).</span><span class="sxs-lookup"><span data-stu-id="e108a-144">Therefore, it does not appear with the controls on the designer surface, but rather in the **Component Designer** (a tray at the bottom of the designer surface).</span></span>  
  
5.  <span data-ttu-id="e108a-145">V **Návrháři součástí**, klikněte na tlačítko **timer1**a poté nastavte <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost `1000` a <xref:System.Windows.Forms.Timer.Enabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="e108a-145">In the **Component Designer**, click **timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="e108a-146"><xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost řídí frekvenci, se kterým <xref:System.Windows.Forms.Timer> rysky součásti.</span><span class="sxs-lookup"><span data-stu-id="e108a-146">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the <xref:System.Windows.Forms.Timer> component ticks.</span></span> <span data-ttu-id="e108a-147">Pokaždé, když `timer1` rysky, spuštěním kódu `timer1_Tick` událostí.</span><span class="sxs-lookup"><span data-stu-id="e108a-147">Each time `timer1` ticks, it runs the code in the `timer1_Tick` event.</span></span> <span data-ttu-id="e108a-148">Interval představuje počet milisekund, po mezi značky.</span><span class="sxs-lookup"><span data-stu-id="e108a-148">The interval represents the number of milliseconds between ticks.</span></span>  
  
6.  <span data-ttu-id="e108a-149">V **Návrháři součástí**, dvakrát klikněte na **timer1** přejít na `timer1_Tick` událost pro `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="e108a-149">In the **Component Designer**, double-click **timer1** to go to the `timer1_Tick` event for `ctlClock`.</span></span>  
  
7.  <span data-ttu-id="e108a-150">Upravte kód tak, aby je podobná následující ukázka kódu.</span><span class="sxs-lookup"><span data-stu-id="e108a-150">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="e108a-151">Ujistěte se, chcete-li změnit – modifikátor přístupu z `private` k `protected`.</span><span class="sxs-lookup"><span data-stu-id="e108a-151">Be sure to change the access modifier from `private` to `protected`.</span></span>  
  
    ```csharp  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     <span data-ttu-id="e108a-152">Tento kód způsobí, že aktuální čas zobrazený v `lblDisplay`.</span><span class="sxs-lookup"><span data-stu-id="e108a-152">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="e108a-153">Protože interval `timer1` byla nastavena na `1000`, tato událost se stane každých tisíc milisekund, proto aktualizace aktuální čas každou sekundu.</span><span class="sxs-lookup"><span data-stu-id="e108a-153">Because the interval of `timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>  
  
8.  <span data-ttu-id="e108a-154">Změňte metodu být přepisovatelné s `virtual` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e108a-154">Modify the method to be overridable with the `virtual` keyword.</span></span> <span data-ttu-id="e108a-155">Další informace najdete v části ", která dědí z uživatelského ovládacího prvku" níže.</span><span class="sxs-lookup"><span data-stu-id="e108a-155">For more information, see the  "Inheriting from a User Control" section below.</span></span>  
  
    ```csharp  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. <span data-ttu-id="e108a-156">Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** k uložení projektu.</span><span class="sxs-lookup"><span data-stu-id="e108a-156">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="e108a-157">Přidání vlastnosti do složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e108a-157">Adding Properties to the Composite Control</span></span>  
 <span data-ttu-id="e108a-158">Vlastní ovládací prvek hodiny nyní zapouzdří <xref:System.Windows.Forms.Label> řízení a <xref:System.Windows.Forms.Timer> součást, každou s vlastní sadou vyplývajících vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e108a-158">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="e108a-159">Zatímco jednotlivé vlastnosti těchto ovládacích prvků nebude přístupný uživatelům následné ovládacího prvku, můžete vytvořit a vystavení vlastní vlastnosti napsáním odpovídající bloky kódu.</span><span class="sxs-lookup"><span data-stu-id="e108a-159">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="e108a-160">V následujícím postupu bude přidávat vlastnosti pro vaše ovládací prvek, který uživateli umožňuje změnit barvu pozadí a text.</span><span class="sxs-lookup"><span data-stu-id="e108a-160">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>  
  
#### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="e108a-161">Přidání vlastnosti do vašeho složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e108a-161">To add a property to your composite control</span></span>  
  
1.  <span data-ttu-id="e108a-162">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClock.cs**a potom klikněte na **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e108a-162">In Solution Explorer, right-click **ctlClock.cs**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="e108a-163">**Editor kódu** pro vlastní ovládací prvek otevře.</span><span class="sxs-lookup"><span data-stu-id="e108a-163">The **Code Editor** for your control opens.</span></span>  
  
2.  <span data-ttu-id="e108a-164">Vyhledejte `public partial class ctlClock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e108a-164">Locate the `public partial class ctlClock` statement.</span></span> <span data-ttu-id="e108a-165">Pod levá složená závorka (`{)`, zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e108a-165">Beneath the opening brace (`{)`, type the following code.</span></span>  
  
    ```csharp  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     <span data-ttu-id="e108a-166">Tyto příkazy vytvářet soukromé proměnné, které budete používat k ukládání hodnoty pro vlastnosti, které se chystáte vytvořit.</span><span class="sxs-lookup"><span data-stu-id="e108a-166">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>  
  
3.  <span data-ttu-id="e108a-167">Zadejte následující kód pod deklarace proměnných z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="e108a-167">Type the following code beneath the variable declarations from step 2.</span></span>  
  
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
  
     <span data-ttu-id="e108a-168">Předchozí kód vytvoří dvě vlastní vlastnosti `ClockForeColor` a `ClockBackColor`, k dispozici pro další uživatelé tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-168">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control.</span></span> <span data-ttu-id="e108a-169">`get` a `set` příkazy zadat pro ukládání a načítání hodnotu vlastnosti, jakož i kód implementovat funkce, které jsou vhodné pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e108a-169">The `get` and `set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>  
  
4.  <span data-ttu-id="e108a-170">Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** k uložení projektu.</span><span class="sxs-lookup"><span data-stu-id="e108a-170">On the **File** menu, click **Save All** to save the project.</span></span>  
  
## <a name="testing-the-control"></a><span data-ttu-id="e108a-171">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e108a-171">Testing the Control</span></span>  
 <span data-ttu-id="e108a-172">Ovládací prvky nejsou samostatné aplikace; musí být hostované v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e108a-172">Controls are not stand-alone applications; they must be hosted in a container.</span></span> <span data-ttu-id="e108a-173">Testování chování ovládacího prvku a jeho vlastnosti s vykonávat **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="e108a-173">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="e108a-174">Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="e108a-174">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-your-control"></a><span data-ttu-id="e108a-175">K otestování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e108a-175">To test your control</span></span>  
  
1.  <span data-ttu-id="e108a-176">Stiskněte klávesu F5, aby se projekt sestavil a spuštění vlastního ovládacího prvku v **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="e108a-176">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="e108a-177">V mřížce vlastnost kontejner testů, vyhledejte `ClockBackColor` vlastnost a potom vyberte vlastnost zobrazíte paletu barev.</span><span class="sxs-lookup"><span data-stu-id="e108a-177">In the test container's property grid, locate the `ClockBackColor` property, and then select the property to display the color palette.</span></span>  
  
3.  <span data-ttu-id="e108a-178">Vyberte barvu kliknutím.</span><span class="sxs-lookup"><span data-stu-id="e108a-178">Choose a color by clicking it.</span></span>  
  
     <span data-ttu-id="e108a-179">Barva pozadí ovládacího prvku změny barev, které jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="e108a-179">The background color of your control changes to the color you selected.</span></span>  
  
4.  <span data-ttu-id="e108a-180">Ověřte, že pomocí posloupnost událostí, podobně jako `ClockForeColor` vlastnost funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="e108a-180">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>  
  
     <span data-ttu-id="e108a-181">V této části a v předchozích částech, jste viděli, jak mohou být kombinovány komponenty a ovládací prvky Windows s kódem a balení vlastní nakonfigurovánu ve formě složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-181">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="e108a-182">Naučili jste se vystavení vlastností ve vaší složeného ovládacího prvku a po dokončení testování vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-182">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="e108a-183">V další části se dozvíte, jak vytvořit k zděděné složeného ovládacího prvku pomocí `ctlClock` jako základ.</span><span class="sxs-lookup"><span data-stu-id="e108a-183">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>  
  
## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="e108a-184">Dědění z složeného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e108a-184">Inheriting from a Composite Control</span></span>  
 <span data-ttu-id="e108a-185">V předchozích částech jste zjistili, jak kombinovat ovládací prvky systému Windows, komponent a kód do opakovatelně použitelných složené ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e108a-185">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="e108a-186">Vaše složeného ovládacího prvku nyní slouží jako základ, na kterém se dají vytvářet další ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e108a-186">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="e108a-187">Proces odvození třídy z základní třídy se nazývá *dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="e108a-187">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="e108a-188">V této části vytvoříte složeného ovládacího prvku názvem `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="e108a-188">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="e108a-189">Tento ovládací prvek bude odvozena z jeho nadřazenému ovládacímu prvku `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="e108a-189">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="e108a-190">Naučíte se rozšířit funkce `ctlClock` přepsání metody nadřazené a přidáním nových metod a vlastností.</span><span class="sxs-lookup"><span data-stu-id="e108a-190">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>  
  
 <span data-ttu-id="e108a-191">Prvním krokem při vytvoření ovládacího prvku zděděné je odvozena z nadřazené.</span><span class="sxs-lookup"><span data-stu-id="e108a-191">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="e108a-192">Tato akce vytvoří nový ovládací prvek, který má všechny vlastnosti, metod a grafické vlastnosti nadřazeného ovládacího prvku, ale mohou chovat i jako základ pro přidání nové nebo změněné funkce.</span><span class="sxs-lookup"><span data-stu-id="e108a-192">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>  
  
#### <a name="to-create-the-inherited-control"></a><span data-ttu-id="e108a-193">Vytvoření zděděné ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e108a-193">To create the inherited control</span></span>  
  
1.  <span data-ttu-id="e108a-194">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClockLib**, přejděte na příkaz **přidat**a potom klikněte na **uživatelský ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="e108a-194">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>  
  
     <span data-ttu-id="e108a-195">**Přidat novou položku** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e108a-195">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="e108a-196">Vyberte **zděděná uživatelský ovládací prvek** šablony.</span><span class="sxs-lookup"><span data-stu-id="e108a-196">Select the **Inherited User Control** template.</span></span>  
  
3.  <span data-ttu-id="e108a-197">V **název** zadejte `ctlAlarmClock.cs`a potom klikněte na **přidat**.</span><span class="sxs-lookup"><span data-stu-id="e108a-197">In the **Name** box, type `ctlAlarmClock.cs`, and then click **Add**.</span></span>  
  
     <span data-ttu-id="e108a-198">**Výběr dědičnosti** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e108a-198">The **Inheritance Picker** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="e108a-199">V části **název komponenty**, dvakrát klikněte na **ctlClock**.</span><span class="sxs-lookup"><span data-stu-id="e108a-199">Under **Component Name**, double-click **ctlClock**.</span></span>  
  
5.  <span data-ttu-id="e108a-200">V Průzkumníku řešení procházet aktuální projekty.</span><span class="sxs-lookup"><span data-stu-id="e108a-200">In Solution Explorer, browse through the current projects.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e108a-201">Soubor nazývá **ctlAlarmClock.cs** byla přidána do aktuálního projektu.</span><span class="sxs-lookup"><span data-stu-id="e108a-201">A file called **ctlAlarmClock.cs** has been added to the current project.</span></span>  
  
### <a name="adding-the-alarm-properties"></a><span data-ttu-id="e108a-202">Přidání vlastnosti výstrahy</span><span class="sxs-lookup"><span data-stu-id="e108a-202">Adding the Alarm Properties</span></span>  
 <span data-ttu-id="e108a-203">Vlastnosti jsou přidány do ovládacího prvku zděděné stejným způsobem, které budou přidány do složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-203">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="e108a-204">Teď použijete syntaxe deklarace vlastnost přidat dvě vlastnosti do vlastního ovládacího prvku: `AlarmTime`, který uloží hodnotu data a je čas vypnutí, a `AlarmSet`, který udává, zda je nastaven na upozornění.</span><span class="sxs-lookup"><span data-stu-id="e108a-204">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>  
  
##### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="e108a-205">Přidání vlastnosti do složených prvků</span><span class="sxs-lookup"><span data-stu-id="e108a-205">To add properties to your composite control</span></span>  
  
1.  <span data-ttu-id="e108a-206">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock**a potom klikněte na **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e108a-206">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="e108a-207">Vyhledejte `public class` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e108a-207">Locate the `public class` statement.</span></span> <span data-ttu-id="e108a-208">Všimněte si, že vlastní ovládací prvek dědí z `ctlClockLib.ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="e108a-208">Note that your control inherits from `ctlClockLib.ctlClock`.</span></span> <span data-ttu-id="e108a-209">Pod levá složená závorka (`{)` příkazu, zadejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e108a-209">Beneath the opening brace (`{)` statement, type the following code.</span></span>  
  
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
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="e108a-210">Přidávání do grafické rozhraní ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e108a-210">Adding to the Graphical Interface of the Control</span></span>  
 <span data-ttu-id="e108a-211">Vizuální rozhraní, který je stejný jako ovládací prvek, který dědí z má vlastní zděděné ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="e108a-211">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="e108a-212">Má k dispozici stejný základní ovládací prvky jako jeho nadřazenému ovládacímu prvku, ale vlastností základních ovládacích prvků nebudete mít k dispozici, pokud byly konkrétně vystavené.</span><span class="sxs-lookup"><span data-stu-id="e108a-212">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="e108a-213">Můžete přidat na grafické rozhraní zděděné složeného ovládacího prvku stejným způsobem jako přidáváte do jakékoli složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-213">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="e108a-214">Chcete-li pokračovat, přidávání do rozhraní visual alarmů hodiny, přidáte ovládacího prvku popisek, který bude flash, když je zvukově na upozornění.</span><span class="sxs-lookup"><span data-stu-id="e108a-214">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>  
  
##### <a name="to-add-the-label-control"></a><span data-ttu-id="e108a-215">Přidání ovládacího prvku popisek</span><span class="sxs-lookup"><span data-stu-id="e108a-215">To add the label control</span></span>  
  
1.  <span data-ttu-id="e108a-216">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock**a potom klikněte na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e108a-216">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="e108a-217">Návrhář pro `ctlAlarmClock` otevře v hlavním okně.</span><span class="sxs-lookup"><span data-stu-id="e108a-217">The designer for `ctlAlarmClock` opens in the main window.</span></span>  
  
2.  <span data-ttu-id="e108a-218">Klikněte na část zobrazení ovládacího prvku a zobrazit okno vlastností.</span><span class="sxs-lookup"><span data-stu-id="e108a-218">Click the display portion of the control, and view the Properties window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e108a-219">Když se zobrazí všechny vlastnosti, jsou neaktivní.</span><span class="sxs-lookup"><span data-stu-id="e108a-219">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="e108a-220">To znamená, že tyto vlastnosti jsou nativní pro `lblDisplay` a nelze změnit ani získat přístup v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e108a-220">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="e108a-221">Ve výchozím nastavení, jsou součástí složeného ovládacího prvku – ovládací prvky `private`, a jejich vlastnosti nejsou dostupné žádné prostředky.</span><span class="sxs-lookup"><span data-stu-id="e108a-221">By default, controls contained in a composite control are `private`, and their properties are not accessible by any means.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e108a-222">Pokud chcete další uživatelé složeného ovládacího prvku tak, aby měl přístup k jeho interní kontrolní mechanismy, deklarovat je jako `public` nebo `protected`.</span><span class="sxs-lookup"><span data-stu-id="e108a-222">If you want subsequent users of your composite control to have access to its internal controls, declare them as `public` or `protected`.</span></span> <span data-ttu-id="e108a-223">To vám umožní nastavit a úpravy vlastností ovládacích prvků, které jsou obsažené v rámci vaší složeného ovládacího prvku pomocí správný kód.</span><span class="sxs-lookup"><span data-stu-id="e108a-223">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>  
  
3.  <span data-ttu-id="e108a-224">Přidat <xref:System.Windows.Forms.Label> řízení pro vaše složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-224">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>  
  
4.  <span data-ttu-id="e108a-225">Pomocí myši, přetáhněte <xref:System.Windows.Forms.Label> ovládací prvek bezprostředně pod rozevíracím seznamu zobrazit.</span><span class="sxs-lookup"><span data-stu-id="e108a-225">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="e108a-226">V okně vlastností nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e108a-226">In the Properties window, set the following properties.</span></span>  
  
    |<span data-ttu-id="e108a-227">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e108a-227">Property</span></span>|<span data-ttu-id="e108a-228">Nastavení</span><span class="sxs-lookup"><span data-stu-id="e108a-228">Setting</span></span>|  
    |--------------|-------------|  
    |<span data-ttu-id="e108a-229">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e108a-229">**Name**</span></span>|`lblAlarm`|  
    |<span data-ttu-id="e108a-230">**Text**</span><span class="sxs-lookup"><span data-stu-id="e108a-230">**Text**</span></span>|<span data-ttu-id="e108a-231">**Varování!**</span><span class="sxs-lookup"><span data-stu-id="e108a-231">**Alarm!**</span></span>|  
    |<span data-ttu-id="e108a-232">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="e108a-232">**TextAlign**</span></span>|`MiddleCenter`|  
    |<span data-ttu-id="e108a-233">**Viditelné**</span><span class="sxs-lookup"><span data-stu-id="e108a-233">**Visible**</span></span>|`false`|  
  
### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="e108a-234">Přidání funkce výstrahy</span><span class="sxs-lookup"><span data-stu-id="e108a-234">Adding the Alarm Functionality</span></span>  
 <span data-ttu-id="e108a-235">V předchozích postupech jste přidali, vlastnosti a ovládací prvek, který vám umožní alarmů funkce ve vašem složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-235">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="e108a-236">V tomto postupu přidáte kód, který porovná aktuální čas je čas alarmů a, pokud jsou stejné, tak, aby alarm.</span><span class="sxs-lookup"><span data-stu-id="e108a-236">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to flash an alarm.</span></span> <span data-ttu-id="e108a-237">Přepsáním `timer1_Tick` metodu `ctlClock` a přidání další kód do, bude rozšířit schopnosti produktu `ctlAlarmClock` při zachování všech vyplývajících funkce `ctlClock`.</span><span class="sxs-lookup"><span data-stu-id="e108a-237">By overriding the `timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a><span data-ttu-id="e108a-238">Chcete-li přepsat metodě timer1_Tick ctlClock</span><span class="sxs-lookup"><span data-stu-id="e108a-238">To override the timer1_Tick method of ctlClock</span></span>  
  
1.  <span data-ttu-id="e108a-239">V **Editor kódu**, vyhledejte `private bool blnAlarmSet;` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e108a-239">In the **Code Editor**, locate the `private bool blnAlarmSet;` statement.</span></span> <span data-ttu-id="e108a-240">Bezprostředně pod něj přidejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="e108a-240">Immediately beneath it, add the following statement.</span></span>  
  
    ```csharp  
    private bool blnColorTicker;  
    ```  
  
2.  <span data-ttu-id="e108a-241">V **Editor kódu**, vyhledejte složená závorka (`})` na konci třídy.</span><span class="sxs-lookup"><span data-stu-id="e108a-241">In the **Code Editor**, locate the closing brace (`})` at the end of the class.</span></span> <span data-ttu-id="e108a-242">Těsně před složené závorce přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="e108a-242">Just before the brace, add the following code.</span></span>  
  
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
  
     <span data-ttu-id="e108a-243">Přidání tento kód provede několik úloh.</span><span class="sxs-lookup"><span data-stu-id="e108a-243">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="e108a-244">`override` Příkaz přesměruje ovládací prvek, který chcete použít tuto metodu místo metody, která byla zděděna od základního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-244">The `override` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="e108a-245">Když tato metoda je volána, zavolá metodu přepíše vyvoláním `base.timer1_Tick` prohlášení, zajistíte, že všechny funkce součástí původní ovládací prvek je uveden v tomto ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-245">When this method is called, it calls the method it overrides by invoking the `base.timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="e108a-246">Pak spustí další kód pro výstrahy funkce součástí.</span><span class="sxs-lookup"><span data-stu-id="e108a-246">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="e108a-247">Blikající ovládací prvek popisek se zobrazí při varování.</span><span class="sxs-lookup"><span data-stu-id="e108a-247">A flashing label control will appear when the alarm occurs.</span></span>  
  
     <span data-ttu-id="e108a-248">Vlastní ovládací prvek alarmů hodiny je téměř dokončena.</span><span class="sxs-lookup"><span data-stu-id="e108a-248">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="e108a-249">Jediné, co zůstane je implementace způsob, jak ho vypnout.</span><span class="sxs-lookup"><span data-stu-id="e108a-249">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="e108a-250">K tomuto účelu přidáte kód, který `lblAlarm_Click` metoda.</span><span class="sxs-lookup"><span data-stu-id="e108a-250">To do this, you will add code to the `lblAlarm_Click` method.</span></span>  
  
##### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="e108a-251">Chcete-li implementovat metodu přístupnými</span><span class="sxs-lookup"><span data-stu-id="e108a-251">To implement the shutoff method</span></span>  
  
1.  <span data-ttu-id="e108a-252">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlAlarmClock.cs**a potom klikněte na **Návrhář zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e108a-252">In Solution Explorer, right-click **ctlAlarmClock.cs**, and then click **View Designer**.</span></span>  
  
     <span data-ttu-id="e108a-253">Otevře se návrháře.</span><span class="sxs-lookup"><span data-stu-id="e108a-253">The designer opens.</span></span>  
  
2.  <span data-ttu-id="e108a-254">Přidání tlačítka do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-254">Add a button to the control.</span></span> <span data-ttu-id="e108a-255">Nastavte vlastnosti tlačítko následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e108a-255">Set the properties of the button as follows.</span></span>  
  
    |<span data-ttu-id="e108a-256">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e108a-256">Property</span></span>|<span data-ttu-id="e108a-257">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e108a-257">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="e108a-258">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e108a-258">**Name**</span></span>|`btnAlarmOff`|  
    |<span data-ttu-id="e108a-259">**Text**</span><span class="sxs-lookup"><span data-stu-id="e108a-259">**Text**</span></span>|<span data-ttu-id="e108a-260">**Zakázat výstrahy**</span><span class="sxs-lookup"><span data-stu-id="e108a-260">**Disable Alarm**</span></span>|  
  
3.  <span data-ttu-id="e108a-261">V návrháři, klikněte dvakrát na **btnAlarmOff**.</span><span class="sxs-lookup"><span data-stu-id="e108a-261">In the designer, double-click **btnAlarmOff**.</span></span>  
  
     <span data-ttu-id="e108a-262">**Editor kódu** se otevře `private void btnAlarmOff_Click` řádku.</span><span class="sxs-lookup"><span data-stu-id="e108a-262">The **Code Editor** opens to the `private void btnAlarmOff_Click` line.</span></span>  
  
4.  <span data-ttu-id="e108a-263">Upravte tuto metodu tak, aby je podobná následující kód.</span><span class="sxs-lookup"><span data-stu-id="e108a-263">Modify this method so that it resembles the following code.</span></span>  
  
    ```csharp  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  <span data-ttu-id="e108a-264">Na **soubor** nabídky, klikněte na tlačítko **Uložit vše** k uložení projektu.</span><span class="sxs-lookup"><span data-stu-id="e108a-264">On the **File** menu, click **Save All** to save the project.</span></span>  
  
### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="e108a-265">Použití zděděné ovládacího prvku ve formuláři</span><span class="sxs-lookup"><span data-stu-id="e108a-265">Using the Inherited Control on a Form</span></span>  
 <span data-ttu-id="e108a-266">Můžete otestovat zděděné kontrolu nad stejným způsobem jako otestovat základní třída prvku, `ctlClock`: stisknutím klávesy F5 se projekt sestavil a spuštění vlastního ovládacího prvku v **UserControl Test kontejneru**.</span><span class="sxs-lookup"><span data-stu-id="e108a-266">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="e108a-267">Další informace najdete v tématu [postupy: testování běhového chování UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="e108a-267">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="e108a-268">Vložit ovládací prvek použít, musíte ji hostovat ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="e108a-268">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="e108a-269">Stejně jako u standardní složeného ovládacího prvku, zděděné složeného ovládacího prvku nelze samostatná a musí být uloženy ve formuláři nebo jiných kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e108a-269">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="e108a-270">Vzhledem k tomu `ctlAlarmClock` má větší hloubky funkcí, je potřeba otestovat další kód.</span><span class="sxs-lookup"><span data-stu-id="e108a-270">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="e108a-271">V tomto postupu budete psát jednoduché program k testování funkčnosti `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="e108a-271">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="e108a-272">Budete psát kód k nastavení a zobrazit `AlarmTime` vlastnost `ctlAlarmClock`a testovat své vyplývajících funkce.</span><span class="sxs-lookup"><span data-stu-id="e108a-272">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="e108a-273">Sestavení a přidat do formuláře testu</span><span class="sxs-lookup"><span data-stu-id="e108a-273">To build and add your control to a test form</span></span>  
  
1.  <span data-ttu-id="e108a-274">V Průzkumníku řešení klikněte pravým tlačítkem na **ctlClockLib**a potom klikněte na **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="e108a-274">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>  
  
2.  <span data-ttu-id="e108a-275">Přidejte nový **aplikace Windows** projektu k řešení a pojmenujte ji `Test`.</span><span class="sxs-lookup"><span data-stu-id="e108a-275">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>  
  
3.  <span data-ttu-id="e108a-276">V Průzkumníku řešení klikněte pravým tlačítkem myši **odkazy** uzel pro projekt test.</span><span class="sxs-lookup"><span data-stu-id="e108a-276">In Solution Explorer, right-click the **References** node for your test project.</span></span> <span data-ttu-id="e108a-277">Klikněte na tlačítko **přidat odkaz na** zobrazíte **přidat odkaz na** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e108a-277">Click **Add Reference** to display the **Add Reference** dialog box.</span></span> <span data-ttu-id="e108a-278">Klikněte na kartu s názvem bez přípony **projekty**.</span><span class="sxs-lookup"><span data-stu-id="e108a-278">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="e108a-279">Vaše `ctlClockLib` projektu, zobrazí se v části **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="e108a-279">Your `ctlClockLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="e108a-280">Dvakrát klikněte na projekt se přidat odkaz na projekt test.</span><span class="sxs-lookup"><span data-stu-id="e108a-280">Double-click the project to add the reference to the test project.</span></span>  
  
4.  <span data-ttu-id="e108a-281">V Průzkumníku řešení klikněte pravým tlačítkem na **Test**a potom klikněte na **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="e108a-281">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>  
  
5.  <span data-ttu-id="e108a-282">V **sada nástrojů**, rozbalte **ctlClockLib součásti** uzlu.</span><span class="sxs-lookup"><span data-stu-id="e108a-282">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>  
  
6.  <span data-ttu-id="e108a-283">Klikněte dvakrát na **ctlAlarmClock** přidat kopii `ctlAlarmClock` do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="e108a-283">Double-click **ctlAlarmClock** to add a copy of `ctlAlarmClock` to your form.</span></span>  
  
7.  <span data-ttu-id="e108a-284">V **sada nástrojů**, vyhledejte a dvakrát klikněte na **DateTimePicker** přidat <xref:System.Windows.Forms.DateTimePicker> řízení do svého formuláře a poté přidejte <xref:System.Windows.Forms.Label> řízení dvojitým kliknutím na soubor **popisek**.</span><span class="sxs-lookup"><span data-stu-id="e108a-284">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>  
  
8.  <span data-ttu-id="e108a-285">Umístění ovládacích prvků na vhodné místo na formuláři pomocí myši.</span><span class="sxs-lookup"><span data-stu-id="e108a-285">Use the mouse to position the controls in a convenient place on the form.</span></span>  
  
9. <span data-ttu-id="e108a-286">Nastavte vlastnosti tyto ovládací prvky následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e108a-286">Set the properties of these controls in the following manner.</span></span>  
  
    |<span data-ttu-id="e108a-287">Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="e108a-287">Control</span></span>|<span data-ttu-id="e108a-288">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="e108a-288">Property</span></span>|<span data-ttu-id="e108a-289">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e108a-289">Value</span></span>|  
    |-------------|--------------|-----------|  
    |`label1`|<span data-ttu-id="e108a-290">**Text**</span><span class="sxs-lookup"><span data-stu-id="e108a-290">**Text**</span></span>|`(blank space)`|  
    ||<span data-ttu-id="e108a-291">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e108a-291">**Name**</span></span>|`lblTest`|  
    |`dateTimePicker1`|<span data-ttu-id="e108a-292">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e108a-292">**Name**</span></span>|`dtpTest`|  
    ||<span data-ttu-id="e108a-293">**Formát**</span><span class="sxs-lookup"><span data-stu-id="e108a-293">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
10. <span data-ttu-id="e108a-294">V návrháři, klikněte dvakrát na **dtpTest**.</span><span class="sxs-lookup"><span data-stu-id="e108a-294">In the designer, double-click **dtpTest**.</span></span>  
  
     <span data-ttu-id="e108a-295">**Editor kódu** otevře `private void dtpTest_ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="e108a-295">The **Code Editor** opens to `private void dtpTest_ValueChanged`.</span></span>  
  
11. <span data-ttu-id="e108a-296">Upravte kód tak, aby vypadá přibližně takto.</span><span class="sxs-lookup"><span data-stu-id="e108a-296">Modify the code so that it resembles the following.</span></span>  
  
    ```csharp  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. <span data-ttu-id="e108a-297">V Průzkumníku řešení klikněte pravým tlačítkem na **Test**a potom klikněte na **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="e108a-297">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>  
  
13. <span data-ttu-id="e108a-298">Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="e108a-298">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="e108a-299">Test program spustí.</span><span class="sxs-lookup"><span data-stu-id="e108a-299">The test program starts.</span></span> <span data-ttu-id="e108a-300">Všimněte si, že je aktuální čas aktualizován v `ctlAlarmClock` ovládací prvek, a že počáteční čas je zobrazen v nabídce <xref:System.Windows.Forms.DateTimePicker> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-300">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>  
  
14. <span data-ttu-id="e108a-301">Klikněte <xref:System.Windows.Forms.DateTimePicker> kde se zobrazují počet minut za hodinu.</span><span class="sxs-lookup"><span data-stu-id="e108a-301">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>  
  
15. <span data-ttu-id="e108a-302">Pomocí klávesnice, nastavte hodnotu pro počet minut, který je větší než aktuální čas zobrazí jednu minutu `ctlAlarmClock`.</span><span class="sxs-lookup"><span data-stu-id="e108a-302">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>  
  
     <span data-ttu-id="e108a-303">Čas pro nastavení upozornění se zobrazí v `lblTest`.</span><span class="sxs-lookup"><span data-stu-id="e108a-303">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="e108a-304">Počkejte, než zobrazených dobu dosáhnout alarmů nastavení času.</span><span class="sxs-lookup"><span data-stu-id="e108a-304">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="e108a-305">Když zobrazených čas dosáhne čas, ke kterému je nastavená na upozornění, `lblAlarm` bude flash.</span><span class="sxs-lookup"><span data-stu-id="e108a-305">When the displayed time reaches the time to which the alarm is set, the `lblAlarm` will flash.</span></span>  
  
16. <span data-ttu-id="e108a-306">Vypnout varování kliknutím `btnAlarmOff`.</span><span class="sxs-lookup"><span data-stu-id="e108a-306">Turn off the alarm by clicking `btnAlarmOff`.</span></span> <span data-ttu-id="e108a-307">Teď může resetovat na upozornění.</span><span class="sxs-lookup"><span data-stu-id="e108a-307">You may now reset the alarm.</span></span>  
  
     <span data-ttu-id="e108a-308">Tento názorný postup obsahuje zahrnutých počet klíčových konceptů.</span><span class="sxs-lookup"><span data-stu-id="e108a-308">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="e108a-309">Jste se naučili vytvoření složeného ovládacího prvku kombinací ovládací prvky a součásti do kontejneru složeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e108a-309">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="e108a-310">Jste se naučili přidání vlastnosti do vlastního ovládacího prvku a napsat kód pro implementaci vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="e108a-310">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="e108a-311">V poslední části jste se dozvěděli rozšířit funkce dané složeného ovládacího prvku prostřednictvím dědičnosti a změnit funkce hostitele metody přepsání těchto metod.</span><span class="sxs-lookup"><span data-stu-id="e108a-311">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e108a-312">Viz také</span><span class="sxs-lookup"><span data-stu-id="e108a-312">See Also</span></span>  
 [<span data-ttu-id="e108a-313">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e108a-313">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [<span data-ttu-id="e108a-314">Programování s komponentami</span><span class="sxs-lookup"><span data-stu-id="e108a-314">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="e108a-315">Součást pro vytváření obsahu návody</span><span class="sxs-lookup"><span data-stu-id="e108a-315">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [<span data-ttu-id="e108a-316">Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="e108a-316">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="e108a-317">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="e108a-317">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
