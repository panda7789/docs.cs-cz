---
title: "Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 941bcb3d69a80ff415cb76d69414ad25e3a8c76d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="55dbc-102">Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="55dbc-102">How to: Develop a Simple Windows Forms Control</span></span>
<span data-ttu-id="55dbc-103">Tato část vás provede procesem klíčové kroky pro vytvoření vlastního ovládacího prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="55dbc-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="55dbc-104">Jednoduché ovládací prvek vyvinuté v tomto návodu umožňuje zarovnání jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost změnit.</span><span class="sxs-lookup"><span data-stu-id="55dbc-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="55dbc-105">Nebudou vyvolat a zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="55dbc-105">It does not raise or handle events.</span></span>  
  
### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="55dbc-106">Chcete-li vytvořit jednoduché vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="55dbc-106">To create a simple custom control</span></span>  
  
1.  <span data-ttu-id="55dbc-107">Definice třídy, která je odvozena z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="55dbc-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control{}  
    ```  
  
2.  <span data-ttu-id="55dbc-108">Definování vlastností.</span><span class="sxs-lookup"><span data-stu-id="55dbc-108">Define properties.</span></span> <span data-ttu-id="55dbc-109">(Není nutné definovat vlastnosti, protože dědí mnoho vlastnosti z ovládacího prvku <xref:System.Windows.Forms.Control> třídy, ale většina vlastní ovládací prvky obecně definovat další vlastnosti.) Následující fragment kódu definuje vlastnost s názvem `TextAlignment` , `FirstControl` používá k formátování zobrazení <xref:System.Windows.Forms.Control.Text%2A> vlastnost zděděna od <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="55dbc-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="55dbc-110">Další informace o definování vlastností v tématu [přehled vlastností](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="55dbc-110">For more information about defining properties, see [Properties Overview](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     <span data-ttu-id="55dbc-111">Když nastavíte vlastnost, která určuje visual zobrazení ovládacího prvku, je nutné vyvolat <xref:System.Windows.Forms.Control.Invalidate%2A> metodu ho překreslit ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="55dbc-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="55dbc-112"><xref:System.Windows.Forms.Control.Invalidate%2A>je definována v základní třídě <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="55dbc-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>  
  
3.  <span data-ttu-id="55dbc-113">Přepsání chráněného <xref:System.Windows.Forms.Control.OnPaint%2A> metoda zděděno z <xref:System.Windows.Forms.Control> zajistit logiku vykreslování vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="55dbc-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="55dbc-114">Pokud není přepíšete <xref:System.Windows.Forms.Control.OnPaint%2A>, vlastní ovládací prvek nebudou mít k vykreslení sám sebe.</span><span class="sxs-lookup"><span data-stu-id="55dbc-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="55dbc-115">V následující fragment kódu <xref:System.Windows.Forms.Control.OnPaint%2A> metoda zobrazí <xref:System.Windows.Forms.Control.Text%2A> vlastnost zděděna od <xref:System.Windows.Forms.Control> s zarovnání určeného `alignmentValue` pole.</span><span class="sxs-lookup"><span data-stu-id="55dbc-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  <span data-ttu-id="55dbc-116">Zadejte atributy pro vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="55dbc-116">Provide attributes for your control.</span></span> <span data-ttu-id="55dbc-117">Atributy povolit vizuálního návrháře správně zobrazit vlastní ovládací prvek a jeho vlastnosti a události v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="55dbc-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="55dbc-118">Následující fragment kódu se vztahuje atributy, které mají `TextAlignment` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="55dbc-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="55dbc-119">V Návrháři třeba v sadě Visual Studio <xref:System.ComponentModel.CategoryAttribute.Category%2A> atribut (zobrazené ve fragmentu kódu) způsobí, že vlastnost, který se má zobrazit v rámci logické kategorie.</span><span class="sxs-lookup"><span data-stu-id="55dbc-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="55dbc-120"><xref:System.ComponentModel.DescriptionAttribute.Description%2A> Atribut způsobuje popisný řetězec, který se má zobrazit v dolní části **vlastnosti** okno při `TextAlignment` vlastnost vybrána.</span><span class="sxs-lookup"><span data-stu-id="55dbc-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="55dbc-121">Další informace o atributech najdete v tématu [atributy doby návrhu pro součásti](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span><span class="sxs-lookup"><span data-stu-id="55dbc-121">For more information about attributes, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  <span data-ttu-id="55dbc-122">(volitelné) Zadejte prostředky pro vaše ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="55dbc-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="55dbc-123">Prostředek, jako je například rastrový obrázek, můžete zadat pro ovládací prvek pomocí možnosti kompilátoru (`/res` pro jazyk C#) k prostředkům balíček pomocí vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="55dbc-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="55dbc-124">V době běhu prostředku se dá načíst pomocí metody <xref:System.Resources.ResourceManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="55dbc-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="55dbc-125">Další informace o vytváření a používání prostředků najdete v tématu [prostředků v aplikacích plochy](../../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="55dbc-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../../../docs/framework/resources/index.md).</span></span>  
  
6.  <span data-ttu-id="55dbc-126">Kompilace a nasadit vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="55dbc-126">Compile and deploy your control.</span></span> <span data-ttu-id="55dbc-127">Pro zkompilování a nasadit `FirstControl,` provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="55dbc-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>  
  
    1.  <span data-ttu-id="55dbc-128">Uložte kód v následující ukázce ke zdrojovému souboru (například FirstControl.cs nebo FirstControl.vb).</span><span class="sxs-lookup"><span data-stu-id="55dbc-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>  
  
    2.  <span data-ttu-id="55dbc-129">Kompilace zdrojového kódu do sestavení a uložte ho do adresáře vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="55dbc-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="55dbc-130">K tomu, že spustíte následující příkaz z adresáře, který obsahuje zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="55dbc-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>  
  
        ```vb  
        vbc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```csharp  
        csc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.cs  
        ```  
  
         <span data-ttu-id="55dbc-131">`/t:library` – Možnost kompilátoru říká kompilátoru, že je sestavení, kterou vytváříte knihovny (a ne spustitelný soubor).</span><span class="sxs-lookup"><span data-stu-id="55dbc-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="55dbc-132">`/out` Možnost určuje cestu a název sestavení.</span><span class="sxs-lookup"><span data-stu-id="55dbc-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="55dbc-133">`/r` Možnost poskytuje název sestavení, které jsou odkazovány pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="55dbc-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="55dbc-134">V tomto příkladu vytvoříte privátní sestavení, které můžete použít jenom vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="55dbc-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="55dbc-135">Proto je nutné uložit v adresáři vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="55dbc-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="55dbc-136">Další informace o balení a nasazení ovládacího prvku pro distribuci najdete v tématu [nasazení](../../../../docs/framework/deployment/index.md).</span><span class="sxs-lookup"><span data-stu-id="55dbc-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../../../docs/framework/deployment/index.md).</span></span>  
  
 <span data-ttu-id="55dbc-137">Následující příklad ukazuje kód pro `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="55dbc-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="55dbc-138">Ovládací prvek je uzavřena v oboru názvů `CustomWinControls`.</span><span class="sxs-lookup"><span data-stu-id="55dbc-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="55dbc-139">Obor názvů poskytuje logické seskupení souvisejících typů.</span><span class="sxs-lookup"><span data-stu-id="55dbc-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="55dbc-140">Můžete vytvořit vlastní ovládací prvek v nových nebo existujících oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="55dbc-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="55dbc-141">V jazyce C# `using` deklarace (v jazyce Visual Basic `Imports`) umožňuje typům přístupná z oboru názvů bez použití plně kvalifikovaný název typu.</span><span class="sxs-lookup"><span data-stu-id="55dbc-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="55dbc-142">V následujícím příkladu `using` deklarace umožňuje kód pro přístup k třídě <xref:System.Windows.Forms.Control> z <xref:System.Windows.Forms?displayProperty=nameWithType> jako jednoduše <xref:System.Windows.Forms.Control> místo nutnosti použít plně kvalifikovaný název <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="55dbc-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="55dbc-143">Pomocí vlastního ovládacího prvku ve formuláři</span><span class="sxs-lookup"><span data-stu-id="55dbc-143">Using the Custom Control on a Form</span></span>  
 <span data-ttu-id="55dbc-144">Následující příklad ukazuje jednoduchý formulář, který používá `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="55dbc-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="55dbc-145">Vytvoří tři instance `FirstControl`, každý s jinou hodnotou `TextAlignment` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="55dbc-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>  
  
