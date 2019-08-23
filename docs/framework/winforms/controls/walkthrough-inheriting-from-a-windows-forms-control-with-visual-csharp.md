---
title: 'Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
ms.openlocfilehash: c06639ef2f2ced8bd128adea636efe8be1715764
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931024"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="9a400-102">Návod: Dědění z ovládacího prvku model Windows Forms s Visual C\#</span><span class="sxs-lookup"><span data-stu-id="9a400-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C\#</span></span>
<span data-ttu-id="9a400-103">Pomocí vizuálu C#můžete vytvořit výkonné vlastní ovládací prvky prostřednictvím *dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="9a400-103">With Visual C#, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="9a400-104">Prostřednictvím dědičnosti můžete vytvářet ovládací prvky, které budou uchovávat veškerou základní funkci standardních model Windows Formsch ovládacích prvků, ale také zahrnovat vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="9a400-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="9a400-105">V tomto návodu vytvoříte jednoduchý Zděděný ovládací prvek s názvem `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="9a400-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="9a400-106">Toto tlačítko zdědí funkce ze standardního ovládacího prvku model Windows Forms <xref:System.Windows.Forms.Button> a zpřístupní vlastní vlastnost s názvem. `ButtonValue`</span><span class="sxs-lookup"><span data-stu-id="9a400-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="9a400-107">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="9a400-107">Creating the Project</span></span>
 <span data-ttu-id="9a400-108">Při vytváření nového projektu zadáte jeho název, aby bylo možné nastavit kořenový obor názvů, název sestavení a název projektu a zajistit, že výchozí komponenta bude ve správném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9a400-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="9a400-109">Vytvoření knihovny ovládacích prvků ValueButtonLib a ovládacího prvku ValueButton</span><span class="sxs-lookup"><span data-stu-id="9a400-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="9a400-110">V nabídce **soubor** přejděte na příkaz **Nový** a potom klikněte na **projekt** . otevře se dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="9a400-110">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="9a400-111">V seznamu vizuálních C# projektů vyberte šablonu projektu `ValueButtonLib` **knihovny ovládacích prvků model Windows Forms** a do pole **název** zadejte.</span><span class="sxs-lookup"><span data-stu-id="9a400-111">Select the **Windows Forms Control Library** project template from the list of Visual C# Projects, and type `ValueButtonLib` in the **Name** box.</span></span>

     <span data-ttu-id="9a400-112">Název projektu, `ValueButtonLib`, je ve výchozím nastavení přiřazen ke kořenovému oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9a400-112">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="9a400-113">Kořenový obor názvů slouží k získání názvů komponent v sestavení.</span><span class="sxs-lookup"><span data-stu-id="9a400-113">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="9a400-114">Například pokud dvě sestavení poskytují komponenty s názvem `ValueButton`, můžete určit svou `ValueButton` komponentu pomocí `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="9a400-114">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="9a400-115">Další informace najdete v tématu [obory názvů](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="9a400-115">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>

3. <span data-ttu-id="9a400-116">V **Průzkumník řešení**klikněte pravým tlačítkem na **UserControl1.cs**a pak zvolte **Přejmenovat** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="9a400-116">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="9a400-117">Změňte název souboru na `ValueButton.cs`.</span><span class="sxs-lookup"><span data-stu-id="9a400-117">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="9a400-118">Pokud se zobrazí dotaz, zda chcete přejmenovat všechny odkazy na prvek kódu '`UserControl1`', klikněte na tlačítko Ano.</span><span class="sxs-lookup"><span data-stu-id="9a400-118">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>

4. <span data-ttu-id="9a400-119">V **Průzkumník řešení**klikněte pravým tlačítkem na **ValueButton.cs** a vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="9a400-119">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>

5. <span data-ttu-id="9a400-120">Vyhledejte řádek `public partial class ValueButton` <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>příkazu, a změňte typ, ze kterého tento ovládací prvek dědí. `class`</span><span class="sxs-lookup"><span data-stu-id="9a400-120">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="9a400-121">Tím umožníte zděděnému ovládacímu prvku dědění všech funkcí <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9a400-121">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

6. <span data-ttu-id="9a400-122">V **Průzkumník řešení**otevřete uzel **ValueButton.cs** pro zobrazení souboru kódu generovaného návrhářem **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="9a400-122">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="9a400-123">Otevřete tento soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="9a400-123">Open this file in the **Code Editor**.</span></span>

7. <span data-ttu-id="9a400-124">Vyhledejte metodu a odstraňte čáru, která <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> přiřadí vlastnost. `InitializeComponent`</span><span class="sxs-lookup"><span data-stu-id="9a400-124">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="9a400-125">Tato vlastnost v <xref:System.Windows.Forms.Button> ovládacím prvku neexistuje.</span><span class="sxs-lookup"><span data-stu-id="9a400-125">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

