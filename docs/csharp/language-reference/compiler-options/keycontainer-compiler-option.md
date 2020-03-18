---
title: -keycontainer (Možnosti kompilátoru Jazyka C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: fead2d4296cfa6fb0195cb4b43f6448c0fc7e6a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970137"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="19aef-102">-keycontainer (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="19aef-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="19aef-103">Určuje název kontejneru kryptografického klíče.</span><span class="sxs-lookup"><span data-stu-id="19aef-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19aef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19aef-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="19aef-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="19aef-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="19aef-106">Název kontejneru klíče silného názvu.</span><span class="sxs-lookup"><span data-stu-id="19aef-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19aef-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19aef-107">Remarks</span></span>  
 <span data-ttu-id="19aef-108">Při použití **-keycontainer** možnost kompilátor vytvoří komponentu sharable.</span><span class="sxs-lookup"><span data-stu-id="19aef-108">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="19aef-109">Kompilátor vloží veřejný klíč ze zadaného kontejneru do manifestu sestavení a podepíše konečné sestavení pomocí soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="19aef-109">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="19aef-110">Chcete-li vygenerovat `sn -k file` soubor klíče, zadejte příkaz na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="19aef-110">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="19aef-111">`sn -i`nainstaluje dvojici klíčů do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="19aef-111">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="19aef-112">Tato možnost není podporována, pokud kompilátor běží na CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19aef-112">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="19aef-113">Chcete-li podepsat sestavení při vytváření na CoreCLR, použijte [-keyfile](keyfile-compiler-option.md) možnost.</span><span class="sxs-lookup"><span data-stu-id="19aef-113">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="19aef-114">Pokud kompilujete s [-target:module](./target-module-compiler-option.md), název souboru klíče je držen v modulu a začleněny do sestavení při kompilaci tohoto modulu do sestavení s [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="19aef-114">If you compile with [-target:module](./target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="19aef-115">Tuto možnost můžete také zadat jako<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>vlastní atribut ( ) ve zdrojovém kódu pro libovolný modul zprostředkujícíjazyk společnosti Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="19aef-115">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="19aef-116">Můžete také předat informace o šifrování kompilátoru s [-keyfile](./keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="19aef-116">You can also pass your encryption information to the compiler with [-keyfile](./keyfile-compiler-option.md).</span></span> <span data-ttu-id="19aef-117">Použijte [-delaysign,](./delaysign-compiler-option.md) pokud chcete veřejný klíč přidán do manifestu sestavení, ale chcete odložit podepsání sestavení, dokud nebude testováno.</span><span class="sxs-lookup"><span data-stu-id="19aef-117">Use [-delaysign](./delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="19aef-118">Další informace naleznete [v tématu Vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) a [zpožděné podepisování sestavení](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="19aef-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="19aef-119">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="19aef-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="19aef-120">Tato možnost kompilátoru není k dispozici ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="19aef-120">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="19aef-121">Tuto možnost kompilátoru můžete <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>programově přistupovat pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="19aef-121">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19aef-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="19aef-122">See also</span></span>

- [<span data-ttu-id="19aef-123">C# Kompilátor -keyfile, volba</span><span class="sxs-lookup"><span data-stu-id="19aef-123">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="19aef-124">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="19aef-124">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="19aef-125">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="19aef-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
