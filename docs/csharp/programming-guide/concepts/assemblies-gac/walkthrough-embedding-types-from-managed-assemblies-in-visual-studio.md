---
title: "Návod: Vložení typů z řízených sestavení v sadě Visual Studio (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cbd95c71525a92714ab5758855964e323345b2e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="d3d22-102">Návod: Vložení typů z řízených sestavení v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="d3d22-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="d3d22-103">Pokud jste pro vložení informací o typu ze spravovaných sestavení se silným názvem, můžete volně spojte typy v aplikaci k dosažení nezávislost verze.</span><span class="sxs-lookup"><span data-stu-id="d3d22-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="d3d22-104">To znamená váš program může být napsán používat typy z více verzí aplikace spravované knihovny aniž byste museli zopakovat pro každou verzi.</span><span class="sxs-lookup"><span data-stu-id="d3d22-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="d3d22-105">Typ vložení se často používá se spoluprací COM, jako je například aplikace, která používá objekty automatizace z aplikace Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="d3d22-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="d3d22-106">Vložení informací o typu umožňuje ve stejném sestavení programu pro práci s různými verzemi nástroje Microsoft Office na různých počítačích.</span><span class="sxs-lookup"><span data-stu-id="d3d22-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="d3d22-107">Však můžete použít také typu vložení v rámci řešení pro plně spravovaná.</span><span class="sxs-lookup"><span data-stu-id="d3d22-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="d3d22-108">Lze jej vkládat informace o typu ze sestavení, který má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d3d22-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="d3d22-109">Sestavení zpřístupní alespoň jeden veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d3d22-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="d3d22-110">Vložené rozhraní jsou opatřen poznámkou `ComImport` atribut a `Guid` atribut (a jedinečný identifikátor GUID).</span><span class="sxs-lookup"><span data-stu-id="d3d22-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="d3d22-111">Sestavení je opatřen poznámkou `ImportedFromTypeLib` atribut nebo `PrimaryInteropAssembly` atribut a úroveň sestavení `Guid` atribut.</span><span class="sxs-lookup"><span data-stu-id="d3d22-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="d3d22-112">(Ve výchozím nastavení, zahrnují šablony projektů Visual C# úrovni sestavení `Guid` atributů.)</span><span class="sxs-lookup"><span data-stu-id="d3d22-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="d3d22-113">Po zadání veřejného rozhraní, která může být vložen, můžete vytvořit runtime třídy, které implementují těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d3d22-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="d3d22-114">Program klienta můžete pak vložení informací o typu pro tyto rozhraní v době návrhu pomocí odkazování na sestavení, které obsahuje veřejné rozhraní a nastavení `Embed Interop Types` vlastnost odkazu na `True`.</span><span class="sxs-lookup"><span data-stu-id="d3d22-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="d3d22-115">Jde o ekvivalent pomocí příkazového řádku kompilátoru a odkazování na sestavení s použitím `/link` – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d3d22-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="d3d22-116">Program klienta pak můžete načíst instancí objektů vaší runtime, která je zadán jako těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d3d22-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="d3d22-117">Pokud vytvoříte novou verzi vašeho sestavení silným názvem modulu runtime, není nutné zopakovat s sestavení aktualizované runtime program klienta.</span><span class="sxs-lookup"><span data-stu-id="d3d22-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="d3d22-118">Místo toho program klienta budou nadále používat kteroukoli verzi modulu runtime sestavení je k dispozici, pomocí informací o vloženého typu pro veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d3d22-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="d3d22-119">Vzhledem k tomu, že primární funkce typ vnoření je podpora vložení informací o typu ze sestavení vzájemné spolupráce COM, při vložení informací o typu ve plně spravovaná řešení platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="d3d22-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="d3d22-120">Pouze atributy, které jsou specifické pro zprostředkovatele komunikace s objekty COM jsou vloženy; ostatní atributy se ignorují.</span><span class="sxs-lookup"><span data-stu-id="d3d22-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="d3d22-121">Pokud typu používá obecné parametry a typ obecný parametr je vloženého typu, typu nelze použít v hranici sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3d22-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="d3d22-122">Při překročení hranici sestavení příklady volání metody z jiného sestavení nebo typ odvozování z typu definovaný v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="d3d22-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="d3d22-123">Konstanty nejsou vložena.</span><span class="sxs-lookup"><span data-stu-id="d3d22-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="d3d22-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> Třída nepodporuje vloženého typu jako klíč.</span><span class="sxs-lookup"><span data-stu-id="d3d22-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="d3d22-125">Můžete implementovat vlastní typ slovníku pro podporu vloženého typu jako klíč.</span><span class="sxs-lookup"><span data-stu-id="d3d22-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="d3d22-126">V tomto návodu se postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="d3d22-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="d3d22-127">Vytvořte sestavení se silným názvem, který má veřejné rozhraní, který obsahuje informace o typu, kterou můžete vložit.</span><span class="sxs-lookup"><span data-stu-id="d3d22-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="d3d22-128">Vytvořte sestavení silným názvem modulu runtime, který implementuje této veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d3d22-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="d3d22-129">Vytvořte program klienta, který se vloží informací o typu ze veřejné rozhraní a vytvoří instanci třídy ze sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d3d22-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="d3d22-130">Upravit a znovu sestavte sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="d3d22-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="d3d22-131">Spusťte klientskou aplikaci, která v tématu, aby se používal novou verzi modulu runtime sestavení bez nutnosti její kompilace programu klienta.</span><span class="sxs-lookup"><span data-stu-id="d3d22-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="d3d22-132">Vytváření rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3d22-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="d3d22-133">Vytvoření projektu typu ekvivalenční rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3d22-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="d3d22-134">V sadě Visual Studio na **soubor** nabídce zvolte **nový** a pak klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="d3d22-135">V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="d3d22-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="d3d22-136">Vyberte **knihovny tříd** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="d3d22-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="d3d22-137">V **název** zadejte `TypeEquivalenceInterface`a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="d3d22-138">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="d3d22-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="d3d22-139">V **Průzkumníku řešení**, klikněte pravým tlačítkem na soubor Class1.cs a klikněte na **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="d3d22-140">Přejmenujte soubor `ISampleInterface.cs` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="d3d22-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="d3d22-141">Přejmenování souboru také přejmenuje třídy pro `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="d3d22-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="d3d22-142">Tato třída bude reprezentovat veřejné rozhraní pro třídu.</span><span class="sxs-lookup"><span data-stu-id="d3d22-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="d3d22-143">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="d3d22-144">Klikněte na **sestavení** karta. Nastavte výstupní cesta na některé platné místo ve svém vývojovém počítači, jako je třeba `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="d3d22-144">Click the the **Build** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="d3d22-145">Toto umístění se taky použije později v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="d3d22-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="d3d22-146">Při úpravách stále vlastností projektu, klikněte **podpisování** karta. Vyberte **podepsání sestavení** možnost.</span><span class="sxs-lookup"><span data-stu-id="d3d22-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="d3d22-147">V **vyberte soubor klíče se silným názvem** seznamu, klikněte na tlačítko **< nová... >**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="d3d22-148">V **název souboru klíče** zadejte `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="d3d22-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="d3d22-149">Vymazat **chránit Moje soubor klíče s heslem** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="d3d22-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="d3d22-150">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="d3d22-151">Otevřete soubor ISampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="d3d22-151">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="d3d22-152">Přidejte následující kód do souboru třídy ISampleInterface k vytvoření rozhraní ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="d3d22-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
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
  