8. <span data-ttu-id="9a400-126">V nabídce **soubor** klikněte na příkaz **Uložit vše** a projekt uložte.</span><span class="sxs-lookup"><span data-stu-id="9a400-126">From the **File** menu, choose **Save All** to save the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9a400-127">Vizuální Návrhář již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9a400-127">A visual designer is no longer available.</span></span> <span data-ttu-id="9a400-128">Vzhledem k tomu, že ovládacíprvekprovedevlastnímalování,nemůžetezměnitjehovzhledvnávrháři.<xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="9a400-128">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="9a400-129">Jeho vizuální reprezentace bude přesně stejná jako třída, ze které dědí ( <xref:System.Windows.Forms.Button>tj.), pokud není upravena v kódu.</span><span class="sxs-lookup"><span data-stu-id="9a400-129">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="9a400-130">Na návrhovou plochu stále můžete přidat komponenty, které nemají žádné prvky uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9a400-130">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="9a400-131">Přidání vlastnosti do zděděného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="9a400-131">Adding a Property to Your Inherited Control</span></span>
 <span data-ttu-id="9a400-132">Jedním z možných použití děděných ovládacích prvků model Windows Forms je vytváření ovládacích prvků, které jsou identické ve vzhledu a chování standardních model Windows Formsch ovládacích prvků, ale zpřístupňují vlastní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9a400-132">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="9a400-133">V této části přidáte k ovládacímu prvku vlastnost s `ButtonValue` názvem.</span><span class="sxs-lookup"><span data-stu-id="9a400-133">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="9a400-134">Přidání vlastnosti Value</span><span class="sxs-lookup"><span data-stu-id="9a400-134">To add the Value property</span></span>

1. <span data-ttu-id="9a400-135">V **Průzkumník řešení**klikněte pravým tlačítkem na **ValueButton.cs**a potom klikněte na **Zobrazit kód** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="9a400-135">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="9a400-136">`class` Vyhledejte příkaz.</span><span class="sxs-lookup"><span data-stu-id="9a400-136">Locate the `class` statement.</span></span> <span data-ttu-id="9a400-137">Hned za `{`a zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="9a400-137">Immediately after the `{`, type the following code:</span></span>

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

     <span data-ttu-id="9a400-138">Tento kód nastaví metody, podle kterých `ButtonValue` je vlastnost uložena a načtena.</span><span class="sxs-lookup"><span data-stu-id="9a400-138">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="9a400-139">Příkaz nastaví hodnotu vrácenou na hodnotu, která je uložena v soukromé proměnné `varValue`, a `set` příkaz nastaví hodnotu soukromé proměnné `value` pomocí klíčového slova. `get`</span><span class="sxs-lookup"><span data-stu-id="9a400-139">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>

3. <span data-ttu-id="9a400-140">V nabídce **soubor** klikněte na příkaz **Uložit vše** a projekt uložte.</span><span class="sxs-lookup"><span data-stu-id="9a400-140">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="testing-your-control"></a><span data-ttu-id="9a400-141">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="9a400-141">Testing Your Control</span></span>
 <span data-ttu-id="9a400-142">Ovládací prvky nejsou samostatné projekty; musí být hostovány v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9a400-142">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="9a400-143">Chcete-li otestovat ovládací prvek, je nutné zadat projekt testů, aby jej bylo možné spustit v.</span><span class="sxs-lookup"><span data-stu-id="9a400-143">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="9a400-144">Je také nutné mít přístup k ovládacímu prvku pro testovací projekt sestavením (kompilováním).</span><span class="sxs-lookup"><span data-stu-id="9a400-144">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="9a400-145">V této části vytvoříte ovládací prvek a otestujete ho ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="9a400-145">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="9a400-146">Sestavení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="9a400-146">To build your control</span></span>

1. <span data-ttu-id="9a400-147">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="9a400-147">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="9a400-148">Sestavení by mělo být úspěšné bez chyb nebo upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="9a400-148">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="9a400-149">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="9a400-149">To create a test project</span></span>

1. <span data-ttu-id="9a400-150">V nabídce **soubor** přejděte na příkaz **Přidat** a potom klikněte na možnost **Nový projekt** . tím otevřete dialogové okno **Přidat nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="9a400-150">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="9a400-151">Vyberte uzel **Windows** pod uzlem **vizuálů C#**  a klikněte na **model Windows Forms aplikace**.</span><span class="sxs-lookup"><span data-stu-id="9a400-151">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="9a400-152">Do pole **název** zadejte `Test`.</span><span class="sxs-lookup"><span data-stu-id="9a400-152">In the **Name** box, type `Test`.</span></span>

