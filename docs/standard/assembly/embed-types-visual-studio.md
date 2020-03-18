---
title: 'Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: f11fbedad766753ee462c5f597b823493cdaf7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75338560"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="483ed-102">Návod: Vložení typů ze spravovaných sestavení v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="483ed-102">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="483ed-103">Pokud vložíte informace o typu ze spravovaného sestavení se silným názvem, můžete volně spárovat typy v aplikaci, abyste dosáhli nezávislosti verze.</span><span class="sxs-lookup"><span data-stu-id="483ed-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="483ed-104">To znamená, že váš program může být zapsán do použití typů z libovolné verze spravované knihovny bez nutnosti překompilovat pro každou novou verzi.</span><span class="sxs-lookup"><span data-stu-id="483ed-104">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="483ed-105">Vkládání typů se často používá s interop modelu COM, například s aplikací, která používá objekty automatizace z aplikace Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="483ed-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="483ed-106">Vkládání informací o typu umožňuje stejné sestavení programu pracovat s různými verzemi sady Microsoft Office v různých počítačích.</span><span class="sxs-lookup"><span data-stu-id="483ed-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="483ed-107">Můžete však také použít vkládání typů s plně spravovanými řešeními.</span><span class="sxs-lookup"><span data-stu-id="483ed-107">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="483ed-108">Po zadání veřejných rozhraní, které mohou být vloženy, vytvoříte runtime třídy, které implementují tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="483ed-108">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="483ed-109">Klientský program může vložit informace o typu rozhraní v době návrhu odkazem na sestavení, které obsahuje veřejná rozhraní a nastavení `Embed Interop Types` vlastnosti odkazu na `True`.</span><span class="sxs-lookup"><span data-stu-id="483ed-109">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="483ed-110">Klientský program pak může načíst instance objektů runtime zadaných jako tato rozhraní.</span><span class="sxs-lookup"><span data-stu-id="483ed-110">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="483ed-111">To je ekvivalentní použití kompilátoru příkazového řádku a odkazování na sestavení pomocí [možnosti kompilátoru -link](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="483ed-111">This is equivalent to using the command line compiler and referencing the assembly by using the [-link compiler option](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span></span>

<span data-ttu-id="483ed-112">Pokud vytvoříte novou verzi sestavení runtime se silným názvem, klientský program nemusí být znovu zkompilován.</span><span class="sxs-lookup"><span data-stu-id="483ed-112">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="483ed-113">Klientský program nadále používá kteroukoli verzi sestavení modulu runtime, která je mu k dispozici, pomocí informací o vloženém typu pro veřejná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="483ed-113">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="483ed-114">V tomto návodu:</span><span class="sxs-lookup"><span data-stu-id="483ed-114">In this walkthrough, you:</span></span>

1. <span data-ttu-id="483ed-115">Vytvořte sestavení se silným názvem s veřejným rozhraním obsahujícím informace o typu, které lze vložit.</span><span class="sxs-lookup"><span data-stu-id="483ed-115">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="483ed-116">Vytvořte sestavení modulu runtime se silným názvem, které implementuje veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="483ed-116">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="483ed-117">Vytvořte klientský program, který vloží informace o typu z veřejného rozhraní a vytvoří instanci třídy ze sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="483ed-117">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="483ed-118">Upravte a znovu vytvořte sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="483ed-118">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="483ed-119">Spusťte klientský program a zjistěte, že používá novou verzi sestavení runtime bez nutnosti opětovné kompilace.</span><span class="sxs-lookup"><span data-stu-id="483ed-119">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="483ed-120">Podmínky a omezení</span><span class="sxs-lookup"><span data-stu-id="483ed-120">Conditions and limitations</span></span>

<span data-ttu-id="483ed-121">Informace o typu můžete vložit ze sestavy za následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="483ed-121">You can embed type information from an assembly under the following conditions:</span></span>

