---
title: Dědění z ovládacího prvku
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 713ccf97a73ce9684b9124a121369f22751861d0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740135"
---
# <a name="walkthrough-inherit-from-a-windows-forms-control-with-c"></a><span data-ttu-id="d70fc-102">Návod: dědění z ovládacího prvku model Windows Forms pomocí jazyka C\#</span><span class="sxs-lookup"><span data-stu-id="d70fc-102">Walkthrough: Inherit from a Windows Forms Control with C\#</span></span>

<span data-ttu-id="d70fc-103">Pomocí C#můžete vytvořit výkonné vlastní ovládací prvky prostřednictvím *dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="d70fc-103">With C#, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="d70fc-104">Prostřednictvím dědičnosti můžete vytvářet ovládací prvky, které budou uchovávat veškerou základní funkci standardních model Windows Formsch ovládacích prvků, ale také zahrnovat vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="d70fc-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="d70fc-105">V tomto návodu vytvoříte jednoduchý Zděděný ovládací prvek s názvem `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="d70fc-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="d70fc-106">Toto tlačítko zdědí funkce ze standardního ovládacího prvku model Windows Forms <xref:System.Windows.Forms.Button> a zpřístupní vlastní vlastnost s názvem `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="d70fc-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="d70fc-107">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="d70fc-107">Create the Project</span></span>

<span data-ttu-id="d70fc-108">Při vytváření nového projektu zadáte jeho název, aby bylo možné nastavit kořenový obor názvů, název sestavení a název projektu a zajistit, že výchozí komponenta bude ve správném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d70fc-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="d70fc-109">Vytvoření knihovny ovládacích prvků ValueButtonLib a ovládacího prvku ValueButton</span><span class="sxs-lookup"><span data-stu-id="d70fc-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="d70fc-110">V aplikaci Visual Studio vytvořte nový projekt **knihovny ovládacích prvků model Windows Forms** a pojmenujte jej **ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-110">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ValueButtonLib**.</span></span>

     <span data-ttu-id="d70fc-111">Název projektu, `ValueButtonLib`, je ve výchozím nastavení přiřazen také kořenovému oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d70fc-111">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="d70fc-112">Kořenový obor názvů slouží k získání názvů komponent v sestavení.</span><span class="sxs-lookup"><span data-stu-id="d70fc-112">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="d70fc-113">Například pokud dvě sestavení poskytují komponenty s názvem `ValueButton`, můžete určit `ValueButton` komponentu pomocí `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="d70fc-113">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="d70fc-114">Další informace najdete v tématu [obory názvů](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="d70fc-114">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>

2. <span data-ttu-id="d70fc-115">V **Průzkumník řešení**klikněte pravým tlačítkem na **UserControl1.cs**a pak zvolte **Přejmenovat** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="d70fc-115">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="d70fc-116">Změňte název souboru na **ValueButton.cs**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-116">Change the file name to **ValueButton.cs**.</span></span> <span data-ttu-id="d70fc-117">Pokud se zobrazí dotaz, zda chcete přejmenovat všechny odkazy na prvek kódu '`UserControl1`', klikněte na tlačítko **Ano** .</span><span class="sxs-lookup"><span data-stu-id="d70fc-117">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>

3. <span data-ttu-id="d70fc-118">V **Průzkumník řešení**klikněte pravým tlačítkem na **ValueButton.cs** a vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-118">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>

4. <span data-ttu-id="d70fc-119">Vyhledejte řádek příkazu `class`, `public partial class ValueButton`a změňte typ, ze kterého tento ovládací prvek dědí z <xref:System.Windows.Forms.UserControl> na <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="d70fc-119">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="d70fc-120">To umožňuje děděnému ovládacímu prvku dědit všechny funkce <xref:System.Windows.Forms.Button>ho ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d70fc-120">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

5. <span data-ttu-id="d70fc-121">V **Průzkumník řešení**otevřete uzel **ValueButton.cs** pro zobrazení souboru kódu generovaného návrhářem **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-121">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="d70fc-122">Otevřete tento soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-122">Open this file in the **Code Editor**.</span></span>

6. <span data-ttu-id="d70fc-123">Vyhledejte metodu `InitializeComponent` a odeberte čáru, která přiřadí vlastnost <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="d70fc-123">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="d70fc-124">Tato vlastnost v ovládacím prvku <xref:System.Windows.Forms.Button> neexistuje.</span><span class="sxs-lookup"><span data-stu-id="d70fc-124">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

