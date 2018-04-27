---
title: 'Návod: Vytváření objektů modelu COM pomocí jazyka Visual Basic'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e660d672fc32455cee349dc44ad20c3244c087b4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="15dc3-102">Návod: Vytváření objektů modelu COM pomocí jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15dc3-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="15dc3-103">Při vytváření nové aplikace nebo součásti, je nejlepší vytvořit sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15dc3-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="15dc3-104">Ale jazyka Visual Basic také umožňuje snadno vystavit rozhraní .NET Framework komponenty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="15dc3-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="15dc3-105">To umožňuje poskytovat nové součásti pro starší aplikace sady, které vyžadují COM – součásti.</span><span class="sxs-lookup"><span data-stu-id="15dc3-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="15dc3-106">Tento návod ukazuje, jak používat Visual Basic vystavit [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objekty jako objekty modelu COM, s i bez šablona třídy COM.</span><span class="sxs-lookup"><span data-stu-id="15dc3-106">This walkthrough demonstrates how to use Visual Basic to expose [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="15dc3-107">Nejjednodušší způsob, jak vystavit objektů COM je pomocí šablony třídy COM.</span><span class="sxs-lookup"><span data-stu-id="15dc3-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="15dc3-108">Šablona třídy COM vytvoří novou třídu a pak nakonfiguruje projektu pro generování tříd a interoperabilita vrstvě jako objekt COM a zaregistrovat ho u operačního systému.</span><span class="sxs-lookup"><span data-stu-id="15dc3-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15dc3-109">I když můžete také zveřejnit třídu vytvořit jako objekt COM pro nespravovaného kódu pro použití v jazyce Visual Basic, není objekt true COM a nemůže být použit jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="15dc3-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="15dc3-110">Další informace najdete v tématu [interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="15dc3-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="15dc3-111">Chcete-li vytvořit objekt modelu COM pomocí šablony třídy COM</span><span class="sxs-lookup"><span data-stu-id="15dc3-111">To create a COM object by using the COM class template</span></span>  
  
1.  <span data-ttu-id="15dc3-112">Otevřete nový projekt aplikace Windows z **soubor** nabídky kliknutím **nový projekt**.</span><span class="sxs-lookup"><span data-stu-id="15dc3-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2.  <span data-ttu-id="15dc3-113">V **nový projekt** dialogového okna **typy projektů** pole, zkontrolujte, zda je vybrána systému Windows.</span><span class="sxs-lookup"><span data-stu-id="15dc3-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="15dc3-114">Vyberte **knihovny tříd** z **šablony** seznamu a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="15dc3-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="15dc3-115">Zobrazí se nový projekt.</span><span class="sxs-lookup"><span data-stu-id="15dc3-115">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="15dc3-116">Vyberte **přidat novou položku** z **projektu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="15dc3-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="15dc3-117">**Přidat novou položku** se zobrazí dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="15dc3-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="15dc3-118">Vyberte **třídy COM** z **šablony** seznamu a pak klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="15dc3-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="15dc3-119">Visual Basic přidá novou třídu a nakonfiguruje nového projektu pro zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="15dc3-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5.  <span data-ttu-id="15dc3-120">Přidejte kód například události, vlastnosti a metody pro třídu COM.</span><span class="sxs-lookup"><span data-stu-id="15dc3-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6.  <span data-ttu-id="15dc3-121">Vyberte **sestavení ClassLibrary1** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="15dc3-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="15dc3-122">Visual Basic sestavení sestavení a zaregistruje objekt COM s operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="15dc3-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="15dc3-123">Vytváření objektů modelu COM bez šablony třídy COM</span><span class="sxs-lookup"><span data-stu-id="15dc3-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="15dc3-124">Můžete také vytvořit třídu COM ručně místo pomocí šablony třídy COM.</span><span class="sxs-lookup"><span data-stu-id="15dc3-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="15dc3-125">Tento postup je užitečné, když pracujete z příkazového řádku, nebo pokud potřebujete větší kontrolu nad jak jsou definovány COM – objekty.</span><span class="sxs-lookup"><span data-stu-id="15dc3-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="15dc3-126">Nastavení projektu pro generování objektu COM</span><span class="sxs-lookup"><span data-stu-id="15dc3-126">To set up your project to generate a COM object</span></span>  
  
1.  <span data-ttu-id="15dc3-127">Otevřete nový projekt aplikace Windows z **soubor** nabídky kliknutím **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="15dc3-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2.  <span data-ttu-id="15dc3-128">V **nový projekt** dialogového okna **typy projektů** pole, zkontrolujte, zda je vybrána systému Windows.</span><span class="sxs-lookup"><span data-stu-id="15dc3-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="15dc3-129">Vyberte **knihovny tříd** z **šablony** seznamu a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="15dc3-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="15dc3-130">Zobrazí se nový projekt.</span><span class="sxs-lookup"><span data-stu-id="15dc3-130">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="15dc3-131">V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="15dc3-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="15dc3-132">**Návrhář projektu** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="15dc3-132">The **Project Designer** is displayed.</span></span>  
  
4.  <span data-ttu-id="15dc3-133">Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="15dc3-133">Click the **Compile** tab.</span></span>  
  
5.  <span data-ttu-id="15dc3-134">Vyberte **zaregistrovat zprostředkovatel komunikace s objekty COM** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="15dc3-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="15dc3-135">Nastavit kód ve třídě vytvoříte objekt modelu COM</span><span class="sxs-lookup"><span data-stu-id="15dc3-135">To set up the code in your class to create a COM object</span></span>  
  
1.  <span data-ttu-id="15dc3-136">V **Průzkumníku řešení**, dvakrát klikněte na **Class1.vb** k zobrazení jeho kódu.</span><span class="sxs-lookup"><span data-stu-id="15dc3-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2.  <span data-ttu-id="15dc3-137">Přejmenujte třídy pro `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="15dc3-137">Rename the class to `ComClass1`.</span></span>  
  
3.  <span data-ttu-id="15dc3-138">Přidejte následující konstanty pro `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="15dc3-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="15dc3-139">Se uloží konstanty globálně jedinečný identifikátor (GUID), které je potřeba mít objektů COM.</span><span class="sxs-lookup"><span data-stu-id="15dc3-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  <span data-ttu-id="15dc3-140">Na **nástroje** nabídky, klikněte na tlačítko **vytvořit Guid**.</span><span class="sxs-lookup"><span data-stu-id="15dc3-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="15dc3-141">V **vytvořit GUID** dialogové okno, klikněte na tlačítko **registru formátu** a pak klikněte na **kopie**.</span><span class="sxs-lookup"><span data-stu-id="15dc3-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="15dc3-142">Klikněte na tlačítko **ukončení**.</span><span class="sxs-lookup"><span data-stu-id="15dc3-142">Click **Exit**.</span></span>  
  
5.  <span data-ttu-id="15dc3-143">Nahraďte prázdný řetězec pro `ClassId` s identifikátorem GUID, složené závorky odebrání úvodní a koncové.</span><span class="sxs-lookup"><span data-stu-id="15dc3-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="15dc3-144">Například, pokud identifikátor GUID poskytované Guidgen – je `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` pak váš kód by měl vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="15dc3-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  <span data-ttu-id="15dc3-145">Opakujte předchozí kroky pro `InterfaceId` a `EventsId` konstanty, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="15dc3-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="15dc3-146">Ujistěte se, že jsou identifikátory GUID nových a jedinečných; příslušné součásti COM, jinak hodnota mohla být v konfliktu s ostatními součástmi COM.</span><span class="sxs-lookup"><span data-stu-id="15dc3-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7.  <span data-ttu-id="15dc3-147">Přidat `ComClass` atribut `ComClass1`, určení identifikátory GUID pro ID třídy, rozhraní ID a ID událostí jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="15dc3-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  <span data-ttu-id="15dc3-148">Třídy COM musí mít bez parametrů `Public Sub New()` konstruktoru nebo třídě se neregistruje správně.</span><span class="sxs-lookup"><span data-stu-id="15dc3-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="15dc3-149">Přidejte do třídy konstruktor bez parametrů:</span><span class="sxs-lookup"><span data-stu-id="15dc3-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. <span data-ttu-id="15dc3-150">Přidejte do třídy, koncová její vlastnosti, metod a události `End Class` příkaz.</span><span class="sxs-lookup"><span data-stu-id="15dc3-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="15dc3-151">Vyberte **sestavit řešení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="15dc3-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="15dc3-152">Visual Basic sestavení sestavení a zaregistruje objekt COM s operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="15dc3-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="15dc3-153">Objekty COM, které můžete vygenerovat pomocí jazyka Visual Basic nelze použít jiné aplikace Visual Basic, protože nejsou true COM – objekty.</span><span class="sxs-lookup"><span data-stu-id="15dc3-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="15dc3-154">Pokusy o přidání odkazů na tyto objekty COM vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="15dc3-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="15dc3-155">Podrobnosti najdete v tématu [interoperabilita modelů COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="15dc3-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15dc3-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="15dc3-156">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [<span data-ttu-id="15dc3-157">Zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="15dc3-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="15dc3-158">Návod: Implementace dědičnosti pomocí objektů COM</span><span class="sxs-lookup"><span data-stu-id="15dc3-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="15dc3-159">Direktiva #Region</span><span class="sxs-lookup"><span data-stu-id="15dc3-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="15dc3-160">Interoperabilita modelů COM v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="15dc3-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="15dc3-161">Řešení potíží s interoperabilitou</span><span class="sxs-lookup"><span data-stu-id="15dc3-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