- <span data-ttu-id="483ed-122">Sestavení zpřístupňuje alespoň jedno veřejné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="483ed-122">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="483ed-123">Vložená rozhraní jsou anotována `ComImport` s `Guid` atributy a atributy s jedinečnými identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="483ed-123">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="483ed-124">Sestavení je anotováno `ImportedFromTypeLib` atributem `PrimaryInteropAssembly` nebo atributem a `Guid` atributem na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="483ed-124">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="483ed-125">Šablony projektu Visual C# a Visual Basic `Guid` obsahují ve výchozím nastavení atribut na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="483ed-125">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="483ed-126">Vzhledem k tomu, že primární funkcí vkládání typu je podpora sestavení interop com, platí následující omezení při vložení informací o typu do plně spravovaného řešení:</span><span class="sxs-lookup"><span data-stu-id="483ed-126">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="483ed-127">Vloženy jsou pouze atributy specifické pro interop com.</span><span class="sxs-lookup"><span data-stu-id="483ed-127">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="483ed-128">Ostatní atributy jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="483ed-128">Other attributes are ignored.</span></span>
- <span data-ttu-id="483ed-129">Pokud typ používá obecné parametry a typ obecného parametru je vložený typ, nelze tento typ použít přes hranice sestavení.</span><span class="sxs-lookup"><span data-stu-id="483ed-129">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="483ed-130">Příklady křížení hranice sestavy zahrnují volání metody z jiné sestavy nebo odvození typu z typu definovaného v jiné sestavě.</span><span class="sxs-lookup"><span data-stu-id="483ed-130">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="483ed-131">Konstanty nejsou vloženy.</span><span class="sxs-lookup"><span data-stu-id="483ed-131">Constants are not embedded.</span></span>
- <span data-ttu-id="483ed-132">Třída <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> nepodporuje vložený typ jako klíč.</span><span class="sxs-lookup"><span data-stu-id="483ed-132">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="483ed-133">Můžete implementovat vlastní typ slovníku pro podporu vloženého typu jako klíč.</span><span class="sxs-lookup"><span data-stu-id="483ed-133">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="483ed-134">Vytvoření rozhraní</span><span class="sxs-lookup"><span data-stu-id="483ed-134">Create an interface</span></span>

<span data-ttu-id="483ed-135">Prvním krokem je vytvoření sestavení rozhraní rovnocennosti typu.</span><span class="sxs-lookup"><span data-stu-id="483ed-135">The first step is to create the type equivalence interface assembly.</span></span>

1. <span data-ttu-id="483ed-136">V sadě Visual Studio vyberte **Soubor** > **nový** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="483ed-136">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="483ed-137">V **dialogovém** okně Vytvořit nový projekt zadejte *knihovnu tříd* do pole **Hledat šablony.**</span><span class="sxs-lookup"><span data-stu-id="483ed-137">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="483ed-138">Vyberte šablonu knihovny tříd jazyka C# nebo Visual Basic **(.NET Framework)** ze seznamu a pak vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="483ed-138">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="483ed-139">V dialogovém okně **Konfigurovat nový projekt** v části Název **projektu**zadejte *typ TypeEquivalenceInterface*a pak vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="483ed-139">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="483ed-140">Nový projekt je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="483ed-140">The new project is created.</span></span>

