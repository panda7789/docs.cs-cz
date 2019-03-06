---
title: 'Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 836d035aab06f18c13e3675fbd72c5ab9879a3d2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359453"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="47972-102">Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47972-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>

<span data-ttu-id="47972-103">Pokud jste pro vložení informací o typu ze spravovaných sestavení se silným názvem, můžete volně zkombinujte typy v aplikaci dosáhnout nezávislosti na verzi.</span><span class="sxs-lookup"><span data-stu-id="47972-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="47972-104">To znamená váš program může zapisovat používat typy z více verzí aplikace spravované knihovny aniž byste museli překompilují. pro každou verzi.</span><span class="sxs-lookup"><span data-stu-id="47972-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>

<span data-ttu-id="47972-105">Typ vložení se často používá se spoluprací COM, jako je například aplikace, která používá objekty automatizace z aplikace Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="47972-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="47972-106">Vložení informací o typu umožňuje jednomu sestavení programu pracovat s různými verzemi sady Microsoft Office na různých počítačích.</span><span class="sxs-lookup"><span data-stu-id="47972-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="47972-107">Ale můžete použít také typ vkládání pomocí plně spravované řešení.</span><span class="sxs-lookup"><span data-stu-id="47972-107">However, you can also use type embedding with a fully managed solution.</span></span>

<span data-ttu-id="47972-108">Lze jej vkládat informace o typu ze sestavení, která má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="47972-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>

- <span data-ttu-id="47972-109">Sestavení poskytuje aspoň jedno veřejných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47972-109">The assembly exposes at least one public interface.</span></span>

- <span data-ttu-id="47972-110">Vložená rozhraní je opatřen poznámkou `ComImport` atribut a `Guid` atribut (a jedinečný identifikátor GUID).</span><span class="sxs-lookup"><span data-stu-id="47972-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>

- <span data-ttu-id="47972-111">Sestavení je opatřen poznámkou `ImportedFromTypeLib` atribut nebo `PrimaryInteropAssembly` atribut a úrovni sestavení `Guid` atribut.</span><span class="sxs-lookup"><span data-stu-id="47972-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="47972-112">(Ve výchozím nastavení, zahrnují šablony projektů Visual Basic úrovni sestavení `Guid` atribut.)</span><span class="sxs-lookup"><span data-stu-id="47972-112">(By default, Visual Basic project templates include an assembly-level `Guid` attribute.)</span></span>

<span data-ttu-id="47972-113">Po zadání veřejného rozhraní, která může být vložen, můžete vytvořit modul runtime třídy, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47972-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="47972-114">Klientský program může potom můžete vložit informace o těchto rozhraní typu v době návrhu pomocí odkazu na sestavení, které obsahuje veřejné rozhraní a nastavení `Embed Interop Types` vlastnosti odkazu na `True`.</span><span class="sxs-lookup"><span data-stu-id="47972-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="47972-115">Jedná se o ekvivalent používání kompilátoru příkazového řádku a odkazování na sestavení s použitím `/link` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="47972-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="47972-116">Klientská aplikace může pak načíst instance objektů modulu runtime typu těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47972-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="47972-117">Pokud vytvoříte novou verzi vašich sestavení silným názvem modulu runtime, není potřeba klientský program překompilují se aktualizovaný modul runtime sestavení.</span><span class="sxs-lookup"><span data-stu-id="47972-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="47972-118">Místo toho klientskou aplikaci dál používat, podle toho, která verze sestavení modulu runtime je k dispozici, pomocí informací o vloženém typu pro veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47972-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="47972-119">Vzhledem k tomu, že primární funkce vkládání typ pro podporu vkládání informací o typu ze sestavení vzájemné spolupráce COM se při vložení informací o typu do plně spravované řešení platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="47972-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>

- <span data-ttu-id="47972-120">Jsou vloženy pouze atributy specifické pro zprostředkovatele komunikace s objekty COM; Další atributy se ignorují.</span><span class="sxs-lookup"><span data-stu-id="47972-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>

