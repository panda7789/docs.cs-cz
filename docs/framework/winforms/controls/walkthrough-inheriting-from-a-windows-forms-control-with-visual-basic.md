---
title: 'Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic'
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
ms.openlocfilehash: 6c70de1bf6a5340b6f5b2c652110ed9be5536665
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45686307"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="681b7-102">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual Basic</span><span class="sxs-lookup"><span data-stu-id="681b7-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="681b7-103">Pomocí jazyka Visual Basic, můžete vytvořit výkonné vlastní ovládací prvky prostřednictvím *dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="681b7-103">With Visual Basic, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="681b7-104">Prostřednictvím dědičnosti je možné vytvořit ovládací prvky, které zachovat všechny vlastní funkce standardní ovládací prvky Windows Forms, ale také začlenit vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="681b7-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="681b7-105">V tomto návodu vytvoříte jednoduchý volá zděděný ovládací prvek `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="681b7-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="681b7-106">Toto tlačítko bude funkce dědit ze standardních formulářů Windows <xref:System.Windows.Forms.Button> řídit a bude vystavovat vlastní vlastnost s názvem `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="681b7-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="681b7-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="681b7-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="681b7-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="681b7-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="681b7-109">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="681b7-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="681b7-110">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="681b7-110">Creating the Project</span></span>  
 <span data-ttu-id="681b7-111">Když vytvoříte nový projekt, zadejte jeho název nastavit kořenový obor názvů, název sestavení a název projektu a ujistěte se, že součást výchozí bude v správný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="681b7-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="681b7-112">Chcete-li vytvořit ValueButtonLib Knihovna ovládacích prvků a ovládací prvek ValueButton</span><span class="sxs-lookup"><span data-stu-id="681b7-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="681b7-113">Na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu** otevřete **nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="681b7-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="681b7-114">Vyberte **Knihovna ovládacích prvků Windows Forms** šablonu projektu ze seznamu projektů jazyka Visual Basic a typ `ValueButtonLib` v **název** pole.</span><span class="sxs-lookup"><span data-stu-id="681b7-114">Select the **Windows Forms Control Library** project template from the list of Visual Basic projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="681b7-115">Název projektu `ValueButtonLib`, je také přiřazený k oboru názvů root ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="681b7-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="681b7-116">Kořenový obor názvů se používá k určení názvů součástí sestavení.</span><span class="sxs-lookup"><span data-stu-id="681b7-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="681b7-117">Například, pokud se dvě sestavení poskytují komponenty s názvem `ValueButton`, můžete zadat vaše `ValueButton` pomocí komponenty `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="681b7-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="681b7-118">Další informace najdete v tématu [obory názvů v jazyce Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="681b7-118">For more information, see [Namespaces in Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
3.  <span data-ttu-id="681b7-119">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **UserControl1.vb**, klikněte na tlačítko **přejmenovat** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="681b7-119">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="681b7-120">Změňte název souboru, aby `ValueButton.vb`.</span><span class="sxs-lookup"><span data-stu-id="681b7-120">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="681b7-121">Klikněte na tlačítko **Ano** tlačítko, pokud budete vyzváni, pokud chcete přejmenovat všechny odkazy na prvek kódu "UserControl1".</span><span class="sxs-lookup"><span data-stu-id="681b7-121">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>  
  
4.  <span data-ttu-id="681b7-122">V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="681b7-122">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5.  <span data-ttu-id="681b7-123">Otevřít **ValueButton.vb** uzel k zobrazení souboru kód generovaný návrhářem **ValueButton.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="681b7-123">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="681b7-124">Tento soubor otevřít v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="681b7-124">Open this file in the **Code Editor**.</span></span>  
  
