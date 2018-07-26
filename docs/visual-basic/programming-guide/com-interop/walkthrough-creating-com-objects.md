---
title: 'Návod: Vytváření objektů modelu COM pomocí jazyka Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: caf0a071d65746f1027052e648ade538d62dc4bb
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245684"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="6c502-102">Návod: Vytváření objektů modelu COM pomocí jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6c502-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="6c502-103">Při vytváření nové aplikace nebo komponenty, je nejlepší vytvořit sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c502-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="6c502-104">Ale jazyka Visual Basic také umožňuje snadno vystavit součásti rozhraní .NET Framework do modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6c502-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="6c502-105">To umožňuje poskytovat nové součásti pro starší aplikace sad, které vyžadují komponenty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6c502-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="6c502-106">Tento návod ukazuje, jak pomocí jazyka Visual Basic k vystavení [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objekty jako objekty modelu COM, s i bez šablony třídy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6c502-106">This walkthrough demonstrates how to use Visual Basic to expose [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="6c502-107">Nejjednodušší způsob, jak vystavit objekty modelu COM je pomocí šablony třídy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6c502-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="6c502-108">Šablona třídy modelu COM vytvoří novou třídu a pak nakonfiguruje projekt na vrstvě třídy a vzájemná funkční spolupráce jako objekt modelu COM vygeneruje a zaregistruje ho s operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="6c502-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c502-109">I když můžete také zpřístupní třídu vytvořené v jazyce Visual Basic jako objekt modelu COM pro nespravovaný kód, který použijete, není objekt modelu COM true a nelze použít v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6c502-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="6c502-110">Další informace najdete v tématu [interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="6c502-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="6c502-111">Chcete-li vytvořit objekt modelu COM s použitím šablony třídy modelu COM</span><span class="sxs-lookup"><span data-stu-id="6c502-111">To create a COM object by using the COM class template</span></span>  
  
1.  <span data-ttu-id="6c502-112">Otevřete nový projekt aplikace Windows z **souboru** nabídky kliknutím **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="6c502-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2.  <span data-ttu-id="6c502-113">V **nový projekt** dialogového okna **typy projektů** pole, zkontrolujte, zda je vybrána Windows.</span><span class="sxs-lookup"><span data-stu-id="6c502-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="6c502-114">Vyberte **knihovny tříd** z **šablony** seznamu a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c502-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="6c502-115">Zobrazí se nový projekt.</span><span class="sxs-lookup"><span data-stu-id="6c502-115">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="6c502-116">Vyberte **přidat novou položku** z **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="6c502-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="6c502-117">**Přidat novou položku** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="6c502-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="6c502-118">Vyberte **třídy COM** z **šablony** seznamu a potom klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="6c502-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="6c502-119">Visual Basic přidá novou třídu a nakonfiguruje nový projekt pro spolupráci s COM.</span><span class="sxs-lookup"><span data-stu-id="6c502-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5.  <span data-ttu-id="6c502-120">Přidání kódu, jako jsou vlastnosti, metody a události do třídy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6c502-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6.  <span data-ttu-id="6c502-121">Vyberte **sestavení ClassLibrary1** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="6c502-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="6c502-122">Visual Basic vytvoří sestavení a registruje objekt modelu COM s operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="6c502-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="6c502-123">Vytváření objektů COM bez šablony třídy modelu COM</span><span class="sxs-lookup"><span data-stu-id="6c502-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="6c502-124">Můžete také vytvořit třídu COM ručně místo pomocí šablony třídy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="6c502-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="6c502-125">Tento postup je užitečný při práci z příkazového řádku, nebo pokud potřebujete větší kontrolu nad jak objekty modelu COM jsou definovány.</span><span class="sxs-lookup"><span data-stu-id="6c502-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="6c502-126">Nastavení projektu pro generování objekt modelu COM</span><span class="sxs-lookup"><span data-stu-id="6c502-126">To set up your project to generate a COM object</span></span>  
  
1.  <span data-ttu-id="6c502-127">Otevřete nový projekt aplikace Windows z **souboru** nabídky kliknutím **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="6c502-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2.  <span data-ttu-id="6c502-128">V **nový projekt** dialogového okna **typy projektů** pole, zkontrolujte, zda je vybrána Windows.</span><span class="sxs-lookup"><span data-stu-id="6c502-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="6c502-129">Vyberte **knihovny tříd** z **šablony** seznamu a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c502-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="6c502-130">Zobrazí se nový projekt.</span><span class="sxs-lookup"><span data-stu-id="6c502-130">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="6c502-131">V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a potom klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="6c502-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="6c502-132">**Návrháře projektu** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="6c502-132">The **Project Designer** is displayed.</span></span>  
  
4.  <span data-ttu-id="6c502-133">Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="6c502-133">Click the **Compile** tab.</span></span>  
  
5.  <span data-ttu-id="6c502-134">Vyberte **zaregistrovat pro interoperabilitu COM** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="6c502-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="6c502-135">K nastavení kódu ve své třídě pro vytvoření objektu modelu COM</span><span class="sxs-lookup"><span data-stu-id="6c502-135">To set up the code in your class to create a COM object</span></span>  
  
1.  <span data-ttu-id="6c502-136">V **Průzkumníka řešení**, dvakrát klikněte na panel **Class1.vb** zobrazíte jeho kód.</span><span class="sxs-lookup"><span data-stu-id="6c502-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2.  <span data-ttu-id="6c502-137">Přejmenujte třídu na `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="6c502-137">Rename the class to `ComClass1`.</span></span>  
  
3.  <span data-ttu-id="6c502-138">Přidejte následující konstanty na `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="6c502-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="6c502-139">Ukládají se konstanty globálně jedinečný identifikátor (GUID), které jsou objekty COM musí mít.</span><span class="sxs-lookup"><span data-stu-id="6c502-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  <span data-ttu-id="6c502-140">Na **nástroje** nabídky, klikněte na tlačítko **Create Guid**.</span><span class="sxs-lookup"><span data-stu-id="6c502-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="6c502-141">V **Create GUID** dialogové okno, klikněte na tlačítko **formát registru** a potom klikněte na tlačítko **kopírování**.</span><span class="sxs-lookup"><span data-stu-id="6c502-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="6c502-142">Klikněte na tlačítko **ukončovací**.</span><span class="sxs-lookup"><span data-stu-id="6c502-142">Click **Exit**.</span></span>  
  
5.  <span data-ttu-id="6c502-143">Prázdný řetězec pro nahrazení `ClassId` s identifikátorem GUID, odebírá se úvodní a koncové závorek.</span><span class="sxs-lookup"><span data-stu-id="6c502-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="6c502-144">Například, pokud identifikátor GUID poskytl Guidgen – je `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` a váš kód by měl vypadat následovně.</span><span class="sxs-lookup"><span data-stu-id="6c502-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  <span data-ttu-id="6c502-145">Opakujte předchozí kroky pro `InterfaceId` a `EventsId` konstant, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6c502-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="6c502-146">Ujistěte se, že jsou identifikátory GUID nových a jedinečných; jinak vaše komponenty modelu COM může jsou v konfliktu s dalšími komponentami COM.</span><span class="sxs-lookup"><span data-stu-id="6c502-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7.  <span data-ttu-id="6c502-147">Přidat `ComClass` atribut `ComClass1`, zadejte identifikátory GUID pro ID třídy, rozhraní ID a události ID jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6c502-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  <span data-ttu-id="6c502-148">Třídy COM musí mít bez parametrů `Public Sub New()` konstruktor nebo třídy nebude správně zaregistrována.</span><span class="sxs-lookup"><span data-stu-id="6c502-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="6c502-149">Přidejte konstruktor pro třídu:</span><span class="sxs-lookup"><span data-stu-id="6c502-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. <span data-ttu-id="6c502-150">Přidejte do třídy, koncové ji vlastnosti, metody a události `End Class` příkazu.</span><span class="sxs-lookup"><span data-stu-id="6c502-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="6c502-151">Vyberte **sestavit řešení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="6c502-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="6c502-152">Visual Basic vytvoří sestavení a registruje objekt modelu COM s operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="6c502-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c502-153">Objekty COM, které vygenerujete pomocí jazyka Visual Basic nelze použít jiné aplikace Visual Basic, protože nejsou splněny objektů COM.</span><span class="sxs-lookup"><span data-stu-id="6c502-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="6c502-154">Pokusy o přidání odkazů na tyto objekty modelu COM vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="6c502-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="6c502-155">Podrobnosti najdete v tématu [interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="6c502-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c502-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c502-156">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [<span data-ttu-id="6c502-157">Zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="6c502-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="6c502-158">Návod: Implementace dědičnosti pomocí objektů COM</span><span class="sxs-lookup"><span data-stu-id="6c502-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="6c502-159">Direktiva #Region</span><span class="sxs-lookup"><span data-stu-id="6c502-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="6c502-160">Interoperabilita modelů COM v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6c502-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="6c502-161">Řešení potíží s interoperabilitou</span><span class="sxs-lookup"><span data-stu-id="6c502-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