7. <span data-ttu-id="d70fc-125">V nabídce **soubor** klikněte na příkaz **Uložit vše** a projekt uložte.</span><span class="sxs-lookup"><span data-stu-id="d70fc-125">From the **File** menu, choose **Save All** to save the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d70fc-126">Vizuální Návrhář již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d70fc-126">A visual designer is no longer available.</span></span> <span data-ttu-id="d70fc-127">Vzhledem k tomu, že ovládací prvek <xref:System.Windows.Forms.Button> vlastní malování, nemůžete změnit jeho vzhled v návrháři.</span><span class="sxs-lookup"><span data-stu-id="d70fc-127">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="d70fc-128">Jeho vizuální reprezentace bude přesně stejná jako třída, ze které dědí (to znamená <xref:System.Windows.Forms.Button>), pokud se v kódu nezmění.</span><span class="sxs-lookup"><span data-stu-id="d70fc-128">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="d70fc-129">Na návrhovou plochu stále můžete přidat komponenty, které nemají žádné prvky uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d70fc-129">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="add-a-property-to-your-inherited-control"></a><span data-ttu-id="d70fc-130">Přidání vlastnosti k Zděděnému ovládacímu prvku</span><span class="sxs-lookup"><span data-stu-id="d70fc-130">Add a Property to Your Inherited Control</span></span>

<span data-ttu-id="d70fc-131">Jedním z možných použití děděných ovládacích prvků model Windows Forms je vytváření ovládacích prvků, které jsou identické ve vzhledu a chování standardních model Windows Formsch ovládacích prvků, ale zpřístupňují vlastní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d70fc-131">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="d70fc-132">V této části přidáte k ovládacímu prvku vlastnost s názvem `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="d70fc-132">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="d70fc-133">Přidání vlastnosti Value</span><span class="sxs-lookup"><span data-stu-id="d70fc-133">To add the Value property</span></span>

1. <span data-ttu-id="d70fc-134">V **Průzkumník řešení**klikněte pravým tlačítkem na **ValueButton.cs**a potom klikněte na **Zobrazit kód** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="d70fc-134">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="d70fc-135">Vyhledejte příkaz `class`.</span><span class="sxs-lookup"><span data-stu-id="d70fc-135">Locate the `class` statement.</span></span> <span data-ttu-id="d70fc-136">Hned za `{`zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="d70fc-136">Immediately after the `{`, type the following code:</span></span>

    ```csharp
    // Creates the private variable that will store the value of your
    // property.
    private int varValue;
    // Declares the property.
    public int ButtonValue
    {
       // Sets the method for retrieving the value of your property.
       get
       {
          return varValue;
       }
       // Sets the method for setting the value of your property.
       set
       {
          varValue = value;
       }
    }
    ```

     <span data-ttu-id="d70fc-137">Tento kód nastaví metody, podle kterých je vlastnost `ButtonValue` uložena a načtena.</span><span class="sxs-lookup"><span data-stu-id="d70fc-137">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="d70fc-138">Příkaz `get` nastaví hodnotu vrácenou na hodnotu, která je uložena v `varValue`privátních proměnných, a příkaz `set` nastaví hodnotu soukromé proměnné pomocí klíčového slova `value`.</span><span class="sxs-lookup"><span data-stu-id="d70fc-138">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>

3. <span data-ttu-id="d70fc-139">V nabídce **soubor** klikněte na příkaz **Uložit vše** a projekt uložte.</span><span class="sxs-lookup"><span data-stu-id="d70fc-139">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="d70fc-140">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d70fc-140">Test the control</span></span>

<span data-ttu-id="d70fc-141">Ovládací prvky nejsou samostatné projekty; musí být hostovány v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d70fc-141">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="d70fc-142">Chcete-li otestovat ovládací prvek, je nutné zadat projekt testů, aby jej bylo možné spustit v.</span><span class="sxs-lookup"><span data-stu-id="d70fc-142">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="d70fc-143">Je také nutné mít přístup k ovládacímu prvku pro testovací projekt sestavením (kompilováním).</span><span class="sxs-lookup"><span data-stu-id="d70fc-143">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="d70fc-144">V této části vytvoříte ovládací prvek a otestujete ho ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="d70fc-144">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="d70fc-145">Sestavení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d70fc-145">To build your control</span></span>

<span data-ttu-id="d70fc-146">V nabídce **Sestavení** klikněte na **Sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-146">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="d70fc-147">Sestavení by mělo být úspěšné bez chyb nebo upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d70fc-147">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="d70fc-148">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="d70fc-148">To create a test project</span></span>

1. <span data-ttu-id="d70fc-149">V nabídce **soubor** přejděte na příkaz **Přidat** a potom klikněte na možnost **Nový projekt** . tím otevřete dialogové okno **Přidat nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="d70fc-149">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="d70fc-150">Vyberte uzel **Windows** pod uzlem **vizuálů C#**  a klikněte na **model Windows Forms aplikace**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-150">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="d70fc-151">Do pole **název** zadejte **test**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-151">In the **Name** box, enter **Test**.</span></span>

