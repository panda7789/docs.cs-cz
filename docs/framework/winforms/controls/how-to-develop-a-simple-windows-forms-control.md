---
title: Vývoj jednoduchého ovládacího prvku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 5383cee5358dbd260fc6c023d3db607da6b10ea4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742254"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="fd571-102">Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fd571-102">How to: Develop a Simple Windows Forms Control</span></span>

<span data-ttu-id="fd571-103">V této části se seznámíte se základními kroky při vytváření vlastního ovládacího prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fd571-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="fd571-104">Jednoduchý ovládací prvek vyvinutý v tomto návodu umožňuje změnit zarovnání jeho <xref:System.Windows.Forms.Control.Text%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="fd571-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="fd571-105">Nevyvolává ani nezpracovává události.</span><span class="sxs-lookup"><span data-stu-id="fd571-105">It does not raise or handle events.</span></span>

### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="fd571-106">Vytvoření jednoduchého vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="fd571-106">To create a simple custom control</span></span>

1. <span data-ttu-id="fd571-107">Definujte třídu, která je odvozena z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd571-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>

    ```vb
    Public Class FirstControl
       Inherits Control

    End Class
    ```

    ```csharp
    public class FirstControl:Control {}
    ```

2. <span data-ttu-id="fd571-108">Definujte vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fd571-108">Define properties.</span></span> <span data-ttu-id="fd571-109">(Nemusíte definovat vlastnosti, protože ovládací prvek dědí mnoho vlastností z <xref:System.Windows.Forms.Control> třídy, ale většina vlastních ovládacích prvků obecně definuje další vlastnosti.) Následující fragment kódu definuje vlastnost s názvem `TextAlignment`, kterou `FirstControl` používá k formátování zobrazení vlastnosti <xref:System.Windows.Forms.Control.Text%2A> zděděné ze <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="fd571-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="fd571-110">Další informace o definování vlastností najdete v tématu [Přehled vlastností](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).</span><span class="sxs-lookup"><span data-stu-id="fd571-110">For more information about defining properties, see [Properties Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).</span></span>

     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]

     <span data-ttu-id="fd571-111">Když nastavíte vlastnost, která změní vizuální zobrazení ovládacího prvku, je nutné vyvolat metodu <xref:System.Windows.Forms.Control.Invalidate%2A> pro překreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fd571-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="fd571-112"><xref:System.Windows.Forms.Control.Invalidate%2A> je definována v základní třídě <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="fd571-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>

3. <span data-ttu-id="fd571-113">Přepsat chráněnou <xref:System.Windows.Forms.Control.OnPaint%2A> metodu zděděnou z <xref:System.Windows.Forms.Control> a poskytnout tak pro svůj ovládací prvek logiku vykreslování.</span><span class="sxs-lookup"><span data-stu-id="fd571-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="fd571-114">Pokud nepřepisujete <xref:System.Windows.Forms.Control.OnPaint%2A>, ovládací prvek nebude moci nakreslit sám sebe.</span><span class="sxs-lookup"><span data-stu-id="fd571-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="fd571-115">V následujícím fragmentu kódu <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda zobrazuje vlastnost <xref:System.Windows.Forms.Control.Text%2A> zděděná z <xref:System.Windows.Forms.Control> s zarovnáním zadaným v poli `alignmentValue`.</span><span class="sxs-lookup"><span data-stu-id="fd571-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]

4. <span data-ttu-id="fd571-116">Zadejte atributy pro svůj ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fd571-116">Provide attributes for your control.</span></span> <span data-ttu-id="fd571-117">Atributy umožňují vizuálnímu návrháři zobrazit ovládací prvek a jeho vlastnosti a události odpovídajícím způsobem v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="fd571-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="fd571-118">Následující fragment kódu používá atributy na vlastnost `TextAlignment`.</span><span class="sxs-lookup"><span data-stu-id="fd571-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="fd571-119">V návrháři, jako je například Visual Studio, atribut <xref:System.ComponentModel.CategoryAttribute.Category%2A> (zobrazený v fragmentu kódu) způsobí, že se vlastnost zobrazí v rámci logické kategorie.</span><span class="sxs-lookup"><span data-stu-id="fd571-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="fd571-120">Atribut <xref:System.ComponentModel.DescriptionAttribute.Description%2A> způsobí, že se popisný řetězec zobrazí v dolní části okna **vlastnosti** , když je vybrána vlastnost `TextAlignment`.</span><span class="sxs-lookup"><span data-stu-id="fd571-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="fd571-121">Další informace o atributech naleznete v tématu [atributy doby návrhu pro součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="fd571-121">For more information about attributes, see [Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).</span></span>

     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]

