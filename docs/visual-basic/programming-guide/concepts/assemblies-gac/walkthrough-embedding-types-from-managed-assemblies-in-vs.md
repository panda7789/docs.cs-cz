---
title: 'Návod: Vložení typů z řízených sestavení v sadě Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 1f6176746b783d020c809fb0b5d55d741ce0148b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644183"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="f1643-102">Návod: Vložení typů z řízených sestavení v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1643-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="f1643-103">Pokud jste pro vložení informací o typu ze spravovaných sestavení se silným názvem, můžete volně spojte typy v aplikaci k dosažení nezávislost verze.</span><span class="sxs-lookup"><span data-stu-id="f1643-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="f1643-104">To znamená váš program může být napsán používat typy z více verzí aplikace spravované knihovny aniž byste museli zopakovat pro každou verzi.</span><span class="sxs-lookup"><span data-stu-id="f1643-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="f1643-105">Typ vložení se často používá se spoluprací COM, jako je například aplikace, která používá objekty automatizace z aplikace Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="f1643-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="f1643-106">Vložení informací o typu umožňuje ve stejném sestavení programu pro práci s různými verzemi nástroje Microsoft Office na různých počítačích.</span><span class="sxs-lookup"><span data-stu-id="f1643-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="f1643-107">Však můžete použít také typu vložení v rámci řešení pro plně spravovaná.</span><span class="sxs-lookup"><span data-stu-id="f1643-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="f1643-108">Lze jej vkládat informace o typu ze sestavení, který má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f1643-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="f1643-109">Sestavení zpřístupní alespoň jeden veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1643-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="f1643-110">Vložené rozhraní jsou opatřen poznámkou `ComImport` atribut a `Guid` atribut (a jedinečný identifikátor GUID).</span><span class="sxs-lookup"><span data-stu-id="f1643-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="f1643-111">Sestavení je opatřen poznámkou `ImportedFromTypeLib` atribut nebo `PrimaryInteropAssembly` atribut a úroveň sestavení `Guid` atribut.</span><span class="sxs-lookup"><span data-stu-id="f1643-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="f1643-112">(Ve výchozím nastavení, zahrnují šablony projektů Visual Basic úrovni sestavení `Guid` atributů.)</span><span class="sxs-lookup"><span data-stu-id="f1643-112">(By default, Visual Basic project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="f1643-113">Po zadání veřejného rozhraní, která může být vložen, můžete vytvořit runtime třídy, které implementují těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1643-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="f1643-114">Program klienta můžete pak vložení informací o typu pro tyto rozhraní v době návrhu pomocí odkazování na sestavení, které obsahuje veřejné rozhraní a nastavení `Embed Interop Types` vlastnost odkazu na `True`.</span><span class="sxs-lookup"><span data-stu-id="f1643-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="f1643-115">Jde o ekvivalent pomocí příkazového řádku kompilátoru a odkazování na sestavení s použitím `/link` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f1643-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="f1643-116">Program klienta pak můžete načíst instancí objektů vaší runtime, která je zadán jako těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1643-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="f1643-117">Pokud vytvoříte novou verzi vašeho sestavení silným názvem modulu runtime, není nutné zopakovat s sestavení aktualizované runtime program klienta.</span><span class="sxs-lookup"><span data-stu-id="f1643-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="f1643-118">Místo toho program klienta budou nadále používat kteroukoli verzi modulu runtime sestavení je k dispozici, pomocí informací o vloženého typu pro veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1643-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="f1643-119">Vzhledem k tomu, že primární funkce typ vnoření je podpora vložení informací o typu ze sestavení vzájemné spolupráce COM, při vložení informací o typu ve plně spravovaná řešení platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="f1643-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="f1643-120">Pouze atributy, které jsou specifické pro zprostředkovatele komunikace s objekty COM jsou vloženy; ostatní atributy se ignorují.</span><span class="sxs-lookup"><span data-stu-id="f1643-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="f1643-121">Pokud typu používá obecné parametry a typ obecný parametr je vloženého typu, typu nelze použít v hranici sestavení.</span><span class="sxs-lookup"><span data-stu-id="f1643-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="f1643-122">Při překročení hranici sestavení příklady volání metody z jiného sestavení nebo typ odvozování z typu definovaný v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="f1643-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="f1643-123">Konstanty nejsou vložena.</span><span class="sxs-lookup"><span data-stu-id="f1643-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="f1643-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Třída nepodporuje vloženého typu jako klíč.</span><span class="sxs-lookup"><span data-stu-id="f1643-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="f1643-125">Můžete implementovat vlastní typ slovníku pro podporu vloženého typu jako klíč.</span><span class="sxs-lookup"><span data-stu-id="f1643-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="f1643-126">V tomto návodu se postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="f1643-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="f1643-127">Vytvořte sestavení se silným názvem, který má veřejné rozhraní, který obsahuje informace o typu, kterou můžete vložit.</span><span class="sxs-lookup"><span data-stu-id="f1643-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="f1643-128">Vytvořte sestavení silným názvem modulu runtime, který implementuje této veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1643-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="f1643-129">Vytvořte program klienta, který se vloží informací o typu ze veřejné rozhraní a vytvoří instanci třídy ze sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f1643-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="f1643-130">Upravit a znovu sestavte sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="f1643-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="f1643-131">Spusťte klientskou aplikaci, která v tématu, aby se používal novou verzi modulu runtime sestavení bez nutnosti její kompilace programu klienta.</span><span class="sxs-lookup"><span data-stu-id="f1643-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="f1643-132">Vytváření rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1643-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="f1643-133">Vytvoření projektu typu ekvivalenční rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1643-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="f1643-134">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="f1643-134">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="f1643-135">V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="f1643-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="f1643-136">Vyberte **knihovny tříd** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="f1643-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="f1643-137">V **název** zadejte `TypeEquivalenceInterface`a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1643-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="f1643-138">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="f1643-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="f1643-139">V **Průzkumníku řešení**, klikněte pravým tlačítkem na soubor Class1.vb a klikněte na **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="f1643-139">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="f1643-140">Přejmenujte soubor `ISampleInterface.vb` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="f1643-140">Rename the file to `ISampleInterface.vb` and press ENTER.</span></span> <span data-ttu-id="f1643-141">Přejmenování souboru také přejmenuje třídy pro `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="f1643-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="f1643-142">Tato třída bude reprezentovat veřejné rozhraní pro třídu.</span><span class="sxs-lookup"><span data-stu-id="f1643-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="f1643-143">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f1643-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="f1643-144">Klikněte **zkompilovat** kartě. Nastavte výstupní cesta na některé platné místo ve svém vývojovém počítači, jako je třeba `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="f1643-144">Click the **Compile** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="f1643-145">Toto umístění se taky použije později v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="f1643-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="f1643-146">Při úpravách stále vlastností projektu, klikněte **podpisování** karta. Vyberte **podepsání sestavení** možnost.</span><span class="sxs-lookup"><span data-stu-id="f1643-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="f1643-147">V **vyberte soubor klíče se silným názvem** seznamu, klikněte na tlačítko **< nová... >**.</span><span class="sxs-lookup"><span data-stu-id="f1643-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="f1643-148">V **název souboru klíče** zadejte `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="f1643-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="f1643-149">Vymazat **chránit Moje soubor klíče s heslem** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="f1643-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="f1643-150">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1643-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="f1643-151">Otevřete soubor ISampleInterface.vb.</span><span class="sxs-lookup"><span data-stu-id="f1643-151">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="f1643-152">Přidejte následující kód do souboru třídy ISampleInterface k vytvoření rozhraní ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="f1643-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
    ```vb  
    Imports System.Runtime.InteropServices  
  
    <ComImport()>  
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>  
    Public Interface ISampleInterface  
        Sub GetUserInput()  
        ReadOnly Property UserInput As String  
    End Interface  
    ```  
  
