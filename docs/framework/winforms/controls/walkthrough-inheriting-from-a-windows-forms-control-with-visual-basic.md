---
title: 'Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: 378d7b0c67791e6c48e9859e0546594df3ccc85e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931005"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="947a9-102">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basicu</span><span class="sxs-lookup"><span data-stu-id="947a9-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="947a9-103">Pomocí Visual Basic můžete pomocí dědičnosti vytvářet výkonné vlastní ovládacíprvky.</span><span class="sxs-lookup"><span data-stu-id="947a9-103">With Visual Basic, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="947a9-104">Prostřednictvím dědičnosti můžete vytvářet ovládací prvky, které budou uchovávat veškerou základní funkci standardních model Windows Formsch ovládacích prvků, ale také zahrnovat vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="947a9-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="947a9-105">V tomto návodu vytvoříte jednoduchý Zděděný ovládací prvek s názvem `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="947a9-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="947a9-106">Toto tlačítko zdědí funkce ze standardního ovládacího prvku model Windows Forms <xref:System.Windows.Forms.Button> a zpřístupní vlastní vlastnost s názvem. `ButtonValue`</span><span class="sxs-lookup"><span data-stu-id="947a9-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="947a9-107">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="947a9-107">Creating the Project</span></span>
 <span data-ttu-id="947a9-108">Při vytváření nového projektu zadáte jeho název, aby bylo možné nastavit kořenový obor názvů, název sestavení a název projektu a zajistit, že výchozí komponenta bude ve správném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="947a9-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="947a9-109">Vytvoření knihovny ovládacích prvků ValueButtonLib a ovládacího prvku ValueButton</span><span class="sxs-lookup"><span data-stu-id="947a9-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="947a9-110">V nabídce **soubor** přejděte na příkaz **Nový** a potom klikněte na **projekt** . otevře se dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="947a9-110">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="947a9-111">V seznamu Visual Basic projektů vyberte šablonu projektu **knihovny ovládacích prvků model Windows Forms** a do pole **název** zadejte `ValueButtonLib` .</span><span class="sxs-lookup"><span data-stu-id="947a9-111">Select the **Windows Forms Control Library** project template from the list of Visual Basic projects, and type `ValueButtonLib` in the **Name** box.</span></span>

     <span data-ttu-id="947a9-112">Název projektu, `ValueButtonLib`, je ve výchozím nastavení přiřazen ke kořenovému oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="947a9-112">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="947a9-113">Kořenový obor názvů slouží k získání názvů komponent v sestavení.</span><span class="sxs-lookup"><span data-stu-id="947a9-113">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="947a9-114">Například pokud dvě sestavení poskytují komponenty s názvem `ValueButton`, můžete určit svou `ValueButton` komponentu pomocí `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="947a9-114">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="947a9-115">Další informace najdete v tématu [obory názvů v Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="947a9-115">For more information, see [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>

3. <span data-ttu-id="947a9-116">V **Průzkumník řešení**klikněte pravým tlačítkem na **UserControl1. vb**a pak zvolte **Přejmenovat** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="947a9-116">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="947a9-117">Změňte název souboru na `ValueButton.vb`.</span><span class="sxs-lookup"><span data-stu-id="947a9-117">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="947a9-118">Pokud se zobrazí dotaz, zda chcete přejmenovat všechny odkazy na prvek kódu ' UserControl1 ', klikněte na tlačítko **Ano** .</span><span class="sxs-lookup"><span data-stu-id="947a9-118">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>

4. <span data-ttu-id="947a9-119">V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** .</span><span class="sxs-lookup"><span data-stu-id="947a9-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>

5. <span data-ttu-id="947a9-120">Otevřete uzel **ValueButton. vb** pro zobrazení souboru kódu generovaného návrhářem **ValueButton. Designer. vb**.</span><span class="sxs-lookup"><span data-stu-id="947a9-120">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="947a9-121">Otevřete tento soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="947a9-121">Open this file in the **Code Editor**.</span></span>

6. <span data-ttu-id="947a9-122">Vyhledejte příkaz, a `Partial Public Class ValueButton`změňte typ, ze <xref:System.Windows.Forms.UserControl> kterého <xref:System.Windows.Forms.Button>tento ovládací prvek dědí. `Class`</span><span class="sxs-lookup"><span data-stu-id="947a9-122">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="947a9-123">Tím umožníte zděděnému ovládacímu prvku dědění všech funkcí <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="947a9-123">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

7. <span data-ttu-id="947a9-124">Vyhledejte metodu a odstraňte čáru, která <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> přiřadí vlastnost. `InitializeComponent`</span><span class="sxs-lookup"><span data-stu-id="947a9-124">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="947a9-125">Tato vlastnost v <xref:System.Windows.Forms.Button> ovládacím prvku neexistuje.</span><span class="sxs-lookup"><span data-stu-id="947a9-125">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

8. <span data-ttu-id="947a9-126">V nabídce **soubor** klikněte na příkaz **Uložit vše** a projekt uložte.</span><span class="sxs-lookup"><span data-stu-id="947a9-126">From the **File** menu, choose **Save All** to save the project.</span></span>

     <span data-ttu-id="947a9-127">Všimněte si, že vizuální Návrhář již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="947a9-127">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="947a9-128">Vzhledem k tomu, že ovládacíprvekprovedevlastnímalování,nemůžetezměnitjehovzhledvnávrháři.<xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="947a9-128">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="947a9-129">Jeho vizuální reprezentace bude přesně stejná jako třída, ze které dědí ( <xref:System.Windows.Forms.Button>tj.), pokud není upravena v kódu.</span><span class="sxs-lookup"><span data-stu-id="947a9-129">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>

> [!NOTE]
> <span data-ttu-id="947a9-130">Na návrhovou plochu stále můžete přidat komponenty, které nemají žádné prvky uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="947a9-130">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="947a9-131">Přidání vlastnosti do zděděného ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="947a9-131">Adding a Property to Your Inherited Control</span></span>
 <span data-ttu-id="947a9-132">Jedním z možných použití děděných ovládacích prvků model Windows Forms je vytváření ovládacích prvků, které jsou identické vzhledy a chování (vzhled a chování) pro standardní model Windows Forms ovládací prvky, ale zpřístupňují vlastní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="947a9-132">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="947a9-133">V této části přidáte k ovládacímu prvku vlastnost s `ButtonValue` názvem.</span><span class="sxs-lookup"><span data-stu-id="947a9-133">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="947a9-134">Přidání vlastnosti Value</span><span class="sxs-lookup"><span data-stu-id="947a9-134">To add the Value property</span></span>

1. <span data-ttu-id="947a9-135">V **Průzkumník řešení**klikněte pravým tlačítkem na **ValueButton. vb**a pak klikněte na **Zobrazit kód** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="947a9-135">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="947a9-136">`Public Class ValueButton` Vyhledejte příkaz.</span><span class="sxs-lookup"><span data-stu-id="947a9-136">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="947a9-137">Hned pod tímto příkazem zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="947a9-137">Immediately beneath this statement, type the following code:</span></span>

    ```vb
    ' Creates the private variable that will store the value of your
    ' property.
    Private varValue as integer
    ' Declares the property.
    Property ButtonValue() as Integer
    ' Sets the method for retrieving the value of your property.
       Get
          Return varValue
       End Get
    ' Sets the method for setting the value of your property.
       Set(ByVal Value as Integer)
          varValue = Value
       End Set
    End Property
    ```

     <span data-ttu-id="947a9-138">Tento kód nastaví metody, podle kterých `ButtonValue` je vlastnost uložena a načtena.</span><span class="sxs-lookup"><span data-stu-id="947a9-138">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="947a9-139">Příkaz nastaví hodnotu vrácenou na hodnotu, která je uložena v soukromé proměnné `varValue`, a `Set` příkaz nastaví hodnotu soukromé proměnné `Value` pomocí klíčového slova. `Get`</span><span class="sxs-lookup"><span data-stu-id="947a9-139">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>

3. <span data-ttu-id="947a9-140">V nabídce **soubor** klikněte na příkaz **Uložit vše** a projekt uložte.</span><span class="sxs-lookup"><span data-stu-id="947a9-140">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="testing-your-control"></a><span data-ttu-id="947a9-141">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="947a9-141">Testing Your Control</span></span>
 <span data-ttu-id="947a9-142">Ovládací prvky nejsou samostatné projekty; musí být hostovány v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="947a9-142">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="947a9-143">Chcete-li otestovat ovládací prvek, je nutné zadat projekt testů, aby jej bylo možné spustit v.</span><span class="sxs-lookup"><span data-stu-id="947a9-143">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="947a9-144">Je také nutné mít přístup k ovládacímu prvku pro testovací projekt sestavením (kompilováním).</span><span class="sxs-lookup"><span data-stu-id="947a9-144">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="947a9-145">V této části vytvoříte ovládací prvek a otestujete ho ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="947a9-145">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="947a9-146">Sestavení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="947a9-146">To build your control</span></span>

1. <span data-ttu-id="947a9-147">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="947a9-147">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="947a9-148">Sestavení by mělo být úspěšné bez chyb nebo upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="947a9-148">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="947a9-149">Vytvoření testovacího projektu</span><span class="sxs-lookup"><span data-stu-id="947a9-149">To create a test project</span></span>

1. <span data-ttu-id="947a9-150">V nabídce **soubor** přejděte na příkaz **Přidat** a potom klikněte na možnost **Nový projekt** . tím otevřete dialogové okno **Přidat nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="947a9-150">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="947a9-151">Vyberte uzel Visual Basic projekty a klikněte na **model Windows Forms aplikace**.</span><span class="sxs-lookup"><span data-stu-id="947a9-151">Select the Visual Basic projects node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="947a9-152">Do pole **název** zadejte `Test`.</span><span class="sxs-lookup"><span data-stu-id="947a9-152">In the **Name** box, type `Test`.</span></span>

4. <span data-ttu-id="947a9-153">V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** .</span><span class="sxs-lookup"><span data-stu-id="947a9-153">In **Solution Explorer**, click the **Show All Files** button.</span></span>

5. <span data-ttu-id="947a9-154">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** pro projekt testů a pak vyberte možnost **Přidat odkaz** z místní nabídky a zobrazte tak dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="947a9-154">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

6. <span data-ttu-id="947a9-155">Klikněte na kartu **projekty** .</span><span class="sxs-lookup"><span data-stu-id="947a9-155">Click the **Projects** tab.</span></span>

7. <span data-ttu-id="947a9-156">Klikněte na kartu s označením **projekty**.</span><span class="sxs-lookup"><span data-stu-id="947a9-156">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="947a9-157">Projekt bude uveden v části **název projektu.** `ValueButtonLib`</span><span class="sxs-lookup"><span data-stu-id="947a9-157">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="947a9-158">Dvojím kliknutím na projekt přidejte odkaz na testovací projekt.</span><span class="sxs-lookup"><span data-stu-id="947a9-158">Double-click the project to add the reference to the test project.</span></span>

8. <span data-ttu-id="947a9-159">V **Průzkumník řešení** klikněte pravým tlačítkem na **test** a vyberte **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="947a9-159">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="947a9-160">Přidání ovládacího prvku do formuláře</span><span class="sxs-lookup"><span data-stu-id="947a9-160">To add your control to the form</span></span>

1. <span data-ttu-id="947a9-161">V **Průzkumník řešení**klikněte pravým tlačítkem na **Form1. vb** a v místní nabídce vyberte **zobrazit Návrhář** .</span><span class="sxs-lookup"><span data-stu-id="947a9-161">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="947a9-162">V sadě **nástrojů**klikněte na **součásti ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="947a9-162">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="947a9-163">Dvakrát klikněte na **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="947a9-163">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="947a9-164">Ve formuláři se zobrazí **ValueButton** .</span><span class="sxs-lookup"><span data-stu-id="947a9-164">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="947a9-165">Klikněte pravým tlačítkem na **ValueButton** a v místní nabídce vyberte **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="947a9-165">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="947a9-166">V okně **vlastnosti** prověřte vlastnosti tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="947a9-166">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="947a9-167">Všimněte si, že jsou stejné jako vlastnosti zveřejněné standardním tlačítkem, s výjimkou toho, že existuje další vlastnost `ButtonValue`,.</span><span class="sxs-lookup"><span data-stu-id="947a9-167">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>

5. <span data-ttu-id="947a9-168">Nastavte `ButtonValue` vlastnost `5`.</span><span class="sxs-lookup"><span data-stu-id="947a9-168">Set the `ButtonValue` property to `5`.</span></span>

6. <span data-ttu-id="947a9-169">Na kartě **Všechny model Windows Forms** **panelu nástrojů**přidejte <xref:System.Windows.Forms.Label> ovládací prvek do formuláře dvojitým kliknutím na položku **popisek** .</span><span class="sxs-lookup"><span data-stu-id="947a9-169">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="947a9-170">Přemístěte popisek na střed formuláře.</span><span class="sxs-lookup"><span data-stu-id="947a9-170">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="947a9-171">Poklikejte na `ValueButton1`.</span><span class="sxs-lookup"><span data-stu-id="947a9-171">Double-click `ValueButton1`.</span></span>

     <span data-ttu-id="947a9-172">Otevře se **Editor kódu** pro `ValueButton1_Click` událost.</span><span class="sxs-lookup"><span data-stu-id="947a9-172">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>

9. <span data-ttu-id="947a9-173">Zadejte následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="947a9-173">Type the following line of code.</span></span>

    ```vb
    Label1.Text = CStr(ValueButton1.ButtonValue)
    ```

10. <span data-ttu-id="947a9-174">V **Průzkumník řešení**klikněte pravým tlačítkem na **test**a v místní nabídce vyberte **nastavit jako spouštěný projekt** .</span><span class="sxs-lookup"><span data-stu-id="947a9-174">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="947a9-175">V nabídce **ladění** vyberte **Spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="947a9-175">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="947a9-176">`Form1`uvedeny.</span><span class="sxs-lookup"><span data-stu-id="947a9-176">`Form1` appears.</span></span>

12. <span data-ttu-id="947a9-177">Klikněte `Valuebutton1`na.</span><span class="sxs-lookup"><span data-stu-id="947a9-177">Click `Valuebutton1`.</span></span>

     <span data-ttu-id="947a9-178">Číslice "5" se zobrazí `Label1`v, `ButtonValue` což demonstruje, že vlastnost zděděného `Label1` ovládacího prvku byla předána prostřednictvím `ValueButton1_Click` metody.</span><span class="sxs-lookup"><span data-stu-id="947a9-178">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="947a9-179">Proto váš `ValueButton` ovládací prvek zdědí všechny funkce standardního model Windows Formsho tlačítka, ale zpřístupňuje další vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="947a9-179">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="947a9-180">Viz také:</span><span class="sxs-lookup"><span data-stu-id="947a9-180">See also</span></span>

- [<span data-ttu-id="947a9-181">Návod: Vytváření složeného ovládacího prvku pomocí Visual Basic</span><span class="sxs-lookup"><span data-stu-id="947a9-181">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="947a9-182">Postupy: Zobrazení ovládacího prvku v dialogovém okně zvolit položky sady nástrojů</span><span class="sxs-lookup"><span data-stu-id="947a9-182">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="947a9-183">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="947a9-183">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="947a9-184">Základy dědičnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="947a9-184">Inheritance basics (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
