---
title: -keyfile (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: bf271cc6b6887e930911071d4603b51daed55e61
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970264"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="bb615-102">-keyfile (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="bb615-102">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="bb615-103">Určuje název souboru, který obsahuje kryptografický klíč.</span><span class="sxs-lookup"><span data-stu-id="bb615-103">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb615-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb615-104">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="bb615-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bb615-105">Arguments</span></span>  
  
|<span data-ttu-id="bb615-106">Termín</span><span class="sxs-lookup"><span data-stu-id="bb615-106">Term</span></span>|<span data-ttu-id="bb615-107">Definice</span><span class="sxs-lookup"><span data-stu-id="bb615-107">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="bb615-108">Název souboru, který obsahuje klíč se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="bb615-108">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb615-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb615-109">Remarks</span></span>  
 <span data-ttu-id="bb615-110">Při použití této možnosti kompilátor vloží veřejný klíč ze zadaného souboru do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem.</span><span class="sxs-lookup"><span data-stu-id="bb615-110">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="bb615-111">Chcete-li vygenerovat soubor klíče, zadejte do `file` příkazového řádku SN-k.</span><span class="sxs-lookup"><span data-stu-id="bb615-111">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="bb615-112">Pokud kompilujete pomocí **-target: Module**, název souboru klíče je uložen v modulu a začleněn do sestavení, které je vytvořeno při kompilaci sestavení pomocí [-addmodule –](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="bb615-112">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="bb615-113">Můžete také předat informace o šifrování kompilátoru s modulem, který [obsahuje](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="bb615-113">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="bb615-114">Použijte [-delaysign](./delaysign-compiler-option.md) , pokud chcete použít částečně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="bb615-114">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="bb615-115">V případě, že jsou zadány oba parametry-keyfile a-in (buď parametrem příkazového řádku nebo vlastním atributem) ve stejné kompilaci, kompilátor nejprve vyhledá kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="bb615-115">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="bb615-116">Pokud je tato operace úspěšná, sestavení je podepsáno informacemi z kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="bb615-116">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="bb615-117">Pokud kompilátor nenalezne kontejner klíčů, pokusí se soubor určený parametrem-keyfile.</span><span class="sxs-lookup"><span data-stu-id="bb615-117">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="bb615-118">Pokud je to úspěšné, sestavení je podepsáno informacemi v souboru klíče a informace o klíči budou nainstalovány do kontejneru klíčů (podobně jako sn-i), takže při další kompilaci bude kontejner klíčů platný.</span><span class="sxs-lookup"><span data-stu-id="bb615-118">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="bb615-119">Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="bb615-119">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="bb615-120">Další informace naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) a [Zpožděné podepisování sestavení](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="bb615-120">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="bb615-121">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb615-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="bb615-122">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="bb615-122">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="bb615-123">Klikněte na stránku vlastností **podepisování** .</span><span class="sxs-lookup"><span data-stu-id="bb615-123">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="bb615-124">Upravte vlastnost **soubor klíče se silným názvem** .</span><span class="sxs-lookup"><span data-stu-id="bb615-124">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="bb615-125">Pomocí <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>programu můžete programově získat přístup k této možnosti kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="bb615-125">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb615-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb615-126">See also</span></span>

- [<span data-ttu-id="bb615-127">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bb615-127">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="bb615-128">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="bb615-128">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
