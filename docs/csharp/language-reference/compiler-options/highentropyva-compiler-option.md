---
title: -highentropyva (C# Compiler Options)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: 2ff63ddc48a4f5c4287fe1badb092a1db93f68dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662852"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="66c37-102">-highentropyva (C# Compiler Options)</span><span class="sxs-lookup"><span data-stu-id="66c37-102">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="66c37-103">**- Highentropyva** – možnost kompilátoru říká jádra Windows, jestli konkrétní spustitelný soubor podporuje vysokou entropie adresu místo rozložení náhodné (ASLR).</span><span class="sxs-lookup"><span data-stu-id="66c37-103">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66c37-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="66c37-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="66c37-105">Arguments</span></span>  
 <span data-ttu-id="66c37-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="66c37-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="66c37-107">Tato možnost určuje, že spustitelný soubor 64-bit nebo spustitelný soubor, který je označen [-platform: anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) – možnost kompilátoru podporuje vysokou entropie virtuálního adresového prostoru.</span><span class="sxs-lookup"><span data-stu-id="66c37-107">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="66c37-108">Možnost je ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="66c37-108">The option is disabled by default.</span></span> <span data-ttu-id="66c37-109">Použití **- highentropyva +** nebo **- highentropyva** ho chcete povolit.</span><span class="sxs-lookup"><span data-stu-id="66c37-109">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66c37-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66c37-110">Remarks</span></span>  
 <span data-ttu-id="66c37-111">**- Highentropyva** možnost povolí kompatibilní verze jádra Windows používat vyšší stupeň entropie v rámci procesu náhodného řazení rozložení prostoru adres procesu jako součást technologie ASLR.</span><span class="sxs-lookup"><span data-stu-id="66c37-111">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="66c37-112">Použitím vyšší stupeň entropie znamená, že větší počet adres je možné přidělit paměti oblastech, jako je zásobníky a haldy.</span><span class="sxs-lookup"><span data-stu-id="66c37-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="66c37-113">V důsledku toho je obtížnější uhádnout umístění konkrétní paměťové oblasti.</span><span class="sxs-lookup"><span data-stu-id="66c37-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="66c37-114">Když **- highentropyva** – možnost kompilátoru je zadán, cílový spustitelný soubor a všechny moduly, které závisí na musí být schopna zpracovávat hodnoty ukazatele, které jsou větší než 4 gigabajty (GB) spuštěná jako 64bitový proces.</span><span class="sxs-lookup"><span data-stu-id="66c37-114">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
