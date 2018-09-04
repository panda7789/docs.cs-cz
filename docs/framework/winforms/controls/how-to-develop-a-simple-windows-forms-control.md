---
title: 'Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 07a4de944e36b0be1a6196d08df33c4f3ab24bcc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560129"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="74af7-102">Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74af7-102">How to: Develop a Simple Windows Forms Control</span></span>
<span data-ttu-id="74af7-103">Tato část vás provede základní kroky pro vytváření vlastního ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="74af7-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="74af7-104">Jednoduché ovládací prvek vytvořili v tomto návodu umožňuje zarovnání jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost změnit.</span><span class="sxs-lookup"><span data-stu-id="74af7-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="74af7-105">Nelze vyvolat nebo zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="74af7-105">It does not raise or handle events.</span></span>  
  
### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="74af7-106">Chcete-li vytvořit jednoduché vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="74af7-106">To create a simple custom control</span></span>  
  
1.  <span data-ttu-id="74af7-107">Definujte třídu, která je odvozena z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="74af7-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control {}  
    ```  
  
2.  <span data-ttu-id="74af7-108">Definujte vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="74af7-108">Define properties.</span></span> <span data-ttu-id="74af7-109">(Není nutné definovat vlastnosti, protože dědí mnoho vlastnosti z ovládacího prvku <xref:System.Windows.Forms.Control> třídy, ale většina vlastních ovládacích prvků obecně definovat další vlastnosti.) Následující fragment kódu definuje vlastnost s názvem `TextAlignment` , který `FirstControl` používá k formátování zobrazení <xref:System.Windows.Forms.Control.Text%2A> dědí vlastnosti z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="74af7-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="74af7-110">Další informace o definování vlastností najdete v tématu [přehled vlastností](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="74af7-110">For more information about defining properties, see [Properties Overview](https://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     <span data-ttu-id="74af7-111">Když nastavíte vlastnost, která změní visual zobrazení ovládacího prvku, je nutné vyvolat <xref:System.Windows.Forms.Control.Invalidate%2A> metoda překreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="74af7-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="74af7-112"><xref:System.Windows.Forms.Control.Invalidate%2A> je definován v základní třídě <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="74af7-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>  
  
3.  <span data-ttu-id="74af7-113">Přepsat chráněnou <xref:System.Windows.Forms.Control.OnPaint%2A> metody zděděné z <xref:System.Windows.Forms.Control> k poskytování logiky vykreslování do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="74af7-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="74af7-114">Pokud jste nesmí být přepsána <xref:System.Windows.Forms.Control.OnPaint%2A>, nebude možné vykreslit ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="74af7-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="74af7-115">V následující fragment kódu <xref:System.Windows.Forms.Control.OnPaint%2A> metoda zobrazí <xref:System.Windows.Forms.Control.Text%2A> dědí vlastnosti z <xref:System.Windows.Forms.Control> se zarovnáním určené `alignmentValue` pole.</span><span class="sxs-lookup"><span data-stu-id="74af7-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  <span data-ttu-id="74af7-116">Zadejte atributy pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="74af7-116">Provide attributes for your control.</span></span> <span data-ttu-id="74af7-117">Atributy umožňují vizuálního návrháře pro zobrazení ovládacího prvku a jeho vlastnosti a události odpovídajícím způsobem v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="74af7-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="74af7-118">Následující fragment kódu se vztahuje atributů, které mají `TextAlignment` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="74af7-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="74af7-119">V návrháři, jako je Visual Studio <xref:System.ComponentModel.CategoryAttribute.Category%2A> atribut (viz část kódu) způsobí, že vlastnost má být zobrazen v rámci logických kategorií.</span><span class="sxs-lookup"><span data-stu-id="74af7-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="74af7-120"><xref:System.ComponentModel.DescriptionAttribute.Description%2A> Atribut způsobí, že popisný řetězec, který se zobrazí v dolní části **vlastnosti** okno při `TextAlignment` vybrána vlastnost.</span><span class="sxs-lookup"><span data-stu-id="74af7-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="74af7-121">Další informace o atributech najdete v tématu [atributy doby návrhu pro komponenty](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span><span class="sxs-lookup"><span data-stu-id="74af7-121">For more information about attributes, see [Design-Time Attributes for Components](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  <span data-ttu-id="74af7-122">(volitelné) Poskytněte zdroje informací pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="74af7-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="74af7-123">Prostředek, jako je například rastrový obrázek, můžete zadat pro ovládací prvek pomocí možnosti kompilátoru (`/res` pro jazyk C#) pro balíček prostředků pomocí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="74af7-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="74af7-124">V době běhu, prostředek se dá načíst pomocí metody <xref:System.Resources.ResourceManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="74af7-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="74af7-125">Další informace o vytváření a používání prostředků najdete v článku [prostředky v desktopových aplikací](../../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="74af7-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../../../docs/framework/resources/index.md).</span></span>  
  
6.  <span data-ttu-id="74af7-126">Zkompilujte a nasaďte svůj ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="74af7-126">Compile and deploy your control.</span></span> <span data-ttu-id="74af7-127">Ke kompilaci a nasazení `FirstControl,` proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="74af7-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>  
  
    1.  <span data-ttu-id="74af7-128">Uložte kód v následujícím příkladu do zdrojového souboru (například FirstControl.cs nebo FirstControl.vb).</span><span class="sxs-lookup"><span data-stu-id="74af7-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>  
  
    2.  <span data-ttu-id="74af7-129">Zdrojový kód zkompilovat do sestavení a uložte ho v adresáři vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="74af7-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="74af7-130">K tomu, že spustíte následující příkaz z adresáře, který obsahuje zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="74af7-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>  
  
        ```console  
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```console 
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs  
        ```  
  
         <span data-ttu-id="74af7-131">`/t:library` – Možnost kompilátoru instruuje kompilátor, že je sestavení při vytváření knihovny (a ne spustitelného souboru).</span><span class="sxs-lookup"><span data-stu-id="74af7-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="74af7-132">`/out` Možnost určuje cestu a název sestavení.</span><span class="sxs-lookup"><span data-stu-id="74af7-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="74af7-133">`/r` Možnost poskytuje název sestavení, na které odkazuje váš kód.</span><span class="sxs-lookup"><span data-stu-id="74af7-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="74af7-134">V tomto příkladu vytvoříte privátní sestavení, které můžete použít jenom vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="74af7-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="74af7-135">Proto budete muset uložit v adresáři vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="74af7-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="74af7-136">Další informace o vytváření balíčků a nasazení ovládacího prvku pro distribuci, naleznete v tématu [nasazení](../../../../docs/framework/deployment/index.md).</span><span class="sxs-lookup"><span data-stu-id="74af7-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../../../docs/framework/deployment/index.md).</span></span>  
  
 <span data-ttu-id="74af7-137">Následující příklad ukazuje kód pro `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="74af7-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="74af7-138">Ovládací prvek je uzavřena v oboru názvů `CustomWinControls`.</span><span class="sxs-lookup"><span data-stu-id="74af7-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="74af7-139">Obor názvů poskytuje logické seskupení souvisejících typů.</span><span class="sxs-lookup"><span data-stu-id="74af7-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="74af7-140">Můžete vytvořit ovládací prvek v nové nebo existující obor názvů.</span><span class="sxs-lookup"><span data-stu-id="74af7-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="74af7-141">V jazyce C# `using` deklarace (v jazyce Visual Basic `Imports`) umožňuje typů přístupný z oboru názvů bez použití plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="74af7-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="74af7-142">V následujícím příkladu `using` deklarace umožňuje kódu ke třídě přistupovat <xref:System.Windows.Forms.Control> z <xref:System.Windows.Forms?displayProperty=nameWithType> stručně <xref:System.Windows.Forms.Control> místo nutnosti použít plně kvalifikovaný název <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="74af7-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="74af7-143">Použití vlastního ovládacího prvku ve formuláři</span><span class="sxs-lookup"><span data-stu-id="74af7-143">Using the Custom Control on a Form</span></span>  
 <span data-ttu-id="74af7-144">Následující příklad ukazuje jednoduchý formulář, který používá `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="74af7-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="74af7-145">Vytvoří tři instance `FirstControl`, každý s jinou hodnotou `TextAlignment` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="74af7-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>  
  