1. <span data-ttu-id="483ed-141">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor *Class1.cs* nebo *Class1.vb,* vyberte **přejmenovat**a přejmenujte soubor z *třídy 1* na *ISampleInterface*.</span><span class="sxs-lookup"><span data-stu-id="483ed-141">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="483ed-142">Odpověď **Ano** na výzvu a přejmenujte třídu také na `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="483ed-142">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="483ed-143">Tato třída představuje veřejné rozhraní pro třídu.</span><span class="sxs-lookup"><span data-stu-id="483ed-143">This class represents the public interface for the class.</span></span>

1. <span data-ttu-id="483ed-144">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="483ed-144">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span>

1. <span data-ttu-id="483ed-145">Vyberte **Možnost Sestavovat** v levém podokně obrazovky **Vlastnosti** a nastavte **výstupní cestu** do umístění v počítači, například *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="483ed-145">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="483ed-146">V tomto návodu se používá stejné umístění.</span><span class="sxs-lookup"><span data-stu-id="483ed-146">You use the same location throughout this walkthrough.</span></span>

1. <span data-ttu-id="483ed-147">V levém podokně obrazovky **Vlastnosti** vyberte **Podepisování** a zaškrtněte políčko **Podepsat sestavení.**</span><span class="sxs-lookup"><span data-stu-id="483ed-147">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="483ed-148">V rozevíracím dokumentu **V části Zvolte soubor klíče silného názvu**vyberte **Nový**.</span><span class="sxs-lookup"><span data-stu-id="483ed-148">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="483ed-149">V dialogovém okně **Vytvořit silný klíč názvu** zadejte v části Název **souboru klíče příkaz** *key.snk*.</span><span class="sxs-lookup"><span data-stu-id="483ed-149">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="483ed-150">Zrušte zaškrtnutí **políčka Zamknout soubor klíče heslem** a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="483ed-150">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="483ed-151">Otevřete soubor třídy *ISampleInterface* v editoru kódu a nahraďte jeho obsah následujícím kódem `ISampleInterface` pro vytvoření rozhraní:</span><span class="sxs-lookup"><span data-stu-id="483ed-151">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>

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

1. <span data-ttu-id="483ed-152">V nabídce **Nástroje** vyberte **Vytvořit identifikátor GUI**a v dialogovém okně Vytvořit identifikátor **GUID** vyberte **Formát registru**.</span><span class="sxs-lookup"><span data-stu-id="483ed-152">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="483ed-153">Vyberte **Kopírovat**a pak vyberte **Ukončit**.</span><span class="sxs-lookup"><span data-stu-id="483ed-153">Select **Copy**, and then select **Exit**.</span></span>

1. <span data-ttu-id="483ed-154">V `Guid` atributu kódu nahraďte ukázkový identifikátor GUID zkopírovaným identifikátorem GUID a odeberte závorky (**{ }**).</span><span class="sxs-lookup"><span data-stu-id="483ed-154">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>

1. <span data-ttu-id="483ed-155">V **Průzkumníku řešení**rozbalte složku **Vlastnosti** a vyberte soubor *AssemblyInfo.cs* nebo *AssemblyInfo.vb.*</span><span class="sxs-lookup"><span data-stu-id="483ed-155">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="483ed-156">V editoru kódu přidejte do souboru následující atribut:</span><span class="sxs-lookup"><span data-stu-id="483ed-156">In the code editor, add the following attribute to the file:</span></span>

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. <span data-ttu-id="483ed-157">Vyberte **Uložit** > **vše** nebo stisknutím **klávesy Ctrl**+**Shift**+**S** uložte soubory a projekt.</span><span class="sxs-lookup"><span data-stu-id="483ed-157">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="483ed-158">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte **příkaz Build**.</span><span class="sxs-lookup"><span data-stu-id="483ed-158">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="483ed-159">Soubor Knihovny dll knihovny tříd je zkompilován a uložen do zadané cesty výstupu sestavení, například *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="483ed-159">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="483ed-160">Vytvoření runtime třídy</span><span class="sxs-lookup"><span data-stu-id="483ed-160">Create a runtime class</span></span>

<span data-ttu-id="483ed-161">Dále vytvořte třídu runtime ekvivalence typu.</span><span class="sxs-lookup"><span data-stu-id="483ed-161">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="483ed-162">V sadě Visual Studio vyberte **Soubor** > **nový** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="483ed-162">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="483ed-163">V **dialogovém** okně Vytvořit nový projekt zadejte *knihovnu tříd* do pole **Hledat šablony.**</span><span class="sxs-lookup"><span data-stu-id="483ed-163">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="483ed-164">Vyberte šablonu knihovny tříd jazyka C# nebo Visual Basic **(.NET Framework)** ze seznamu a pak vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="483ed-164">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="483ed-165">V dialogovém okně **Konfigurovat nový projekt** v části Název **projektu**zadejte *typ TypEquivalenceRuntime*a pak vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="483ed-165">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="483ed-166">Nový projekt je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="483ed-166">The new project is created.</span></span>

1. <span data-ttu-id="483ed-167">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor *Class1.cs* nebo *Class1.vb,* vyberte **přejmenovat**a přejmenujte soubor z *Třídy1* na *SampleClass*.</span><span class="sxs-lookup"><span data-stu-id="483ed-167">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="483ed-168">Odpověď **Ano** na výzvu a přejmenujte třídu také na `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="483ed-168">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="483ed-169">Tato třída implementuje `ISampleInterface` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="483ed-169">This class implements the `ISampleInterface` interface.</span></span>

