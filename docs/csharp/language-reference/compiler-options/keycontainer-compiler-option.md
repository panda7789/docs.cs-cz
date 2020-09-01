---
description: -obsahoval (možnosti kompilátoru C#)
title: -obsahoval (možnosti kompilátoru C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 8b11380683159b7792149558a5dd432707ba3818
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125498"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="d08b7-103">-obsahoval (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="d08b7-103">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="d08b7-104">Určuje název kontejneru kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="d08b7-104">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d08b7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d08b7-105">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="d08b7-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d08b7-106">Arguments</span></span>  
 `string`  
 <span data-ttu-id="d08b7-107">Název kontejneru klíčů se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="d08b7-107">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d08b7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d08b7-108">Remarks</span></span>  
 <span data-ttu-id="d08b7-109">Je-li použita možnost **-** držitele, kompilátor vytvoří součást, kterou lze sdílet.</span><span class="sxs-lookup"><span data-stu-id="d08b7-109">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="d08b7-110">Kompilátor vloží veřejný klíč ze zadaného kontejneru do manifestu sestavení a podepíše konečné sestavení pomocí privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="d08b7-110">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="d08b7-111">Chcete-li vygenerovat soubor klíče, zadejte do `sn -k file` příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d08b7-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="d08b7-112">`sn -i` nainstaluje dvojici klíčů do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d08b7-112">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="d08b7-113">Tato možnost není podporována, pokud kompilátor běží na CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d08b7-113">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="d08b7-114">Pro podepsání sestavení při sestavování na CoreCLR použijte možnost [-keyfile](keyfile-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="d08b7-114">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="d08b7-115">Pokud kompilujete pomocí [-target: Module](./target-module-compiler-option.md), název souboru klíče je uložen v modulu a začleněn do sestavení při kompilaci tohoto modulu do sestavení s [-addmodule –](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d08b7-115">If you compile with [-target:module](./target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="d08b7-116">Tuto možnost lze také zadat jako vlastní atribut ( <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType> ) ve zdrojovém kódu pro libovolný modul jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="d08b7-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="d08b7-117">Můžete také předat informace o šifrování kompilátoru s parametrem [-keyfile](./keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d08b7-117">You can also pass your encryption information to the compiler with [-keyfile](./keyfile-compiler-option.md).</span></span> <span data-ttu-id="d08b7-118">Použijte [-delaysign](./delaysign-compiler-option.md) , pokud chcete, aby byl do manifestu sestavení přidán veřejný klíč, ale chcete zpozdit podepisování sestavení, dokud nebylo testováno.</span><span class="sxs-lookup"><span data-stu-id="d08b7-118">Use [-delaysign](./delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="d08b7-119">Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) a [Zpožděné podepisování sestavení](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="d08b7-119">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d08b7-120">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d08b7-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d08b7-121">Tato možnost kompilátoru není k dispozici ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d08b7-121">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="d08b7-122">Pomocí programu můžete programově získat přístup k této možnosti kompilátoru <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A> .</span><span class="sxs-lookup"><span data-stu-id="d08b7-122">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d08b7-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="d08b7-123">See also</span></span>

- [<span data-ttu-id="d08b7-124">C# – možnost kompilátoru – parametr keyfile</span><span class="sxs-lookup"><span data-stu-id="d08b7-124">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="d08b7-125">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="d08b7-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="d08b7-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="d08b7-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
