---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 5d948817d4bc71aa31c5890f6740248f4c309588
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181498"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="d8416-102">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8416-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="d8416-103">Označuje, zda spustitelný soubor 64-bit nebo spustitelný soubor, který je označen [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) – možnost kompilátoru podporuje vysokou entropie adresu místo rozložení náhodné (ASLR).</span><span class="sxs-lookup"><span data-stu-id="d8416-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8416-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8416-104">Syntax</span></span>  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d8416-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d8416-105">Arguments</span></span>  
 <span data-ttu-id="d8416-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d8416-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d8416-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d8416-107">Optional.</span></span> <span data-ttu-id="d8416-108">Možnost je vypnuto ve výchozím nastavení nebo pokud zadáte `-highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="d8416-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="d8416-109">Možnost zapnutá, pokud zadáte `-highentropyva` nebo `-highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="d8416-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8416-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8416-110">Remarks</span></span>  
 <span data-ttu-id="d8416-111">Pokud zadáte tuto možnost, kompatibilní verze jádra Windows můžete použít vyšší stupeň entropie při jádra náhodně rozložení prostoru adres procesu určí jako součást technologie ASLR.</span><span class="sxs-lookup"><span data-stu-id="d8416-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="d8416-112">Pokud jádru používá vyšší stupeň entropie, větší počet adres je možné přidělit paměti oblastech, jako je zásobníky a haldy.</span><span class="sxs-lookup"><span data-stu-id="d8416-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="d8416-113">V důsledku toho je obtížnější uhádnout umístění konkrétní paměťové oblasti.</span><span class="sxs-lookup"><span data-stu-id="d8416-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="d8416-114">Při možnost je pro cílový spustitelný soubor a všechny moduly, na které závisí musí být schopná zpracovat hodnoty ukazatele, které jsou větší než 4 gigabajty (GB), pokud tyto moduly spuštěné jako 64bitové procesy.</span><span class="sxs-lookup"><span data-stu-id="d8416-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8416-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8416-115">See Also</span></span>  
 [<span data-ttu-id="d8416-116">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d8416-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d8416-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="d8416-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
