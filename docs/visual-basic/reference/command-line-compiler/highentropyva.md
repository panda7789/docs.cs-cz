---
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 7934dcaada4675bf687624bef5ed1ea25e842832
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344243"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="d8bee-102">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8bee-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="d8bee-103">Indicates whether a 64-bit executable or an executable that's marked by the [-platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span><span class="sxs-lookup"><span data-stu-id="d8bee-103">Indicates whether a 64-bit executable or an executable that's marked by the [-platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8bee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8bee-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d8bee-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d8bee-105">Arguments</span></span>  
 <span data-ttu-id="d8bee-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d8bee-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d8bee-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d8bee-107">Optional.</span></span> <span data-ttu-id="d8bee-108">The option is off by default or if you specify `-highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="d8bee-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="d8bee-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="d8bee-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8bee-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8bee-110">Remarks</span></span>  
 <span data-ttu-id="d8bee-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span><span class="sxs-lookup"><span data-stu-id="d8bee-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="d8bee-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span><span class="sxs-lookup"><span data-stu-id="d8bee-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="d8bee-113">As a result, it is more difficult to guess the location of a particular memory region.</span><span class="sxs-lookup"><span data-stu-id="d8bee-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="d8bee-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span><span class="sxs-lookup"><span data-stu-id="d8bee-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8bee-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8bee-115">See also</span></span>

- [<span data-ttu-id="d8bee-116">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="d8bee-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d8bee-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="d8bee-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
