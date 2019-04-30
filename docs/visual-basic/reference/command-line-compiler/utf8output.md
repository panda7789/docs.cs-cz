---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 75369c3bcb19afbf98bfb80bc3e439f996d2a9d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796075"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="7bb41-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bb41-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="7bb41-103">Zobrazí výstup kompilátoru pomocí kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7bb41-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bb41-104">Syntax</span></span>  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7bb41-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7bb41-105">Arguments</span></span>  
 <span data-ttu-id="7bb41-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="7bb41-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="7bb41-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="7bb41-107">Optional.</span></span> <span data-ttu-id="7bb41-108">Výchozí hodnota pro tuto možnost je `-utf8output-`, což znamená, že výstup kompilátoru nepoužívá kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7bb41-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="7bb41-109">Určení `-utf8output` je stejné jako zadání `-utf8output+`.</span><span class="sxs-lookup"><span data-stu-id="7bb41-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bb41-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7bb41-110">Remarks</span></span>  
 <span data-ttu-id="7bb41-111">V některých konfiguracích mezinárodní není výstup kompilátoru správně zobrazovat v konzole.</span><span class="sxs-lookup"><span data-stu-id="7bb41-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="7bb41-112">V takových situacích použít `-utf8output` a přesměrovat výstup kompilátoru do souboru.</span><span class="sxs-lookup"><span data-stu-id="7bb41-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bb41-113">`-utf8output` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7bb41-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bb41-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7bb41-114">Example</span></span>  
 <span data-ttu-id="7bb41-115">Následující kód zkompiluje `In.vb` a instruuje kompilátor, aby zobrazení výstupu pomocí kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7bb41-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7bb41-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7bb41-116">See also</span></span>

- [<span data-ttu-id="7bb41-117">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="7bb41-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7bb41-118">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="7bb41-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
