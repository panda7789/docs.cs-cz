---
title: 'Postupy: podepsání sestavení silným názvem'
description: V tomto článku se dozvíte, jak podepsat sestavení .NET se silným názvem pomocí karty podepisování, linkeru sestavení, atributů sestavení nebo možností kompilátoru.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: d4888a12ac0494ca34eac3553a5374c3517fee38
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378623"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="69bf1-103">Postupy: podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="69bf1-103">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="69bf1-104">I když .NET Core podporuje sestavení se silným názvem a všechna sestavení v knihovně .NET Core jsou podepsaná, většina sestavení třetích stran nepotřebuje silné názvy.</span><span class="sxs-lookup"><span data-stu-id="69bf1-104">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="69bf1-105">Další informace najdete v tématu [podepisování silného názvu](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="69bf1-105">For more information, see [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="69bf1-106">Existuje několik způsobů, jak můžete podepsat sestavení pomocí silného názvu:</span><span class="sxs-lookup"><span data-stu-id="69bf1-106">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="69bf1-107">Pomocí karty **podepisování** v dialogovém okně **vlastnosti** projektu v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="69bf1-107">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="69bf1-108">Nejjednodušším a nejpohodlnějším způsobem je podepsání sestavení pomocí silného názvu.</span><span class="sxs-lookup"><span data-stu-id="69bf1-108">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="69bf1-109">Pomocí [linkeru sestavení (Al. exe)](../../framework/tools/al-exe-assembly-linker.md) můžete propojit modul kódu .NET Framework (soubor *. netmodule* ) se souborem klíče.</span><span class="sxs-lookup"><span data-stu-id="69bf1-109">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="69bf1-110">Pomocí atributů sestavení pro vložení informací o silném názvu do kódu.</span><span class="sxs-lookup"><span data-stu-id="69bf1-110">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="69bf1-111">Můžete použít buď <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> atribut, nebo, v závislosti na tom, kde je umístěn soubor klíče, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="69bf1-111">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="69bf1-112">Pomocí možností kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="69bf1-112">By using compiler options.</span></span>  
  
 <span data-ttu-id="69bf1-113">Pro podepsání sestavení silným názvem musíte mít pár kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="69bf1-113">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="69bf1-114">Další informace o vytváření páru klíčů naleznete v tématu [How to: Create a Public-Private Key páru](create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="69bf1-114">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="69bf1-115">Vytvoření a podepsání sestavení silným názvem pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="69bf1-115">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="69bf1-116">V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="69bf1-116">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="69bf1-117">Klikněte na kartu **podepisování** .</span><span class="sxs-lookup"><span data-stu-id="69bf1-117">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="69bf1-118">Vyberte pole **podepsat sestavení** .</span><span class="sxs-lookup"><span data-stu-id="69bf1-118">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="69bf1-119">V poli **Zvolte soubor klíče se silným názvem** zvolte možnost **Procházet**a potom přejděte k souboru klíče.</span><span class="sxs-lookup"><span data-stu-id="69bf1-119">In the **Choose a strong name key file** box, choose **Browse**, and then navigate to the key file.</span></span> <span data-ttu-id="69bf1-120">Chcete-li vytvořit nový soubor klíče, vyberte možnost **Nový** a zadejte jeho název do dialogového okna **vytvořit klíč se silným názvem** .</span><span class="sxs-lookup"><span data-stu-id="69bf1-120">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69bf1-121">Aby bylo možné [zpozdit podepsání sestavení](delay-sign.md), vyberte soubor veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="69bf1-121">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="69bf1-122">Vytvoření a podepsání sestavení silným názvem pomocí linkeru sestavení</span><span class="sxs-lookup"><span data-stu-id="69bf1-122">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="69bf1-123">V [Developer Command Prompt pro Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md)zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="69bf1-123">At the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), enter the following command:</span></span>  

<span data-ttu-id="69bf1-124">**Al** **/out:** \< *AssemblyName* >  \* \< Module>\* **/keyfile:** název \< *souboru*></span><span class="sxs-lookup"><span data-stu-id="69bf1-124">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="69bf1-125">Kde:</span><span class="sxs-lookup"><span data-stu-id="69bf1-125">Where:</span></span>  

- <span data-ttu-id="69bf1-126">*AssemblyName* je název silně podepsaného sestavení (soubor *. dll* nebo *. exe* ), který bude linker sestavení generovat.</span><span class="sxs-lookup"><span data-stu-id="69bf1-126">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="69bf1-127">název *modulu* je název modulu .NET Frameworkho kódu (soubor *. netmodule* ), který obsahuje jeden nebo více typů.</span><span class="sxs-lookup"><span data-stu-id="69bf1-127">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="69bf1-128">Můžete vytvořit soubor *. netmodule* kompilováním kódu s `/target:module` přepínačem v jazyce C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="69bf1-128">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="69bf1-129">název *souboru* je název kontejneru nebo souboru, který obsahuje pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="69bf1-129">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="69bf1-130">Linker sestavení interpretuje relativní cestu ve vztahu k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="69bf1-130">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="69bf1-131">Následující příklad podepíše sestavení *MyAssembly. dll* se silným názvem pomocí souboru Key *klíči sgKey. snk*.</span><span class="sxs-lookup"><span data-stu-id="69bf1-131">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="69bf1-132">Další informace o tomto nástroji naleznete v tématu [linker sestavení](../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="69bf1-132">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="69bf1-133">Podepsání sestavení silným názvem pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="69bf1-133">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="69bf1-134">Přidejte <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> atribut nebo <xref:System.Reflection.AssemblyKeyNameAttribute> do souboru zdrojového kódu a zadejte název souboru nebo kontejneru, který obsahuje dvojici klíčů pro použití při podepisování sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="69bf1-134">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  

2. <span data-ttu-id="69bf1-135">Zkompilujte soubor zdrojového kódu běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="69bf1-135">Compile the source code file normally.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="69bf1-136">Kompilátory jazyka C# a Visual Basic vydávají upozornění kompilátoru (CS1699 a BC41008) při výskytu <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> atributu nebo ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="69bf1-136">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="69bf1-137">Upozornění můžete ignorovat.</span><span class="sxs-lookup"><span data-stu-id="69bf1-137">You can ignore the warnings.</span></span>  

<span data-ttu-id="69bf1-138">Následující příklad používá <xref:System.Reflection.AssemblyKeyFileAttribute> atribut se souborem klíče s názvem *keyfile. snk*, který je umístěn v adresáři, kde je sestavení zkompilováno.</span><span class="sxs-lookup"><span data-stu-id="69bf1-138">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk*, which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="69bf1-139">Při kompilaci zdrojového souboru můžete také podepsání sestavení pozdržet.</span><span class="sxs-lookup"><span data-stu-id="69bf1-139">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="69bf1-140">Další informace naleznete v tématu [opožděné podepsání sestavení](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="69bf1-140">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="69bf1-141">Podepsání sestavení silným názvem pomocí kompilátoru</span><span class="sxs-lookup"><span data-stu-id="69bf1-141">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="69bf1-142">Zkompilujte soubor zdrojového kódu nebo soubory pomocí `/keyfile` `/delaysign` Možnosti kompilátoru nebo v jazyce C# a Visual Basic nebo `/KEYFILE` `/DELAYSIGN` možnost linkeru v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="69bf1-142">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="69bf1-143">Za název možnosti přidejte dvojtečku a název souboru s klíčem.</span><span class="sxs-lookup"><span data-stu-id="69bf1-143">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="69bf1-144">Při použití kompilátorů příkazového řádku můžete jednoduše zkopírovat soubor klíče do aktuálního adresáře, který obsahuje soubory zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="69bf1-144">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="69bf1-145">Informace o zpožděném podepisování naleznete v tématu [opožděné podepsání sestavení](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="69bf1-145">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="69bf1-146">Následující příklad používá kompilátor jazyka C# a podepíše sestavení *UtilityLibrary. dll* se silným názvem pomocí souboru klíče *klíči sgKey. snk*.</span><span class="sxs-lookup"><span data-stu-id="69bf1-146">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="69bf1-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="69bf1-147">See also</span></span>

- [<span data-ttu-id="69bf1-148">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="69bf1-148">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="69bf1-149">Postupy: Vytvoření páru veřejného a soukromého klíče</span><span class="sxs-lookup"><span data-stu-id="69bf1-149">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="69bf1-150">Al. exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="69bf1-150">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="69bf1-151">Opožděný podpis sestavení</span><span class="sxs-lookup"><span data-stu-id="69bf1-151">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="69bf1-152">Správa podepsání sestavení a manifestu</span><span class="sxs-lookup"><span data-stu-id="69bf1-152">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="69bf1-153">Stránka podepisování, Návrhář projektu</span><span class="sxs-lookup"><span data-stu-id="69bf1-153">Signing page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