7.  <span data-ttu-id="f1643-153">Na **nástroje** nabídky, klikněte na tlačítko **vytvořit Guid**.</span><span class="sxs-lookup"><span data-stu-id="f1643-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="f1643-154">V **vytvořit GUID** dialogové okno, klikněte na tlačítko **registru formátu** a pak klikněte na **kopie**.</span><span class="sxs-lookup"><span data-stu-id="f1643-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="f1643-155">Klikněte na tlačítko **ukončení**.</span><span class="sxs-lookup"><span data-stu-id="f1643-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="f1643-156">V `Guid` atribut, odstraňte ukázka GUID a vložte identifikátor GUID, který jste zkopírovali ze **vytvořit GUID** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="f1643-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="f1643-157">Odebrat složené závorky ({}) ze zkopírovaného identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="f1643-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="f1643-158">Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="f1643-158">On the **Project** menu, click **Show All Files**.</span></span>  
  
10. <span data-ttu-id="f1643-159">V **Průzkumníku řešení**, rozbalte **Můj projekt** složky.</span><span class="sxs-lookup"><span data-stu-id="f1643-159">In **Solution Explorer**, expand the **My Project** folder.</span></span> <span data-ttu-id="f1643-160">Dvakrát klikněte AssemblyInfo.vb.</span><span class="sxs-lookup"><span data-stu-id="f1643-160">Double-click the AssemblyInfo.vb.</span></span> <span data-ttu-id="f1643-161">Do souboru přidejte následující atribut.</span><span class="sxs-lookup"><span data-stu-id="f1643-161">Add the following attribute to the file.</span></span>  
  
    ```vb  
    <Assembly: ImportedFromTypeLib("")>  
    ```  
  
     <span data-ttu-id="f1643-162">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="f1643-162">Save the file.</span></span>  
  
