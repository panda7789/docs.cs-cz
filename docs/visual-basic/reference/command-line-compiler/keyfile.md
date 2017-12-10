---
title: /keyfile
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b7f41b659399ae5a12663d4e359c02606bb6f952
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="keyfile"></a><span data-ttu-id="455ee-102">/keyfile</span><span class="sxs-lookup"><span data-stu-id="455ee-102">/keyfile</span></span>
<span data-ttu-id="455ee-103">Určuje soubor, který obsahuje klíč nebo pár klíčů umožnit sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="455ee-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="455ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="455ee-104">Syntax</span></span>  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="455ee-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="455ee-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="455ee-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="455ee-106">Required.</span></span> <span data-ttu-id="455ee-107">Soubor, který obsahuje klíč.</span><span class="sxs-lookup"><span data-stu-id="455ee-107">File that contains the key.</span></span> <span data-ttu-id="455ee-108">Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="455ee-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="455ee-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="455ee-109">Remarks</span></span>  
 <span data-ttu-id="455ee-110">Kompilátor vloží veřejný klíč do manifestu a následně podepíše konečné sestavení s privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="455ee-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="455ee-111">Chcete-li vygenerovat soubor klíče, zadejte `sn -k file` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="455ee-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="455ee-112">Další informace najdete v tématu [Sn.exe (nástroj silným názvem)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="455ee-112">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
 <span data-ttu-id="455ee-113">Pokud je kompilovat s `/target:module`, název souboru klíče je udržován v modulu a součástí sestavení, které se vytvoří při kompilaci sestavení s [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="455ee-113">If you compile with `/target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="455ee-114">Vaše informace šifrování můžete předat také kompilátoru s [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="455ee-114">You can also pass your encryption information to the compiler with [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="455ee-115">Použití [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) Pokud chcete, aby částečně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="455ee-115">Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="455ee-116">Tuto možnost můžete také určit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyFileAttribute>) ve zdrojovém kódu pro libovolný modul převodní jazyk Microsoft.</span><span class="sxs-lookup"><span data-stu-id="455ee-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="455ee-117">V případě obě `/keyfile` a [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) jsou zadány (pomocí parametru příkazového řádku nebo pomocí vlastního atributu) ve stejné kompilaci kompilátor poprvé pokusí kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="455ee-117">In case both `/keyfile` and [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="455ee-118">Pokud tato operace úspěšná, je podepsaný sestavení s informacemi v kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="455ee-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="455ee-119">Pokud kompilátor nenajde kontejner klíčů, se pokusí o zadaný soubor s `/keyfile`.</span><span class="sxs-lookup"><span data-stu-id="455ee-119">If the compiler does not find the key container, it tries the file specified with `/keyfile`.</span></span> <span data-ttu-id="455ee-120">Pokud to úspěšné, sestavení je podepsaná pomocí informací v souboru klíče a informace o klíči je nainstalován v kontejneru klíčů (podobně jako `sn -i`) tak, aby na další kompilace kontejner klíče budou platné.</span><span class="sxs-lookup"><span data-stu-id="455ee-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="455ee-121">Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="455ee-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="455ee-122">V tématu [vytvoření a použití sestavení](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="455ee-122">See [Creating and Using Strong-Named Assemblies](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="455ee-123">`/keyfile` Možnost není k dispozici v rámci [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] vývojového prostředí; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="455ee-123">The `/keyfile` option is not available from within the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="455ee-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="455ee-124">Example</span></span>  
 <span data-ttu-id="455ee-125">Následující kód zkompiluje zdrojový soubor `Input.vb` a určuje soubor klíče.</span><span class="sxs-lookup"><span data-stu-id="455ee-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="455ee-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="455ee-126">See Also</span></span>  
 [<span data-ttu-id="455ee-127">Sestavení a globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="455ee-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="455ee-128">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="455ee-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="455ee-129">/ Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="455ee-129">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="455ee-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="455ee-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