- <span data-ttu-id="47972-121">Pokud typ používá obecné parametry a vložený typ je typ obecný parametr, tento typ nelze použít přes hranice sestavení.</span><span class="sxs-lookup"><span data-stu-id="47972-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="47972-122">Příklady přes hranice sestavení, jsou volání metody z jiného sestavení nebo typ odvozený od typu definované v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="47972-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>

- <span data-ttu-id="47972-123">Konstanty nejsou vložené.</span><span class="sxs-lookup"><span data-stu-id="47972-123">Constants are not embedded.</span></span>

- <span data-ttu-id="47972-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Třída nepodporuje vložený typ jako klíč.</span><span class="sxs-lookup"><span data-stu-id="47972-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="47972-125">Můžete implementovat vlastní typ slovníku pro podporu vložený typ jako klíč.</span><span class="sxs-lookup"><span data-stu-id="47972-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>

 <span data-ttu-id="47972-126">V tomto návodu provedete následující:</span><span class="sxs-lookup"><span data-stu-id="47972-126">In this walkthrough, you will do the following:</span></span>

- <span data-ttu-id="47972-127">Vytvořte sestavení se silným názvem, který má veřejné rozhraní, který obsahuje informace o typu, který může být vložen.</span><span class="sxs-lookup"><span data-stu-id="47972-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>

- <span data-ttu-id="47972-128">Vytvořte sestavení silným názvem modulu runtime, který implementuje veřejných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47972-128">Create a strong-named runtime assembly that implements that public interface.</span></span>

- <span data-ttu-id="47972-129">Vytvořte program klienta, který se vloží informace o typu z veřejného rozhraní a vytvoří instanci třídy v sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="47972-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>

- <span data-ttu-id="47972-130">Upravit a znovu sestavte sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="47972-130">Modify and rebuild the runtime assembly.</span></span>

- <span data-ttu-id="47972-131">Spusťte klientskou aplikaci, která věděli, že nová verze sestavení modulu runtime používá bez nutnosti znovu kompilovat program klienta.</span><span class="sxs-lookup"><span data-stu-id="47972-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a><span data-ttu-id="47972-132">Vytvoření rozhraní</span><span class="sxs-lookup"><span data-stu-id="47972-132">Creating an Interface</span></span>

#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="47972-133">Vytvoření projektu rozhraní rovnocennosti typu</span><span class="sxs-lookup"><span data-stu-id="47972-133">To create the type equivalence interface project</span></span>

1. <span data-ttu-id="47972-134">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="47972-134">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="47972-135">V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="47972-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="47972-136">Vyberte **knihovny tříd** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="47972-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="47972-137">V **název** zadejte `TypeEquivalenceInterface`a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="47972-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="47972-138">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="47972-138">The new project is created.</span></span>

3. <span data-ttu-id="47972-139">V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor Class1.vb a klikněte na tlačítko **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="47972-139">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="47972-140">Přejmenujte soubor na `ISampleInterface.vb` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="47972-140">Rename the file to `ISampleInterface.vb` and press ENTER.</span></span> <span data-ttu-id="47972-141">Přejmenování souboru se také přejmenujte třídu na `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="47972-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="47972-142">Tato třída bude reprezentovat veřejného rozhraní pro třídu.</span><span class="sxs-lookup"><span data-stu-id="47972-142">This class will represent the public interface for the class.</span></span>

4. <span data-ttu-id="47972-143">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="47972-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="47972-144">Klikněte na tlačítko **kompilaci** kartu. Nastavte výstupní cesta platná umístění na vašem vývojovém počítači, jako je třeba `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="47972-144">Click the **Compile** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="47972-145">Toto umístění se taky použije v pozdějším kroku v tomto názorném postupu.</span><span class="sxs-lookup"><span data-stu-id="47972-145">This location will also be used in a later step in this walkthrough.</span></span>