1. <span data-ttu-id="483ed-170">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="483ed-170">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="483ed-171">Vyberte **Možnost Sestavovat** v levém podokně obrazovky **Vlastnosti** a pak nastavte **výstupní cestu** do stejného umístění, jaké jste použili pro projekt TypeEquivalenceInterface, například *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="483ed-171">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="483ed-172">V levém podokně obrazovky **Vlastnosti** vyberte **Podepisování** a zaškrtněte políčko **Podepsat sestavení.**</span><span class="sxs-lookup"><span data-stu-id="483ed-172">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="483ed-173">V rozevíracím dokumentu **V části Zvolte soubor klíče silného názvu**vyberte **Nový**.</span><span class="sxs-lookup"><span data-stu-id="483ed-173">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="483ed-174">V dialogovém okně **Vytvořit silný klíč názvu** zadejte v části Název **souboru klíče příkaz** *key.snk*.</span><span class="sxs-lookup"><span data-stu-id="483ed-174">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="483ed-175">Zrušte zaškrtnutí **políčka Zamknout soubor klíče heslem** a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="483ed-175">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="483ed-176">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte **příkaz Přidat** > **odkaz**.</span><span class="sxs-lookup"><span data-stu-id="483ed-176">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="483ed-177">V dialogovém okně **Správce odkazů** vyberte **Procházet** a vyhledejte složku výstupní cesty.</span><span class="sxs-lookup"><span data-stu-id="483ed-177">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="483ed-178">Vyberte soubor *TypeEquivalenceInterface.dll,* vyberte **Přidat**a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="483ed-178">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>

1. <span data-ttu-id="483ed-179">V **Průzkumníku řešení**rozbalte složku **Reference a** vyberte odkaz **TypeEquivalenceInterface.**</span><span class="sxs-lookup"><span data-stu-id="483ed-179">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="483ed-180">V podokně **Vlastnosti** nastavte **konkrétní verzi** na **hodnotu False,** pokud ještě není.</span><span class="sxs-lookup"><span data-stu-id="483ed-180">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>

1. <span data-ttu-id="483ed-181">Otevřete soubor třídy *SampleClass* v editoru kódu a nahraďte jeho obsah následujícím kódem `SampleClass` pro vytvoření třídy:</span><span class="sxs-lookup"><span data-stu-id="483ed-181">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="483ed-182">Vyberte **Uložit** > **vše** nebo stisknutím **klávesy Ctrl**+**Shift**+**S** uložte soubory a projekt.</span><span class="sxs-lookup"><span data-stu-id="483ed-182">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="483ed-183">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte **příkaz Build**.</span><span class="sxs-lookup"><span data-stu-id="483ed-183">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="483ed-184">Soubor DLL knihovny tříd je zkompilován a uložen do zadané cesty výstupu sestavení.</span><span class="sxs-lookup"><span data-stu-id="483ed-184">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="483ed-185">Vytvoření klientského projektu</span><span class="sxs-lookup"><span data-stu-id="483ed-185">Create a client project</span></span>

