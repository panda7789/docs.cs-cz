---
title: -HIGHENTROPYVA (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: b710bb829f6a7591159d2f2e6bacc670d21c42d1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606855"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="a2f53-102">-HIGHENTROPYVA (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="a2f53-102">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="a2f53-103">Možnost kompilátoru **-HIGHENTROPYVA** přikáže jádru systému Windows, zda určitý spustitelný soubor podporuje náhodné vygenerování rozložení adresního prostoru (ASLR) vysoké entropie.</span><span class="sxs-lookup"><span data-stu-id="a2f53-103">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2f53-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a2f53-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a2f53-105">Arguments</span></span>  
 <span data-ttu-id="a2f53-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a2f53-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a2f53-107">Tato možnost určuje, že 64 spustitelný soubor nebo spustitelný soubor, který je označený pomocí možnosti kompilátoru [-Platform: anycpu](./platform-compiler-option.md) , podporuje virtuální adresní prostor s vysokou entropií.</span><span class="sxs-lookup"><span data-stu-id="a2f53-107">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="a2f53-108">Možnost je ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="a2f53-108">The option is disabled by default.</span></span> <span data-ttu-id="a2f53-109">K povolení použijte **-HIGHENTROPYVA +** nebo **-HIGHENTROPYVA** .</span><span class="sxs-lookup"><span data-stu-id="a2f53-109">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2f53-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2f53-110">Remarks</span></span>  
 <span data-ttu-id="a2f53-111">Možnost **-HIGHENTROPYVA** umožňuje kompatibilní verze jádra Windows pro použití vyšších stupňů entropie při náhodném rozložení adresního prostoru procesu jako součást ASLR.</span><span class="sxs-lookup"><span data-stu-id="a2f53-111">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="a2f53-112">Použití vyšších stupňů entropie znamená, že větší počet adres může být přidělen do oblastí paměti, jako jsou zásobníky a haldy.</span><span class="sxs-lookup"><span data-stu-id="a2f53-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="a2f53-113">V důsledku toho je obtížné odhadnout umístění konkrétní oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="a2f53-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="a2f53-114">Je-li zadána možnost kompilátoru **-HIGHENTROPYVA** , musí být cílový spustitelný soubor a všechny moduly, na kterých závisí, schopny zpracovat hodnoty ukazatele, které jsou větší než 4 gigabajty (GB), pokud jsou spuštěny jako 64 proces.</span><span class="sxs-lookup"><span data-stu-id="a2f53-114">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