6.  <span data-ttu-id="681b7-125">Vyhledejte `Class` příkazu `Partial Public Class ValueButton`a změňte typ, ze kterého dědí tohoto ovládacího prvku z <xref:System.Windows.Forms.UserControl> k <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="681b7-125">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="681b7-126">To umožňuje dědí všechny funkce, které jsou součástí zděděný ovládací prvek <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="681b7-126">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
7.  <span data-ttu-id="681b7-127">Vyhledejte `InitializeComponent` metoda a odebrat řádek, který se přiřadí <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="681b7-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="681b7-128">Tato vlastnost neexistuje v <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="681b7-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="681b7-129">Z **souboru** nabídce zvolte **Uložit vše** chcete projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="681b7-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
     <span data-ttu-id="681b7-130">Všimněte si, že vizuálního návrháře již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="681b7-130">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="681b7-131">Vzhledem k tomu, <xref:System.Windows.Forms.Button> ovládací prvek provede vlastní vykreslovací, nemůžete změnit její vzhled v návrháři.</span><span class="sxs-lookup"><span data-stu-id="681b7-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="681b7-132">Jeho vizuální znázornění byla přesně stejná jako, který dědí z třídy (to znamená <xref:System.Windows.Forms.Button>) není-li upravit v kódu.</span><span class="sxs-lookup"><span data-stu-id="681b7-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="681b7-133">Součásti, které mají bez prvků uživatelského rozhraní, stále můžete přidat na návrhovou plochu.</span><span class="sxs-lookup"><span data-stu-id="681b7-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="681b7-134">Přidání vlastnosti do zděděný ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="681b7-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="681b7-135">Je to možné užívání zděděný ovládací prvky Windows Forms je vytváření ovládacích prvků, které jsou stejné ve vzhledu a chování (vzhled a chování) pro standardní ovládací prvky Windows Forms, ale vystavovat vlastní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="681b7-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="681b7-136">V této části přidáte vlastnost s názvem `ButtonValue` do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="681b7-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="681b7-137">Chcete-li přidat vlastnost Value</span><span class="sxs-lookup"><span data-stu-id="681b7-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="681b7-138">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ValueButton.vb**a potom klikněte na tlačítko **zobrazit kód** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="681b7-138">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="681b7-139">Vyhledejte `Public Class ValueButton` příkazu.</span><span class="sxs-lookup"><span data-stu-id="681b7-139">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="681b7-140">Hned pod tento příkaz, zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="681b7-140">Immediately beneath this statement, type the following code:</span></span>  
  
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
  
     <span data-ttu-id="681b7-141">Tento kód nastaví metody, pomocí kterého `ButtonValue` vlastnost je uložená a načíst.</span><span class="sxs-lookup"><span data-stu-id="681b7-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="681b7-142">`Get` Příkaz nastaví hodnotu vrácenou hodnotu, která je uložen v soukromé proměnné `varValue`a `Set` příkaz nastaví hodnotu vlastnosti soukromé proměnné pomocí `Value` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="681b7-142">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>  
  
3.  <span data-ttu-id="681b7-143">Z **souboru** nabídce zvolte **Uložit vše** chcete projekt uložit.</span><span class="sxs-lookup"><span data-stu-id="681b7-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="681b7-144">Testování ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="681b7-144">Testing Your Control</span></span>  
 <span data-ttu-id="681b7-145">Ovládací prvky nejsou samostatné projekty; musí být uložen v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="681b7-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="681b7-146">Pokud chcete otestovat ovládacího prvku, je nutné zadat testovací projekt, ke spuštění v.</span><span class="sxs-lookup"><span data-stu-id="681b7-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="681b7-147">Musíte také zajistit ovládacího prvku přístupné pro testovací projekt sestavením (kompilace) ji.</span><span class="sxs-lookup"><span data-stu-id="681b7-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="681b7-148">V této části bude sestavení ovládacího prvku a otestovat ho ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="681b7-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="681b7-149">K sestavení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="681b7-149">To build your control</span></span>  
  
1.  <span data-ttu-id="681b7-150">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="681b7-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="681b7-151">Sestavení by měl být úspěšný bez chyby kompilátoru nebo upozornění.</span><span class="sxs-lookup"><span data-stu-id="681b7-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="681b7-152">Chcete-li vytvořit projekt testů</span><span class="sxs-lookup"><span data-stu-id="681b7-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="681b7-153">Na **souboru** nabídky, přejděte k **přidat** a potom klikněte na tlačítko **nový projekt** otevřít **přidat nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="681b7-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="681b7-154">Vyberte uzel projekty Visual Basic a klikněte na tlačítko **formulářová aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="681b7-154">Select the Visual Basic projects node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="681b7-155">V **název** zadejte `Test`.</span><span class="sxs-lookup"><span data-stu-id="681b7-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="681b7-156">V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="681b7-156">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
5.  <span data-ttu-id="681b7-157">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** vyberte uzel projektu testu **přidat odkaz** v místní nabídce zobrazíte  **Přidat odkaz na** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="681b7-157">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
6.  <span data-ttu-id="681b7-158">Klikněte na tlačítko **projekty** kartu.</span><span class="sxs-lookup"><span data-stu-id="681b7-158">Click the **Projects** tab.</span></span>  
  
