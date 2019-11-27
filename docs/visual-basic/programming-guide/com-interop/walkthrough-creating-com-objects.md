---
title: 'Návod: vytváření objektů COM'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 5d00aff07358a0c40159fde9c12c70e0842d848b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338621"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="56e91-102">Návod: Vytváření objektů modelu COM pomocí jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56e91-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="56e91-103">Při vytváření nových aplikací nebo součástí je nejvhodnější vytvořit .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="56e91-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="56e91-104">Visual Basic ale také usnadňuje vystavení .NET Framework součásti modelu COM.</span><span class="sxs-lookup"><span data-stu-id="56e91-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="56e91-105">To vám umožní poskytnout nové komponenty pro starší sady aplikací, které vyžadují komponenty modelu COM.</span><span class="sxs-lookup"><span data-stu-id="56e91-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="56e91-106">Tento návod ukazuje, jak použít Visual Basic k vystavení objektů .NET Framework jako objektů COM, a to s šablonou třídy modelu COM i bez ní.</span><span class="sxs-lookup"><span data-stu-id="56e91-106">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="56e91-107">Nejjednodušší způsob, jak vystavit objekty COM, je použití šablony třídy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="56e91-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="56e91-108">Šablona třídy modelu COM vytvoří novou třídu a potom nakonfiguruje projekt tak, aby generoval třídu a interoperabilitu vrstvu jako objekt modelu COM a zaregistroval jej s operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="56e91-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56e91-109">I když můžete vystavit třídu vytvořenou v Visual Basic jako objekt modelu COM pro použití nespravovaného kódu, nejedná se o skutečný objekt COM a nelze jej použít Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="56e91-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="56e91-110">Další informace najdete v tématu [interoperabilita modelu COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="56e91-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="56e91-111">Vytvoření objektu COM pomocí šablony třídy modelu COM</span><span class="sxs-lookup"><span data-stu-id="56e91-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="56e91-112">Kliknutím na **Nový projekt**otevřete v nabídce **soubor** nový projekt aplikace pro Windows.</span><span class="sxs-lookup"><span data-stu-id="56e91-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="56e91-113">V dialogovém okně **Nový projekt** v poli **typy projektů** zaškrtněte políčko Windows je vybráno.</span><span class="sxs-lookup"><span data-stu-id="56e91-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="56e91-114">V seznamu **šablony** vyberte možnost **Knihovna tříd** a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="56e91-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="56e91-115">Zobrazí se nový projekt.</span><span class="sxs-lookup"><span data-stu-id="56e91-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="56e91-116">V nabídce **projekt** vyberte **Přidat novou položku** .</span><span class="sxs-lookup"><span data-stu-id="56e91-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="56e91-117">Zobrazí se dialogové okno **Přidat novou položku** .</span><span class="sxs-lookup"><span data-stu-id="56e91-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="56e91-118">V seznamu **šablony** vyberte možnost **třída com** a potom klikněte na tlačítko **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="56e91-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="56e91-119">Visual Basic přidá novou třídu a nakonfiguruje nový projekt pro zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="56e91-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="56e91-120">Přidejte do třídy COM kód, jako jsou vlastnosti, metody a události.</span><span class="sxs-lookup"><span data-stu-id="56e91-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="56e91-121">V nabídce **sestavení** vyberte **Build ClassLibrary1** .</span><span class="sxs-lookup"><span data-stu-id="56e91-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="56e91-122">Visual Basic sestavení sestavení a registruje objekt COM s operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="56e91-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="56e91-123">Vytváření objektů COM bez šablony třídy modelu COM</span><span class="sxs-lookup"><span data-stu-id="56e91-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="56e91-124">Třídu COM lze také vytvořit ručně namísto použití šablony třídy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="56e91-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="56e91-125">Tento postup je užitečný při práci z příkazového řádku nebo v případě, že chcete mít větší kontrolu nad tím, jak jsou objekty modelu COM definovány.</span><span class="sxs-lookup"><span data-stu-id="56e91-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="56e91-126">Nastavení projektu pro vygenerování objektu COM</span><span class="sxs-lookup"><span data-stu-id="56e91-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="56e91-127">Kliknutím na **NewProject**otevřete v nabídce **soubor** nový projekt aplikace pro Windows.</span><span class="sxs-lookup"><span data-stu-id="56e91-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="56e91-128">V dialogovém okně **Nový projekt** v poli **typy projektů** zaškrtněte políčko Windows je vybráno.</span><span class="sxs-lookup"><span data-stu-id="56e91-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="56e91-129">V seznamu **šablony** vyberte možnost **Knihovna tříd** a pak klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="56e91-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="56e91-130">Zobrazí se nový projekt.</span><span class="sxs-lookup"><span data-stu-id="56e91-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="56e91-131">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a pak klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="56e91-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="56e91-132">Zobrazí se **Návrhář projektu** .</span><span class="sxs-lookup"><span data-stu-id="56e91-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="56e91-133">Klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="56e91-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="56e91-134">Zaškrtněte políčko **zaregistrovat pro zprostředkovatele komunikace s objekty COM** .</span><span class="sxs-lookup"><span data-stu-id="56e91-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="56e91-135">Nastavení kódu ve vaší třídě pro vytvoření objektu COM</span><span class="sxs-lookup"><span data-stu-id="56e91-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="56e91-136">V **Průzkumník řešení**dvakrát klikněte na **Class1. vb** pro zobrazení kódu.</span><span class="sxs-lookup"><span data-stu-id="56e91-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="56e91-137">Přejmenujte třídu na `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="56e91-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="56e91-138">Přidejte následující konstanty pro `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="56e91-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="56e91-139">Budou ukládat konstanty globálně jedinečného identifikátoru (GUID), které objekty COM musí mít.</span><span class="sxs-lookup"><span data-stu-id="56e91-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="56e91-140">V nabídce **nástroje** klikněte na příkaz **vytvořit identifikátor GUID**.</span><span class="sxs-lookup"><span data-stu-id="56e91-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="56e91-141">V dialogovém okně **vytvořit GUID** klikněte na **Formát registru** a pak klikněte na **Kopírovat**.</span><span class="sxs-lookup"><span data-stu-id="56e91-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="56e91-142">Klikněte na tlačítko **konec**.</span><span class="sxs-lookup"><span data-stu-id="56e91-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="56e91-143">Nahraďte prázdný řetězec pro `ClassId` identifikátorem GUID a odeberte úvodní a koncové složené závorky.</span><span class="sxs-lookup"><span data-stu-id="56e91-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="56e91-144">Například pokud je identifikátor GUID poskytovaný nástrojem Guidgen `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` pak by se měl váš kód zobrazit takto.</span><span class="sxs-lookup"><span data-stu-id="56e91-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="56e91-145">Opakujte předchozí postup pro konstanty `InterfaceId` a `EventsId`, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="56e91-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > <span data-ttu-id="56e91-146">Ujistěte se, že identifikátory GUID jsou nové a jedinečné; v opačném případě by komponenta modelu COM mohla být v konfliktu s jinými komponentami modelu COM.</span><span class="sxs-lookup"><span data-stu-id="56e91-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="56e91-147">Přidejte atribut `ComClass` do `ComClass1`a zadejte identifikátory GUID pro ID třídy, ID rozhraní a ID událostí, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="56e91-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="56e91-148">Třídy COM musí mít konstruktor `Public Sub New()` bez parametrů, jinak se třída nebude registrovat správně.</span><span class="sxs-lookup"><span data-stu-id="56e91-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="56e91-149">Přidejte do třídy konstruktor bez parametrů:</span><span class="sxs-lookup"><span data-stu-id="56e91-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="56e91-150">Do třídy přidejte vlastnosti, metody a události a končící je příkazem `End Class`.</span><span class="sxs-lookup"><span data-stu-id="56e91-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="56e91-151">V nabídce **sestavení** vyberte **sestavení řešení** .</span><span class="sxs-lookup"><span data-stu-id="56e91-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="56e91-152">Visual Basic sestavení sestavení a registruje objekt COM s operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="56e91-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="56e91-153">Objekty modelu COM, které vygenerujete pomocí Visual Basic, nemohou být používány jinými Visual Basic aplikacemi, protože neplatí pro objekty COM.</span><span class="sxs-lookup"><span data-stu-id="56e91-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="56e91-154">Pokusí se přidat odkazy na takové objekty COM a vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="56e91-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="56e91-155">Podrobnosti najdete v tématu [interoperabilita modelu COM v aplikacích .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="56e91-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e91-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56e91-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="56e91-157">Zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="56e91-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="56e91-158">Návod: Implementace dědičnosti pomocí objektů COM</span><span class="sxs-lookup"><span data-stu-id="56e91-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="56e91-159">Direktiva #Region</span><span class="sxs-lookup"><span data-stu-id="56e91-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="56e91-160">Interoperabilita modelů COM v aplikacích .NET Framework</span><span class="sxs-lookup"><span data-stu-id="56e91-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="56e91-161">Řešení potíží s interoperabilitou</span><span class="sxs-lookup"><span data-stu-id="56e91-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
