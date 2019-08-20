---
title: 'Návod: Vložení typů ze spravovaných sestavení v aplikaci Visual StudioC#()'
ms.date: 07/20/2015
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
ms.openlocfilehash: 5e6494f133128e3982aa07323d2c65b9fa5de47b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595805"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="fb941-102">Návod: Vložení typů ze spravovaných sestavení v aplikaci Visual StudioC#()</span><span class="sxs-lookup"><span data-stu-id="fb941-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>

<span data-ttu-id="fb941-103">Pokud vložíte informace o typu ze spravovaného sestavení se silným názvem, můžete volně kombinovat typy v aplikaci, aby se dosáhlo nezávislosti verzí.</span><span class="sxs-lookup"><span data-stu-id="fb941-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="fb941-104">To znamená, že program může být napsán tak, aby používal typy z více verzí spravované knihovny, aniž by bylo nutné znovu kompilovat pro každou verzi.</span><span class="sxs-lookup"><span data-stu-id="fb941-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>

<span data-ttu-id="fb941-105">Vkládání typů se často používá u zprostředkovatele komunikace s objekty COM, jako je například aplikace, která používá automatizační objekty z systém Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="fb941-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="fb941-106">Vložení informací o typu umožňuje stejné sestavení programu pracovat s různými verzemi systém Microsoft Office v různých počítačích.</span><span class="sxs-lookup"><span data-stu-id="fb941-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="fb941-107">Můžete však také použít vkládání typů s plně spravovaným řešením.</span><span class="sxs-lookup"><span data-stu-id="fb941-107">However, you can also use type embedding with a fully managed solution.</span></span>

<span data-ttu-id="fb941-108">Informace o typu mohou být vloženy ze sestavení, které má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="fb941-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>

- <span data-ttu-id="fb941-109">Sestavení zveřejňuje alespoň jedno veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb941-109">The assembly exposes at least one public interface.</span></span>

- <span data-ttu-id="fb941-110">Vložená rozhraní jsou opatřena `ComImport` atributem `Guid` a atributem (a jedinečným identifikátorem GUID).</span><span class="sxs-lookup"><span data-stu-id="fb941-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>

- <span data-ttu-id="fb941-111">Sestavení je opatřeno poznámkou `ImportedFromTypeLib` s atributem `PrimaryInteropAssembly` nebo atributem a atributem na `Guid` úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="fb941-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="fb941-112">(Ve výchozím nastavení šablony C# Visual Projectu zahrnují atribut na úrovni `Guid` sestavení.)</span><span class="sxs-lookup"><span data-stu-id="fb941-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>

<span data-ttu-id="fb941-113">Po zadání veřejných rozhraní, která lze vložit, můžete vytvořit třídy modulu runtime, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb941-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="fb941-114">Klientský program pak může vložit informace o typu pro tato rozhraní v době návrhu odkazem na sestavení, které obsahuje veřejné rozhraní a nastavením `Embed Interop Types` vlastnosti odkazu na. `True`</span><span class="sxs-lookup"><span data-stu-id="fb941-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="fb941-115">To je ekvivalentní použití kompilátoru příkazového řádku a odkazování na sestavení pomocí `/link` možnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="fb941-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="fb941-116">Klientský program pak může načíst instance objektů za běhu, které jsou zadány jako tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb941-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="fb941-117">Pokud vytvoříte novou verzi sestavení modulu runtime se silným názvem, není nutné znovu kompilovat klientský program s aktualizovaným sestavením modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="fb941-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="fb941-118">Místo toho bude mít klientský program nadále k dispozici jakoukoli verzi sestavení modulu runtime s použitím vložených informací o typu pro veřejná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb941-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="fb941-119">Vzhledem k tomu, že primární funkce vloženého typu je podpora vkládání informací o typu ze sestavení spolupracujících s objekty COM, platí při vložení informací o typu do plně spravovaného řešení následující omezení:</span><span class="sxs-lookup"><span data-stu-id="fb941-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>

- <span data-ttu-id="fb941-120">Jsou vložené pouze atributy specifické pro zprostředkovatele komunikace s objekty COM. ostatní atributy se ignorují.</span><span class="sxs-lookup"><span data-stu-id="fb941-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>

- <span data-ttu-id="fb941-121">Pokud typ používá obecné parametry a typ obecného parametru je vložený typ, tento typ nelze použít napříč hranicí sestavení.</span><span class="sxs-lookup"><span data-stu-id="fb941-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="fb941-122">Příklady křížení hranice sestavení zahrnují volání metody z jiného sestavení nebo odvození typu z typu definovaného v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="fb941-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>

