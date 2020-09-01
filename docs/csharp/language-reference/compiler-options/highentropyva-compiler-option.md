---
description: -HIGHENTROPYVA (možnosti kompilátoru C#)
title: -HIGHENTROPYVA (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2c2e2780693a89072c4bb55b318be94089bf3ced
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125654"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="59de0-103">-HIGHENTROPYVA (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="59de0-103">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="59de0-104">Možnost kompilátoru **-HIGHENTROPYVA** přikáže jádru systému Windows, zda určitý spustitelný soubor podporuje náhodné vygenerování rozložení adresního prostoru (ASLR) vysoké entropie.</span><span class="sxs-lookup"><span data-stu-id="59de0-104">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59de0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59de0-105">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="59de0-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="59de0-106">Arguments</span></span>  
 <span data-ttu-id="59de0-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="59de0-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="59de0-108">Tato možnost určuje, že 64 spustitelný soubor nebo spustitelný soubor, který je označený pomocí možnosti kompilátoru [-Platform: anycpu](./platform-compiler-option.md) , podporuje virtuální adresní prostor s vysokou entropií.</span><span class="sxs-lookup"><span data-stu-id="59de0-108">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="59de0-109">Možnost je ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="59de0-109">The option is disabled by default.</span></span> <span data-ttu-id="59de0-110">K povolení použijte **-HIGHENTROPYVA +** nebo **-HIGHENTROPYVA** .</span><span class="sxs-lookup"><span data-stu-id="59de0-110">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59de0-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59de0-111">Remarks</span></span>  
 <span data-ttu-id="59de0-112">Možnost **-HIGHENTROPYVA** umožňuje kompatibilní verze jádra Windows pro použití vyšších stupňů entropie při náhodném rozložení adresního prostoru procesu jako součást ASLR.</span><span class="sxs-lookup"><span data-stu-id="59de0-112">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="59de0-113">Použití vyšších stupňů entropie znamená, že větší počet adres může být přidělen do oblastí paměti, jako jsou zásobníky a haldy.</span><span class="sxs-lookup"><span data-stu-id="59de0-113">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="59de0-114">V důsledku toho je obtížné odhadnout umístění konkrétní oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="59de0-114">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="59de0-115">Je-li zadána možnost kompilátoru **-HIGHENTROPYVA** , musí být cílový spustitelný soubor a všechny moduly, na kterých závisí, schopny zpracovat hodnoty ukazatele, které jsou větší než 4 gigabajty (GB), pokud jsou spuštěny jako 64 proces.</span><span class="sxs-lookup"><span data-stu-id="59de0-115">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