4. <span data-ttu-id="9a400-153">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** pro projekt testů a pak vyberte možnost **Přidat odkaz** z místní nabídky a zobrazte tak dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="9a400-153">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="9a400-154">Klikněte na kartu s označením **projekty**.</span><span class="sxs-lookup"><span data-stu-id="9a400-154">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="9a400-155">Projekt bude uveden v části **název projektu.** `ValueButtonLib`</span><span class="sxs-lookup"><span data-stu-id="9a400-155">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="9a400-156">Dvojím kliknutím na projekt přidejte odkaz na testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="9a400-156">Double-click the project to add the reference to the test project.</span></span>

6. <span data-ttu-id="9a400-157">V **Průzkumník řešení** klikněte pravým tlačítkem na **test** a vyberte **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="9a400-157">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="9a400-158">Přidání ovládacího prvku do formuláře</span><span class="sxs-lookup"><span data-stu-id="9a400-158">To add your control to the form</span></span>

1. <span data-ttu-id="9a400-159">V **Průzkumník řešení**klikněte pravým tlačítkem na **Form1.cs** a v místní nabídce vyberte **zobrazit Návrhář** .</span><span class="sxs-lookup"><span data-stu-id="9a400-159">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="9a400-160">V sadě **nástrojů**klikněte na **součásti ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="9a400-160">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="9a400-161">Dvakrát klikněte na **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="9a400-161">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="9a400-162">Ve formuláři se zobrazí **ValueButton** .</span><span class="sxs-lookup"><span data-stu-id="9a400-162">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="9a400-163">Klikněte pravým tlačítkem na **ValueButton** a v místní nabídce vyberte **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="9a400-163">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="9a400-164">V okně **vlastnosti** prověřte vlastnosti tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9a400-164">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="9a400-165">Všimněte si, že jsou stejné jako vlastnosti zveřejněné standardním tlačítkem, s výjimkou toho, že existuje další vlastnost `ButtonValue`,.</span><span class="sxs-lookup"><span data-stu-id="9a400-165">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>

5. <span data-ttu-id="9a400-166">Nastavte `ButtonValue` vlastnost `5`.</span><span class="sxs-lookup"><span data-stu-id="9a400-166">Set the `ButtonValue` property to `5`.</span></span>

6. <span data-ttu-id="9a400-167">Na kartě **Všechny model Windows Forms** **panelu nástrojů**přidejte <xref:System.Windows.Forms.Label> ovládací prvek do formuláře dvojitým kliknutím na položku **popisek** .</span><span class="sxs-lookup"><span data-stu-id="9a400-167">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="9a400-168">Přemístěte popisek na střed formuláře.</span><span class="sxs-lookup"><span data-stu-id="9a400-168">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="9a400-169">Poklikejte na `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="9a400-169">Double-click `valueButton1`.</span></span>

     <span data-ttu-id="9a400-170">Otevře se **Editor kódu** pro `valueButton1_Click` událost.</span><span class="sxs-lookup"><span data-stu-id="9a400-170">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>

9. <span data-ttu-id="9a400-171">Vložte následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="9a400-171">Insert the following line of code.</span></span>

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. <span data-ttu-id="9a400-172">V **Průzkumník řešení**klikněte pravým tlačítkem na **test**a v místní nabídce vyberte **nastavit jako spouštěný projekt** .</span><span class="sxs-lookup"><span data-stu-id="9a400-172">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="9a400-173">V nabídce **ladění** vyberte **Spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="9a400-173">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="9a400-174">`Form1`uvedeny.</span><span class="sxs-lookup"><span data-stu-id="9a400-174">`Form1` appears.</span></span>

12. <span data-ttu-id="9a400-175">Klikněte `valueButton1`na.</span><span class="sxs-lookup"><span data-stu-id="9a400-175">Click `valueButton1`.</span></span>

     <span data-ttu-id="9a400-176">Číslice "5" se zobrazí `label1`v, `ButtonValue` což demonstruje, že vlastnost zděděného `label1` ovládacího prvku byla předána prostřednictvím `valueButton1_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="9a400-176">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="9a400-177">Proto váš `ValueButton` ovládací prvek zdědí všechny funkce standardního model Windows Formsho tlačítka, ale zpřístupňuje další vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9a400-177">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a400-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a400-178">See also</span></span>

- [<span data-ttu-id="9a400-179">Postupy: Zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="9a400-179">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="9a400-180">Návod: Vytváření složeného ovládacího prvku pomocí vizuáluC#</span><span class="sxs-lookup"><span data-stu-id="9a400-180">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
