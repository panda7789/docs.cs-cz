---
title: "-highentropyva (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5746caed8c1bf61038c97a49987c4c168eef9f3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="highentropyva-c-compiler-options"></a><span data-ttu-id="d2c60-102">/highentropyva (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="d2c60-102">/highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="d2c60-103">**/Highentropyva** – možnost kompilátoru informuje jádro systému Windows, jestli konkrétní spustitelný soubor podporuje vysokou entropie místo rozložení náhodného přeskupování (technologie ASLR) adres.</span><span class="sxs-lookup"><span data-stu-id="d2c60-103">The **/highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2c60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2c60-104">Syntax</span></span>  
  
```console  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d2c60-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d2c60-105">Arguments</span></span>  
 <span data-ttu-id="d2c60-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d2c60-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d2c60-107">Tato možnost určuje, že spustitelný soubor 64-bit nebo jenom spustitelný soubor, která je označena kvalifikátorem [/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) – možnost kompilátoru podporuje virtuální adresní prostor vysoké šifrování.</span><span class="sxs-lookup"><span data-stu-id="d2c60-107">This option specifies that a 64-bit executable or an executable that is marked by the [/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="d2c60-108">Tato možnost je ve výchozím nastavení vypnuta.</span><span class="sxs-lookup"><span data-stu-id="d2c60-108">The option is disabled by default.</span></span> <span data-ttu-id="d2c60-109">Použití **/highentropyva+** nebo **/highentropyva** povolit.</span><span class="sxs-lookup"><span data-stu-id="d2c60-109">Use **/highentropyva+** or **/highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2c60-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2c60-110">Remarks</span></span>  
 <span data-ttu-id="d2c60-111">**/Highentropyva** možnost umožňuje kompatibilní verze používat vyšší stupňů entropii v rámci procesu náhodného řazení rozložení prostoru adres procesu v rámci technologie ASLR jádro systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d2c60-111">The **/highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="d2c60-112">Použití vyšší stupňů šifrování znamená, že větší počet adres může být přidělen k oblasti paměti, jako je například zásobníky a hald.</span><span class="sxs-lookup"><span data-stu-id="d2c60-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="d2c60-113">V důsledku toho je obtížnější uhádnout umístění paměti konkrétní oblasti.</span><span class="sxs-lookup"><span data-stu-id="d2c60-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="d2c60-114">Když **/highentropyva** – možnost kompilátoru je zadán, cílový spustitelný soubor a všechny moduly, které závisí na musí být schopna zpracovávat ukazatel hodnoty, které jsou větší než 4 gigabajty (GB), když používají jako 64bitový proces.</span><span class="sxs-lookup"><span data-stu-id="d2c60-114">When the **/highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
