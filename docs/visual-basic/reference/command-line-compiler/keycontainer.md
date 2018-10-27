---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: f64e47922aea35ac9ddf51428107af0d4002d33e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185820"
---
# <a name="-keycontainer"></a><span data-ttu-id="8afcb-102">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="8afcb-102">-keycontainer</span></span>
<span data-ttu-id="8afcb-103">Určuje název kontejneru klíčů pro dvojice klíčů poskytnout sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="8afcb-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8afcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8afcb-104">Syntax</span></span>  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="8afcb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8afcb-105">Arguments</span></span>  
  
|<span data-ttu-id="8afcb-106">Termín</span><span class="sxs-lookup"><span data-stu-id="8afcb-106">Term</span></span>|<span data-ttu-id="8afcb-107">Definice</span><span class="sxs-lookup"><span data-stu-id="8afcb-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="8afcb-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8afcb-108">Required.</span></span> <span data-ttu-id="8afcb-109">Soubor kontejneru, který obsahuje klíč.</span><span class="sxs-lookup"><span data-stu-id="8afcb-109">Container file that contains the key.</span></span> <span data-ttu-id="8afcb-110">Název souboru uzavřete do uvozovek ("") Pokud název obsahuje mezery.</span><span class="sxs-lookup"><span data-stu-id="8afcb-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8afcb-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8afcb-111">Remarks</span></span>  
 <span data-ttu-id="8afcb-112">Kompilátor vytvoří komponentu sdílet tak, že vloží veřejný klíč do manifestu sestavení a podepíše konečné sestavení soukromým klíčem.</span><span class="sxs-lookup"><span data-stu-id="8afcb-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="8afcb-113">Chcete-li generovat soubor s klíčem, zadejte `sn -k file` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="8afcb-113">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="8afcb-114">`-i` Možnost nainstaluje pár klíčů do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8afcb-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="8afcb-115">Další informace najdete v tématu [Sn.exe (nástroj Strong Name)][Sn.exe (nástroj Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="8afcb-115">For more information, see [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="8afcb-116">Pokud kompilujete s `-target:module`, je název souboru klíče uložené v modulu a součástí sestavení, které se vytvoří, když kompilujete sestavení s [- addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="8afcb-116">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="8afcb-117">Tuto možnost lze také nastavit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyNameAttribute>) ve zdrojovém kódu pro jakýkoli modul Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="8afcb-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="8afcb-118">Můžete také předat údaje o šifrování pro kompilátor [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span><span class="sxs-lookup"><span data-stu-id="8afcb-118">You can also pass your encryption information to the compiler with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span></span> <span data-ttu-id="8afcb-119">Použití [- delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) potřebujete částečně podepsaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="8afcb-119">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="8afcb-120">Zobrazit [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="8afcb-120">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8afcb-121">`-keycontainer` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="8afcb-121">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8afcb-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="8afcb-122">Example</span></span>  
 <span data-ttu-id="8afcb-123">Následující kód se zkompiluje zdrojový soubor `Input.vb` a Určuje kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="8afcb-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8afcb-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="8afcb-124">See Also</span></span>  
 [<span data-ttu-id="8afcb-125">Sestavení a globální mezipaměť sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="8afcb-125">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="8afcb-126">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8afcb-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="8afcb-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="8afcb-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="8afcb-128">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="8afcb-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