4. <span data-ttu-id="d70fc-152">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** pro projekt testů a pak vyberte možnost **Přidat odkaz** z místní nabídky a zobrazte tak dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="d70fc-152">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="d70fc-153">Klikněte na kartu s označením **projekty**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-153">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="d70fc-154">Váš projekt ValueButtonLib bude uveden v části **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-154">Your ValueButtonLib project will be listed under **Project Name**.</span></span> <span data-ttu-id="d70fc-155">Dvojím kliknutím na projekt přidejte odkaz na testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="d70fc-155">Double-click the project to add the reference to the test project.</span></span>

6. <span data-ttu-id="d70fc-156">V **Průzkumník řešení** klikněte pravým tlačítkem na **test** a vyberte **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-156">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="d70fc-157">Přidání ovládacího prvku do formuláře</span><span class="sxs-lookup"><span data-stu-id="d70fc-157">To add your control to the form</span></span>

1. <span data-ttu-id="d70fc-158">V **Průzkumník řešení**klikněte pravým tlačítkem na **Form1.cs** a v místní nabídce vyberte **zobrazit Návrhář** .</span><span class="sxs-lookup"><span data-stu-id="d70fc-158">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="d70fc-159">V sadě **nástrojů**vyberte **součásti ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-159">In the **Toolbox**, select **ValueButtonLib Components**.</span></span> <span data-ttu-id="d70fc-160">Dvakrát klikněte na **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-160">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="d70fc-161">Ve formuláři se zobrazí **ValueButton** .</span><span class="sxs-lookup"><span data-stu-id="d70fc-161">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="d70fc-162">Klikněte pravým tlačítkem na **ValueButton** a v místní nabídce vyberte **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="d70fc-162">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="d70fc-163">V okně **vlastnosti** prověřte vlastnosti tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d70fc-163">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="d70fc-164">Všimněte si, že jsou stejné jako vlastnosti zveřejněné standardním tlačítkem, s výjimkou toho, že existuje další vlastnost ButtonValue.</span><span class="sxs-lookup"><span data-stu-id="d70fc-164">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, ButtonValue.</span></span>

5. <span data-ttu-id="d70fc-165">Nastavte vlastnost **ButtonValue** na hodnotu **5**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-165">Set the **ButtonValue** property to **5**.</span></span>

6. <span data-ttu-id="d70fc-166">Na kartě **všechny model Windows Forms** **panelu nástrojů**přidejte ovládací prvek <xref:System.Windows.Forms.Label> do formuláře dvojitým kliknutím na položku **popisek** .</span><span class="sxs-lookup"><span data-stu-id="d70fc-166">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="d70fc-167">Přemístěte popisek na střed formuláře.</span><span class="sxs-lookup"><span data-stu-id="d70fc-167">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="d70fc-168">Dvakrát klikněte na `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="d70fc-168">Double-click `valueButton1`.</span></span>

     <span data-ttu-id="d70fc-169">Otevře se **Editor kódu** pro událost `valueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="d70fc-169">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>

9. <span data-ttu-id="d70fc-170">Vložte následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="d70fc-170">Insert the following line of code.</span></span>

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. <span data-ttu-id="d70fc-171">V **Průzkumník řešení**klikněte pravým tlačítkem na **test**a v místní nabídce vyberte **nastavit jako spouštěný projekt** .</span><span class="sxs-lookup"><span data-stu-id="d70fc-171">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="d70fc-172">V nabídce **ladění** vyberte **Spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="d70fc-172">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="d70fc-173">zobrazí se `Form1`.</span><span class="sxs-lookup"><span data-stu-id="d70fc-173">`Form1` appears.</span></span>

12. <span data-ttu-id="d70fc-174">Klikněte na `valueButton1` (Další).</span><span class="sxs-lookup"><span data-stu-id="d70fc-174">Click `valueButton1`.</span></span>

     <span data-ttu-id="d70fc-175">V `label1`se zobrazí číslice 5, které demonstruje, že vlastnost `ButtonValue` zděděného ovládacího prvku byla předána `label1` prostřednictvím metody `valueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="d70fc-175">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="d70fc-176">Proto váš ovládací prvek `ValueButton` dědí všechny funkce standardního model Windows Formsho tlačítka, ale zpřístupňuje další vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d70fc-176">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="d70fc-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="d70fc-177">See also</span></span>

- [<span data-ttu-id="d70fc-178">Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="d70fc-178">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="d70fc-179">Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="d70fc-179">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
