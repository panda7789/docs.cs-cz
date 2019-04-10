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
ms.openlocfilehash: c5668bd056c180f2cdf9b6160aa4d96e2ac2f5f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228598"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="7309f-102">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C\#</span><span class="sxs-lookup"><span data-stu-id="7309f-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C\#</span></span>
<span data-ttu-id="7309f-103">S [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], můžete vytvořit výkonné vlastní ovládací prvky prostřednictvím *dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="7309f-103">With [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="7309f-104">Prostřednictvím dědičnosti je možné vytvořit ovládací prvky, které zachovat všechny vlastní funkce standardní ovládací prvky Windows Forms, ale také začlenit vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="7309f-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="7309f-105">V tomto návodu vytvoříte jednoduchý volá zděděný ovládací prvek `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="7309f-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="7309f-106">Toto tlačítko bude funkce dědit ze standardních formulářů Windows <xref:System.Windows.Forms.Button> řídit a bude vystavovat vlastní vlastnost s názvem `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="7309f-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7309f-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="7309f-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7309f-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="7309f-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7309f-109">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7309f-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="7309f-110">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="7309f-110">Creating the Project</span></span>  
 <span data-ttu-id="7309f-111">Když vytvoříte nový projekt, zadejte jeho název nastavit kořenový obor názvů, název sestavení a název projektu a ujistěte se, že součást výchozí bude v správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="7309f-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="7309f-112">Chcete-li vytvořit ValueButtonLib Knihovna ovládacích prvků a ovládací prvek ValueButton</span><span class="sxs-lookup"><span data-stu-id="7309f-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="7309f-113">Na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu** otevřete **nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7309f-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="7309f-114">Vyberte **Knihovna ovládacích prvků Windows Forms** šablonu projektu ze seznamu Projekty Visual C# a typ `ValueButtonLib` v **název** pole.</span><span class="sxs-lookup"><span data-stu-id="7309f-114">Select the **Windows Forms Control Library** project template from the list of Visual C# Projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="7309f-115">Název projektu `ValueButtonLib`, je také přiřazený k oboru názvů root ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="7309f-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="7309f-116">Kořenový obor názvů se používá k určení názvů součástí sestavení.</span><span class="sxs-lookup"><span data-stu-id="7309f-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="7309f-117">Například, pokud se dvě sestavení poskytují komponenty s názvem `ValueButton`, můžete zadat vaše `ValueButton` pomocí komponenty `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="7309f-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="7309f-118">Další informace najdete v tématu [obory názvů](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="7309f-118">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>  
  
3.  <span data-ttu-id="7309f-119">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **UserControl1.cs**, klikněte na tlačítko **přejmenovat** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="7309f-119">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="7309f-120">Změňte název souboru, aby `ValueButton.cs`.</span><span class="sxs-lookup"><span data-stu-id="7309f-120">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="7309f-121">Klikněte na tlačítko **Ano** tlačítko, pokud budete vyzváni, pokud chcete přejmenovat všechny odkazy na prvek kódu '`UserControl1`".</span><span class="sxs-lookup"><span data-stu-id="7309f-121">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>  
  
4.  <span data-ttu-id="7309f-122">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ValueButton.cs** a vyberte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="7309f-122">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="7309f-123">Vyhledejte `class` řádek příkazu `public partial class ValueButton`a změňte typ, ze kterého dědí tohoto ovládacího prvku z <xref:System.Windows.Forms.UserControl> k <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="7309f-123">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="7309f-124">To umožňuje dědí všechny funkce, které jsou součástí zděděný ovládací prvek <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7309f-124">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
6.  <span data-ttu-id="7309f-125">V **Průzkumníka řešení**, otevřete **ValueButton.cs** uzel k zobrazení souboru kód generovaný návrhářem **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="7309f-125">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="7309f-126">Tento soubor otevřít v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="7309f-126">Open this file in the **Code Editor**.</span></span>  
  
7.  <span data-ttu-id="7309f-127">Vyhledejte `InitializeComponent` metoda a odebrat řádek, který se přiřadí <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7309f-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="7309f-128">Tato vlastnost neexistuje v <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7309f-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="7309f-129">Z **souboru** nabídce zvolte **Uložit vše** chcete projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="7309f-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7309f-130">Vizuálního návrháře již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7309f-130">A visual designer is no longer available.</span></span> <span data-ttu-id="7309f-131">Vzhledem k tomu, <xref:System.Windows.Forms.Button> ovládací prvek provede vlastní vykreslovací, nemůžete změnit její vzhled v návrháři.</span><span class="sxs-lookup"><span data-stu-id="7309f-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="7309f-132">Jeho vizuální znázornění byla přesně stejná jako, který dědí z třídy (to znamená <xref:System.Windows.Forms.Button>) není-li upravit v kódu.</span><span class="sxs-lookup"><span data-stu-id="7309f-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="7309f-133">Součásti, které mají bez prvků uživatelského rozhraní, stále můžete přidat na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="7309f-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="7309f-134">Přidání vlastnosti do zděděný ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="7309f-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="7309f-135">Je to možné užívání zděděný ovládací prvky Windows Forms je vytváření ovládacích prvků, které jsou stejné ve vzhledu a chování standardní ovládací prvky Windows Forms, ale vystavovat vlastní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7309f-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="7309f-136">V této části přidáte vlastnost s názvem `ButtonValue` do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7309f-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="7309f-137">Chcete-li přidat vlastnost Value</span><span class="sxs-lookup"><span data-stu-id="7309f-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="7309f-138">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ValueButton.cs**a potom klikněte na tlačítko **zobrazit kód** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="7309f-138">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="7309f-139">Vyhledejte `class` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7309f-139">Locate the `class` statement.</span></span> <span data-ttu-id="7309f-140">Ihned po `{`, zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="7309f-140">Immediately after the `{`, type the following code:</span></span>  
  
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
  
     <span data-ttu-id="7309f-141">Tento kód nastaví metody, pomocí kterého `ButtonValue` vlastnost je uložená a načíst.</span><span class="sxs-lookup"><span data-stu-id="7309f-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="7309f-142">`get` Příkaz nastaví hodnotu vrácenou hodnotu, která je uložen v soukromé proměnné `varValue`a `set` příkaz nastaví hodnotu vlastnosti soukromé proměnné pomocí `value` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="7309f-142">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>  
  
3.  <span data-ttu-id="7309f-143">Z **souboru** nabídce zvolte **Uložit vše** chcete projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="7309f-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="7309f-144">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="7309f-144">Testing Your Control</span></span>  
 <span data-ttu-id="7309f-145">Ovládací prvky nejsou samostatné projekty; musí být uložen v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="7309f-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="7309f-146">Pokud chcete otestovat ovládacího prvku, je nutné zadat testovací projekt, ke spuštění v.</span><span class="sxs-lookup"><span data-stu-id="7309f-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="7309f-147">Musíte také zajistit ovládacího prvku přístupné pro testovací projekt sestavením (kompilace) ji.</span><span class="sxs-lookup"><span data-stu-id="7309f-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="7309f-148">V této části bude sestavení ovládacího prvku a otestovat ho ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="7309f-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="7309f-149">K sestavení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="7309f-149">To build your control</span></span>  
  
1.  <span data-ttu-id="7309f-150">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="7309f-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="7309f-151">Sestavení by měl být úspěšný bez chyby kompilátoru nebo upozornění.</span><span class="sxs-lookup"><span data-stu-id="7309f-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="7309f-152">Chcete-li vytvořit projekt testů</span><span class="sxs-lookup"><span data-stu-id="7309f-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="7309f-153">Na **souboru** nabídky, přejděte k **přidat** a potom klikněte na tlačítko **nový projekt** otevřít **přidat nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7309f-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="7309f-154">Vyberte **Windows** uzlu, ybrat **Visual C#** uzel a klikněte na tlačítko **formulářová aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="7309f-154">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="7309f-155">V **název** zadejte `Test`.</span><span class="sxs-lookup"><span data-stu-id="7309f-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="7309f-156">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** vyberte uzel projektu testu **přidat odkaz** v místní nabídce zobrazíte  **Přidat odkaz na** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7309f-156">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="7309f-157">Klikněte na kartu **projekty**.</span><span class="sxs-lookup"><span data-stu-id="7309f-157">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="7309f-158">Vaše `ValueButtonLib` projektu budou uvedené v části **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="7309f-158">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="7309f-159">Dvakrát klikněte na projekt tak, aby do testovacího projektu přidejte odkaz.</span><span class="sxs-lookup"><span data-stu-id="7309f-159">Double-click the project to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="7309f-160">V **Průzkumníku řešení** klikněte pravým tlačítkem na **testovací** a vyberte **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="7309f-160">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="7309f-161">Chcete-li přidat ovládací prvek do formuláře</span><span class="sxs-lookup"><span data-stu-id="7309f-161">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="7309f-162">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Form1.cs** a zvolte **Návrhář zobrazení** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="7309f-162">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="7309f-163">V **nástrojů**, klikněte na tlačítko **ValueButtonLib komponenty**.</span><span class="sxs-lookup"><span data-stu-id="7309f-163">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="7309f-164">Dvakrát klikněte na panel **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="7309f-164">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="7309f-165">A **ValueButton** se zobrazí ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="7309f-165">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="7309f-166">Klikněte pravým tlačítkem myši **ValueButton** a vyberte **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="7309f-166">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="7309f-167">V **vlastnosti** okna, podívejte se na vlastnosti tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7309f-167">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="7309f-168">Všimněte si, že jsou shodné s vlastností vystavovaných třídami standardní tlačítko s tím rozdílem, že je další vlastnost `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="7309f-168">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="7309f-169">Nastavte `ButtonValue` vlastnost `5`.</span><span class="sxs-lookup"><span data-stu-id="7309f-169">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="7309f-170">V **všechny formuláře Windows** kartě **nástrojů**, dvakrát klikněte na panel **popisek** přidáte <xref:System.Windows.Forms.Label> ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="7309f-170">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="7309f-171">Přemístěte popisek středu tvaru.</span><span class="sxs-lookup"><span data-stu-id="7309f-171">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="7309f-172">Dvakrát klikněte na panel `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="7309f-172">Double-click `valueButton1`.</span></span>  
  
     <span data-ttu-id="7309f-173">**Editor kódu** se otevře `valueButton1_Click` událostí.</span><span class="sxs-lookup"><span data-stu-id="7309f-173">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="7309f-174">Vložte následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="7309f-174">Insert the following line of code.</span></span>  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. <span data-ttu-id="7309f-175">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **testovací**a zvolte **nastavit jako spouštěný projekt** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="7309f-175">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="7309f-176">Z **ladění** nabídce vyberte možnost **spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="7309f-176">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     `Form1` <span data-ttu-id="7309f-177">Zobrazí se.</span><span class="sxs-lookup"><span data-stu-id="7309f-177">appears.</span></span>  
  
12. <span data-ttu-id="7309f-178">Klikněte na tlačítko `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="7309f-178">Click `valueButton1`.</span></span>  
  
     <span data-ttu-id="7309f-179">Číslice "5" se zobrazí v `label1`ukázku, který `ButtonValue` byla předána vlastnost zděděný ovládací prvek `label1` prostřednictvím `valueButton1_Click` metoda.</span><span class="sxs-lookup"><span data-stu-id="7309f-179">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="7309f-180">Proto váš `ValueButton` dědí všechny funkce standardní tlačítko Windows Forms ovládací prvek, ale zpřístupňuje další, vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7309f-180">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7309f-181">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7309f-181">See also</span></span>

- [<span data-ttu-id="7309f-182">Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="7309f-182">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="7309f-183">Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="7309f-183">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