7.  <span data-ttu-id="d3d22-153">Na **nástroje** nabídky, klikněte na tlačítko **vytvořit Guid**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="d3d22-154">V **vytvořit GUID** dialogové okno, klikněte na tlačítko **registru formátu** a pak klikněte na **kopie**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="d3d22-155">Klikněte na tlačítko **ukončení**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="d3d22-156">V `Guid` atribut, odstraňte ukázka GUID a vložte identifikátor GUID, který jste zkopírovali ze **vytvořit GUID** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="d3d22-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="d3d22-157">Odebrání zkopírovaný GUID složené závorky ({}).</span><span class="sxs-lookup"><span data-stu-id="d3d22-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="d3d22-158">V **Průzkumníku řešení**, rozbalte **vlastnosti** složky.</span><span class="sxs-lookup"><span data-stu-id="d3d22-158">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="d3d22-159">Poklikejte na soubor AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="d3d22-159">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="d3d22-160">Do souboru přidejte následující atribut.</span><span class="sxs-lookup"><span data-stu-id="d3d22-160">Add the following attribute to the file.</span></span>  
  
    ```csharp  
    [assembly: ImportedFromTypeLib("")]  
    ```  
  
     <span data-ttu-id="d3d22-161">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="d3d22-161">Save the file.</span></span>  
  
10. <span data-ttu-id="d3d22-162">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="d3d22-162">Save the project.</span></span>  
  
11. <span data-ttu-id="d3d22-163">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-163">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="d3d22-164">Soubor DLL knihovny tříd jsou kompilované a uložit na zadaná sestavení výstupní cestu (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="d3d22-164">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="d3d22-165">Vytvoření třídy modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="d3d22-165">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="d3d22-166">Vytvoření projektu typu ekvivalenční modulu runtime</span><span class="sxs-lookup"><span data-stu-id="d3d22-166">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="d3d22-167">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-167">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="d3d22-168">V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="d3d22-168">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="d3d22-169">Vyberte **knihovny tříd** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="d3d22-169">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="d3d22-170">V **název** zadejte `TypeEquivalenceRuntime`a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-170">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="d3d22-171">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="d3d22-171">The new project is created.</span></span>  
  