<span data-ttu-id="483ed-186">Nakonec vytvořte klientský program ekvivalence typu, který odkazuje na sestavení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="483ed-186">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="483ed-187">V sadě Visual Studio vyberte **Soubor** > **nový** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="483ed-187">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="483ed-188">V **dialogovém** okně Vytvořit nový projekt zadejte *konzolu* do pole **Hledat šablony.**</span><span class="sxs-lookup"><span data-stu-id="483ed-188">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="483ed-189">Vyberte šablonu konzoly C# nebo Visual Basic **Console App (.NET Framework)** ze seznamu a pak vyberte **Další**.</span><span class="sxs-lookup"><span data-stu-id="483ed-189">Select either the C# or Visual Basic **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="483ed-190">V dialogovém okně **Konfigurovat nový projekt** v části Název **projektu**zadejte *typ TypuEquivalenceClient*a pak vyberte **Vytvořit**.</span><span class="sxs-lookup"><span data-stu-id="483ed-190">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="483ed-191">Nový projekt je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="483ed-191">The new project is created.</span></span>

1. <span data-ttu-id="483ed-192">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceClient** a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="483ed-192">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span>

1. <span data-ttu-id="483ed-193">Vyberte **Možnost Sestavovat** v levém podokně obrazovky **Vlastnosti** a pak nastavte **výstupní cestu** do stejného umístění, jaké jste použili pro projekt TypeEquivalenceInterface, například *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="483ed-193">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="483ed-194">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceClient** a vyberte **příkaz Přidat** > **odkaz**.</span><span class="sxs-lookup"><span data-stu-id="483ed-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="483ed-195">Pokud je v dialogovém **okně Správce odkazů** soubor **TypeEquivalenceInterface.dll** již uveden, vyberte jej.</span><span class="sxs-lookup"><span data-stu-id="483ed-195">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="483ed-196">Pokud ne, vyberte **Procházet**, vyhledejte složku výstupní cesty, vyberte soubor *TypeEquivalenceInterface.dll* (nikoli *TypeEquivalenceRuntime.dll*) a vyberte **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="483ed-196">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="483ed-197">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="483ed-197">Select **OK**.</span></span>

1. <span data-ttu-id="483ed-198">V **Průzkumníku řešení**rozbalte složku **Reference a** vyberte odkaz **TypeEquivalenceInterface.**</span><span class="sxs-lookup"><span data-stu-id="483ed-198">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="483ed-199">V podokně **Vlastnosti** nastavte **vložit typy interop** na **hodnotu True**.</span><span class="sxs-lookup"><span data-stu-id="483ed-199">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>

1. <span data-ttu-id="483ed-200">Otevřete soubor *Program.cs* nebo *Module1.vb* v editoru kódu a nahraďte jeho obsah následujícím kódem pro vytvoření klientského programu:</span><span class="sxs-lookup"><span data-stu-id="483ed-200">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>

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

1. <span data-ttu-id="483ed-201">Vyberte **Uložit** > **vše** nebo stisknutím **klávesy Ctrl**+**Shift**+**S** uložte soubory a projekt.</span><span class="sxs-lookup"><span data-stu-id="483ed-201">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="483ed-202">Stisknutím **klávesy Ctrl**+**F5** vytvořte a spusťte program.</span><span class="sxs-lookup"><span data-stu-id="483ed-202">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="483ed-203">Všimněte si, že výstup konzoly vrátí verzi sestavení **1.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="483ed-203">Note that the console output returns the assembly version **1.0.0.0**.</span></span>

## <a name="modify-the-interface"></a><span data-ttu-id="483ed-204">Úprava rozhraní</span><span class="sxs-lookup"><span data-stu-id="483ed-204">Modify the interface</span></span>

<span data-ttu-id="483ed-205">Nyní upravte sestavení rozhraní a změňte jeho verzi.</span><span class="sxs-lookup"><span data-stu-id="483ed-205">Now, modify the interface assembly, and change its version.</span></span>

1. <span data-ttu-id="483ed-206">V sadě Visual Studio vyberte **soubor** > **otevřít** > **projekt/řešení**a otevřete projekt **TypeEquivalenceInterface.**</span><span class="sxs-lookup"><span data-stu-id="483ed-206">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>

