---
title: /utf8output (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 23c7c308865a6b6afb07443a42090fff3d9e2efb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="utf8output-visual-basic"></a><span data-ttu-id="a70c5-102">/utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a70c5-102">/utf8output (Visual Basic)</span></span>
<span data-ttu-id="a70c5-103">Zobrazí výstup kompilátoru pomocí kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a70c5-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a70c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a70c5-104">Syntax</span></span>  
  
```  
/utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a70c5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a70c5-105">Arguments</span></span>  
 <span data-ttu-id="a70c5-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a70c5-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a70c5-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a70c5-107">Optional.</span></span> <span data-ttu-id="a70c5-108">Výchozí hodnota pro tuto možnost je `/utf8output-`, což znamená, že výstup kompilátoru nepoužívá kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a70c5-108">The default for this option is `/utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="a70c5-109">Určení `/utf8output` je stejné jako zadání `/utf8output+`.</span><span class="sxs-lookup"><span data-stu-id="a70c5-109">Specifying `/utf8output` is the same as specifying `/utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a70c5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a70c5-110">Remarks</span></span>  
 <span data-ttu-id="a70c5-111">V některých konfiguracích mezinárodní výstupu kompilátoru nelze správně v konzole.</span><span class="sxs-lookup"><span data-stu-id="a70c5-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="a70c5-112">V takových situacích použít `/utf8output` a přesměrujte výstup kompilátoru do souboru.</span><span class="sxs-lookup"><span data-stu-id="a70c5-112">In such situations, use `/utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a70c5-113">`/utf8output` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a70c5-113">The `/utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a70c5-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a70c5-114">Example</span></span>  
 <span data-ttu-id="a70c5-115">Následující kód zkompiluje `In.vb` a přesměruje kompilátoru k zobrazení výstupu pomocí kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="a70c5-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```  
vbc /utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a70c5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a70c5-116">See Also</span></span>  
 [<span data-ttu-id="a70c5-117">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a70c5-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a70c5-118">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="a70c5-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
