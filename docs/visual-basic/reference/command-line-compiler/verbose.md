---
title: -verbose
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0523409e53a8c7ea34de7dcc24b1bce2885a183
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-verbose"></a><span data-ttu-id="ae41d-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="ae41d-102">-verbose</span></span>
<span data-ttu-id="ae41d-103">Způsobí, že kompilátoru vytvoření podrobné zprávy o stavu a chyb.</span><span class="sxs-lookup"><span data-stu-id="ae41d-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae41d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae41d-104">Syntax</span></span>  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae41d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ae41d-105">Arguments</span></span>  
 <span data-ttu-id="ae41d-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ae41d-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="ae41d-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ae41d-107">Optional.</span></span> <span data-ttu-id="ae41d-108">Určení `-verbose` je stejné jako zadání `-verbose+`, což způsobí, že kompilátoru pro generování podrobné zprávy.</span><span class="sxs-lookup"><span data-stu-id="ae41d-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="ae41d-109">Výchozí hodnota pro tuto možnost je `-verbose-`.</span><span class="sxs-lookup"><span data-stu-id="ae41d-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae41d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae41d-110">Remarks</span></span>  
 <span data-ttu-id="ae41d-111">`-verbose` Možnost zobrazí informace o celkový počet chyb vystavený kompilátor, sestavy, které sestavení jsou načítány pomocí modulu a soubory, které jsou nyní kompilována.</span><span class="sxs-lookup"><span data-stu-id="ae41d-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae41d-112">`-verbose` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ae41d-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae41d-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae41d-113">Example</span></span>  
 <span data-ttu-id="ae41d-114">Následující kód zkompiluje `In.vb` a přesměruje kompilátoru zobrazíte podrobné stavové informace.</span><span class="sxs-lookup"><span data-stu-id="ae41d-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae41d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae41d-115">See Also</span></span>  
 [<span data-ttu-id="ae41d-116">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="ae41d-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ae41d-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="ae41d-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
