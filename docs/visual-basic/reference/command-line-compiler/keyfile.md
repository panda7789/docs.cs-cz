---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 84b291a28cd4e253f44063258894aa672904d15b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581995"
---
# <a name="-keyfile"></a><span data-ttu-id="24246-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="24246-102">-keyfile</span></span>

<span data-ttu-id="24246-103">Určuje soubor obsahující klíč nebo dvojici klíčů, které sestavení poskytují silný název.</span><span class="sxs-lookup"><span data-stu-id="24246-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>

## <a name="syntax"></a><span data-ttu-id="24246-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24246-104">Syntax</span></span>

```console
-keyfile:file
```

## <a name="arguments"></a><span data-ttu-id="24246-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="24246-105">Arguments</span></span>

`file`  
<span data-ttu-id="24246-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="24246-106">Required.</span></span> <span data-ttu-id="24246-107">Soubor, který obsahuje klíč.</span><span class="sxs-lookup"><span data-stu-id="24246-107">File that contains the key.</span></span> <span data-ttu-id="24246-108">Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="24246-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="24246-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24246-109">Remarks</span></span>

<span data-ttu-id="24246-110">Kompilátor vloží veřejný klíč do manifestu sestavení a pak podepíše konečné sestavení pomocí privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="24246-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="24246-111">Chcete-li vygenerovat soubor klíče, zadejte `sn -k file` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="24246-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="24246-112">Další informace naleznete v tématu [sn. exe (Nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="24246-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>

<span data-ttu-id="24246-113">Pokud kompilujete s `-target:module`, název souboru klíče je uložen v modulu a začleněn do sestavení, které je vytvořeno při kompilování sestavení pomocí [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="24246-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>

<span data-ttu-id="24246-114">Můžete také předat informace o šifrování kompilátoru s modulem, který [obsahuje](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="24246-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="24246-115">Použijte [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) , pokud chcete použít částečně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="24246-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>

<span data-ttu-id="24246-116">Tuto možnost můžete také zadat jako vlastní atribut (<xref:System.Reflection.AssemblyKeyFileAttribute>) ve zdrojovém kódu pro libovolný modul Microsoft Intermediate Language.</span><span class="sxs-lookup"><span data-stu-id="24246-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>

<span data-ttu-id="24246-117">V případě, že jsou zadány oba `-keyfile` a [-](../../../visual-basic/reference/command-line-compiler/keycontainer.md) klíčové pole (buď parametr příkazového řádku nebo vlastní atribut) ve stejné kompilaci, kompilátor nejprve pokusí kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="24246-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="24246-118">Pokud je tato operace úspěšná, sestavení je podepsáno informacemi z kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="24246-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="24246-119">Pokud kompilátor nenalezne kontejner klíčů, pokusí se soubor zadaný pomocí `-keyfile`.</span><span class="sxs-lookup"><span data-stu-id="24246-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="24246-120">Pokud je to úspěšné, sestavení je podepsáno informacemi v souboru klíče a informace o klíči jsou nainstalovány v kontejneru klíčů (podobně jako `sn -i`), takže při další kompilaci bude kontejner klíčů platný.</span><span class="sxs-lookup"><span data-stu-id="24246-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>

<span data-ttu-id="24246-121">Všimněte si, že soubor klíče může obsahovat pouze veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="24246-121">Note that a key file might contain only the public key.</span></span>

<span data-ttu-id="24246-122">Další informace o podepsání sestavení naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) .</span><span class="sxs-lookup"><span data-stu-id="24246-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="24246-123">Možnost `-keyfile` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="24246-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="24246-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="24246-124">Example</span></span>

<span data-ttu-id="24246-125">Následující kód zkompiluje zdrojový soubor `Input.vb` a určí soubor klíče.</span><span class="sxs-lookup"><span data-stu-id="24246-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="24246-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24246-126">See also</span></span>

- [<span data-ttu-id="24246-127">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="24246-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="24246-128">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="24246-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="24246-129">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24246-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="24246-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="24246-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