5. <span data-ttu-id="47972-146">Při úpravách stále vlastnosti projektu, klikněte na tlačítko **podepisování** kartu. Vyberte **podepsat sestavení** možnost.</span><span class="sxs-lookup"><span data-stu-id="47972-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="47972-147">V **vyberte soubor klíče se silným názvem** klikněte na možnost **< Nový … >**.</span><span class="sxs-lookup"><span data-stu-id="47972-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="47972-148">V **název souboru klíče** zadejte `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="47972-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="47972-149">Zrušte **chránit můj soubor klíče s heslem** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="47972-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="47972-150">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="47972-150">Click **OK**.</span></span>

6. <span data-ttu-id="47972-151">Otevřete soubor ISampleInterface.vb.</span><span class="sxs-lookup"><span data-stu-id="47972-151">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="47972-152">Přidejte následující kód do souboru třídy ISampleInterface k vytvoření ISampleInterface rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47972-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>

    ```vb
    Imports System.Runtime.InteropServices

    <ComImport()>
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
    Public Interface ISampleInterface
        Sub GetUserInput()
        ReadOnly Property UserInput As String
    End Interface
    ```

7. <span data-ttu-id="47972-153">Na **nástroje** nabídky, klikněte na tlačítko **Create Guid**.</span><span class="sxs-lookup"><span data-stu-id="47972-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="47972-154">V **Create GUID** dialogové okno, klikněte na tlačítko **formát registru** a potom klikněte na tlačítko **kopírování**.</span><span class="sxs-lookup"><span data-stu-id="47972-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="47972-155">Klikněte na tlačítko **ukončovací**.</span><span class="sxs-lookup"><span data-stu-id="47972-155">Click **Exit**.</span></span>

8. <span data-ttu-id="47972-156">V `Guid` atribut, odstraňte ukázkový identifikátor GUID a vložte identifikátor GUID, který jste zkopírovali **Create GUID** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="47972-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="47972-157">Odebrat složené závorky ({}) ze zkopírovaného identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="47972-157">Remove the braces ({}) from the copied GUID.</span></span>

9. <span data-ttu-id="47972-158">Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="47972-158">On the **Project** menu, click **Show All Files**.</span></span>

10. <span data-ttu-id="47972-159">V **Průzkumníka řešení**, rozbalte **Můj projekt** složky.</span><span class="sxs-lookup"><span data-stu-id="47972-159">In **Solution Explorer**, expand the **My Project** folder.</span></span> <span data-ttu-id="47972-160">Dvakrát klikněte AssemblyInfo.vb.</span><span class="sxs-lookup"><span data-stu-id="47972-160">Double-click the AssemblyInfo.vb.</span></span> <span data-ttu-id="47972-161">Přidejte následující atribut souboru.</span><span class="sxs-lookup"><span data-stu-id="47972-161">Add the following attribute to the file.</span></span>

    ```vb
    <Assembly: ImportedFromTypeLib("")>
    ```

    <span data-ttu-id="47972-162">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="47972-162">Save the file.</span></span>

11. <span data-ttu-id="47972-163">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="47972-163">Save the project.</span></span>

12. <span data-ttu-id="47972-164">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="47972-164">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="47972-165">Soubor DLL knihovny tříd je zkompilován a uloží do zadané sestavení výstupní cestu (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="47972-165">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-runtime-class"></a><span data-ttu-id="47972-166">Vytvoření třídy modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="47972-166">Creating a Runtime Class</span></span>

#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="47972-167">Vytvoření projektu typu ekvivalence modulu runtime</span><span class="sxs-lookup"><span data-stu-id="47972-167">To create the type equivalence runtime project</span></span>

1. <span data-ttu-id="47972-168">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="47972-168">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="47972-169">V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="47972-169">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="47972-170">Vyberte **knihovny tříd** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="47972-170">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="47972-171">V **název** zadejte `TypeEquivalenceRuntime`a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="47972-171">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="47972-172">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="47972-172">The new project is created.</span></span>

3. <span data-ttu-id="47972-173">V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor Class1.vb a klikněte na tlačítko **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="47972-173">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="47972-174">Přejmenujte soubor na `SampleClass.vb` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="47972-174">Rename the file to `SampleClass.vb` and press ENTER.</span></span> <span data-ttu-id="47972-175">Přejmenování souboru třídy, která se také přejmenuje `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="47972-175">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="47972-176">Tato třída implementuje `ISampleInterface` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47972-176">This class will implement the `ISampleInterface` interface.</span></span>