3.  <span data-ttu-id="d3d22-172">V **Průzkumníku řešení**, klikněte pravým tlačítkem na soubor Class1.cs a klikněte na **přejmenovat**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-172">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="d3d22-173">Přejmenujte soubor `SampleClass.cs` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="d3d22-173">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="d3d22-174">Přejmenování souboru také přejmenuje třídy pro `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="d3d22-174">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="d3d22-175">Tato třída se implementovat `ISampleInterface` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d3d22-175">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="d3d22-176">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-176">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="d3d22-177">Klikněte **sestavení** kartě. Nastavit výstupní cesta do stejného umístění, které jste použili v TypeEquivalenceInterface projektu, například `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="d3d22-177">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="d3d22-178">Při úpravách stále vlastností projektu, klikněte **podpisování** karta. Vyberte **podepsání sestavení** možnost.</span><span class="sxs-lookup"><span data-stu-id="d3d22-178">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="d3d22-179">V **vyberte soubor klíče se silným názvem** seznamu, klikněte na tlačítko **< nová... >**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-179">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="d3d22-180">V **název souboru klíče** zadejte `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="d3d22-180">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="d3d22-181">Vymazat **chránit Moje soubor klíče s heslem** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="d3d22-181">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="d3d22-182">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-182">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="d3d22-183">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-183">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="d3d22-184">Klikněte **Procházet** kartě a přejděte do složky výstupní cesta.</span><span class="sxs-lookup"><span data-stu-id="d3d22-184">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="d3d22-185">Vyberte soubor TypeEquivalenceInterface.dll a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-185">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="d3d22-186">V **Průzkumníku řešení**, rozbalte **odkazy** složky.</span><span class="sxs-lookup"><span data-stu-id="d3d22-186">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="d3d22-187">Vyberte odkaz na TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="d3d22-187">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="d3d22-188">V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **konkrétní verzi** vlastnost **False**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-188">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
8.  <span data-ttu-id="d3d22-189">Přidejte následující kód do souboru SampleClass třídy pro vytvoření třídy SampleClass.</span><span class="sxs-lookup"><span data-stu-id="d3d22-189">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
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
    )  
    ```  
  
9. <span data-ttu-id="d3d22-190">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="d3d22-190">Save the project.</span></span>  
  
10. <span data-ttu-id="d3d22-191">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-191">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="d3d22-192">Soubor DLL knihovny tříd jsou kompilované a uložit na zadaná sestavení výstupní cestu (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="d3d22-192">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="d3d22-193">Vytvoření projektu klienta</span><span class="sxs-lookup"><span data-stu-id="d3d22-193">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="d3d22-194">Vytvoření projektu klienta ekvivalenční typu</span><span class="sxs-lookup"><span data-stu-id="d3d22-194">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="d3d22-195">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **nový** a pak klikněte na **projektu**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-195">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="d3d22-196">V **nový projekt** dialogovém **typy projektů** podokně, ujistěte se, že **Windows** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="d3d22-196">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="d3d22-197">Vyberte **konzolové aplikace** v **šablony** podokně.</span><span class="sxs-lookup"><span data-stu-id="d3d22-197">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="d3d22-198">V **název** zadejte `TypeEquivalenceClient`a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-198">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="d3d22-199">Vytvoření nového projektu.</span><span class="sxs-lookup"><span data-stu-id="d3d22-199">The new project is created.</span></span>  
  
3.  <span data-ttu-id="d3d22-200">Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-200">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="d3d22-201">Klikněte **sestavení** kartě. Nastavit výstupní cesta do stejného umístění, které jste použili v TypeEquivalenceInterface projektu, například `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="d3d22-201">Click the **Build** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="d3d22-202">Klikněte pravým tlačítkem na projekt TypeEquivalenceClient a klikněte na tlačítko **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-202">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="d3d22-203">Klikněte **Procházet** kartě a přejděte do složky výstupní cesta.</span><span class="sxs-lookup"><span data-stu-id="d3d22-203">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="d3d22-204">Vyberte soubor TypeEquivalenceInterface.dll (ne TypeEquivalenceRuntime.dll) a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-204">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="d3d22-205">V **Průzkumníku řešení**, rozbalte **odkazy** složky.</span><span class="sxs-lookup"><span data-stu-id="d3d22-205">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="d3d22-206">Vyberte odkaz na TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="d3d22-206">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="d3d22-207">V okně Vlastnosti pro odkaz na TypeEquivalenceInterface nastavit **vložit zprostředkovatel komunikace s objekty typy** vlastnost **True**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-207">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
6.  <span data-ttu-id="d3d22-208">Přidejte následující kód do souboru Program.cs vytvoření programu klienta.</span><span class="sxs-lookup"><span data-stu-id="d3d22-208">Add the following code to the Program.cs file to create the client program.</span></span>  
  
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
  
