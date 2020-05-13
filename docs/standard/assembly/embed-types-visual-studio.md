---
title: 'Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio'
description: Tento návod ukazuje, jak vložit typy ze spravovaných sestavení v rozhraní .NET pomocí sady Visual Studio. Vložené typy mohou podporovat nezávislost verzí.
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 636e5f8095b64cd0f445555c96d00945ccf7eaf8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378988"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="0cae9-104">Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0cae9-104">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="0cae9-105">Pokud vložíte informace o typu ze spravovaného sestavení se silným názvem, můžete volně kombinovat typy v aplikaci, aby se dosáhlo nezávislosti verzí.</span><span class="sxs-lookup"><span data-stu-id="0cae9-105">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="0cae9-106">To znamená, že program může být napsán tak, aby používal typy z jakékoli verze spravované knihovny, aniž by bylo nutné znovu kompilovat pro každou novou verzi.</span><span class="sxs-lookup"><span data-stu-id="0cae9-106">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="0cae9-107">Vkládání typů se často používá u zprostředkovatele komunikace s objekty COM, jako je například aplikace, která používá automatizační objekty z systém Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="0cae9-107">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="0cae9-108">Vložení informací o typu umožňuje stejné sestavení programu pracovat s různými verzemi systém Microsoft Office v různých počítačích.</span><span class="sxs-lookup"><span data-stu-id="0cae9-108">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="0cae9-109">Můžete ale také použít vkládání typů s plně spravovanými řešeními.</span><span class="sxs-lookup"><span data-stu-id="0cae9-109">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="0cae9-110">Po zadání veřejných rozhraní, která mohou být vložena, vytvoříte třídy modulu runtime, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0cae9-110">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="0cae9-111">Klientský program může vložit informace o typu pro rozhraní v době návrhu, a to tak, že odkazuje na sestavení, které obsahuje veřejná rozhraní a nastavuje `Embed Interop Types` vlastnost odkazu na `True` .</span><span class="sxs-lookup"><span data-stu-id="0cae9-111">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="0cae9-112">Klientský program pak může načíst instance objektů za běhu, které jsou zadány jako tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0cae9-112">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="0cae9-113">To je ekvivalentní použití kompilátoru příkazového řádku a odkazování na sestavení pomocí [Možnosti kompilátoru-Link](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="0cae9-113">This is equivalent to using the command line compiler and referencing the assembly by using the [-link compiler option](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span></span>

<span data-ttu-id="0cae9-114">Vytvoříte-li novou verzi sestavení modulu runtime se silným názvem, klientský program nebude nutné znovu kompilovat.</span><span class="sxs-lookup"><span data-stu-id="0cae9-114">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="0cae9-115">Klientský program nadále používá, je-li k dispozici verze sestavení modulu runtime, používá informace vloženého typu pro veřejná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0cae9-115">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="0cae9-116">V tomto návodu:</span><span class="sxs-lookup"><span data-stu-id="0cae9-116">In this walkthrough, you:</span></span>

1. <span data-ttu-id="0cae9-117">Vytvořte sestavení se silným názvem pomocí veřejného rozhraní obsahujícího informace o typu, které mohou být vloženy.</span><span class="sxs-lookup"><span data-stu-id="0cae9-117">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="0cae9-118">Vytvořte sestavení modulu runtime se silným názvem, které implementuje veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0cae9-118">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="0cae9-119">Vytvořte klientský program, který vloží informace o typu z veřejného rozhraní a vytvoří instanci třídy ze sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0cae9-119">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="0cae9-120">Upravte a znovu sestavte sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0cae9-120">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="0cae9-121">Spusťte klientský program, aby bylo vidět, že používá novou verzi sestavení modulu runtime, aniž by bylo nutné znovu kompilovat.</span><span class="sxs-lookup"><span data-stu-id="0cae9-121">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="0cae9-122">Podmínky a omezení</span><span class="sxs-lookup"><span data-stu-id="0cae9-122">Conditions and limitations</span></span>

<span data-ttu-id="0cae9-123">Můžete vložit informace o typu ze sestavení za následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="0cae9-123">You can embed type information from an assembly under the following conditions:</span></span>

- <span data-ttu-id="0cae9-124">Sestavení zveřejňuje alespoň jedno veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0cae9-124">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="0cae9-125">Vložená rozhraní jsou opatřena `ComImport` atributy a atributy `Guid` s jedinečnými identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="0cae9-125">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="0cae9-126">Sestavení je opatřeno poznámkou s atributem nebo atributem `ImportedFromTypeLib` `PrimaryInteropAssembly` a atributem na úrovni sestavení `Guid` .</span><span class="sxs-lookup"><span data-stu-id="0cae9-126">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="0cae9-127">Šablony projektů Visual C# a Visual Basic `Guid` ve výchozím nastavení zahrnují atribut na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cae9-127">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="0cae9-128">Vzhledem k tomu, že primární funkce vkládání typů je podpora sestavení COM interop, platí při vložení informací o typu do plně spravovaného řešení následující omezení:</span><span class="sxs-lookup"><span data-stu-id="0cae9-128">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="0cae9-129">Jsou vložené pouze atributy specifické pro zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="0cae9-129">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="0cae9-130">Ostatní atributy se ignorují.</span><span class="sxs-lookup"><span data-stu-id="0cae9-130">Other attributes are ignored.</span></span>
- <span data-ttu-id="0cae9-131">Pokud typ používá obecné parametry a typ obecného parametru je vložený typ, tento typ nelze použít napříč hranicí sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cae9-131">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="0cae9-132">Příklady křížení hranice sestavení zahrnují volání metody z jiného sestavení nebo odvození typu z typu definovaného v jiném sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cae9-132">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="0cae9-133">Konstanty nejsou vloženy.</span><span class="sxs-lookup"><span data-stu-id="0cae9-133">Constants are not embedded.</span></span>
- <span data-ttu-id="0cae9-134"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>Třída nepodporuje vložený typ jako klíč.</span><span class="sxs-lookup"><span data-stu-id="0cae9-134">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="0cae9-135">Můžete implementovat vlastní typ slovníku pro podporu vloženého typu jako klíče.</span><span class="sxs-lookup"><span data-stu-id="0cae9-135">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="0cae9-136">Vytvoření rozhraní</span><span class="sxs-lookup"><span data-stu-id="0cae9-136">Create an interface</span></span>

<span data-ttu-id="0cae9-137">Prvním krokem je vytvoření sestavení rozhraní rovnocennosti typů.</span><span class="sxs-lookup"><span data-stu-id="0cae9-137">The first step is to create the type equivalence interface assembly.</span></span>

1. <span data-ttu-id="0cae9-138">V aplikaci Visual Studio vyberte **soubor**  >  **Nový**  >  **projekt**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-138">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="0cae9-139">V dialogovém okně **vytvořit nový projekt** zadejte do pole **Hledat šablony** *knihovnu tříd* .</span><span class="sxs-lookup"><span data-stu-id="0cae9-139">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="0cae9-140">V seznamu vyberte šablonu **Knihovna tříd (.NET Framework)** C# nebo Visual Basic a pak vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-140">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="0cae9-141">V dialogovém okně **Konfigurovat nový projekt** , v části **název projektu**zadejte *TypeEquivalenceInterface*a pak vyberte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-141">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="0cae9-142">Vytvoří se nový projekt.</span><span class="sxs-lookup"><span data-stu-id="0cae9-142">The new project is created.</span></span>

1. <span data-ttu-id="0cae9-143">V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor *Class1.cs* nebo *Class1. vb* , vyberte položku **Přejmenovat**a přejmenujte soubor z *Class1* na *ISampleInterface*.</span><span class="sxs-lookup"><span data-stu-id="0cae9-143">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="0cae9-144">Chcete-li také přejmenovat třídu na, odpovězte na výzvu **Ano** `ISampleInterface` .</span><span class="sxs-lookup"><span data-stu-id="0cae9-144">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="0cae9-145">Tato třída reprezentuje veřejné rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="0cae9-145">This class represents the public interface for the class.</span></span>

1. <span data-ttu-id="0cae9-146">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TypeEquivalenceInterface** a pak vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-146">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span>

1. <span data-ttu-id="0cae9-147">V levém podokně obrazovky **vlastnosti** vyberte **sestavovat** a nastavte **výstupní cestu** k umístění v počítači, například *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="0cae9-147">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="0cae9-148">V rámci tohoto Názorného postupu použijete stejné umístění.</span><span class="sxs-lookup"><span data-stu-id="0cae9-148">You use the same location throughout this walkthrough.</span></span>

1. <span data-ttu-id="0cae9-149">V levém podokně obrazovky **vlastnosti** vyberte **podepisování** a zaškrtněte políčko **podepsat sestavení** .</span><span class="sxs-lookup"><span data-stu-id="0cae9-149">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="0cae9-150">V rozevíracím seznamu pro **Výběr souboru klíče se silným názvem**vyberte možnost **Nový**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-150">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="0cae9-151">V dialogovém okně **vytvořit klíč se silným názvem** zadejte do pole **název souboru klíče** *Key. snk*.</span><span class="sxs-lookup"><span data-stu-id="0cae9-151">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="0cae9-152">Zrušte zaškrtnutí políčka **chránit soubor klíče heslem** a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-152">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="0cae9-153">V editoru kódu otevřete soubor třídy *ISampleInterface* a nahraďte jeho obsah následujícím kódem pro vytvoření `ISampleInterface` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="0cae9-153">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>

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

   ```vb
   Imports System.Runtime.InteropServices

   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```

1. <span data-ttu-id="0cae9-154">V nabídce **nástroje** vyberte možnost **vytvořit GUID**a v dialogovém okně **vytvořit identifikátor GUID** vyberte **Formát registru**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-154">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="0cae9-155">Vyberte možnost **Kopírovat**a pak vyberte možnost **ukončit**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-155">Select **Copy**, and then select **Exit**.</span></span>

1. <span data-ttu-id="0cae9-156">V `Guid` atributu kódu nahraďte vzorový identifikátor GUID identifikátorem GUID, který jste zkopírovali, a odeberte složené závorky (**{}**).</span><span class="sxs-lookup"><span data-stu-id="0cae9-156">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>

1. <span data-ttu-id="0cae9-157">V **Průzkumník řešení**rozbalte složku **Properties (vlastnosti** ) a vyberte soubor *AssemblyInfo.cs* nebo *AssemblyInfo. vb* .</span><span class="sxs-lookup"><span data-stu-id="0cae9-157">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="0cae9-158">V editoru kódu přidejte do souboru následující atribut:</span><span class="sxs-lookup"><span data-stu-id="0cae9-158">In the code editor, add the following attribute to the file:</span></span>

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. <span data-ttu-id="0cae9-159">Vyberte **soubor**  >  **Uložit vše** nebo stiskněte klávesovou **zkratku CTRL** + **+ SHIFT** + **s** a uložte soubory a projekt.</span><span class="sxs-lookup"><span data-stu-id="0cae9-159">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="0cae9-160">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte možnost **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-160">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="0cae9-161">Soubor DLL knihovny tříd je zkompilován a uložen do zadané výstupní cesty sestavení, například *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="0cae9-161">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="0cae9-162">Vytvoření běhové třídy</span><span class="sxs-lookup"><span data-stu-id="0cae9-162">Create a runtime class</span></span>

<span data-ttu-id="0cae9-163">Dále vytvořte třídu prostředí runtime ekvivalenci typu.</span><span class="sxs-lookup"><span data-stu-id="0cae9-163">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="0cae9-164">V aplikaci Visual Studio vyberte **soubor**  >  **Nový**  >  **projekt**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-164">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="0cae9-165">V dialogovém okně **vytvořit nový projekt** zadejte do pole **Hledat šablony** *knihovnu tříd* .</span><span class="sxs-lookup"><span data-stu-id="0cae9-165">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="0cae9-166">V seznamu vyberte šablonu **Knihovna tříd (.NET Framework)** C# nebo Visual Basic a pak vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-166">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="0cae9-167">V dialogovém okně **Konfigurovat nový projekt** , v části **název projektu**zadejte *TypeEquivalenceRuntime*a pak vyberte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-167">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="0cae9-168">Vytvoří se nový projekt.</span><span class="sxs-lookup"><span data-stu-id="0cae9-168">The new project is created.</span></span>

1. <span data-ttu-id="0cae9-169">V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor *Class1.cs* nebo *Class1. vb* , vyberte položku **Přejmenovat**a přejmenujte soubor z *Class1* na *SampleClass*.</span><span class="sxs-lookup"><span data-stu-id="0cae9-169">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="0cae9-170">Chcete-li také přejmenovat třídu na, odpovězte na výzvu **Ano** `SampleClass` .</span><span class="sxs-lookup"><span data-stu-id="0cae9-170">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="0cae9-171">Tato třída implementuje `ISampleInterface` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0cae9-171">This class implements the `ISampleInterface` interface.</span></span>

1. <span data-ttu-id="0cae9-172">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TypeEquivalenceInterface** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-172">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="0cae9-173">V levém podokně obrazovky **vlastnosti** vyberte **sestavit** a pak nastavte **výstupní cestu** ke stejnému umístění, které jste použili pro projekt TypeEquivalenceInterface, například *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="0cae9-173">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="0cae9-174">V levém podokně obrazovky **vlastnosti** vyberte **podepisování** a zaškrtněte políčko **podepsat sestavení** .</span><span class="sxs-lookup"><span data-stu-id="0cae9-174">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="0cae9-175">V rozevíracím seznamu pro **Výběr souboru klíče se silným názvem**vyberte možnost **Nový**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-175">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="0cae9-176">V dialogovém okně **vytvořit klíč se silným názvem** zadejte do pole **název souboru klíče** *Key. snk*.</span><span class="sxs-lookup"><span data-stu-id="0cae9-176">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="0cae9-177">Zrušte zaškrtnutí políčka **chránit soubor klíče heslem** a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-177">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="0cae9-178">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte možnost **Přidat**  >  **odkaz**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-178">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="0cae9-179">V dialogovém okně **Správce odkazů** vyberte **Procházet** a přejděte do složky výstupní cesta.</span><span class="sxs-lookup"><span data-stu-id="0cae9-179">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="0cae9-180">Vyberte soubor *TypeEquivalenceInterface. dll* , vyberte **Přidat**a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-180">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>

1. <span data-ttu-id="0cae9-181">V **Průzkumník řešení**rozbalte složku **odkazy** a vyberte odkaz **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="0cae9-181">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="0cae9-182">V podokně **vlastnosti** nastavte **konkrétní verzi** na **hodnotu NEPRAVDA** , pokud ještě není.</span><span class="sxs-lookup"><span data-stu-id="0cae9-182">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>

1. <span data-ttu-id="0cae9-183">V editoru kódu otevřete soubor třídy *SampleClass* a nahraďte jeho obsah následujícím kódem pro vytvoření `SampleClass` třídy:</span><span class="sxs-lookup"><span data-stu-id="0cae9-183">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>

   ```csharp
   using System;
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

1. <span data-ttu-id="0cae9-184">Vyberte **soubor**  >  **Uložit vše** nebo stiskněte klávesovou **zkratku CTRL** + **+ SHIFT** + **s** a uložte soubory a projekt.</span><span class="sxs-lookup"><span data-stu-id="0cae9-184">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="0cae9-185">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte možnost **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-185">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="0cae9-186">Soubor DLL knihovny tříd je zkompilován a uložen do zadané výstupní cesty sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cae9-186">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="0cae9-187">Vytvořit klientský projekt</span><span class="sxs-lookup"><span data-stu-id="0cae9-187">Create a client project</span></span>

<span data-ttu-id="0cae9-188">Nakonec vytvořte rovnocenný typ klientského programu, který odkazuje na sestavení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0cae9-188">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="0cae9-189">V aplikaci Visual Studio vyberte **soubor**  >  **Nový**  >  **projekt**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-189">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="0cae9-190">V dialogovém okně **vytvořit nový projekt** zadejte do pole **Hledat šablony** text *Konzola* .</span><span class="sxs-lookup"><span data-stu-id="0cae9-190">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="0cae9-191">V seznamu vyberte šablonu aplikace konzoly C# nebo Visual Basic **(.NET Framework)** a pak vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-191">Select either the C# or Visual Basic **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="0cae9-192">V dialogovém okně **Konfigurovat nový projekt** , v části **název projektu**zadejte *TypeEquivalenceClient*a pak vyberte **vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-192">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="0cae9-193">Vytvoří se nový projekt.</span><span class="sxs-lookup"><span data-stu-id="0cae9-193">The new project is created.</span></span>

1. <span data-ttu-id="0cae9-194">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TypeEquivalenceClient** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span>

1. <span data-ttu-id="0cae9-195">V levém podokně obrazovky **vlastnosti** vyberte **sestavit** a pak nastavte **výstupní cestu** ke stejnému umístění, které jste použili pro projekt TypeEquivalenceInterface, například *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="0cae9-195">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="0cae9-196">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **TypeEquivalenceClient** a vyberte možnost **Přidat**  >  **odkaz**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-196">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="0cae9-197">Pokud je soubor **TypeEquivalenceInterface. dll** již v dialogovém okně **Správce odkazů** uveden, vyberte jej.</span><span class="sxs-lookup"><span data-stu-id="0cae9-197">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="0cae9-198">Pokud ne, vyberte **Procházet**, přejděte do složky výstupní cesta, vyberte soubor *TypeEquivalenceInterface. dll* (ne *TypeEquivalenceRuntime. dll*) a vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-198">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="0cae9-199">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-199">Select **OK**.</span></span>

1. <span data-ttu-id="0cae9-200">V **Průzkumník řešení**rozbalte složku **odkazy** a vyberte odkaz **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="0cae9-200">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="0cae9-201">V podokně **Vlastnosti nastavte možnosti** **Vložit typy spolupráce** na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-201">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>

1. <span data-ttu-id="0cae9-202">Otevřete soubor *program.cs* nebo *Module1. vb* v editoru kódu a nahraďte jeho obsah následujícím kódem pro vytvoření klientského programu:</span><span class="sxs-lookup"><span data-stu-id="0cae9-202">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

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

   ```vb
   Imports System.Reflection
   Imports TypeEquivalenceInterface

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

1. <span data-ttu-id="0cae9-203">Vyberte **soubor**  >  **Uložit vše** nebo stiskněte klávesovou **zkratku CTRL** + **+ SHIFT** + **s** a uložte soubory a projekt.</span><span class="sxs-lookup"><span data-stu-id="0cae9-203">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="0cae9-204">Stisknutím klávesy **CTRL** + **F5** Sestavte a spusťte program.</span><span class="sxs-lookup"><span data-stu-id="0cae9-204">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="0cae9-205">Všimněte si, že výstup konzoly vrátí sestavení verze **1.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-205">Note that the console output returns the assembly version **1.0.0.0**.</span></span>

## <a name="modify-the-interface"></a><span data-ttu-id="0cae9-206">Změna rozhraní</span><span class="sxs-lookup"><span data-stu-id="0cae9-206">Modify the interface</span></span>

<span data-ttu-id="0cae9-207">Nyní upravte sestavení rozhraní a změňte jeho verzi.</span><span class="sxs-lookup"><span data-stu-id="0cae9-207">Now, modify the interface assembly, and change its version.</span></span>

1. <span data-ttu-id="0cae9-208">V aplikaci Visual Studio vyberte **soubor**  >  **otevřít**  >  **projekt/řešení**a otevřete projekt **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="0cae9-208">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>

1. <span data-ttu-id="0cae9-209">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TypeEquivalenceInterface** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-209">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="0cae9-210">V levém podokně obrazovky **vlastnosti** vyberte **aplikace** a pak vyberte **informace o sestavení**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-210">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="0cae9-211">V dialogovém okně **informace o sestavení** změňte **verzi sestavení** a hodnoty **verze souboru** na *2.0.0.0*a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-211">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="0cae9-212">Otevřete soubor *SampleInterface.cs* nebo *SampleInterface. vb* a přidejte následující řádek kódu do `ISampleInterface` rozhraní:</span><span class="sxs-lookup"><span data-stu-id="0cae9-212">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. <span data-ttu-id="0cae9-213">Vyberte **soubor**  >  **Uložit vše** nebo stiskněte klávesovou **zkratku CTRL** + **+ SHIFT** + **s** a uložte soubory a projekt.</span><span class="sxs-lookup"><span data-stu-id="0cae9-213">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="0cae9-214">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte možnost **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-214">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="0cae9-215">Nová verze souboru DLL knihovny tříd je zkompilována a uložena do výstupní cesty sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cae9-215">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="0cae9-216">Úprava běhové třídy</span><span class="sxs-lookup"><span data-stu-id="0cae9-216">Modify the runtime class</span></span>

<span data-ttu-id="0cae9-217">Také upravte třídu modulu runtime a aktualizujte její verzi.</span><span class="sxs-lookup"><span data-stu-id="0cae9-217">Also modify the runtime class and update its version.</span></span>

1. <span data-ttu-id="0cae9-218">V aplikaci Visual Studio vyberte **soubor**  >  **otevřít**  >  **projekt/řešení**a otevřete projekt **TypeEquivalenceRuntime** .</span><span class="sxs-lookup"><span data-stu-id="0cae9-218">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>

1. <span data-ttu-id="0cae9-219">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt **TypeEquivalenceRuntime** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-219">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span>

1. <span data-ttu-id="0cae9-220">V levém podokně obrazovky **vlastnosti** vyberte **aplikace** a pak vyberte **informace o sestavení**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-220">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="0cae9-221">V dialogovém okně **informace o sestavení** změňte **verzi sestavení** a hodnoty **verze souboru** na *2.0.0.0*a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-221">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="0cae9-222">Otevřete soubor *SampleClass.cs* nebo *SampleClass. vb* a do třídy přidejte následující kód `SampleClass` :</span><span class="sxs-lookup"><span data-stu-id="0cae9-222">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>

   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```

   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```

1. <span data-ttu-id="0cae9-223">Vyberte **soubor**  >  **Uložit vše** nebo stiskněte klávesovou **zkratku CTRL** + **+ SHIFT** + **s** a uložte soubory a projekt.</span><span class="sxs-lookup"><span data-stu-id="0cae9-223">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="0cae9-224">V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte možnost **sestavit**.</span><span class="sxs-lookup"><span data-stu-id="0cae9-224">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="0cae9-225">Nová verze souboru DLL knihovny tříd je zkompilována a uložena do výstupní cesty sestavení.</span><span class="sxs-lookup"><span data-stu-id="0cae9-225">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="0cae9-226">Spustit aktualizovaný klientský program</span><span class="sxs-lookup"><span data-stu-id="0cae9-226">Run the updated client program</span></span>

<span data-ttu-id="0cae9-227">Přejít do umístění výstupní složky sestavení a spustit *TypeEquivalenceClient. exe*.</span><span class="sxs-lookup"><span data-stu-id="0cae9-227">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="0cae9-228">Všimněte si, že výstup konzoly nyní odráží novou verzi `TypeEquivalenceRuntime` sestavení *2.0.0.0*, aniž by byl program znovu zkompilován.</span><span class="sxs-lookup"><span data-stu-id="0cae9-228">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="0cae9-229">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cae9-229">See also</span></span>

- [<span data-ttu-id="0cae9-230">-Link (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="0cae9-230">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="0cae9-231">-Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cae9-231">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="0cae9-232">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="0cae9-232">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0cae9-233">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cae9-233">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="0cae9-234">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="0cae9-234">Assemblies in .NET</span></span>](index.md)
