---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: c13f34c23cad9c909c2c5bd3447f1a8fa53f9b4d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833303"
---
# <a name="-keyfile"></a><span data-ttu-id="8f5ee-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="8f5ee-102">-keyfile</span></span>
<span data-ttu-id="8f5ee-103">Určuje soubor, který obsahuje klíč nebo dvojici klíčů poskytnout sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f5ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f5ee-104">Syntax</span></span>  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="8f5ee-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8f5ee-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="8f5ee-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-106">Required.</span></span> <span data-ttu-id="8f5ee-107">Soubor, který obsahuje klíč.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-107">File that contains the key.</span></span> <span data-ttu-id="8f5ee-108">Pokud název souboru obsahuje mezery, uzavřete název do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="8f5ee-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f5ee-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f5ee-109">Remarks</span></span>  
 <span data-ttu-id="8f5ee-110">Kompilátor vloží veřejný klíč do manifestu sestavení a poté podepíše konečné sestavení soukromým klíčem.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="8f5ee-111">Chcete-li generovat soubor s klíčem, zadejte `sn -k file` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="8f5ee-112">Další informace najdete v tématu [Sn.exe (nástroj Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="8f5ee-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="8f5ee-113">Pokud kompilujete s `-target:module`, je název souboru klíče uložené v modulu a součástí sestavení, které se vytvoří, když kompilujete sestavení s [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="8f5ee-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="8f5ee-114">Můžete také předat údaje o šifrování pro kompilátor [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="8f5ee-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="8f5ee-115">Použití [- delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) potřebujete částečně podepsaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="8f5ee-116">Tuto možnost lze také nastavit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyFileAttribute>) ve zdrojovém kódu pro jakýkoli modul jazyka Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="8f5ee-117">V případě obě `-keyfile` a [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) zadávají (pomocí možnosti příkazového řádku nebo pomocí vlastního atributu) ve stejné kompilaci, kompilátor se pokusí nejprve kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="8f5ee-118">Pokud tato operace úspěšná, sestavení je podepsáno pomocí informací v kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="8f5ee-119">Pokud kompilátor nenajde kontejneru klíčů, pokusí se použít soubor určený `-keyfile`.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="8f5ee-120">Pokud se toto povede, sestavení je podepsáno informacemi ze souboru klíčů a informace o klíči se instaluje v kontejneru klíčů (podobné `sn -i`) tak, aby při další kompilaci bude platný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="8f5ee-121">Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="8f5ee-122">Zobrazit [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-122">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f5ee-123">`-keyfile` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f5ee-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f5ee-124">Example</span></span>  
 <span data-ttu-id="8f5ee-125">Následující kód se zkompiluje zdrojový soubor `Input.vb` a určuje soubor klíče.</span><span class="sxs-lookup"><span data-stu-id="8f5ee-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f5ee-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f5ee-126">See also</span></span>

- [<span data-ttu-id="8f5ee-127">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="8f5ee-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="8f5ee-128">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="8f5ee-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8f5ee-129">– referenční dokumentace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f5ee-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="8f5ee-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="8f5ee-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