11. <span data-ttu-id="f1643-163">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="f1643-163">Save the project.</span></span>  
  
12. <span data-ttu-id="f1643-164">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="f1643-164">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="f1643-165">Soubor DLL knihovny tříd jsou kompilované a uložit na zadaná sestavení výstupní cestu (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="f1643-165">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="f1643-166">Vytvoření třídy modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="f1643-166">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="f1643-167">Vytvoření projektu typu ekvivalenční modulu runtime</span><span class="sxs-lookup"><span data-stu-id="f1643-167">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="f1643-168">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="f1643-168">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="f1643-169">V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="f1643-169">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="f1643-170">Vyberte **knihovny tříd** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="f1643-170">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="f1643-171">V **název** zadejte `TypeEquivalenceRuntime`a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1643-171">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="f1643-172">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="f1643-172">The new project is created.</span></span>  
  
3.  <span data-ttu-id="f1643-173">V **Průzkumníku řešení**, klikněte pravým tlačítkem na soubor Class1.vb a klikněte na **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="f1643-173">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="f1643-174">Přejmenujte soubor `SampleClass.vb` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="f1643-174">Rename the file to `SampleClass.vb` and press ENTER.</span></span> <span data-ttu-id="f1643-175">Přejmenování souboru také přejmenuje třídy pro `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="f1643-175">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="f1643-176">Tato třída se implementovat `ISampleInterface` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1643-176">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="f1643-177">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f1643-177">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="f1643-178">Klikněte **zkompilovat** kartě. Nastavit výstupní cesta do stejného umístění, které jste použili v TypeEquivalenceInterface projektu, například `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="f1643-178">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="f1643-179">Při úpravách stále vlastností projektu, klikněte **podpisování** karta. Vyberte **podepsání sestavení** možnost.</span><span class="sxs-lookup"><span data-stu-id="f1643-179">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="f1643-180">V **vyberte soubor klíče se silným názvem** seznamu, klikněte na tlačítko **< nová... >**.</span><span class="sxs-lookup"><span data-stu-id="f1643-180">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="f1643-181">V **název souboru klíče** zadejte `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="f1643-181">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="f1643-182">Vymazat **chránit Moje soubor klíče s heslem** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="f1643-182">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="f1643-183">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1643-183">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="f1643-184">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="f1643-184">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="f1643-185">Klikněte **Procházet** kartě a přejděte do složky výstupní cesta.</span><span class="sxs-lookup"><span data-stu-id="f1643-185">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="f1643-186">Vyberte soubor TypeEquivalenceInterface.dll a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1643-186">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="f1643-187">Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="f1643-187">On the **Project** menu, click **Show All Files**.</span></span>  
  
8.  <span data-ttu-id="f1643-188">V **Průzkumníku řešení**, rozbalte **odkazy** složky.</span><span class="sxs-lookup"><span data-stu-id="f1643-188">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="f1643-189">Vyberte odkaz na TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="f1643-189">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="f1643-190">V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **konkrétní verzi** vlastnost **False**.</span><span class="sxs-lookup"><span data-stu-id="f1643-190">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
9. <span data-ttu-id="f1643-191">Přidejte následující kód do souboru SampleClass třídy pro vytvoření třídy SampleClass.</span><span class="sxs-lookup"><span data-stu-id="f1643-191">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
    ```vb  
    Imports TypeEquivalenceInterface  
  
    Public Class SampleClass  
        Implements ISampleInterface  
  
        Private p_UserInput As String  
        Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput  
            Get  
                Return p_UserInput  
            End Get  
        End Property  
  
        Public Sub GetUserInput() Implements ISampleInterface.GetUserInput  
            Console.WriteLine("Please enter a value:")  
            p_UserInput = Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
10. <span data-ttu-id="f1643-192">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="f1643-192">Save the project.</span></span>  
  
11. <span data-ttu-id="f1643-193">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="f1643-193">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="f1643-194">Soubor DLL knihovny tříd jsou kompilované a uložit na zadaná sestavení výstupní cestu (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="f1643-194">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="f1643-195">Vytvoření projektu klienta</span><span class="sxs-lookup"><span data-stu-id="f1643-195">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="f1643-196">Vytvoření projektu klienta ekvivalenční typu</span><span class="sxs-lookup"><span data-stu-id="f1643-196">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="f1643-197">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="f1643-197">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="f1643-198">V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="f1643-198">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="f1643-199">Vyberte **konzolové aplikace** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="f1643-199">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="f1643-200">V **název** zadejte `TypeEquivalenceClient`a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1643-200">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="f1643-201">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="f1643-201">The new project is created.</span></span>  
  
3.  <span data-ttu-id="f1643-202">Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f1643-202">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="f1643-203">Klikněte **zkompilovat** kartě. Nastavit výstupní cesta do stejného umístění, které jste použili v TypeEquivalenceInterface projektu, například `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="f1643-203">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="f1643-204">Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="f1643-204">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="f1643-205">Klikněte **Procházet** kartě a přejděte do složky výstupní cesta.</span><span class="sxs-lookup"><span data-stu-id="f1643-205">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="f1643-206">Vyberte soubor TypeEquivalenceInterface.dll (ne TypeEquivalenceRuntime.dll) a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1643-206">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="f1643-207">Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="f1643-207">On the **Project** menu, click **Show All Files**.</span></span>  
  
6.  <span data-ttu-id="f1643-208">V **Průzkumníku řešení**, rozbalte **odkazy** složky.</span><span class="sxs-lookup"><span data-stu-id="f1643-208">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="f1643-209">Vyberte odkaz na TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="f1643-209">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="f1643-210">V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **vložit zprostředkovatel komunikace s objekty typy** vlastnost **True**.</span><span class="sxs-lookup"><span data-stu-id="f1643-210">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
7.  <span data-ttu-id="f1643-211">Přidejte následující kód do souboru Module1.vb vytvoření programu klienta.</span><span class="sxs-lookup"><span data-stu-id="f1643-211">Add the following code to the Module1.vb file to create the client program.</span></span>  
  
    ```vb  
    Imports TypeEquivalenceInterface  
    Imports System.Reflection  
  
    Module Module1  
  
        Sub Main()  
            Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")  
            Dim sampleClass As ISampleInterface = CType( _  
                sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)  
            sampleClass.GetUserInput()  
            Console.WriteLine(sampleClass.UserInput)  
            Console.WriteLine(sampleAssembly.GetName().Version)  
            Console.ReadLine()  
        End Sub  
  
    End Module  
    ```  
  
8.  <span data-ttu-id="f1643-212">Stisknutím klávesy CTRL + F5 sestavit a spustit program.</span><span class="sxs-lookup"><span data-stu-id="f1643-212">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="f1643-213">Úprava rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1643-213">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="f1643-214">Chcete-li upravit rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1643-214">To modify the interface</span></span>  
  
1.  <span data-ttu-id="f1643-215">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **otevřete**a potom klikněte na **projekt nebo řešení**.</span><span class="sxs-lookup"><span data-stu-id="f1643-215">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="f1643-216">V **otevřeného projektu** dialogové okno, klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a pak klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f1643-216">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="f1643-217">Klikněte **aplikace** kartě. Klikněte **informací o sestavení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f1643-217">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="f1643-218">Změna **verze sestavení** a **verze souboru** hodnoty k `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="f1643-218">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="f1643-219">Otevřete soubor ISampleInterface.vb.</span><span class="sxs-lookup"><span data-stu-id="f1643-219">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="f1643-220">Přidejte následující řádek kódu rozhraní ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="f1643-220">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```vb  
    Function GetDate() As Date  
    ```  
  
     <span data-ttu-id="f1643-221">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="f1643-221">Save the file.</span></span>  
  
4.  <span data-ttu-id="f1643-222">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="f1643-222">Save the project.</span></span>  
  
5.  <span data-ttu-id="f1643-223">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="f1643-223">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="f1643-224">Nová verze souboru třídy knihovny DLL je zkompilovat a uloží do výstupní cesta zadaná sestavení (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="f1643-224">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="f1643-225">Úprava Runtime – třída</span><span class="sxs-lookup"><span data-stu-id="f1643-225">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="f1643-226">Chcete-li upravit runtime – třída</span><span class="sxs-lookup"><span data-stu-id="f1643-226">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="f1643-227">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **otevřete**a potom klikněte na **projekt nebo řešení**.</span><span class="sxs-lookup"><span data-stu-id="f1643-227">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="f1643-228">V **otevřeného projektu** dialogové okno pole, klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f1643-228">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="f1643-229">Klikněte **aplikace** kartě. Klikněte **informací o sestavení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f1643-229">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="f1643-230">Změna **verze sestavení** a **verze souboru** hodnoty k `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="f1643-230">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="f1643-231">Otevřete SampleClass.vbfile.</span><span class="sxs-lookup"><span data-stu-id="f1643-231">Open the SampleClass.vbfile.</span></span> <span data-ttu-id="f1643-232">Přidejte následující řádky kódu do třídy SampleClass.</span><span class="sxs-lookup"><span data-stu-id="f1643-232">Add the following lines of code to the SampleClass class.</span></span>  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  <span data-ttu-id="f1643-233">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="f1643-233">Save the project.</span></span>  
  
5.  <span data-ttu-id="f1643-234">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="f1643-234">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="f1643-235">Aktualizovaná verze souboru třídy knihovny DLL je zkompilovat a uloží do výstupní cesta dříve zadané sestavení (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="f1643-235">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="f1643-236">V Průzkumníku souborů otevřete složku výstupu cestu (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="f1643-236">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="f1643-237">Dvakrát klikněte na TypeEquivalenceClient.exe ke spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="f1643-237">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="f1643-238">Program se projeví novou verzi sestavení TypeEquivalenceRuntime bez nutnosti znovu kompilovány.</span><span class="sxs-lookup"><span data-stu-id="f1643-238">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1643-239">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1643-239">See Also</span></span>  
 [<span data-ttu-id="f1643-240">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1643-240">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)  
 [<span data-ttu-id="f1643-241">Koncepty programování</span><span class="sxs-lookup"><span data-stu-id="f1643-241">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="f1643-242">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="f1643-242">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="f1643-243">Sestavení a globální mezipaměti sestavení (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1643-243">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
