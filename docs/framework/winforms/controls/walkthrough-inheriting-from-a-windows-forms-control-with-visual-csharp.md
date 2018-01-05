---
title: "Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c28e41ad7c9e07dae150035e205e79b3d8cac84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="ff6d0-102">Návod: Dědění z ovládacího prvku Windows Forms pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="ff6d0-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span> #
<span data-ttu-id="ff6d0-103">S [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], můžete vytvořit výkonné vlastní ovládací prvky prostřednictvím *dědičnosti*.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-103">With [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="ff6d0-104">Prostřednictvím dědičnosti budete moci vytvořit ovládací prvky, které nezachovají vyplývajících funkce standardní ovládací prvky Windows Forms, ale také obsahovat vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="ff6d0-105">V tomto návodu vytvoříte jednoduchý zděděné ovládací prvek názvem `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="ff6d0-106">Toto tlačítko bude funkce dědit ze standardní Windows Forms <xref:System.Windows.Forms.Button> řízení a zveřejní vlastní vlastnost s názvem `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff6d0-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ff6d0-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ff6d0-109">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="ff6d0-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="ff6d0-110">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="ff6d0-110">Creating the Project</span></span>  
 <span data-ttu-id="ff6d0-111">Když vytvoříte nový projekt, aby bylo možné nastavit kořenový obor názvů, název sestavení a název projektu a zajistit, že součást výchozí bude ve správném oboru názvů zadejte její název.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="ff6d0-112">K vytvoření knihovny řízení ValueButtonLib a ValueButton ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="ff6d0-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="ff6d0-113">Na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu** otevřete **nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="ff6d0-114">Vyberte **knihovny ovládacích prvků Windows Forms** šablona projektu ze seznamu [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] projekty a typ `ValueButtonLib` v **název** pole.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-114">Select the **Windows Forms Control Library** project template from the list of [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] Projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="ff6d0-115">Název projektu `ValueButtonLib`, je také přiřazený k oboru názvů root ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="ff6d0-116">Kořenový obor názvů se použijí pro kvalifikaci názvy součásti v sestavení.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="ff6d0-117">Například, pokud dvě sestavení poskytují komponenty s názvem `ValueButton`, můžete zadat vaše `ValueButton` pomocí součásti `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="ff6d0-118">Další informace najdete v tématu [obory názvů](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="ff6d0-118">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>  
  
3.  <span data-ttu-id="ff6d0-119">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **UserControl1.cs**, zvolte **přejmenovat** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-119">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="ff6d0-120">Změňte název souboru `ValueButton.cs`.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-120">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="ff6d0-121">Klikněte **Ano** tlačítko po zobrazení dotazu, pokud chcete přejmenovat všechny odkazy na tento element kódu '`UserControl1`'.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-121">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>  
  
4.  <span data-ttu-id="ff6d0-122">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **ValueButton.cs** a vyberte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-122">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="ff6d0-123">Vyhledejte `class` řádku příkaz `public partial class ValueButton`a změnit typ, ze kterého tento ovládací prvek dědí z <xref:System.Windows.Forms.UserControl> k <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-123">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="ff6d0-124">To umožňuje vaší zděděné řídit dědění všechny funkce <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-124">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
6.  <span data-ttu-id="ff6d0-125">V **Průzkumníku řešení**, otevřete **ValueButton.cs** uzel k zobrazení souboru generovaném kódu **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-125">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="ff6d0-126">Otevřete tento soubor **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-126">Open this file in the **Code Editor**.</span></span>  
  
7.  <span data-ttu-id="ff6d0-127">Vyhledejte `InitializeComponent` metoda a odebrat řádek, který přiřazuje <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="ff6d0-128">Tato vlastnost neexistuje v <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="ff6d0-129">Z **soubor** nabídce zvolte **Uložit vše** k uložení projektu.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ff6d0-130">Vizuální návrhář již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-130">A visual designer is no longer available.</span></span> <span data-ttu-id="ff6d0-131">Protože <xref:System.Windows.Forms.Button> ovládací prvek provádí vlastní Malování, nebudete moci upravit její vzhled v návrháři.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="ff6d0-132">Jeho vizuální znázornění budou přesně stejné jako příkaz, který dědí z třídy (tedy <xref:System.Windows.Forms.Button>) není-li upravit v kódu.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="ff6d0-133">Součásti, které mají žádné elementy uživatelského rozhraní, můžete přesto přidat na plochu návrháře.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="ff6d0-134">Přidání vlastnosti do vlastního zděděné ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ff6d0-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="ff6d0-135">Je možné použití zděděné ovládacích prvků Windows Forms vytváření ovládacích prvků, které jsou identické v vzhledu a chování standardní ovládací prvky Windows Forms, ale vystavit vlastní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="ff6d0-136">V této části přidáte vlastnost s názvem `ButtonValue` do vašeho ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="ff6d0-137">Chcete-li přidat hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ff6d0-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="ff6d0-138">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **ValueButton.cs**a potom klikněte na **kód zobrazení** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-138">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="ff6d0-139">Vyhledejte `class` příkaz.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-139">Locate the `class` statement.</span></span> <span data-ttu-id="ff6d0-140">Ihned po `{`, zadejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="ff6d0-140">Immediately after the `{`, type the following code:</span></span>  
  
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
  
     <span data-ttu-id="ff6d0-141">Tento kód nastaví metody, pomocí kterého `ButtonValue` vlastnost uložena a následně načtena.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="ff6d0-142">`get` Příkaz nastaví hodnotu, vrátí hodnotu, která v soukromé proměnné je uloženo `varValue`a `set` příkaz nastaví hodnotu soukromé proměnné pomocí `value` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-142">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>  
  
3.  <span data-ttu-id="ff6d0-143">Z **soubor** nabídce zvolte **Uložit vše** k uložení projektu.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="ff6d0-144">Testování vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ff6d0-144">Testing Your Control</span></span>  
 <span data-ttu-id="ff6d0-145">Ovládací prvky nejsou samostatné projekty; musí být hostované v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="ff6d0-146">Chcete-li otestovat vlastní ovládací prvek, je nutné zadat pro něj spustit v testovacího projektu.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="ff6d0-147">Je nutné provést kontrolu nad přístupné pro projekt test podle budovy (kompilace) ho.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="ff6d0-148">V této části bude sestavovat vlastní ovládací prvek a otestovat ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="ff6d0-149">K vytvoření vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ff6d0-149">To build your control</span></span>  
  
1.  <span data-ttu-id="ff6d0-150">Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="ff6d0-151">Sestavení by měl být úspěšné bez chyb kompilátoru a upozornění.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="ff6d0-152">K vytvoření projektu testů</span><span class="sxs-lookup"><span data-stu-id="ff6d0-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="ff6d0-153">Na **soubor** nabídky, přejděte na příkaz **přidat** a pak klikněte na **nový projekt** otevřete **přidat nový projekt** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="ff6d0-154">Vyberte **Windows** uzlu, ybrat **Visual C#** uzel a klikněte na tlačítko **formulářové aplikace Windows**.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-154">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="ff6d0-155">V **název** zadejte `Test`.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="ff6d0-156">V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** vyberte uzel pro váš projekt test **přidat odkaz na** z místní nabídky k zobrazení  **Přidat odkaz** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-156">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="ff6d0-157">Klikněte na kartu s názvem bez přípony **projekty**.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-157">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="ff6d0-158">Vaše `ValueButtonLib` projektu, zobrazí se v části **název projektu**.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-158">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="ff6d0-159">Dvakrát klikněte na projekt se přidat odkaz na projekt test.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-159">Double-click the project to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="ff6d0-160">V **Průzkumníku řešení** klikněte pravým tlačítkem na **Test** a vyberte **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-160">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="ff6d0-161">Chcete-li přidat vlastní ovládací prvek formuláře</span><span class="sxs-lookup"><span data-stu-id="ff6d0-161">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="ff6d0-162">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Form1.cs** a zvolte **Návrhář zobrazení** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-162">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="ff6d0-163">V **sada nástrojů**, klikněte na tlačítko **ValueButtonLib součásti**.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-163">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="ff6d0-164">Klikněte dvakrát na **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-164">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="ff6d0-165">A **ValueButton** se zobrazí na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-165">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="ff6d0-166">Klikněte pravým tlačítkem myši **ValueButton** a vyberte **vlastnosti** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-166">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="ff6d0-167">V **vlastnosti** okno, podívejte se na vlastnosti tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-167">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="ff6d0-168">Všimněte si, jestli se shodují na vlastnosti vystavené standardní tlačítko s tím rozdílem, že další vlastnost, `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-168">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="ff6d0-169">Nastavte `ButtonValue` vlastnost `5`.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-169">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="ff6d0-170">V **všechny formuláře Windows** kartě **sada nástrojů**, dvakrát klikněte na **popisek** přidat <xref:System.Windows.Forms.Label> ovládacího prvku do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-170">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="ff6d0-171">Popisek přemístěte na střed tvaru.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-171">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="ff6d0-172">Klikněte dvakrát na `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-172">Double-click `valueButton1`.</span></span>  
  
     <span data-ttu-id="ff6d0-173">**Editor kódu** se otevře `valueButton1_Click` událostí.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-173">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="ff6d0-174">Vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-174">Insert the following line of code.</span></span>  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. <span data-ttu-id="ff6d0-175">V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Test**a zvolte **nastavit jako spouštěný projekt** z místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-175">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="ff6d0-176">Z **ladění** nabídce vyberte možnost **spustit ladění**.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-176">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="ff6d0-177">`Form1`Zobrazí se.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-177">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="ff6d0-178">Klikněte na tlačítko `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-178">Click `valueButton1`.</span></span>  
  
     <span data-ttu-id="ff6d0-179">Číslo "5" se zobrazí v `label1`, představujících, `ButtonValue` byla předána vlastnost zděděné ovládacího prvku `label1` prostřednictvím `valueButton1_Click` metoda.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-179">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="ff6d0-180">Proto vaše `ValueButton` řízení dědí všechny funkce standardní tlačítka Windows Forms, ale zveřejňuje o další, vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ff6d0-180">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6d0-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff6d0-181">See Also</span></span>  
 [<span data-ttu-id="ff6d0-182">Programování s komponentami</span><span class="sxs-lookup"><span data-stu-id="ff6d0-182">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="ff6d0-183">Součást pro vytváření obsahu návody</span><span class="sxs-lookup"><span data-stu-id="ff6d0-183">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [<span data-ttu-id="ff6d0-184">Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů</span><span class="sxs-lookup"><span data-stu-id="ff6d0-184">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="ff6d0-185">Návod: Vytvoření složeného ovládacího prvku pomocí Visual C#</span><span class="sxs-lookup"><span data-stu-id="ff6d0-185">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