7.  <span data-ttu-id="d3d22-209">Stisknutím klávesy CTRL + F5 sestavit a spustit program.</span><span class="sxs-lookup"><span data-stu-id="d3d22-209">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="d3d22-210">Úprava rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3d22-210">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="d3d22-211">Chcete-li upravit rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3d22-211">To modify the interface</span></span>  
  
1.  <span data-ttu-id="d3d22-212">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **otevřete**a potom klikněte na **projekt nebo řešení**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-212">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="d3d22-213">V **otevřeného projektu** dialogové okno, klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a pak klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-213">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="d3d22-214">Klikněte **aplikace** kartě. Klikněte **informací o sestavení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d3d22-214">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="d3d22-215">Změna **verze sestavení** a **verze souboru** hodnoty k `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="d3d22-215">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="d3d22-216">Otevřete soubor SampleInterface.cs.</span><span class="sxs-lookup"><span data-stu-id="d3d22-216">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="d3d22-217">Přidejte následující řádek kódu rozhraní ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="d3d22-217">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```csharp  
    DateTime GetDate();  
    ```  
  
     <span data-ttu-id="d3d22-218">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="d3d22-218">Save the file.</span></span>  
  
4.  <span data-ttu-id="d3d22-219">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="d3d22-219">Save the project.</span></span>  
  
5.  <span data-ttu-id="d3d22-220">Klikněte pravým tlačítkem na projekt TypeEquivalenceInterface a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-220">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="d3d22-221">Nová verze souboru třídy knihovny DLL je zkompilovat a uloží do výstupní cesta zadaná sestavení (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="d3d22-221">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="d3d22-222">Úprava Runtime – třída</span><span class="sxs-lookup"><span data-stu-id="d3d22-222">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="d3d22-223">Chcete-li upravit runtime – třída</span><span class="sxs-lookup"><span data-stu-id="d3d22-223">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="d3d22-224">V sadě Visual Studio na **soubor** nabídky, přejděte na příkaz **otevřete**a potom klikněte na **projekt nebo řešení**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="d3d22-225">V **otevřeného projektu** dialogové okno pole, klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-225">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="d3d22-226">Klikněte **aplikace** kartě. Klikněte **informací o sestavení** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d3d22-226">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="d3d22-227">Změna **verze sestavení** a **verze souboru** hodnoty k `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="d3d22-227">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="d3d22-228">Otevřete soubor SampleClass.cs.</span><span class="sxs-lookup"><span data-stu-id="d3d22-228">Open the SampleClass.cs file.</span></span> <span data-ttu-id="d3d22-229">Přidejte následující řádky kódu do třídy SampleClass.</span><span class="sxs-lookup"><span data-stu-id="d3d22-229">Add the following lines of code to the SampleClass class.</span></span>  
  
    ```csharp  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     <span data-ttu-id="d3d22-230">Uložte soubor.</span><span class="sxs-lookup"><span data-stu-id="d3d22-230">Save the file.</span></span>  
  
4.  <span data-ttu-id="d3d22-231">Uložte projekt.</span><span class="sxs-lookup"><span data-stu-id="d3d22-231">Save the project.</span></span>  
  
5.  <span data-ttu-id="d3d22-232">Klikněte pravým tlačítkem na projekt TypeEquivalenceRuntime a klikněte na tlačítko **sestavení**.</span><span class="sxs-lookup"><span data-stu-id="d3d22-232">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="d3d22-233">Aktualizovaná verze souboru třídy knihovny DLL je zkompilovat a uloží do výstupní cesta dříve zadané sestavení (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="d3d22-233">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="d3d22-234">V Průzkumníku souborů otevřete složku výstupu cestu (například C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="d3d22-234">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="d3d22-235">Dvakrát klikněte na TypeEquivalenceClient.exe ke spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="d3d22-235">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="d3d22-236">Program se projeví novou verzi sestavení TypeEquivalenceRuntime bez nutnosti znovu kompilovány.</span><span class="sxs-lookup"><span data-stu-id="d3d22-236">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d22-237">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3d22-237">See Also</span></span>  
 [<span data-ttu-id="d3d22-238">/ Link (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="d3d22-238">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)  
 [<span data-ttu-id="d3d22-239">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d3d22-239">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d3d22-240">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="d3d22-240">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="d3d22-241">Sestavení a globální mezipaměti sestavení (C#)</span><span class="sxs-lookup"><span data-stu-id="d3d22-241">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
