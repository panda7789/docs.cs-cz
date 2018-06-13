---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fef3f922d3089eaca1762ffe35fa38cfe94baf22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656312"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="63536-102">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63536-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="63536-103">Určuje, zda spustitelný soubor 64-bit nebo jenom spustitelný soubor, která je označena kvalifikátorem [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) – možnost kompilátoru podporuje vysokou entropie místo rozložení náhodného přeskupování (technologie ASLR) adres.</span><span class="sxs-lookup"><span data-stu-id="63536-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63536-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63536-104">Syntax</span></span>  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="63536-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="63536-105">Arguments</span></span>  
 <span data-ttu-id="63536-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="63536-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="63536-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="63536-107">Optional.</span></span> <span data-ttu-id="63536-108">Možnost je vypnuta ve výchozím nastavení nebo pokud zadáte `-highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="63536-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="63536-109">Možnost zapnutý, pokud zadáte `-highentropyva` nebo `-highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="63536-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63536-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63536-110">Remarks</span></span>  
 <span data-ttu-id="63536-111">Pokud zadáte tuto možnost, můžete kompatibilní verze jádro systému Windows použít vyšší stupňů entropie při jádra randomizes rozložení prostoru adres procesu v rámci technologie ASLR.</span><span class="sxs-lookup"><span data-stu-id="63536-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="63536-112">Pokud jádra používá vyšší stupňů entropie, oblasti paměti, jako je například zásobníky a haldách můžete přidělit větší počet adres.</span><span class="sxs-lookup"><span data-stu-id="63536-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="63536-113">V důsledku toho je obtížnější uhádnout umístění paměti konkrétní oblasti.</span><span class="sxs-lookup"><span data-stu-id="63536-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="63536-114">Pokud možnost je na cílový spustitelný soubor a všechny moduly, na které závisí musí být schopen zpracování ukazatele hodnot, které jsou větší než 4 gigabajty (GB), pokud se tyto moduly se spustí jako 64bitové procesy.</span><span class="sxs-lookup"><span data-stu-id="63536-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63536-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="63536-115">See Also</span></span>  
 [<span data-ttu-id="63536-116">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="63536-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="63536-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="63536-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