7.  <span data-ttu-id="681b7-159">Klikněte na kartu **projekty**.</span><span class="sxs-lookup"><span data-stu-id="681b7-159">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="681b7-160">Vaše `ValueButtonLib` projektu budou uvedené v části **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="681b7-160">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="681b7-161">Dvakrát klikněte na projekt tak, aby do testovacího projektu přidejte odkaz.</span><span class="sxs-lookup"><span data-stu-id="681b7-161">Double-click the project to add the reference to the test project.</span></span>  
  
8.  <span data-ttu-id="681b7-162">V **Průzkumníku řešení** klikněte pravým tlačítkem na **testovací** a vyberte **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="681b7-162">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="681b7-163">Chcete-li přidat ovládací prvek do formuláře</span><span class="sxs-lookup"><span data-stu-id="681b7-163">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="681b7-164">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Form1.vb** a zvolte **Návrhář zobrazení** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="681b7-164">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="681b7-165">V **nástrojů**, klikněte na tlačítko **ValueButtonLib komponenty**.</span><span class="sxs-lookup"><span data-stu-id="681b7-165">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="681b7-166">Dvakrát klikněte na panel **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="681b7-166">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="681b7-167">A **ValueButton** se zobrazí ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="681b7-167">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="681b7-168">Klikněte pravým tlačítkem myši **ValueButton** a vyberte **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="681b7-168">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="681b7-169">V **vlastnosti** okna, podívejte se na vlastnosti tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="681b7-169">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="681b7-170">Všimněte si, že jsou shodné s vlastností vystavovaných třídami standardní tlačítko s tím rozdílem, že je další vlastnost `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="681b7-170">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="681b7-171">Nastavte `ButtonValue` vlastnost `5`.</span><span class="sxs-lookup"><span data-stu-id="681b7-171">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="681b7-172">Na **všechny formuláře Windows** kartě **nástrojů**, dvakrát klikněte na panel **popisek** přidáte <xref:System.Windows.Forms.Label> ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="681b7-172">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="681b7-173">Přemístěte popisek středu tvaru.</span><span class="sxs-lookup"><span data-stu-id="681b7-173">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="681b7-174">Dvakrát klikněte na panel `ValueButton1`.</span><span class="sxs-lookup"><span data-stu-id="681b7-174">Double-click `ValueButton1`.</span></span>  
  
     <span data-ttu-id="681b7-175">**Editor kódu** se otevře `ValueButton1_Click` událostí.</span><span class="sxs-lookup"><span data-stu-id="681b7-175">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="681b7-176">Zadejte následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="681b7-176">Type the following line of code.</span></span>  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. <span data-ttu-id="681b7-177">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **testovací**a zvolte **nastavit jako spouštěný projekt** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="681b7-177">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="681b7-178">Z **ladění** nabídce vyberte možnost **spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="681b7-178">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="681b7-179">`Form1` Zobrazí se.</span><span class="sxs-lookup"><span data-stu-id="681b7-179">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="681b7-180">Klikněte na tlačítko `Valuebutton1`.</span><span class="sxs-lookup"><span data-stu-id="681b7-180">Click `Valuebutton1`.</span></span>  
  
     <span data-ttu-id="681b7-181">Číslice "5" se zobrazí v `Label1`ukázku, který `ButtonValue` byla předána vlastnost zděděný ovládací prvek `Label1` prostřednictvím `ValueButton1_Click` metoda.</span><span class="sxs-lookup"><span data-stu-id="681b7-181">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="681b7-182">Proto váš `ValueButton` dědí všechny funkce standardní tlačítko Windows Forms ovládací prvek, ale zpřístupňuje další, vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="681b7-182">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="681b7-183">Viz také</span><span class="sxs-lookup"><span data-stu-id="681b7-183">See Also</span></span>  
 [<span data-ttu-id="681b7-184">Návod: Vytvoření složeného ovládacího prvku pomocí Visual Basicu</span><span class="sxs-lookup"><span data-stu-id="681b7-184">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="681b7-185">Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="681b7-185">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="681b7-186">Vývoj vlastních ovládacích prvků Windows Forms pomocí rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="681b7-186">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="681b7-187">Základní informace o dědičnosti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="681b7-187">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="681b7-188">Návody pro vytváření součástí</span><span class="sxs-lookup"><span data-stu-id="681b7-188">Component Authoring Walkthroughs</span></span>](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
