---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266739"
---
# <a name="-keyfile"></a><span data-ttu-id="c4d46-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="c4d46-102">-keyfile</span></span>
<span data-ttu-id="c4d46-103">Určuje soubor obsahující klíč nebo pár klíčů, aby sestava byla silně pojmenujena.</span><span class="sxs-lookup"><span data-stu-id="c4d46-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4d46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4d46-104">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="c4d46-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c4d46-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="c4d46-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="c4d46-106">Required.</span></span> <span data-ttu-id="c4d46-107">Soubor, který obsahuje klíč.</span><span class="sxs-lookup"><span data-stu-id="c4d46-107">File that contains the key.</span></span> <span data-ttu-id="c4d46-108">Pokud název souboru obsahuje mezeru, uzavřete jej do uvozovek (" ").</span><span class="sxs-lookup"><span data-stu-id="c4d46-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4d46-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4d46-109">Remarks</span></span>  
 <span data-ttu-id="c4d46-110">Kompilátor vloží veřejný klíč do manifestu sestavení a podepíše konečné sestavení pomocí soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="c4d46-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="c4d46-111">Chcete-li vygenerovat `sn -k file` soubor klíče, zadejte příkaz na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="c4d46-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="c4d46-112">Další informace naleznete v [tématu Sn.exe (Strong Name Tool).](../../../framework/tools/sn-exe-strong-name-tool.md)</span><span class="sxs-lookup"><span data-stu-id="c4d46-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="c4d46-113">Pokud kompilujete s `-target:module`, název souboru klíče je držen v modulu a začleněny do sestavení, který je vytvořen při kompilaci sestavení s [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="c4d46-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="c4d46-114">Můžete také předat informace o šifrování kompilátoru s [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="c4d46-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="c4d46-115">Použijte [-delaysign,](../../../visual-basic/reference/command-line-compiler/delaysign.md) pokud chcete částečně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4d46-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="c4d46-116">Tuto možnost můžete také zadat jako<xref:System.Reflection.AssemblyKeyFileAttribute>vlastní atribut ( ) ve zdrojovém kódu pro libovolný modul zprostředkujících jazyků společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c4d46-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="c4d46-117">V případě, že oba `-keyfile` a [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) jsou určeny (buď příkazového řádku možnost nebo vlastní atribut) ve stejné kompilaci, kompilátor nejprve pokusí kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="c4d46-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="c4d46-118">Pokud se to podaří, sestavení je podepsáno informacemi v kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="c4d46-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="c4d46-119">Pokud kompilátor nenajde kontejner klíčů, pokusí se `-keyfile`o soubor zadaný .</span><span class="sxs-lookup"><span data-stu-id="c4d46-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="c4d46-120">Pokud se to podaří, sestavení je podepsáno s informacemi v souboru klíče a `sn -i`informace o klíči jsou nainstalovány v kontejneru klíčů (podobně jako ) tak, aby v další kompilaci byl kontejner klíčů platný.</span><span class="sxs-lookup"><span data-stu-id="c4d46-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="c4d46-121">Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="c4d46-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="c4d46-122">Další informace o podepisování sestavení najdete v tématu [Vytváření a používání sestavení se silným názvem.](../../../standard/assembly/create-use-strong-named.md)</span><span class="sxs-lookup"><span data-stu-id="c4d46-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4d46-123">Tato `-keyfile` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c4d46-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="c4d46-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4d46-124">Example</span></span>

<span data-ttu-id="c4d46-125">Následující kód zkompiluje zdrojový soubor `Input.vb` a určuje soubor klíče.</span><span class="sxs-lookup"><span data-stu-id="c4d46-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="c4d46-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4d46-126">See also</span></span>

- [<span data-ttu-id="c4d46-127">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="c4d46-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="c4d46-128">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4d46-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c4d46-129">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4d46-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="c4d46-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="c4d46-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