- <span data-ttu-id="fb941-123">Konstanty nejsou vloženy.</span><span class="sxs-lookup"><span data-stu-id="fb941-123">Constants are not embedded.</span></span>

- <span data-ttu-id="fb941-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Třída nepodporuje vložený typ jako klíč.</span><span class="sxs-lookup"><span data-stu-id="fb941-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="fb941-125">Můžete implementovat vlastní typ slovníku pro podporu vloženého typu jako klíče.</span><span class="sxs-lookup"><span data-stu-id="fb941-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>

<span data-ttu-id="fb941-126">V tomto návodu provedete následující akce:</span><span class="sxs-lookup"><span data-stu-id="fb941-126">In this walkthrough, you will do the following:</span></span>

- <span data-ttu-id="fb941-127">Vytvořte sestavení se silným názvem, které má veřejné rozhraní obsahující informace o typu, které mohou být vloženy.</span><span class="sxs-lookup"><span data-stu-id="fb941-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>

- <span data-ttu-id="fb941-128">Vytvořte sestavení modulu runtime se silným názvem, které implementuje toto veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb941-128">Create a strong-named runtime assembly that implements that public interface.</span></span>

- <span data-ttu-id="fb941-129">Vytvořte klientský program, který vloží informace o typu z veřejného rozhraní a vytvoří instanci třídy ze sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="fb941-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>

- <span data-ttu-id="fb941-130">Upravte a znovu sestavte sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="fb941-130">Modify and rebuild the runtime assembly.</span></span>

- <span data-ttu-id="fb941-131">Spusťte klientský program, aby bylo vidět, že se nová verze sestavení modulu runtime používá, aniž by bylo nutné znovu kompilovat klientský program.</span><span class="sxs-lookup"><span data-stu-id="fb941-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a><span data-ttu-id="fb941-132">Vytvoření rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb941-132">Creating an Interface</span></span>

#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="fb941-133">Vytvoření projektu rozhraní ekvivalenci typů</span><span class="sxs-lookup"><span data-stu-id="fb941-133">To create the type equivalence interface project</span></span>

1. <span data-ttu-id="fb941-134">V aplikaci Visual Studio v nabídce **soubor** zvolte možnost **Nový** a poté klikněte na možnost **projekt**.</span><span class="sxs-lookup"><span data-stu-id="fb941-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>

2. <span data-ttu-id="fb941-135">V dialogovém okně **Nový projekt** v podokně **typy projektů** se ujistěte, že je vybrána možnost **Windows** .</span><span class="sxs-lookup"><span data-stu-id="fb941-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="fb941-136">V podokně **šablony** vyberte **Knihovna tříd** .</span><span class="sxs-lookup"><span data-stu-id="fb941-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="fb941-137">Do pole **název** zadejte `TypeEquivalenceInterface`a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="fb941-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="fb941-138">Vytvoří se nový projekt.</span><span class="sxs-lookup"><span data-stu-id="fb941-138">The new project is created.</span></span>

3. <span data-ttu-id="fb941-139">V **Průzkumník řešení**klikněte pravým tlačítkem na soubor Class1.cs a klikněte na **Přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="fb941-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="fb941-140">Přejmenujte soubor `ISampleInterface.cs` na a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="fb941-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="fb941-141">Přejmenováním souboru dojde také k přejmenování třídy na `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="fb941-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="fb941-142">Tato třída bude představovat veřejné rozhraní pro třídu.</span><span class="sxs-lookup"><span data-stu-id="fb941-142">This class will represent the public interface for the class.</span></span>

4. <span data-ttu-id="fb941-143">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fb941-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="fb941-144">Klikněte na kartu **sestavení** . Nastavte výstupní cestu na platné umístění ve vývojovém počítači, například `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="fb941-144">Click the **Build** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="fb941-145">Toto umístění bude také použito v pozdějším kroku tohoto návodu.</span><span class="sxs-lookup"><span data-stu-id="fb941-145">This location will also be used in a later step in this walkthrough.</span></span>

5. <span data-ttu-id="fb941-146">I když stále upravujete vlastnosti projektu, klikněte na kartu **podepisování** . Vyberte možnost **podepsat sestavení** .</span><span class="sxs-lookup"><span data-stu-id="fb941-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="fb941-147">V seznamu **Vyberte soubor klíče se silným názvem** klikněte na  **\<nový... >** .</span><span class="sxs-lookup"><span data-stu-id="fb941-147">In the **Choose a strong name key file** list, click **\<New...>**.</span></span> <span data-ttu-id="fb941-148">Do pole **název souboru klíče** zadejte `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="fb941-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="fb941-149">Zrušte zaškrtnutí políčka **chránit soubor klíče heslem** .</span><span class="sxs-lookup"><span data-stu-id="fb941-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="fb941-150">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="fb941-150">Click **OK**.</span></span>

