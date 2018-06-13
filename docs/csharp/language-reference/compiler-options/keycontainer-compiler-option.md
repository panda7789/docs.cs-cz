---
title: -keycontainer (možnosti kompilátoru C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 5a7b378cad7a1df9249fcbefa28bb9aa9a6a3da4
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472565"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="74490-102">-keycontainer (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="74490-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="74490-103">Určuje název kontejneru kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="74490-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74490-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74490-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="74490-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="74490-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="74490-106">Název kontejneru klíčů silným názvem.</span><span class="sxs-lookup"><span data-stu-id="74490-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74490-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74490-107">Remarks</span></span>  
 <span data-ttu-id="74490-108">Když **- keycontainer** možnost, kompilátor vytvoří komponentu lze sdílet.</span><span class="sxs-lookup"><span data-stu-id="74490-108">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="74490-109">Kompilátor vloží veřejný klíč ze zadaného kontejneru do manifestu a podepíše konečné sestavení s privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="74490-109">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="74490-110">Chcete-li vygenerovat soubor klíče, zadejte `sn -k file` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="74490-110">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="74490-111">`sn -i` nainstaluje páru klíčů do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="74490-111">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="74490-112">Tato možnost není podporovaná, když kompilátor běží na CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74490-112">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="74490-113">Chcete-li při sestavování na CoreCLR podepsání sestavení, použijte [- keyfile](keyfile-compiler-option.md) možnost.</span><span class="sxs-lookup"><span data-stu-id="74490-113">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="74490-114">Pokud je kompilovat s [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), název souboru klíče je udržován v modulu a začleněn do sestavení při kompilaci tohoto modulu do sestavení s [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="74490-114">If you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="74490-115">Tuto možnost můžete také určit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) ve zdrojovém kódu pro libovolný modul (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="74490-115">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="74490-116">Vaše informace šifrování můžete předat také kompilátoru s [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="74490-116">You can also pass your encryption information to the compiler with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="74490-117">Použití [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) Pokud chcete přidat do manifestu sestavení veřejný klíč, ale chcete zpoždění podepsání sestavení, dokud po testování.</span><span class="sxs-lookup"><span data-stu-id="74490-117">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="74490-118">Další informace najdete v tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) a [zpoždění podepsání sestavení](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="74490-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="74490-119">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="74490-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="74490-120">Tato možnost kompilátoru není k dispozici ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="74490-120">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="74490-121">Prostřednictvím kódu programu přístup k této možnosti kompilátoru s <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="74490-121">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74490-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="74490-122">See Also</span></span>  
 <span data-ttu-id="74490-123">[-Keyfile – možnost kompilátor jazyka C#](keyfile-compiler-option.md) [možnosti kompilátoru C#](index.md)</span><span class="sxs-lookup"><span data-stu-id="74490-123">[C# Compiler -keyfile option](keyfile-compiler-option.md) [C# Compiler Options](index.md)</span></span>  
 [<span data-ttu-id="74490-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="74490-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