#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="55dbc-146">Pro zkompilování a spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="55dbc-146">To compile and run this sample</span></span>  
  
1.  <span data-ttu-id="55dbc-147">Uložte kód v následujícím příkladu do zdrojového souboru (SimpleForm.cs nebo SimpleForms.vb).</span><span class="sxs-lookup"><span data-stu-id="55dbc-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
2.  <span data-ttu-id="55dbc-148">Kompilace zdrojový kód do spustitelného souboru sestavení tak, že spustíte následující příkaz z adresáře, který obsahuje zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="55dbc-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>  
  
    ```vb  
    vbc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```csharp  
    csc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     <span data-ttu-id="55dbc-149">CustomWinControls.dll je sestavení obsahující třídu `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="55dbc-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="55dbc-150">Toto sestavení musí být ve stejném adresáři jako zdrojový soubor pro daný formulář, který přistupuje k (SimpleForm.cs nebo SimpleForms.vb).</span><span class="sxs-lookup"><span data-stu-id="55dbc-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
3.  <span data-ttu-id="55dbc-151">Spusťte SimpleForm.exe pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="55dbc-151">Execute SimpleForm.exe using the following command.</span></span>  
  
    ```  
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="55dbc-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="55dbc-152">See Also</span></span>  
 [<span data-ttu-id="55dbc-153">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="55dbc-153">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="55dbc-154">Události v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="55dbc-154">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
