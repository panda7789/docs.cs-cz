---
title: /verbose
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5480f828fa1f0b6d71fa649bf44513ce806bb440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="verbose"></a><span data-ttu-id="2c77e-102">/verbose</span><span class="sxs-lookup"><span data-stu-id="2c77e-102">/verbose</span></span>
<span data-ttu-id="2c77e-103">Způsobí, že kompilátoru vytvoření podrobné zprávy o stavu a chyb.</span><span class="sxs-lookup"><span data-stu-id="2c77e-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c77e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c77e-104">Syntax</span></span>  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2c77e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2c77e-105">Arguments</span></span>  
 <span data-ttu-id="2c77e-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="2c77e-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="2c77e-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2c77e-107">Optional.</span></span> <span data-ttu-id="2c77e-108">Určení `/verbose` je stejné jako zadání `/verbose+`, což způsobí, že kompilátoru pro generování podrobné zprávy.</span><span class="sxs-lookup"><span data-stu-id="2c77e-108">Specifying `/verbose` is the same as specifying `/verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="2c77e-109">Výchozí hodnota pro tuto možnost je `/verbose-`.</span><span class="sxs-lookup"><span data-stu-id="2c77e-109">The default for this option is `/verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c77e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c77e-110">Remarks</span></span>  
 <span data-ttu-id="2c77e-111">`/verbose` Možnost zobrazí informace o celkový počet chyb vystavený kompilátor, sestavy, které sestavení jsou načítány pomocí modulu a soubory, které jsou nyní kompilována.</span><span class="sxs-lookup"><span data-stu-id="2c77e-111">The `/verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c77e-112">`/verbose` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2c77e-112">The `/verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c77e-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c77e-113">Example</span></span>  
 <span data-ttu-id="2c77e-114">Následující kód zkompiluje `In.vb` a přesměruje kompilátoru zobrazíte podrobné stavové informace.</span><span class="sxs-lookup"><span data-stu-id="2c77e-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c77e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c77e-115">See Also</span></span>  
 [<span data-ttu-id="2c77e-116">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2c77e-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="2c77e-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="2c77e-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
