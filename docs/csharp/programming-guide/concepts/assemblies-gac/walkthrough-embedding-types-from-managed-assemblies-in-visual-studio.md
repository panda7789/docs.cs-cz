---
title: 'Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)'
ms.date: 07/20/2015
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
ms.openlocfilehash: ca1acab5dc08bc7790d86b0dda3b9c7f58cab10c
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57844882"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="8c50d-102">Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="8c50d-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>

<span data-ttu-id="8c50d-103">Pokud jste pro vložení informací o typu ze spravovaných sestavení se silným názvem, můžete volně zkombinujte typy v aplikaci dosáhnout nezávislosti na verzi.</span><span class="sxs-lookup"><span data-stu-id="8c50d-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="8c50d-104">To znamená váš program může zapisovat používat typy z více verzí aplikace spravované knihovny aniž byste museli překompilují. pro každou verzi.</span><span class="sxs-lookup"><span data-stu-id="8c50d-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>

<span data-ttu-id="8c50d-105">Typ vložení se často používá se spoluprací COM, jako je například aplikace, která používá objekty automatizace z aplikace Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="8c50d-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="8c50d-106">Vložení informací o typu umožňuje jednomu sestavení programu pracovat s různými verzemi sady Microsoft Office na různých počítačích.</span><span class="sxs-lookup"><span data-stu-id="8c50d-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="8c50d-107">Ale můžete použít také typ vkládání pomocí plně spravované řešení.</span><span class="sxs-lookup"><span data-stu-id="8c50d-107">However, you can also use type embedding with a fully managed solution.</span></span>

<span data-ttu-id="8c50d-108">Lze jej vkládat informace o typu ze sestavení, která má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="8c50d-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>

- <span data-ttu-id="8c50d-109">Sestavení poskytuje aspoň jedno veřejných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c50d-109">The assembly exposes at least one public interface.</span></span>

- <span data-ttu-id="8c50d-110">Vložená rozhraní je opatřen poznámkou `ComImport` atribut a `Guid` atribut (a jedinečný identifikátor GUID).</span><span class="sxs-lookup"><span data-stu-id="8c50d-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>

- <span data-ttu-id="8c50d-111">Sestavení je opatřen poznámkou `ImportedFromTypeLib` atribut nebo `PrimaryInteropAssembly` atribut a úrovni sestavení `Guid` atribut.</span><span class="sxs-lookup"><span data-stu-id="8c50d-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="8c50d-112">(Ve výchozím nastavení, zahrnují šablony projektů Visual C# úrovni sestavení `Guid` atribut.)</span><span class="sxs-lookup"><span data-stu-id="8c50d-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>

<span data-ttu-id="8c50d-113">Po zadání veřejného rozhraní, která může být vložen, můžete vytvořit modul runtime třídy, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c50d-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="8c50d-114">Klientský program může potom můžete vložit informace o těchto rozhraní typu v době návrhu pomocí odkazu na sestavení, které obsahuje veřejné rozhraní a nastavení `Embed Interop Types` vlastnosti odkazu na `True`.</span><span class="sxs-lookup"><span data-stu-id="8c50d-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="8c50d-115">Jedná se o ekvivalent používání kompilátoru příkazového řádku a odkazování na sestavení s použitím `/link` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8c50d-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="8c50d-116">Klientská aplikace může pak načíst instance objektů modulu runtime typu těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c50d-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="8c50d-117">Pokud vytvoříte novou verzi vašich sestavení silným názvem modulu runtime, není potřeba klientský program překompilují se aktualizovaný modul runtime sestavení.</span><span class="sxs-lookup"><span data-stu-id="8c50d-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="8c50d-118">Místo toho klientskou aplikaci dál používat, podle toho, která verze sestavení modulu runtime je k dispozici, pomocí informací o vloženém typu pro veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c50d-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="8c50d-119">Vzhledem k tomu, že primární funkce vkládání typ pro podporu vkládání informací o typu ze sestavení vzájemné spolupráce COM se při vložení informací o typu do plně spravované řešení platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="8c50d-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>

- <span data-ttu-id="8c50d-120">Jsou vloženy pouze atributy specifické pro zprostředkovatele komunikace s objekty COM; Další atributy se ignorují.</span><span class="sxs-lookup"><span data-stu-id="8c50d-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>