6. <span data-ttu-id="fb941-151">Otevřete soubor ISampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="fb941-151">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="fb941-152">Přidejte následující kód do souboru třídy ISampleInterface a vytvořte tak rozhraní ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="fb941-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>

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

7. <span data-ttu-id="fb941-153">V nabídce **nástroje** klikněte na příkaz **vytvořit identifikátor GUID**.</span><span class="sxs-lookup"><span data-stu-id="fb941-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="fb941-154">V dialogovém okně **vytvořit GUID** klikněte na **Formát registru** a pak klikněte na **Kopírovat**.</span><span class="sxs-lookup"><span data-stu-id="fb941-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="fb941-155">Klikněte na tlačítko **ukončovací**.</span><span class="sxs-lookup"><span data-stu-id="fb941-155">Click **Exit**.</span></span>

8. <span data-ttu-id="fb941-156">V atributu odstraňte ukázkový identifikátor GUID a vložte ho do identifikátoru GUID, který jste zkopírovali v dialogovém okně **vytvořit GUID.** `Guid`</span><span class="sxs-lookup"><span data-stu-id="fb941-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="fb941-157">Odeberte složené závorky ({}) ze zkopírovaného identifikátoru GUID.</span><span class="sxs-lookup"><span data-stu-id="fb941-157">Remove the braces ({}) from the copied GUID.</span></span>

9. <span data-ttu-id="fb941-158">V **Průzkumník řešení**rozbalte složku **Properties (vlastnosti** ).</span><span class="sxs-lookup"><span data-stu-id="fb941-158">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="fb941-159">Dvakrát klikněte na soubor AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="fb941-159">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="fb941-160">Do souboru přidejte následující atribut.</span><span class="sxs-lookup"><span data-stu-id="fb941-160">Add the following attribute to the file.</span></span>

    ```csharp
    [assembly: ImportedFromTypeLib("")]
    ```

     <span data-ttu-id="fb941-161">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="fb941-161">Save the file.</span></span>

10. <span data-ttu-id="fb941-162">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="fb941-162">Save the project.</span></span>