1. <span data-ttu-id="483ed-207">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="483ed-207">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="483ed-208">V levém podokně obrazovky **Vlastnosti** vyberte **Aplikace** a pak vyberte Informace **o sestavení**.</span><span class="sxs-lookup"><span data-stu-id="483ed-208">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="483ed-209">V dialogovém okně **Informace o sestavení** změňte hodnoty verze **sestavení** a **verze souboru** na *2.0.0.0*a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="483ed-209">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="483ed-210">Otevřete soubor *SampleInterface.cs* nebo *SampleInterface.vb* a do `ISampleInterface` rozhraní přidejte následující řádek kódu:</span><span class="sxs-lookup"><span data-stu-id="483ed-210">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. <span data-ttu-id="483ed-211">Vyberte **Uložit** > **vše** nebo stisknutím **klávesy Ctrl**+**Shift**+**S** uložte soubory a projekt.</span><span class="sxs-lookup"><span data-stu-id="483ed-211">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="483ed-212">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceInterface** a vyberte **příkaz Build**.</span><span class="sxs-lookup"><span data-stu-id="483ed-212">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="483ed-213">Nová verze souboru DLL knihovny tříd je zkompilován a uložena do cesty výstupu sestavení.</span><span class="sxs-lookup"><span data-stu-id="483ed-213">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="483ed-214">Úprava třídy runtime</span><span class="sxs-lookup"><span data-stu-id="483ed-214">Modify the runtime class</span></span>

<span data-ttu-id="483ed-215">Upravte také třídu runtime a aktualizujte její verzi.</span><span class="sxs-lookup"><span data-stu-id="483ed-215">Also modify the runtime class and update its version.</span></span>

1. <span data-ttu-id="483ed-216">V sadě Visual Studio vyberte **soubor** > **otevřít** > **projekt/řešení**a otevřete projekt **TypeEquivalenceRuntime.**</span><span class="sxs-lookup"><span data-stu-id="483ed-216">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>

1. <span data-ttu-id="483ed-217">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="483ed-217">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span>

1. <span data-ttu-id="483ed-218">V levém podokně obrazovky **Vlastnosti** vyberte **Aplikace** a pak vyberte Informace **o sestavení**.</span><span class="sxs-lookup"><span data-stu-id="483ed-218">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="483ed-219">V dialogovém okně **Informace o sestavení** změňte hodnoty verze **sestavení** a **verze souboru** na *2.0.0.0*a pak vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="483ed-219">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="483ed-220">Otevřete soubor *SampleClass.cs* nebo *SampleClass.vb* a přidejte do `SampleClass` třídy následující kód:</span><span class="sxs-lookup"><span data-stu-id="483ed-220">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="483ed-221">Vyberte **Uložit** > **vše** nebo stisknutím **klávesy Ctrl**+**Shift**+**S** uložte soubory a projekt.</span><span class="sxs-lookup"><span data-stu-id="483ed-221">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="483ed-222">V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt **TypeEquivalenceRuntime** a vyberte **příkaz Build**.</span><span class="sxs-lookup"><span data-stu-id="483ed-222">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="483ed-223">Nová verze souboru DLL knihovny tříd je zkompilován a uložena do cesty výstupu sestavení.</span><span class="sxs-lookup"><span data-stu-id="483ed-223">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="483ed-224">Spuštění aktualizovaného klientského programu</span><span class="sxs-lookup"><span data-stu-id="483ed-224">Run the updated client program</span></span>

<span data-ttu-id="483ed-225">Přejděte do umístění výstupní složky sestavení a spusťte *soubor TypeEquivalenceClient.exe*.</span><span class="sxs-lookup"><span data-stu-id="483ed-225">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="483ed-226">Všimněte si, že výstup konzoly `TypeEquivalenceRuntime` nyní odráží novou verzi sestavení, *2.0.0.0*, bez překompilován programu.</span><span class="sxs-lookup"><span data-stu-id="483ed-226">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="483ed-227">Viz také</span><span class="sxs-lookup"><span data-stu-id="483ed-227">See also</span></span>

- [<span data-ttu-id="483ed-228">-link (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="483ed-228">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="483ed-229">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="483ed-229">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="483ed-230">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="483ed-230">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="483ed-231">Koncepty programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="483ed-231">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="483ed-232">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="483ed-232">Assemblies in .NET</span></span>](index.md)
