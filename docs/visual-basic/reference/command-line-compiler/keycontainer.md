---
title: /keycontainer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f7c5ffa255ba9ac2f062ea52eb3471659e0192b
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="keycontainer"></a><span data-ttu-id="5202f-102">/keycontainer</span><span class="sxs-lookup"><span data-stu-id="5202f-102">/keycontainer</span></span>
<span data-ttu-id="5202f-103">Určuje název kontejneru klíčů pro pár klíčů umožnit sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="5202f-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5202f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5202f-104">Syntax</span></span>  
  
```  
/keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="5202f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5202f-105">Arguments</span></span>  
  
|<span data-ttu-id="5202f-106">Termín</span><span class="sxs-lookup"><span data-stu-id="5202f-106">Term</span></span>|<span data-ttu-id="5202f-107">Definice</span><span class="sxs-lookup"><span data-stu-id="5202f-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="5202f-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="5202f-108">Required.</span></span> <span data-ttu-id="5202f-109">Soubor kontejneru, který obsahuje klíč.</span><span class="sxs-lookup"><span data-stu-id="5202f-109">Container file that contains the key.</span></span> <span data-ttu-id="5202f-110">Uzavřete název souboru v uvozovkách ("") Pokud název obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="5202f-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5202f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5202f-111">Remarks</span></span>  
 <span data-ttu-id="5202f-112">Kompilátor vytvoří komponentu lze sdílet vložením veřejný klíč do manifestu a podepíše konečné sestavení s privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="5202f-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="5202f-113">Chcete-li vygenerovat soubor klíče, zadejte `sn -k``file` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="5202f-113">To generate a key file, type `sn -k``file` at the command line.</span></span> <span data-ttu-id="5202f-114">`-i` Možnost nainstaluje pár klíčů do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5202f-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="5202f-115">Další informace najdete v tématu [Sn.exe (nástroj silným názvem)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="5202f-115">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
 <span data-ttu-id="5202f-116">Pokud je kompilovat s `/target:module`, název souboru klíče je udržován v modulu a součástí sestavení, které se vytvoří při kompilaci sestavení s [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="5202f-116">If you compile with `/target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="5202f-117">Tuto možnost můžete také určit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyNameAttribute>) ve zdrojovém kódu pro libovolný modul (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5202f-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="5202f-118">Vaše informace šifrování můžete předat také kompilátoru s [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span><span class="sxs-lookup"><span data-stu-id="5202f-118">You can also pass your encryption information to the compiler with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span></span> <span data-ttu-id="5202f-119">Použití [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) Pokud chcete, aby částečně podepsané sestavení.</span><span class="sxs-lookup"><span data-stu-id="5202f-119">Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="5202f-120">V tématu [vytvoření a použití sestavení](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.</span><span class="sxs-lookup"><span data-stu-id="5202f-120">See [Creating and Using Strong-Named Assemblies](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5202f-121">`/keycontainer` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5202f-121">The `/keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5202f-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="5202f-122">Example</span></span>  
 <span data-ttu-id="5202f-123">Následující kód zkompiluje zdrojový soubor `Input.vb` a určuje kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="5202f-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5202f-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5202f-124">See Also</span></span>  
 [<span data-ttu-id="5202f-125">Sestavení a globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="5202f-125">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="5202f-126">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="5202f-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5202f-127">/ keyfile</span><span class="sxs-lookup"><span data-stu-id="5202f-127">/keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="5202f-128">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="5202f-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