5. <span data-ttu-id="fd571-122">volitelné Poskytněte prostředky pro váš ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fd571-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="fd571-123">Můžete poskytnout prostředek, jako je rastrový obrázek, pro váš ovládací prvek pomocí možnosti kompilátoru (`/res` pro C#) k balíčku prostředků s vaším ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="fd571-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="fd571-124">V době spuštění lze prostředek načíst pomocí metod třídy <xref:System.Resources.ResourceManager>.</span><span class="sxs-lookup"><span data-stu-id="fd571-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="fd571-125">Další informace o vytváření a používání prostředků najdete v tématu [prostředky v aplikacích klasické pracovní plochy](../../resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="fd571-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../resources/index.md).</span></span>

6. <span data-ttu-id="fd571-126">Zkompilujte a nasaďte svůj ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="fd571-126">Compile and deploy your control.</span></span> <span data-ttu-id="fd571-127">Pro zkompilování a nasazení `FirstControl,` proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="fd571-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>

    1. <span data-ttu-id="fd571-128">Uložte kód v následující ukázce do zdrojového souboru (například FirstControl.cs nebo FirstControl. vb).</span><span class="sxs-lookup"><span data-stu-id="fd571-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>

    2. <span data-ttu-id="fd571-129">Zkompilujte zdrojový kód do sestavení a uložte ho do adresáře vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd571-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="fd571-130">Chcete-li to provést, spusťte následující příkaz z adresáře, který obsahuje zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="fd571-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>

        ```console
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb
        ```

        ```console
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs
        ```

         <span data-ttu-id="fd571-131">Možnost kompilátoru `/t:library` instruuje kompilátor, že sestavení, které vytváříte, je knihovna (a ne spustitelný soubor).</span><span class="sxs-lookup"><span data-stu-id="fd571-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="fd571-132">Možnost `/out` Určuje cestu a název sestavení.</span><span class="sxs-lookup"><span data-stu-id="fd571-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="fd571-133">Možnost`/r` poskytuje název sestavení, na které odkazuje váš kód.</span><span class="sxs-lookup"><span data-stu-id="fd571-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="fd571-134">V tomto příkladu vytvoříte soukromé sestavení, které může používat pouze vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd571-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="fd571-135">Proto je nutné jej uložit v adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd571-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="fd571-136">Další informace o balení a nasazení ovládacího prvku pro distribuci najdete v tématu [nasazení](../../deployment/index.md).</span><span class="sxs-lookup"><span data-stu-id="fd571-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../deployment/index.md).</span></span>

<span data-ttu-id="fd571-137">Následující příklad ukazuje kód pro `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="fd571-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="fd571-138">Ovládací prvek je uzavřený v oboru názvů `CustomWinControls`.</span><span class="sxs-lookup"><span data-stu-id="fd571-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="fd571-139">Obor názvů poskytuje logické seskupení souvisejících typů.</span><span class="sxs-lookup"><span data-stu-id="fd571-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="fd571-140">Svůj ovládací prvek lze vytvořit v novém nebo existujícím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fd571-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="fd571-141">V C#, deklarace `using` (v Visual Basic, `Imports`) umožňuje k typům pøístup z oboru názvů bez použití plně kvalifikovaného názvu typu.</span><span class="sxs-lookup"><span data-stu-id="fd571-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="fd571-142">V následujícím příkladu deklarace `using` umožňuje kódu přistupovat ke třídě <xref:System.Windows.Forms.Control> z <xref:System.Windows.Forms?displayProperty=nameWithType>, jako jednoduše <xref:System.Windows.Forms.Control> namísto použití plně kvalifikovaného názvu <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd571-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>

[!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
[!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]

## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="fd571-143">Používání vlastního ovládacího prvku na formuláři</span><span class="sxs-lookup"><span data-stu-id="fd571-143">Using the Custom Control on a Form</span></span>

<span data-ttu-id="fd571-144">Následující příklad ukazuje jednoduchý formulář, který používá `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="fd571-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="fd571-145">Vytvoří tři instance `FirstControl`, každé s jinou hodnotou pro vlastnost `TextAlignment`.</span><span class="sxs-lookup"><span data-stu-id="fd571-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>

#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="fd571-146">Pro zkompilování a spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="fd571-146">To compile and run this sample</span></span>

1. <span data-ttu-id="fd571-147">Uložte kód v následujícím příkladu do zdrojového souboru (SimpleForm.cs nebo SimpleForms. vb).</span><span class="sxs-lookup"><span data-stu-id="fd571-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>

2. <span data-ttu-id="fd571-148">Zkompilujte zdrojový kód do spustitelného sestavení spuštěním následujícího příkazu z adresáře, který obsahuje zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="fd571-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>

    ```console
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb
    ```

    ```console
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs
    ```

     <span data-ttu-id="fd571-149">CustomWinControls. dll je sestavení, které obsahuje třídu `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="fd571-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="fd571-150">Toto sestavení musí být ve stejném adresáři jako zdrojový soubor pro formulář, který k němu přistupuje (SimpleForm.cs nebo SimpleForms. vb).</span><span class="sxs-lookup"><span data-stu-id="fd571-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>

3. <span data-ttu-id="fd571-151">Spusťte SimpleForm. exe pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="fd571-151">Execute SimpleForm.exe using the following command.</span></span>

    ```console
    SimpleForm
    ```

[!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
[!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]

## <a name="see-also"></a><span data-ttu-id="fd571-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd571-152">See also</span></span>

- [<span data-ttu-id="fd571-153">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fd571-153">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="fd571-154">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fd571-154">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
