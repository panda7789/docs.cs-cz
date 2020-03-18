---
title: -highentropyva (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: b710bb829f6a7591159d2f2e6bacc670d21c42d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606855"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="1c00e-102">-highentropyva (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="1c00e-102">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="1c00e-103">Možnost kompilátoru **-highentropyva** informuje jádro systému Windows, zda určitý spustitelný soubor podporuje randomizaci rozložení adresního prostoru vysoké entropie (ASLR).</span><span class="sxs-lookup"><span data-stu-id="1c00e-103">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c00e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c00e-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1c00e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1c00e-105">Arguments</span></span>  
 <span data-ttu-id="1c00e-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="1c00e-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="1c00e-107">Tato možnost určuje, že 64bitový spustitelný soubor nebo spustitelný soubor, který je označen možností kompilátoru [-platform:anycpu,](./platform-compiler-option.md) podporuje virtuální adresní prostor s vysokou entropie.</span><span class="sxs-lookup"><span data-stu-id="1c00e-107">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="1c00e-108">Tato možnost je ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="1c00e-108">The option is disabled by default.</span></span> <span data-ttu-id="1c00e-109">Použijte **-highentropyva+** nebo **-highentropyva,** abyste ji povolili.</span><span class="sxs-lookup"><span data-stu-id="1c00e-109">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c00e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c00e-110">Remarks</span></span>  
 <span data-ttu-id="1c00e-111">Možnost **-highentropyva** umožňuje kompatibilním verzím jádra Systému Windows používat vyšší stupně entropie při randomizaci rozložení adresního prostoru procesu jako součásti ASLR.</span><span class="sxs-lookup"><span data-stu-id="1c00e-111">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="1c00e-112">Použití vyšších stupňů entropie znamená, že větší počet adres lze přidělit do oblastí paměti, jako jsou zásobníky a hromady.</span><span class="sxs-lookup"><span data-stu-id="1c00e-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="1c00e-113">V důsledku toho je obtížnější odhadnout umístění určité oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="1c00e-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="1c00e-114">Když je zadána možnost kompilátoru **-highentropyva,** cílový spustitelný soubor a všechny moduly, na kterých závisí, musí být schopny zpracovat hodnoty ukazatele, které jsou větší než 4 gigabajty (GB), pokud jsou spuštěny jako 64bitový proces.</span><span class="sxs-lookup"><span data-stu-id="1c00e-114">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