- <span data-ttu-id="8c50d-121">Pokud typ používá obecné parametry a vložený typ je typ obecný parametr, tento typ nelze použít přes hranice sestavení.</span><span class="sxs-lookup"><span data-stu-id="8c50d-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="8c50d-122">Příklady přes hranice sestavení, jsou volání metody z jiného sestavení nebo typ odvozený od typu definované v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="8c50d-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>

- <span data-ttu-id="8c50d-123">Konstanty nejsou vložené.</span><span class="sxs-lookup"><span data-stu-id="8c50d-123">Constants are not embedded.</span></span>

- <span data-ttu-id="8c50d-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Třída nepodporuje vložený typ jako klíč.</span><span class="sxs-lookup"><span data-stu-id="8c50d-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="8c50d-125">Můžete implementovat vlastní typ slovníku pro podporu vložený typ jako klíč.</span><span class="sxs-lookup"><span data-stu-id="8c50d-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>

<span data-ttu-id="8c50d-126">V tomto návodu provedete následující:</span><span class="sxs-lookup"><span data-stu-id="8c50d-126">In this walkthrough, you will do the following:</span></span>

- <span data-ttu-id="8c50d-127">Vytvořte sestavení se silným názvem, který má veřejné rozhraní, který obsahuje informace o typu, který může být vložen.</span><span class="sxs-lookup"><span data-stu-id="8c50d-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>

- <span data-ttu-id="8c50d-128">Vytvořte sestavení silným názvem modulu runtime, který implementuje veřejných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c50d-128">Create a strong-named runtime assembly that implements that public interface.</span></span>

- <span data-ttu-id="8c50d-129">Vytvořte program klienta, který se vloží informace o typu z veřejného rozhraní a vytvoří instanci třídy v sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8c50d-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>

- <span data-ttu-id="8c50d-130">Upravit a znovu sestavte sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8c50d-130">Modify and rebuild the runtime assembly.</span></span>

- <span data-ttu-id="8c50d-131">Spusťte klientskou aplikaci, která věděli, že nová verze sestavení modulu runtime používá bez nutnosti znovu kompilovat program klienta.</span><span class="sxs-lookup"><span data-stu-id="8c50d-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a><span data-ttu-id="8c50d-132">Vytvoření rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c50d-132">Creating an Interface</span></span>

#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="8c50d-133">Vytvoření projektu rozhraní rovnocennosti typu</span><span class="sxs-lookup"><span data-stu-id="8c50d-133">To create the type equivalence interface project</span></span>

1. <span data-ttu-id="8c50d-134">V sadě Visual Studio na **souboru** nabídce zvolte **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>

2. <span data-ttu-id="8c50d-135">V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="8c50d-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="8c50d-136">Vyberte **knihovny tříd** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="8c50d-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="8c50d-137">V **název** zadejte `TypeEquivalenceInterface`a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="8c50d-138">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="8c50d-138">The new project is created.</span></span>

3. <span data-ttu-id="8c50d-139">V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor Class1.cs a klikněte na tlačítko **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="8c50d-140">Přejmenujte soubor na `ISampleInterface.cs` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="8c50d-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="8c50d-141">Přejmenování souboru se také přejmenujte třídu na `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="8c50d-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="8c50d-142">Tato třída bude reprezentovat veřejného rozhraní pro třídu.</span><span class="sxs-lookup"><span data-stu-id="8c50d-142">This class will represent the public interface for the class.</span></span>

4. <span data-ttu-id="8c50d-143">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="8c50d-144">Klikněte na tlačítko **sestavení** kartu. Nastavte výstupní cesta platná umístění na vašem vývojovém počítači, jako je třeba `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="8c50d-144">Click the **Build** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="8c50d-145">Toto umístění se taky použije v pozdějším kroku v tomto názorném postupu.</span><span class="sxs-lookup"><span data-stu-id="8c50d-145">This location will also be used in a later step in this walkthrough.</span></span>

5. <span data-ttu-id="8c50d-146">Při úpravách stále vlastnosti projektu, klikněte na tlačítko **podepisování** kartu. Vyberte **podepsat sestavení** možnost.</span><span class="sxs-lookup"><span data-stu-id="8c50d-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="8c50d-147">V **vyberte soubor klíče se silným názvem** klikněte na možnost  **\<nový... >**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-147">In the **Choose a strong name key file** list, click **\<New...>**.</span></span> <span data-ttu-id="8c50d-148">V **název souboru klíče** zadejte `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="8c50d-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="8c50d-149">Zrušte **chránit můj soubor klíče s heslem** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="8c50d-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="8c50d-150">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-150">Click **OK**.</span></span>

