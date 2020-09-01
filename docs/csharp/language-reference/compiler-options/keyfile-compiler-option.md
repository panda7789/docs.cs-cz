---
description: -keyfile (možnosti kompilátoru C#)
title: -keyfile (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: a97fc00201be1cf8043fc353b20ef447468a06bf
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125485"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="3ac7d-103">-keyfile (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="3ac7d-103">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="3ac7d-104">Určuje název souboru, který obsahuje kryptografický klíč.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-104">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ac7d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ac7d-105">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="3ac7d-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3ac7d-106">Arguments</span></span>  
  
|<span data-ttu-id="3ac7d-107">Pojem</span><span class="sxs-lookup"><span data-stu-id="3ac7d-107">Term</span></span>|<span data-ttu-id="3ac7d-108">Definice</span><span class="sxs-lookup"><span data-stu-id="3ac7d-108">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="3ac7d-109">Název souboru, který obsahuje klíč se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-109">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ac7d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ac7d-110">Remarks</span></span>  
 <span data-ttu-id="3ac7d-111">Při použití této možnosti kompilátor vloží veřejný klíč ze zadaného souboru do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-111">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="3ac7d-112">Chcete-li vygenerovat soubor klíče, zadejte do `file` příkazového řádku SN-k.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-112">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="3ac7d-113">Pokud kompilujete pomocí **-target: Module**, název souboru klíče je uložen v modulu a začleněn do sestavení, které je vytvořeno při kompilaci sestavení pomocí [-addmodule –](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3ac7d-113">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="3ac7d-114">Můžete také předat informace o šifrování kompilátoru s modulem, který [obsahuje](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3ac7d-114">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="3ac7d-115">Použijte [-delaysign](./delaysign-compiler-option.md) , pokud chcete použít částečně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-115">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="3ac7d-116">V případě, že jsou zadány oba parametry-keyfile a-in (buď parametrem příkazového řádku nebo vlastním atributem) ve stejné kompilaci, kompilátor nejprve vyhledá kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-116">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="3ac7d-117">Pokud je tato operace úspěšná, sestavení je podepsáno informacemi z kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-117">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="3ac7d-118">Pokud kompilátor nenalezne kontejner klíčů, pokusí se soubor určený parametrem-keyfile.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-118">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="3ac7d-119">Pokud je to úspěšné, sestavení je podepsáno informacemi v souboru klíče a informace o klíči budou nainstalovány do kontejneru klíčů (podobně jako sn-i), takže při další kompilaci bude kontejner klíčů platný.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-119">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="3ac7d-120">Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-120">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="3ac7d-121">Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) a [Zpožděné podepisování sestavení](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="3ac7d-121">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3ac7d-122">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3ac7d-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3ac7d-123">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="3ac7d-123">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="3ac7d-124">Klikněte na stránku vlastností **podepisování** .</span><span class="sxs-lookup"><span data-stu-id="3ac7d-124">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="3ac7d-125">Upravte vlastnost **soubor klíče se silným názvem** .</span><span class="sxs-lookup"><span data-stu-id="3ac7d-125">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="3ac7d-126">Pomocí programu můžete programově získat přístup k této možnosti kompilátoru <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A> .</span><span class="sxs-lookup"><span data-stu-id="3ac7d-126">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ac7d-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ac7d-127">See also</span></span>

- [<span data-ttu-id="3ac7d-128">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="3ac7d-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3ac7d-129">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="3ac7d-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
