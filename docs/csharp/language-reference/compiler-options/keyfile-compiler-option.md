---
title: -keyfile (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: bf271cc6b6887e930911071d4603b51daed55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970264"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="ce740-102">-keyfile (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ce740-102">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="ce740-103">Určuje název souboru obsahující kryptografický klíč.</span><span class="sxs-lookup"><span data-stu-id="ce740-103">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce740-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce740-104">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ce740-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ce740-105">Arguments</span></span>  
  
|<span data-ttu-id="ce740-106">Označení</span><span class="sxs-lookup"><span data-stu-id="ce740-106">Term</span></span>|<span data-ttu-id="ce740-107">Definice</span><span class="sxs-lookup"><span data-stu-id="ce740-107">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="ce740-108">Název souboru obsahujícího klíč silného názvu.</span><span class="sxs-lookup"><span data-stu-id="ce740-108">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce740-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce740-109">Remarks</span></span>  
 <span data-ttu-id="ce740-110">Při použití této možnosti kompilátor vloží veřejný klíč ze zadaného souboru do manifestu sestavení a podepíše konečné sestavení pomocí soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="ce740-110">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="ce740-111">Chcete-li vygenerovat soubor klíče, zadejte příkaz sn -k `file` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="ce740-111">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="ce740-112">Pokud kompilujete s **-target:module**, název souboru klíče je držen v modulu a začleněny do sestavení, který je vytvořen při kompilaci sestavení s [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ce740-112">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="ce740-113">Můžete také předat informace o šifrování kompilátoru s [-keycontainer](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ce740-113">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="ce740-114">Použijte [-delaysign,](./delaysign-compiler-option.md) pokud chcete částečně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="ce740-114">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="ce740-115">V případě, že oba -keyfile a -keycontainer jsou určeny (buď příkazového řádku možnost nebo vlastní atribut) ve stejné kompilaci, kompilátor nejprve vyzkoušet kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="ce740-115">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="ce740-116">Pokud se to podaří, sestavení je podepsáno informacemi v kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="ce740-116">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="ce740-117">Pokud kompilátor nenajde kontejner klíčů, pokusí se soubor zadaný souborem -keyfile.</span><span class="sxs-lookup"><span data-stu-id="ce740-117">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="ce740-118">Pokud se to podaří, sestavení je podepsáno s informacemi v souboru klíče a informace o klíči budou nainstalovány v kontejneru klíčů (podobně jako sn-i), takže při další kompilaci bude kontejner klíčů platný.</span><span class="sxs-lookup"><span data-stu-id="ce740-118">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="ce740-119">Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="ce740-119">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="ce740-120">Další informace naleznete [v tématu Vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) a [zpožděné podepisování sestavení](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="ce740-120">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ce740-121">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ce740-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ce740-122">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="ce740-122">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="ce740-123">Klikněte na stránku **vlastností Podpisu.**</span><span class="sxs-lookup"><span data-stu-id="ce740-123">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="ce740-124">Upravte vlastnost **Zvolit vlastnost souboru klíče se silným názvem.**</span><span class="sxs-lookup"><span data-stu-id="ce740-124">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="ce740-125">Tuto možnost kompilátoru můžete <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>programově přistupovat pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="ce740-125">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce740-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce740-126">See also</span></span>

- [<span data-ttu-id="ce740-127">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ce740-127">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ce740-128">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="ce740-128">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