4. <span data-ttu-id="47972-177">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="47972-177">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="47972-178">Klikněte na tlačítko **kompilaci** kartu. Nastavte výstupní cestu do stejného umístění, například použít v projektu TypeEquivalenceInterface `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="47972-178">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

5. <span data-ttu-id="47972-179">Při úpravách stále vlastnosti projektu, klikněte na tlačítko **podepisování** kartu. Vyberte **podepsat sestavení** možnost.</span><span class="sxs-lookup"><span data-stu-id="47972-179">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="47972-180">V **vyberte soubor klíče se silným názvem** klikněte na možnost **< Nový … >**.</span><span class="sxs-lookup"><span data-stu-id="47972-180">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="47972-181">V **název souboru klíče** zadejte `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="47972-181">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="47972-182">Zrušte **chránit můj soubor klíče s heslem** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="47972-182">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="47972-183">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="47972-183">Click **OK**.</span></span>

6. <span data-ttu-id="47972-184">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="47972-184">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="47972-185">Klikněte na tlačítko **Procházet** kartu a přejděte do složky cesta pro výstup.</span><span class="sxs-lookup"><span data-stu-id="47972-185">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="47972-186">Vyberte soubor TypeEquivalenceInterface.dll a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="47972-186">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>

7. <span data-ttu-id="47972-187">Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="47972-187">On the **Project** menu, click **Show All Files**.</span></span>

8. <span data-ttu-id="47972-188">V **Průzkumníka řešení**, rozbalte **odkazy** složky.</span><span class="sxs-lookup"><span data-stu-id="47972-188">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="47972-189">Vyberte odkaz TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="47972-189">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="47972-190">V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **konkrétní verzi** vlastnost **False**.</span><span class="sxs-lookup"><span data-stu-id="47972-190">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>

9. <span data-ttu-id="47972-191">Přidejte následující kód do souboru třídy SampleClass SampleClass třídu vytvořte.</span><span class="sxs-lookup"><span data-stu-id="47972-191">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>

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

10. <span data-ttu-id="47972-192">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="47972-192">Save the project.</span></span>