6. <span data-ttu-id="8c50d-151">Otevřete soubor ISampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="8c50d-151">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="8c50d-152">Přidejte následující kód do souboru třídy ISampleInterface k vytvoření ISampleInterface rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c50d-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace TypeEquivalenceInterface
    {
        [ComImport]
        [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
        public interface ISampleInterface
        {
            void GetUserInput();
            string UserInput { get; }
        }
    }
    ```

7. <span data-ttu-id="8c50d-153">Na **nástroje** nabídky, klikněte na tlačítko **Create Guid**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="8c50d-154">V **Create GUID** dialogové okno, klikněte na tlačítko **formát registru** a potom klikněte na tlačítko **kopírování**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="8c50d-155">Klikněte na tlačítko **ukončovací**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-155">Click **Exit**.</span></span>

8. <span data-ttu-id="8c50d-156">V `Guid` atribut, odstraňte ukázkový identifikátor GUID a vložte identifikátor GUID, který jste zkopírovali **Create GUID** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="8c50d-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="8c50d-157">Odebrat složené závorky ({}) ze zkopírovaného identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="8c50d-157">Remove the braces ({}) from the copied GUID.</span></span>

9. <span data-ttu-id="8c50d-158">V **Průzkumníka řešení**, rozbalte **vlastnosti** složky.</span><span class="sxs-lookup"><span data-stu-id="8c50d-158">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="8c50d-159">Poklikejte na soubor AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="8c50d-159">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="8c50d-160">Přidejte následující atribut souboru.</span><span class="sxs-lookup"><span data-stu-id="8c50d-160">Add the following attribute to the file.</span></span>

    ```csharp
    [assembly: ImportedFromTypeLib("")]
    ```

     <span data-ttu-id="8c50d-161">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="8c50d-161">Save the file.</span></span>

10. <span data-ttu-id="8c50d-162">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="8c50d-162">Save the project.</span></span>

11. <span data-ttu-id="8c50d-163">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-163">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="8c50d-164">Soubor DLL knihovny tříd je zkompilován a uloží do zadané sestavení výstupní cestu (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="8c50d-164">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-runtime-class"></a><span data-ttu-id="8c50d-165">Vytvoření třídy modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="8c50d-165">Creating a Runtime Class</span></span>

#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="8c50d-166">Vytvoření projektu typu ekvivalence modulu runtime</span><span class="sxs-lookup"><span data-stu-id="8c50d-166">To create the type equivalence runtime project</span></span>

1. <span data-ttu-id="8c50d-167">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-167">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="8c50d-168">V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="8c50d-168">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="8c50d-169">Vyberte **knihovny tříd** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="8c50d-169">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="8c50d-170">V **název** zadejte `TypeEquivalenceRuntime`a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-170">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="8c50d-171">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="8c50d-171">The new project is created.</span></span>

3. <span data-ttu-id="8c50d-172">V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor Class1.cs a klikněte na tlačítko **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-172">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="8c50d-173">Přejmenujte soubor na `SampleClass.cs` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="8c50d-173">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="8c50d-174">Přejmenování souboru třídy, která se také přejmenuje `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="8c50d-174">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="8c50d-175">Tato třída implementuje `ISampleInterface` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c50d-175">This class will implement the `ISampleInterface` interface.</span></span>

4. <span data-ttu-id="8c50d-176">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-176">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="8c50d-177">Klikněte na tlačítko **sestavení** kartu. Nastavte výstupní cestu do stejného umístění, například použít v projektu TypeEquivalenceInterface `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="8c50d-177">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

5. <span data-ttu-id="8c50d-178">Při úpravách stále vlastnosti projektu, klikněte na tlačítko **podepisování** kartu. Vyberte **podepsat sestavení** možnost.</span><span class="sxs-lookup"><span data-stu-id="8c50d-178">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="8c50d-179">V **vyberte soubor klíče se silným názvem** klikněte na možnost  **\<nový... >**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-179">In the **Choose a strong name key file** list, click **\<New...>**.</span></span> <span data-ttu-id="8c50d-180">V **název souboru klíče** zadejte `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="8c50d-180">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="8c50d-181">Zrušte **chránit můj soubor klíče s heslem** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="8c50d-181">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="8c50d-182">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-182">Click **OK**.</span></span>

6. <span data-ttu-id="8c50d-183">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-183">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="8c50d-184">Klikněte na tlačítko **Procházet** kartu a přejděte do složky cesta pro výstup.</span><span class="sxs-lookup"><span data-stu-id="8c50d-184">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="8c50d-185">Vyberte soubor TypeEquivalenceInterface.dll a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-185">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>

7. <span data-ttu-id="8c50d-186">V **Průzkumníka řešení**, rozbalte **odkazy** složky.</span><span class="sxs-lookup"><span data-stu-id="8c50d-186">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="8c50d-187">Vyberte odkaz TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="8c50d-187">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="8c50d-188">V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **konkrétní verzi** vlastnost **False**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-188">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>

8. <span data-ttu-id="8c50d-189">Přidejte následující kód do souboru třídy SampleClass SampleClass třídu vytvořte.</span><span class="sxs-lookup"><span data-stu-id="8c50d-189">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using TypeEquivalenceInterface;

    namespace TypeEquivalenceRuntime
    {
        public class SampleClass : ISampleInterface
        {
            private string p_UserInput;
            public string UserInput { get { return p_UserInput; } }

            public void GetUserInput()
            {
                Console.WriteLine("Please enter a value:");
                p_UserInput = Console.ReadLine();
            }
        }
    }
    ```

9. <span data-ttu-id="8c50d-190">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="8c50d-190">Save the project.</span></span>

10. <span data-ttu-id="8c50d-191">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-191">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="8c50d-192">Soubor DLL knihovny tříd je zkompilován a uloží do zadané sestavení výstupní cestu (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="8c50d-192">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-client-project"></a><span data-ttu-id="8c50d-193">Vytvoření projektu klienta</span><span class="sxs-lookup"><span data-stu-id="8c50d-193">Creating a Client Project</span></span>

#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="8c50d-194">Vytvoření projektu klienta rovnocennosti typu</span><span class="sxs-lookup"><span data-stu-id="8c50d-194">To create the type equivalence client project</span></span>

1. <span data-ttu-id="8c50d-195">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-195">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="8c50d-196">V **nový projekt** v dialogu **typy projektů** podokno, ujistěte se, že **Windows** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="8c50d-196">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="8c50d-197">Vyberte **konzolovou aplikaci** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="8c50d-197">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="8c50d-198">V **název** zadejte `TypeEquivalenceClient`a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-198">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="8c50d-199">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="8c50d-199">The new project is created.</span></span>

3. <span data-ttu-id="8c50d-200">Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-200">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="8c50d-201">Klikněte na tlačítko **sestavení** kartu. Nastavte výstupní cestu do stejného umístění, například použít v projektu TypeEquivalenceInterface `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="8c50d-201">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

4. <span data-ttu-id="8c50d-202">Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-202">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="8c50d-203">Klikněte na tlačítko **Procházet** kartu a přejděte do složky cesta pro výstup.</span><span class="sxs-lookup"><span data-stu-id="8c50d-203">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="8c50d-204">Vyberte soubor TypeEquivalenceInterface.dll (ne TypeEquivalenceRuntime.dll) a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-204">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>

5. <span data-ttu-id="8c50d-205">V **Průzkumníka řešení**, rozbalte **odkazy** složky.</span><span class="sxs-lookup"><span data-stu-id="8c50d-205">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="8c50d-206">Vyberte odkaz TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="8c50d-206">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="8c50d-207">V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **Embed Interop Types** vlastnost **True**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-207">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>

6. <span data-ttu-id="8c50d-208">Přidejte následující kód do souboru Program.cs vytvořte klientský program.</span><span class="sxs-lookup"><span data-stu-id="8c50d-208">Add the following code to the Program.cs file to create the client program.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using TypeEquivalenceInterface;
    using System.Reflection;

    namespace TypeEquivalenceClient
    {
        class Program
        {
            static void Main(string[] args)
            {
                Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
                ISampleInterface sampleClass =
                    (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
                sampleClass.GetUserInput();
                Console.WriteLine(sampleClass.UserInput);
                Console.WriteLine(sampleAssembly.GetName().Version.ToString());
                Console.ReadLine();
            }
        }
    }
    ```

7. <span data-ttu-id="8c50d-209">Stisknutím kláves CTRL + F5 sestavte a spusťte program.</span><span class="sxs-lookup"><span data-stu-id="8c50d-209">Press CTRL+F5 to build and run the program.</span></span>

## <a name="modifying-the-interface"></a><span data-ttu-id="8c50d-210">Úprava rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c50d-210">Modifying the Interface</span></span>

#### <a name="to-modify-the-interface"></a><span data-ttu-id="8c50d-211">Chcete-li změnit rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c50d-211">To modify the interface</span></span>

1. <span data-ttu-id="8c50d-212">V sadě Visual Studio na **souboru** nabídky, přejděte k **otevřít**a potom klikněte na tlačítko **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-212">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="8c50d-213">V **otevřít projekt** dialogové okno, klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a potom klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-213">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="8c50d-214">Klikněte na tlačítko **aplikace** kartu. Klikněte na tlačítko **informace o sestavení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8c50d-214">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="8c50d-215">Změnit **verze sestavení** a **verze souboru** hodnoty `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="8c50d-215">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="8c50d-216">Otevřete soubor SampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="8c50d-216">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="8c50d-217">Přidejte následující řádek kódu do rozhraní ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="8c50d-217">Add the following line of code to the ISampleInterface interface.</span></span>

    ```csharp
    DateTime GetDate();
    ```

    <span data-ttu-id="8c50d-218">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="8c50d-218">Save the file.</span></span>

4. <span data-ttu-id="8c50d-219">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="8c50d-219">Save the project.</span></span>

5. <span data-ttu-id="8c50d-220">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-220">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="8c50d-221">Novou verzi souboru DLL knihovny třídy je zkompilován a uloží do zadané výstupní cesty zadané sestavení (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="8c50d-221">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="modifying-the-runtime-class"></a><span data-ttu-id="8c50d-222">Úprava třídy modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="8c50d-222">Modifying the Runtime Class</span></span>

#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="8c50d-223">Chcete-li změnit třídy modulu runtime</span><span class="sxs-lookup"><span data-stu-id="8c50d-223">To modify the runtime class</span></span>

1. <span data-ttu-id="8c50d-224">V sadě Visual Studio na **souboru** nabídky, přejděte k **otevřít**a potom klikněte na tlačítko **projekt či řešení**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="8c50d-225">V **otevřít projekt** dialogovém poli, klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-225">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="8c50d-226">Klikněte na tlačítko **aplikace** kartu. Klikněte na tlačítko **informace o sestavení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8c50d-226">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="8c50d-227">Změnit **verze sestavení** a **verze souboru** hodnoty `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="8c50d-227">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="8c50d-228">Otevřete soubor SampleClass.cs.</span><span class="sxs-lookup"><span data-stu-id="8c50d-228">Open the SampleClass.cs file.</span></span> <span data-ttu-id="8c50d-229">Přidejte následující řádky kódu do třídy SampleClass.</span><span class="sxs-lookup"><span data-stu-id="8c50d-229">Add the following lines of code to the SampleClass class.</span></span>

    ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
    ```

    <span data-ttu-id="8c50d-230">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="8c50d-230">Save the file.</span></span>

4. <span data-ttu-id="8c50d-231">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="8c50d-231">Save the project.</span></span>

5. <span data-ttu-id="8c50d-232">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="8c50d-232">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="8c50d-233">Aktualizovanou verzi souboru DLL knihovny třídy je zkompilován a uložen v sestavení dříve zadaná výstupní cesta (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="8c50d-233">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

6. <span data-ttu-id="8c50d-234">V Průzkumníku souborů otevřete složku výstupu cestu (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="8c50d-234">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="8c50d-235">Dvakrát klikněte na panel TypeEquivalenceClient.exe ke spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="8c50d-235">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="8c50d-236">Program bude odrážet nové verze sestavení TypeEquivalenceRuntime bez nutnosti znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="8c50d-236">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c50d-237">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c50d-237">See also</span></span>

- [<span data-ttu-id="8c50d-238">/ Link (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="8c50d-238">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="8c50d-239">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8c50d-239">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8c50d-240">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="8c50d-240">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="8c50d-241">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="8c50d-241">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
