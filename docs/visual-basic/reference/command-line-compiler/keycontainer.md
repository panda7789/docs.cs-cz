---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: 575b337c262fbb36a9e118aa293916c296cc2db3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408559"
---
# <a name="-keycontainer"></a><span data-ttu-id="6ab6b-102">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="6ab6b-102">-keycontainer</span></span>
<span data-ttu-id="6ab6b-103">Určuje název kontejneru klíče pro dvojici klíčů, který poskytne sestavení silného názvu.</span><span class="sxs-lookup"><span data-stu-id="6ab6b-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ab6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ab6b-104">Syntax</span></span>  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ab6b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6ab6b-105">Arguments</span></span>  
  
|<span data-ttu-id="6ab6b-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="6ab6b-106">Term</span></span>|<span data-ttu-id="6ab6b-107">Definice</span><span class="sxs-lookup"><span data-stu-id="6ab6b-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="6ab6b-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="6ab6b-108">Required.</span></span> <span data-ttu-id="6ab6b-109">Soubor kontejneru, který obsahuje klíč.</span><span class="sxs-lookup"><span data-stu-id="6ab6b-109">Container file that contains the key.</span></span> <span data-ttu-id="6ab6b-110">Uzavřete název souboru do uvozovek (""), pokud název obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="6ab6b-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ab6b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ab6b-111">Remarks</span></span>  
 <span data-ttu-id="6ab6b-112">Kompilátor vytvoří součást, kterou může sdílet, vložením veřejného klíče do manifestu sestavení a podepsáním konečného sestavení pomocí privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="6ab6b-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="6ab6b-113">Chcete-li vygenerovat soubor klíče, zadejte do `sn -k file` příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6ab6b-113">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="6ab6b-114">`-i`Možnost nainstaluje dvojici klíčů do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6ab6b-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="6ab6b-115">Další informace naleznete v tématu [sn. exe (Nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="6ab6b-115">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="6ab6b-116">Pokud kompilujete s `-target:module` , název souboru klíče je uložen v modulu a začleněn do sestavení, které je vytvořeno při kompilaci sestavení pomocí [-addmodule –](addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="6ab6b-116">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="6ab6b-117">Tuto možnost lze také zadat jako vlastní atribut ( <xref:System.Reflection.AssemblyKeyNameAttribute> ) ve zdrojovém kódu pro libovolný modul jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="6ab6b-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="6ab6b-118">Můžete také předat informace o šifrování kompilátoru s parametrem [-keyfile](keyfile.md).</span><span class="sxs-lookup"><span data-stu-id="6ab6b-118">You can also pass your encryption information to the compiler with [-keyfile](keyfile.md).</span></span> <span data-ttu-id="6ab6b-119">Použijte [-delaysign](delaysign.md) , pokud chcete použít částečně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="6ab6b-119">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="6ab6b-120">Další informace o podepsání sestavení naleznete v tématu [vytváření a používání sestavení se silným názvem](../../../standard/assembly/create-use-strong-named.md) .</span><span class="sxs-lookup"><span data-stu-id="6ab6b-120">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ab6b-121">Tato `-keycontainer` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6ab6b-121">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ab6b-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ab6b-122">Example</span></span>  
 <span data-ttu-id="6ab6b-123">Následující kód zkompiluje zdrojový soubor `Input.vb` a určí kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="6ab6b-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ab6b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ab6b-124">See also</span></span>

- [<span data-ttu-id="6ab6b-125">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="6ab6b-125">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="6ab6b-126">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="6ab6b-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="6ab6b-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="6ab6b-127">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="6ab6b-128">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="6ab6b-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
