---
title: 'Postupy: Podepsání sestavení silným názvem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5580b6d8af7319397ad7eb6416941c2be0dcdb76
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303417"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="a7dec-102">Postupy: Podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="a7dec-102">How to: Sign an Assembly with a Strong Name</span></span>
<span data-ttu-id="a7dec-103">Existuje několik způsobů, jak můžete podepsat sestavení pomocí silného názvu:</span><span class="sxs-lookup"><span data-stu-id="a7dec-103">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
-   <span data-ttu-id="a7dec-104">S použitím **podepisování** kartu v projektu **vlastnosti** dialogové okno v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a7dec-104">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="a7dec-105">Nejjednodušším a nejpohodlnějším způsobem je podepsání sestavení pomocí silného názvu.</span><span class="sxs-lookup"><span data-stu-id="a7dec-105">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
-   <span data-ttu-id="a7dec-106">S použitím [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) propojení se souborem klíče modulu kódu rozhraní .NET Framework (soubor .netmodule).</span><span class="sxs-lookup"><span data-stu-id="a7dec-106">By using the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a .netmodule file) with a key file.</span></span>  
  
-   <span data-ttu-id="a7dec-107">Pomocí atributů sestavení pro vložení informací o silném názvu do kódu.</span><span class="sxs-lookup"><span data-stu-id="a7dec-107">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="a7dec-108">Můžete použít buď <xref:System.Reflection.AssemblyKeyFileAttribute> nebo <xref:System.Reflection.AssemblyKeyNameAttribute> atribut, podle toho, kde je umístěn soubor klíče, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="a7dec-108">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
-   <span data-ttu-id="a7dec-109">Pomocí možností kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="a7dec-109">By using compiler options.</span></span>  
  
 <span data-ttu-id="a7dec-110">Pro podepsání sestavení silným názvem musíte mít pár kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="a7dec-110">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="a7dec-111">Další informace o vytváření páru klíčů naleznete v tématu [jak: Vytvoření páru veřejného a privátního klíče](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="a7dec-111">For more information about creating a key pair, see [How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="a7dec-112">Vytvoření a podepsání sestavení silným názvem pomocí aplikace Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a7dec-112">To create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="a7dec-113">V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a7dec-113">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="a7dec-114">Zvolte **podepisování** kartu.</span><span class="sxs-lookup"><span data-stu-id="a7dec-114">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="a7dec-115">Vyberte **podepsat sestavení** pole.</span><span class="sxs-lookup"><span data-stu-id="a7dec-115">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="a7dec-116">V **vyberte soubor klíče se silným názvem** zvolte  **\<Procházet... >** a potom přejděte k souboru klíče.</span><span class="sxs-lookup"><span data-stu-id="a7dec-116">In the **Choose a strong name key file** box, choose **\<Browse…>**, and then navigate to the key file.</span></span> <span data-ttu-id="a7dec-117">Chcete-li vytvořit nový soubor klíče, zvolte  **\<nový … >** a zadejte jeho název **vytvořit klíč se silným názvem** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="a7dec-117">To create a new key file, choose **\<New…>** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7dec-118">Za účelem [zpoždění podepsání sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md), vyberte soubor veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="a7dec-118">In order to [delay sign an assembly](../../../docs/framework/app-domains/delay-sign-assembly.md), choose a public key file.</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="a7dec-119">Vytvoření a podepsání sestavení silným názvem pomocí programu Assembly Linker</span><span class="sxs-lookup"><span data-stu-id="a7dec-119">To create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
-   <span data-ttu-id="a7dec-120">Na [Developer Command Prompt pro sadu Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="a7dec-120">At the [Developer Command Prompt for Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="a7dec-121">**Al** **/out:**\<*assemblyName*> *\<moduleName >* **/keyfile:** \<  *keyfileName*></span><span class="sxs-lookup"><span data-stu-id="a7dec-121">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  
  
     <span data-ttu-id="a7dec-122">kde:</span><span class="sxs-lookup"><span data-stu-id="a7dec-122">where:</span></span>  
  
     *<span data-ttu-id="a7dec-123">assemblyName</span><span class="sxs-lookup"><span data-stu-id="a7dec-123">assemblyName</span></span>*  
     <span data-ttu-id="a7dec-124">Název silně podepsaného sestavení (soubor .dll nebo .exe), který vygeneruje program Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="a7dec-124">The name of the strongly signed assembly (a .dll or .exe file) that Assembly Linker will emit.</span></span>  
  
     *<span data-ttu-id="a7dec-125">moduleName</span><span class="sxs-lookup"><span data-stu-id="a7dec-125">moduleName</span></span>*  
     <span data-ttu-id="a7dec-126">Název modulu kódu rozhraní .NET Framework (soubor .netmodule), který obsahuje jeden nebo několik typů.</span><span class="sxs-lookup"><span data-stu-id="a7dec-126">The name of a .NET Framework code module (a .netmodule file) that includes one or more types.</span></span> <span data-ttu-id="a7dec-127">Soubor .netmodule můžete vytvořit kompilací kódu pomocí `/target:module` přepínače v C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a7dec-127">You can create a .netmodule file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>  
  
     *<span data-ttu-id="a7dec-128">keyfileName</span><span class="sxs-lookup"><span data-stu-id="a7dec-128">keyfileName</span></span>*  
     <span data-ttu-id="a7dec-129">Název kontejneru nebo souboru, který obsahuje pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="a7dec-129">The name of the container or file that contains the key pair.</span></span> <span data-ttu-id="a7dec-130">Program Assembly Linker interpretuje relativní cestu vzhledem k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="a7dec-130">Assembly Linker interprets a relative path in relationship to the current directory.</span></span>  
  
 <span data-ttu-id="a7dec-131">Následující příklad podepíše sestavení `MyAssembly.dll` se silným názvem pomocí souboru klíče `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="a7dec-131">The following example signs the assembly `MyAssembly.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 <span data-ttu-id="a7dec-132">Další informace o tomto nástroji najdete v tématu [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="a7dec-132">For more information about this tool, see [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="a7dec-133">Podepsání sestavení silným názvem pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="a7dec-133">To sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="a7dec-134">Přidat <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> nebo <xref:System.Reflection.AssemblyKeyNameAttribute> atribut souboru zdrojového kódu a zadejte název souboru nebo kontejneru, který obsahuje pár klíčů má použít při podepisování sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="a7dec-134">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
  
2. <span data-ttu-id="a7dec-135">Zkompilujte soubor zdrojového kódu běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="a7dec-135">Compile the source code file normally.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7dec-136">Jazyce C# a Visual Basic vydají upozornění kompilátoru (CS1699 a BC41008, v uvedeném pořadí) pokud narazí <xref:System.Reflection.AssemblyKeyFileAttribute> nebo <xref:System.Reflection.AssemblyKeyNameAttribute> atributů ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="a7dec-136">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="a7dec-137">Upozornění můžete ignorovat.</span><span class="sxs-lookup"><span data-stu-id="a7dec-137">You can ignore the warnings.</span></span>  
  
 <span data-ttu-id="a7dec-138">V následujícím příkladu <xref:System.Reflection.AssemblyKeyFileAttribute> atribut se souborem klíčů nazvaným `keyfile.snk`, který se nachází v adresáři, ve kterém je sestavení zkompilováno.</span><span class="sxs-lookup"><span data-stu-id="a7dec-138">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called `keyfile.snk`, which is located in the directory where the assembly is compiled.</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 <span data-ttu-id="a7dec-139">Při kompilaci zdrojového souboru můžete také podepsání sestavení pozdržet.</span><span class="sxs-lookup"><span data-stu-id="a7dec-139">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="a7dec-140">Další informace najdete v tématu [zpožděné podepisování sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="a7dec-140">For more information, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="a7dec-141">Podepsání sestavení silným názvem pomocí kompilátoru</span><span class="sxs-lookup"><span data-stu-id="a7dec-141">To sign an assembly with a strong name by using the compiler</span></span>  
  
-   <span data-ttu-id="a7dec-142">Zkompilujte soubor zdrojového kódu nebo soubory s `/keyfile` nebo `/delaysign` – možnost kompilátoru v jazyce C# a Visual Basic nebo `/KEYFILE` nebo `/DELAYSIGN` – možnost linkeru v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="a7dec-142">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="a7dec-143">Za název možnosti přidejte dvojtečku a název souboru s klíčem.</span><span class="sxs-lookup"><span data-stu-id="a7dec-143">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="a7dec-144">Při použití kompilátorů příkazového řádku můžete jednoduše zkopírovat soubor klíče do aktuálního adresáře, který obsahuje soubory zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="a7dec-144">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  
  
     <span data-ttu-id="a7dec-145">Informace o dodatečném podepisování naleznete v tématu [zpožděné podepisování sestavení](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="a7dec-145">For information on delay signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
     <span data-ttu-id="a7dec-146">Následující příklad použije kompilátor C# a podepíše sestavení `UtilityLibrary.dll` se silným názvem pomocí souboru klíče `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="a7dec-146">The following example uses the C# compiler and signs the assembly `UtilityLibrary.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a7dec-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7dec-147">See also</span></span>

- [<span data-ttu-id="a7dec-148">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="a7dec-148">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="a7dec-149">Postupy: Vytvoření páru veřejného a privátního klíče</span><span class="sxs-lookup"><span data-stu-id="a7dec-149">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="a7dec-150">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="a7dec-150">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="a7dec-151">Zpoždění podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="a7dec-151">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [<span data-ttu-id="a7dec-152">Správa sestavení a podepsání manifestu</span><span class="sxs-lookup"><span data-stu-id="a7dec-152">Managing Assembly and Manifest Signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="a7dec-153">Stránka Podepisování, návrhář projektu (C#)</span><span class="sxs-lookup"><span data-stu-id="a7dec-153">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