#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="74af7-146">Kompilace a spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="74af7-146">To compile and run this sample</span></span>  
  
1.  <span data-ttu-id="74af7-147">Uložte kód v následujícím příkladu do zdrojového souboru (SimpleForm.cs nebo SimpleForms.vb).</span><span class="sxs-lookup"><span data-stu-id="74af7-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
2.  <span data-ttu-id="74af7-148">Spuštěním následujícího příkazu z adresáře, který obsahuje zdrojový soubor Zkompilujte zdrojový kód do spustitelného souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="74af7-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>  
  
    ```console  
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```console 
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     <span data-ttu-id="74af7-149">CustomWinControls.dll je sestavení, které obsahuje třídu `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="74af7-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="74af7-150">Toto sestavení musí být ve stejném adresáři jako zdrojový soubor pro formulář k přístupu (SimpleForm.cs nebo SimpleForms.vb).</span><span class="sxs-lookup"><span data-stu-id="74af7-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
3.  <span data-ttu-id="74af7-151">Spusťte SimpleForm.exe pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="74af7-151">Execute SimpleForm.exe using the following command.</span></span>  
  
    ```console
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="74af7-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="74af7-152">See Also</span></span>  
 [<span data-ttu-id="74af7-153">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74af7-153">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="74af7-154">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74af7-154">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
