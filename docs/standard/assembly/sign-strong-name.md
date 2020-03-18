---
title: 'Postup: Podepsání sestavení se silným názvem'
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
ms.openlocfilehash: 9998e69e8bf1505bcfc7a9103e9d89616dad9633
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160310"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="df9c9-102">Postup: Podepsání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="df9c9-102">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="df9c9-103">Přestože .NET Core podporuje sestavení se silným názvem a všechna sestavení v knihovně .NET Core jsou podepsána, většina sestavení třetích stran nepotřebují silné názvy.</span><span class="sxs-lookup"><span data-stu-id="df9c9-103">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="df9c9-104">Další informace najdete [v tématu Podpis silného názvu](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="df9c9-104">For more information, see [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="df9c9-105">Existuje několik způsobů, jak můžete podepsat sestavení pomocí silného názvu:</span><span class="sxs-lookup"><span data-stu-id="df9c9-105">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="df9c9-106">Pomocí karty **Podpisv** dialogovém okně **Vlastnosti** projektu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df9c9-106">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="df9c9-107">Nejjednodušším a nejpohodlnějším způsobem je podepsání sestavení pomocí silného názvu.</span><span class="sxs-lookup"><span data-stu-id="df9c9-107">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="df9c9-108">Pomocí [propojovacího programu sestavení (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) propojte modul kódu rozhraní .NET Framework (soubor *.netmodule)* se souborem klíče.</span><span class="sxs-lookup"><span data-stu-id="df9c9-108">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="df9c9-109">Pomocí atributů sestavení pro vložení informací o silném názvu do kódu.</span><span class="sxs-lookup"><span data-stu-id="df9c9-109">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="df9c9-110">Můžete použít buď <xref:System.Reflection.AssemblyKeyFileAttribute> nebo <xref:System.Reflection.AssemblyKeyNameAttribute> atribut, v závislosti na tom, kde je umístěn soubor klíče, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="df9c9-110">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="df9c9-111">Pomocí možností kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="df9c9-111">By using compiler options.</span></span>  
  
 <span data-ttu-id="df9c9-112">Pro podepsání sestavení silným názvem musíte mít pár kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="df9c9-112">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="df9c9-113">Další informace o vytvoření páru klíčů naleznete v [tématu Postup: Vytvoření páru klíčů veřejného a soukromého sektoru](create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="df9c9-113">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="df9c9-114">Vytvoření a podepsání sestavení se silným názvem pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df9c9-114">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="df9c9-115">V **Průzkumníku řešení**otevřete místní nabídku projektu a pak zvolte **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="df9c9-115">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="df9c9-116">Zvolte kartu **Podpisování.**</span><span class="sxs-lookup"><span data-stu-id="df9c9-116">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="df9c9-117">Vyberte podepsat pole **sestavy.**</span><span class="sxs-lookup"><span data-stu-id="df9c9-117">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="df9c9-118">V poli **Zvolit soubor klíče se silným názvem** zvolte **Procházet**a přejděte na soubor klíče.</span><span class="sxs-lookup"><span data-stu-id="df9c9-118">In the **Choose a strong name key file** box, choose **Browse**, and then navigate to the key file.</span></span> <span data-ttu-id="df9c9-119">Chcete-li vytvořit nový soubor klíče, zvolte **Nový** a zadejte jeho název do dialogového okna **Vytvořit silný klíč názvu.**</span><span class="sxs-lookup"><span data-stu-id="df9c9-119">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df9c9-120">Chcete-li [zpozdit podepsání sestavení](delay-sign.md), zvolte soubor veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="df9c9-120">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="df9c9-121">Vytvoření a podepsání sestavení se silným názvem pomocí propojovacího zařízení sestavení</span><span class="sxs-lookup"><span data-stu-id="df9c9-121">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="df9c9-122">Na [příkazovém řádku pro vývojáře pro visual studio](../../framework/tools/developer-command-prompt-for-vs.md)zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="df9c9-122">At the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), enter the following command:</span></span>  

<span data-ttu-id="df9c9-123">**al** **/out:**\<*moduleName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="df9c9-123">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="df9c9-124">Kde:</span><span class="sxs-lookup"><span data-stu-id="df9c9-124">Where:</span></span>  

- <span data-ttu-id="df9c9-125">*assemblyName* je název silně podepsaného sestavení (soubor *U.dll* nebo *.exe),* který bude vyzařovávat Linker sestavení.</span><span class="sxs-lookup"><span data-stu-id="df9c9-125">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="df9c9-126">*moduleName* je název modulu kódu rozhraní .NET Framework (soubor *.netmodule),* který obsahuje jeden nebo více typů.</span><span class="sxs-lookup"><span data-stu-id="df9c9-126">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="df9c9-127">Soubor *.netmodule* můžete vytvořit kompilací kódu pomocí `/target:module` přepínače v jazyce C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="df9c9-127">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="df9c9-128">*keyfileName* je název kontejneru nebo souboru, který obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="df9c9-128">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="df9c9-129">Linker sestavení interpretuje relativní cestu ve vztahu k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="df9c9-129">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="df9c9-130">Následující příklad podepisuje sestavení *MyAssembly.dll* silným názvem pomocí souboru klíče *sgKey.snk*.</span><span class="sxs-lookup"><span data-stu-id="df9c9-130">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="df9c9-131">Další informace o tomto nástroji naleznete v [tématu Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="df9c9-131">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="df9c9-132">Podepsání sestavení silným názvem pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="df9c9-132">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="df9c9-133">Přidejte <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> <xref:System.Reflection.AssemblyKeyNameAttribute> atribut nebo do souboru zdrojového kódu a zadejte název souboru nebo kontejneru, který obsahuje dvojici klíčů, která se má použít při podepisování sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="df9c9-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  

2. <span data-ttu-id="df9c9-134">Zkompilujte soubor zdrojového kódu běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="df9c9-134">Compile the source code file normally.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="df9c9-135">Kompilátory jazyka C# a Visual Basic vydávají upozornění kompilátoru (CS1699 a <xref:System.Reflection.AssemblyKeyFileAttribute> <xref:System.Reflection.AssemblyKeyNameAttribute> BC41008, v uvedeném pořadí), když narazí na atribut nebo ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="df9c9-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="df9c9-136">Upozornění můžete ignorovat.</span><span class="sxs-lookup"><span data-stu-id="df9c9-136">You can ignore the warnings.</span></span>  

<span data-ttu-id="df9c9-137">Následující příklad používá <xref:System.Reflection.AssemblyKeyFileAttribute> atribut s klíčovým souborem s názvem *keyfile.snk*, který je umístěn v adresáři, kde je sestavení kompilován.</span><span class="sxs-lookup"><span data-stu-id="df9c9-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk*, which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="df9c9-138">Při kompilaci zdrojového souboru můžete také podepsání sestavení pozdržet.</span><span class="sxs-lookup"><span data-stu-id="df9c9-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="df9c9-139">Další informace naleznete v [tématu Delay-sign sestavení](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="df9c9-139">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="df9c9-140">Podepsání sestavení se silným názvem pomocí kompilátoru</span><span class="sxs-lookup"><span data-stu-id="df9c9-140">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="df9c9-141">Kompilace souboru zdrojového `/keyfile` kódu `/delaysign` nebo soubory s možností nebo kompilátoru v jazyce C# a Visual Basic nebo `/KEYFILE` možnost nebo `/DELAYSIGN` linker v jazyce C++.</span><span class="sxs-lookup"><span data-stu-id="df9c9-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="df9c9-142">Za název možnosti přidejte dvojtečku a název souboru s klíčem.</span><span class="sxs-lookup"><span data-stu-id="df9c9-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="df9c9-143">Při použití kompilátorů příkazového řádku můžete jednoduše zkopírovat soubor klíče do aktuálního adresáře, který obsahuje soubory zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="df9c9-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="df9c9-144">Informace o zpoždění podepisování naleznete v [tématu Delay-sign sestavení](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="df9c9-144">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="df9c9-145">Následující příklad používá kompilátor Jazyka C# a podepisuje soubor *Assembly UtilityLibrary.dll* silným názvem pomocí souboru klíče *sgKey.snk*.</span><span class="sxs-lookup"><span data-stu-id="df9c9-145">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="df9c9-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="df9c9-146">See also</span></span>

- [<span data-ttu-id="df9c9-147">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="df9c9-147">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="df9c9-148">Postup: Vytvoření páru klíčů veřejného a soukromého sektoru</span><span class="sxs-lookup"><span data-stu-id="df9c9-148">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="df9c9-149">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="df9c9-149">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="df9c9-150">Opožděný podpis sestavení</span><span class="sxs-lookup"><span data-stu-id="df9c9-150">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="df9c9-151">Správa podepsání sestavení a manifestu</span><span class="sxs-lookup"><span data-stu-id="df9c9-151">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="df9c9-152">Podepisovací stránka, Návrhář projektu</span><span class="sxs-lookup"><span data-stu-id="df9c9-152">Signing page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