11. <span data-ttu-id="47972-193">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="47972-193">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="47972-194">Soubor DLL knihovny tříd je zkompilován a uloží do zadané sestavení výstupní cestu (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="47972-194">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-client-project"></a><span data-ttu-id="47972-195">Vytvoření projektu klienta</span><span class="sxs-lookup"><span data-stu-id="47972-195">Creating a Client Project</span></span>

#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="47972-196">Vytvoření projektu klienta rovnocennosti typu</span><span class="sxs-lookup"><span data-stu-id="47972-196">To create the type equivalence client project</span></span>

1. <span data-ttu-id="47972-197">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="47972-197">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="47972-198">V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="47972-198">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="47972-199">Vyberte **konzolovou aplikaci** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="47972-199">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="47972-200">V **název** zadejte `TypeEquivalenceClient`a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="47972-200">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="47972-201">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="47972-201">The new project is created.</span></span>

3. <span data-ttu-id="47972-202">Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="47972-202">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="47972-203">Klikněte na tlačítko **kompilaci** kartu. Nastavte výstupní cestu do stejného umístění, například použít v projektu TypeEquivalenceInterface `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="47972-203">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

4. <span data-ttu-id="47972-204">Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="47972-204">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="47972-205">Klikněte na tlačítko **Procházet** kartu a přejděte do složky cesta pro výstup.</span><span class="sxs-lookup"><span data-stu-id="47972-205">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="47972-206">Vyberte soubor TypeEquivalenceInterface.dll (ne TypeEquivalenceRuntime.dll) a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="47972-206">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>

5. <span data-ttu-id="47972-207">Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="47972-207">On the **Project** menu, click **Show All Files**.</span></span>

6. <span data-ttu-id="47972-208">V **Průzkumníka řešení**, rozbalte **odkazy** složky.</span><span class="sxs-lookup"><span data-stu-id="47972-208">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="47972-209">Vyberte odkaz TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="47972-209">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="47972-210">V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **Embed Interop Types** vlastnost **True**.</span><span class="sxs-lookup"><span data-stu-id="47972-210">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>

7. <span data-ttu-id="47972-211">Přidejte následující kód do souboru Module1.vb vytvořit klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="47972-211">Add the following code to the Module1.vb file to create the client program.</span></span>

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

8. <span data-ttu-id="47972-212">Stisknutím kláves CTRL + F5 sestavte a spusťte program.</span><span class="sxs-lookup"><span data-stu-id="47972-212">Press CTRL+F5 to build and run the program.</span></span>

## <a name="modifying-the-interface"></a><span data-ttu-id="47972-213">Úprava rozhraní</span><span class="sxs-lookup"><span data-stu-id="47972-213">Modifying the Interface</span></span>

#### <a name="to-modify-the-interface"></a><span data-ttu-id="47972-214">Chcete-li změnit rozhraní</span><span class="sxs-lookup"><span data-stu-id="47972-214">To modify the interface</span></span>

1. <span data-ttu-id="47972-215">V sadě Visual Studio na **souboru** nabídky, přejděte k **otevřít**a potom klikněte na tlačítko **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="47972-215">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="47972-216">V **otevřít projekt** dialogové okno, klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a potom klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="47972-216">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="47972-217">Klikněte na tlačítko **aplikace** kartu. Klikněte na tlačítko **informace o sestavení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="47972-217">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="47972-218">Změnit **verze sestavení** a **verze souboru** hodnoty `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="47972-218">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="47972-219">Otevřete soubor ISampleInterface.vb.</span><span class="sxs-lookup"><span data-stu-id="47972-219">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="47972-220">Přidejte následující řádek kódu do rozhraní ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="47972-220">Add the following line of code to the ISampleInterface interface.</span></span>

    ```vb
    Function GetDate() As Date
    ```

    <span data-ttu-id="47972-221">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="47972-221">Save the file.</span></span>

4. <span data-ttu-id="47972-222">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="47972-222">Save the project.</span></span>

5. <span data-ttu-id="47972-223">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="47972-223">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="47972-224">Novou verzi souboru DLL knihovny třídy je zkompilován a uloží do zadané výstupní cesty zadané sestavení (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="47972-224">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="modifying-the-runtime-class"></a><span data-ttu-id="47972-225">Úprava třídy modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="47972-225">Modifying the Runtime Class</span></span>

#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="47972-226">Chcete-li změnit třídy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="47972-226">To modify the runtime class</span></span>

1. <span data-ttu-id="47972-227">V sadě Visual Studio na **souboru** nabídky, přejděte k **otevřít**a potom klikněte na tlačítko **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="47972-227">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="47972-228">V **otevřít projekt** dialogovém poli, klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="47972-228">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="47972-229">Klikněte na tlačítko **aplikace** kartu. Klikněte na tlačítko **informace o sestavení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="47972-229">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="47972-230">Změnit **verze sestavení** a **verze souboru** hodnoty `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="47972-230">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="47972-231">Otevřete soubor SampleClass.vb.</span><span class="sxs-lookup"><span data-stu-id="47972-231">Open the SampleClass.vb file.</span></span> <span data-ttu-id="47972-232">Přidejte následující řádky kódu do třídy SampleClass.</span><span class="sxs-lookup"><span data-stu-id="47972-232">Add the following lines of code to the SampleClass class.</span></span>

```vb
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
    Return Now
End Function
```

    Save the file.

4. <span data-ttu-id="47972-233">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="47972-233">Save the project.</span></span>

5. <span data-ttu-id="47972-234">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="47972-234">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="47972-235">Aktualizovanou verzi souboru DLL knihovny třídy je zkompilován a uložen v sestavení dříve zadaná výstupní cesta (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="47972-235">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

6. <span data-ttu-id="47972-236">V Průzkumníku souborů otevřete složku výstupu cestu (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="47972-236">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="47972-237">Dvakrát klikněte na panel TypeEquivalenceClient.exe ke spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="47972-237">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="47972-238">Program bude odrážet nové verze sestavení TypeEquivalenceRuntime bez nutnosti znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="47972-238">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="47972-239">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47972-239">See also</span></span>

- [<span data-ttu-id="47972-240">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47972-240">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="47972-241">Koncepty programování</span><span class="sxs-lookup"><span data-stu-id="47972-241">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="47972-242">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="47972-242">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="47972-243">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="47972-243">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
