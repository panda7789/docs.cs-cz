---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 12895e4a18203a0d6c409a3b2117abbc59fab7a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653478"
---
# <a name="-keyfile"></a><span data-ttu-id="be97f-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="be97f-102">-keyfile</span></span>
<span data-ttu-id="be97f-103">Určuje soubor, který obsahuje klíč nebo pár klíčů umožnit sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="be97f-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be97f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be97f-104">Syntax</span></span>  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="be97f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="be97f-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="be97f-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="be97f-106">Required.</span></span> <span data-ttu-id="be97f-107">Soubor, který obsahuje klíč.</span><span class="sxs-lookup"><span data-stu-id="be97f-107">File that contains the key.</span></span> <span data-ttu-id="be97f-108">Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="be97f-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be97f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be97f-109">Remarks</span></span>  
 <span data-ttu-id="be97f-110">Kompilátor vloží veřejný klíč do manifestu a následně podepíše konečné sestavení s privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="be97f-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="be97f-111">Chcete-li vygenerovat soubor klíče, zadejte `sn -k file` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="be97f-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="be97f-112">Další informace najdete v tématu [Sn.exe (nástroj silným názvem)][Sn.exe (nástroj silným názvem)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="be97f-112">For more information, see [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="be97f-113">Pokud je kompilovat s `-target:module`, název souboru klíče je udržován v modulu a součástí sestavení, které se vytvoří při kompilaci sestavení s [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="be97f-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="be97f-114">Vaše informace šifrování můžete předat také kompilátoru s [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="be97f-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="be97f-115">Použití [- delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) Pokud chcete, aby částečně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="be97f-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="be97f-116">Tuto možnost můžete také určit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyFileAttribute>) ve zdrojovém kódu pro libovolný modul převodní jazyk Microsoft.</span><span class="sxs-lookup"><span data-stu-id="be97f-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="be97f-117">V případě obě `-keyfile` a [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) jsou zadány (pomocí parametru příkazového řádku nebo pomocí vlastního atributu) ve stejné kompilaci kompilátor poprvé pokusí kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="be97f-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="be97f-118">Pokud tato operace úspěšná, je podepsaný sestavení s informacemi v kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="be97f-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="be97f-119">Pokud kompilátor nenajde kontejner klíčů, se pokusí o zadaný soubor s `-keyfile`.</span><span class="sxs-lookup"><span data-stu-id="be97f-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="be97f-120">Pokud to úspěšné, sestavení je podepsaná pomocí informací v souboru klíče a informace o klíči je nainstalován v kontejneru klíčů (podobně jako `sn -i`) tak, aby na další kompilace kontejner klíče budou platné.</span><span class="sxs-lookup"><span data-stu-id="be97f-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="be97f-121">Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="be97f-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="be97f-122">V tématu [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="be97f-122">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be97f-123">`-keyfile` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="be97f-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be97f-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="be97f-124">Example</span></span>  
 <span data-ttu-id="be97f-125">Následující kód zkompiluje zdrojový soubor `Input.vb` a určuje soubor klíče.</span><span class="sxs-lookup"><span data-stu-id="be97f-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="be97f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="be97f-126">See Also</span></span>  
 [<span data-ttu-id="be97f-127">Sestavení a globální mezipaměť sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="be97f-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="be97f-128">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="be97f-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="be97f-129">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be97f-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="be97f-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="be97f-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