11. <span data-ttu-id="fb941-163">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="fb941-163">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="fb941-164">Soubor Library. dll knihovny tříd je zkompilován a uložen do zadané výstupní cesty sestavení (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="fb941-164">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-runtime-class"></a><span data-ttu-id="fb941-165">Vytvoření běhové třídy</span><span class="sxs-lookup"><span data-stu-id="fb941-165">Creating a Runtime Class</span></span>

#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="fb941-166">Vytvoření projektu pro ekvivalenty typu za běhu</span><span class="sxs-lookup"><span data-stu-id="fb941-166">To create the type equivalence runtime project</span></span>

1. <span data-ttu-id="fb941-167">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="fb941-167">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="fb941-168">V dialogovém okně **Nový projekt** v podokně **typy projektů** se ujistěte, že je vybrána možnost **Windows** .</span><span class="sxs-lookup"><span data-stu-id="fb941-168">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="fb941-169">V podokně **šablony** vyberte **Knihovna tříd** .</span><span class="sxs-lookup"><span data-stu-id="fb941-169">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="fb941-170">Do pole **název** zadejte `TypeEquivalenceRuntime`a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="fb941-170">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="fb941-171">Vytvoří se nový projekt.</span><span class="sxs-lookup"><span data-stu-id="fb941-171">The new project is created.</span></span>

3. <span data-ttu-id="fb941-172">V **Průzkumník řešení**klikněte pravým tlačítkem na soubor Class1.cs a klikněte na **Přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="fb941-172">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="fb941-173">Přejmenujte soubor `SampleClass.cs` na a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="fb941-173">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="fb941-174">Přejmenování souboru také přejmenuje třídu na `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="fb941-174">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="fb941-175">Tato třída implementuje `ISampleInterface` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb941-175">This class will implement the `ISampleInterface` interface.</span></span>

4. <span data-ttu-id="fb941-176">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fb941-176">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="fb941-177">Klikněte na kartu **sestavení** . Nastavte cestu výstupu do stejného umístění, které jste použili v projektu TypeEquivalenceInterface, `C:\TypeEquivalenceSample`například.</span><span class="sxs-lookup"><span data-stu-id="fb941-177">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

5. <span data-ttu-id="fb941-178">I když stále upravujete vlastnosti projektu, klikněte na kartu **podepisování** . Vyberte možnost **podepsat sestavení** .</span><span class="sxs-lookup"><span data-stu-id="fb941-178">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="fb941-179">V seznamu **Vyberte soubor klíče se silným názvem** klikněte na  **\<nový... >** .</span><span class="sxs-lookup"><span data-stu-id="fb941-179">In the **Choose a strong name key file** list, click **\<New...>**.</span></span> <span data-ttu-id="fb941-180">Do pole **název souboru klíče** zadejte `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="fb941-180">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="fb941-181">Zrušte zaškrtnutí políčka **chránit soubor klíče heslem** .</span><span class="sxs-lookup"><span data-stu-id="fb941-181">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="fb941-182">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="fb941-182">Click **OK**.</span></span>

6. <span data-ttu-id="fb941-183">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="fb941-183">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="fb941-184">Klikněte na kartu **Procházet** a přejděte do složky výstupní cesta.</span><span class="sxs-lookup"><span data-stu-id="fb941-184">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="fb941-185">Vyberte soubor TypeEquivalenceInterface. dll a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="fb941-185">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>

7. <span data-ttu-id="fb941-186">V **Průzkumník řešení**rozbalte složku **odkazy** .</span><span class="sxs-lookup"><span data-stu-id="fb941-186">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="fb941-187">Vyberte odkaz na TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="fb941-187">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="fb941-188">V okno Vlastnosti odkazu TypeEquivalenceInterface nastavte vlastnost **specifická verze** na **hodnotu false**.</span><span class="sxs-lookup"><span data-stu-id="fb941-188">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>

8. <span data-ttu-id="fb941-189">Přidejte následující kód do souboru třídy SampleClass a vytvořte tak třídu SampleClass.</span><span class="sxs-lookup"><span data-stu-id="fb941-189">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>

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

9. <span data-ttu-id="fb941-190">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="fb941-190">Save the project.</span></span>

10. <span data-ttu-id="fb941-191">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="fb941-191">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="fb941-192">Soubor Library. dll knihovny tříd je zkompilován a uložen do zadané výstupní cesty sestavení (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="fb941-192">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-client-project"></a><span data-ttu-id="fb941-193">Vytvoření projektu klienta</span><span class="sxs-lookup"><span data-stu-id="fb941-193">Creating a Client Project</span></span>

#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="fb941-194">Vytvoření projektu klienta ekvivalenci typu</span><span class="sxs-lookup"><span data-stu-id="fb941-194">To create the type equivalence client project</span></span>

1. <span data-ttu-id="fb941-195">V sadě Visual Studio na **souboru** nabídky, přejděte k **nový** a potom klikněte na tlačítko **projektu**.</span><span class="sxs-lookup"><span data-stu-id="fb941-195">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="fb941-196">V dialogovém okně **Nový projekt** v podokně **typy projektů** se ujistěte, že je vybrána možnost **Windows** .</span><span class="sxs-lookup"><span data-stu-id="fb941-196">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="fb941-197">V podokně **šablony** vyberte **Konzolová aplikace** .</span><span class="sxs-lookup"><span data-stu-id="fb941-197">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="fb941-198">Do pole **název** zadejte `TypeEquivalenceClient`a pak klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="fb941-198">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="fb941-199">Vytvoří se nový projekt.</span><span class="sxs-lookup"><span data-stu-id="fb941-199">The new project is created.</span></span>

3. <span data-ttu-id="fb941-200">Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fb941-200">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="fb941-201">Klikněte na kartu **sestavení** . Nastavte cestu výstupu do stejného umístění, které jste použili v projektu TypeEquivalenceInterface, `C:\TypeEquivalenceSample`například.</span><span class="sxs-lookup"><span data-stu-id="fb941-201">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

4. <span data-ttu-id="fb941-202">Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="fb941-202">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="fb941-203">Klikněte na kartu **Procházet** a přejděte do složky výstupní cesta.</span><span class="sxs-lookup"><span data-stu-id="fb941-203">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="fb941-204">Vyberte soubor TypeEquivalenceInterface. dll (ne TypeEquivalenceRuntime. dll) a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="fb941-204">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>

5. <span data-ttu-id="fb941-205">V **Průzkumník řešení**rozbalte složku **odkazy** .</span><span class="sxs-lookup"><span data-stu-id="fb941-205">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="fb941-206">Vyberte odkaz na TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="fb941-206">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="fb941-207">V okno Vlastnosti odkazu TypeEquivalenceInterface nastavte vlastnost **Embed Interop Types** na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="fb941-207">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>

6. <span data-ttu-id="fb941-208">Do souboru Program.cs přidejte následující kód, který vytvoří klientský program.</span><span class="sxs-lookup"><span data-stu-id="fb941-208">Add the following code to the Program.cs file to create the client program.</span></span>

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

7. <span data-ttu-id="fb941-209">Stisknutím kombinace kláves CTRL + F5 Sestavte a spusťte program.</span><span class="sxs-lookup"><span data-stu-id="fb941-209">Press CTRL+F5 to build and run the program.</span></span>

## <a name="modifying-the-interface"></a><span data-ttu-id="fb941-210">Změna rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb941-210">Modifying the Interface</span></span>

#### <a name="to-modify-the-interface"></a><span data-ttu-id="fb941-211">Změna rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb941-211">To modify the interface</span></span>

1. <span data-ttu-id="fb941-212">V aplikaci Visual Studio v nabídce **soubor** přejděte na **otevřít**a potom klikněte na **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="fb941-212">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="fb941-213">V dialogovém okně **Otevřít projekt** klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a pak klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fb941-213">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="fb941-214">Klikněte na kartu **aplikace** . Klikněte na tlačítko **informace o sestavení** .</span><span class="sxs-lookup"><span data-stu-id="fb941-214">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="fb941-215">Změňte **verze sestavení** a hodnoty **verze souboru** na `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="fb941-215">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="fb941-216">Otevřete soubor SampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="fb941-216">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="fb941-217">Do rozhraní ISampleInterface přidejte následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="fb941-217">Add the following line of code to the ISampleInterface interface.</span></span>

    ```csharp
    DateTime GetDate();
    ```

    <span data-ttu-id="fb941-218">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="fb941-218">Save the file.</span></span>

4. <span data-ttu-id="fb941-219">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="fb941-219">Save the project.</span></span>

5. <span data-ttu-id="fb941-220">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="fb941-220">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="fb941-221">Nová verze souboru Library. dll je zkompilována a uložena do zadané výstupní cesty sestavení (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="fb941-221">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="modifying-the-runtime-class"></a><span data-ttu-id="fb941-222">Úprava běhové třídy</span><span class="sxs-lookup"><span data-stu-id="fb941-222">Modifying the Runtime Class</span></span>

#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="fb941-223">Úprava běhové třídy</span><span class="sxs-lookup"><span data-stu-id="fb941-223">To modify the runtime class</span></span>

1. <span data-ttu-id="fb941-224">V aplikaci Visual Studio v nabídce **soubor** přejděte na **otevřít**a potom klikněte na **projekt/řešení**.</span><span class="sxs-lookup"><span data-stu-id="fb941-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="fb941-225">V dialogovém okně **Otevřít projekt** klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fb941-225">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="fb941-226">Klikněte na kartu **aplikace** . Klikněte na tlačítko **informace o sestavení** .</span><span class="sxs-lookup"><span data-stu-id="fb941-226">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="fb941-227">Změňte **verze sestavení** a hodnoty **verze souboru** na `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="fb941-227">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="fb941-228">Otevřete soubor SampleClass.cs.</span><span class="sxs-lookup"><span data-stu-id="fb941-228">Open the SampleClass.cs file.</span></span> <span data-ttu-id="fb941-229">Do třídy SampleClass přidejte následující řádky kódu.</span><span class="sxs-lookup"><span data-stu-id="fb941-229">Add the following lines of code to the SampleClass class.</span></span>

    ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
    ```

    <span data-ttu-id="fb941-230">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="fb941-230">Save the file.</span></span>

4. <span data-ttu-id="fb941-231">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="fb941-231">Save the project.</span></span>

5. <span data-ttu-id="fb941-232">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="fb941-232">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="fb941-233">Aktualizovaná verze souboru Library. dll je zkompilována a uložena v dříve zadané výstupní cestě sestavení (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="fb941-233">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

6. <span data-ttu-id="fb941-234">V Průzkumníku souborů otevřete složku výstupní cesta (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="fb941-234">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="fb941-235">Dvakrát klikněte na TypeEquivalenceClient. exe a program spusťte.</span><span class="sxs-lookup"><span data-stu-id="fb941-235">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="fb941-236">Program bude odrážet novou verzi TypeEquivalenceRuntime sestavení, aniž by byla znovu zkompilována.</span><span class="sxs-lookup"><span data-stu-id="fb941-236">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb941-237">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb941-237">See also</span></span>

- [<span data-ttu-id="fb941-238">/Link (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="fb941-238">/link (C# Compiler Options)</span></span>](../../../language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="fb941-239">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fb941-239">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="fb941-240">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="fb941-240">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="fb941-241">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="fb941-241">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
