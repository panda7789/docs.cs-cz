---
title: "-keycontainer (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 944a9b4dbbed76f388642d67be9518343f750de5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="372a4-102">-keycontainer (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="372a4-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="372a4-103">Určuje název kontejneru kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="372a4-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="372a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="372a4-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="372a4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="372a4-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="372a4-106">Název kontejneru klíčů silným názvem.</span><span class="sxs-lookup"><span data-stu-id="372a4-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="372a4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="372a4-107">Remarks</span></span>  
 <span data-ttu-id="372a4-108">Když **- keycontainer** možnost, kompilátor vytvoří komponentu lze sdílet vložením veřejný klíč ze zadaného kontejneru do manifestu a podepíše konečné sestavení s privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="372a4-108">When the **-keycontainer** option is used, the compiler creates a sharable component by inserting a public key from the specified container into the assembly manifest and signing the final assembly with the private key.</span></span> <span data-ttu-id="372a4-109">Chcete-li vygenerovat soubor klíče, zadejte sn -k `file` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="372a4-109">To generate a key file, type sn -k `file` at the command line.</span></span> <span data-ttu-id="372a4-110">sn -i nainstaluje pár klíčů do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="372a4-110">sn -i installs the key pair into a container.</span></span>  
  
 <span data-ttu-id="372a4-111">Pokud je kompilovat s [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), název souboru klíče je udržován v modulu a začleněn do sestavení při kompilaci tohoto modulu do sestavení s [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="372a4-111">If you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="372a4-112">Tuto možnost můžete také určit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) ve zdrojovém kódu pro libovolný modul (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="372a4-112">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="372a4-113">Vaše informace šifrování můžete předat také kompilátoru s [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="372a4-113">You can also pass your encryption information to the compiler with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="372a4-114">Použití [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Pokud chcete přidat do manifestu sestavení veřejný klíč, ale chcete zpoždění podepsání sestavení, dokud po testování.</span><span class="sxs-lookup"><span data-stu-id="372a4-114">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="372a4-115">Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpoždění podepsání sestavení](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="372a4-115">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="372a4-116">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="372a4-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="372a4-117">Tato možnost kompilátoru není k dispozici ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="372a4-117">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="372a4-118">Prostřednictvím kódu programu přístup k této možnosti kompilátoru s <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="372a4-118">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="372a4-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="372a4-119">See Also</span></span>  
 [<span data-ttu-id="372a4-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="372a4-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="372a4-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="372a4-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
