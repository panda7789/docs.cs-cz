---
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 9501ea46eb13baa171208e20d0c9645d118c4301
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408618"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="9b575-102">-HIGHENTROPYVA (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b575-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="9b575-103">Označuje, jestli 64 spustitelný soubor nebo spustitelný soubor, který je označený parametrem [-Platform: anycpu](platform.md) , podporuje funkci náhodnosti rozložení adresního prostoru s vysokou entropií (ASLR).</span><span class="sxs-lookup"><span data-stu-id="9b575-103">Indicates whether a 64-bit executable or an executable that's marked by the [-platform:anycpu](platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b575-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b575-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9b575-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9b575-105">Arguments</span></span>  
 <span data-ttu-id="9b575-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="9b575-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="9b575-107">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9b575-107">Optional.</span></span> <span data-ttu-id="9b575-108">Možnost je ve výchozím nastavení vypnutá nebo pokud zadáte `-highentropyva-` .</span><span class="sxs-lookup"><span data-stu-id="9b575-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="9b575-109">Možnost je zapnutá, pokud zadáte `-highentropyva` nebo `-highentropyva+` .</span><span class="sxs-lookup"><span data-stu-id="9b575-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b575-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b575-110">Remarks</span></span>  
 <span data-ttu-id="9b575-111">Zadáte-li tuto možnost, kompatibilní verze jádra systému Windows mohou používat vyšší stupně entropie v případě, že jádro v rámci procesu ASLR náhodné rozložení adresního prostoru.</span><span class="sxs-lookup"><span data-stu-id="9b575-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="9b575-112">Pokud jádro používá vyšší stupně entropie, je možné přidělit větší počet adres do oblastí paměti, jako jsou zásobníky a haldy.</span><span class="sxs-lookup"><span data-stu-id="9b575-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="9b575-113">V důsledku toho je obtížné odhadnout umístění konkrétní oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="9b575-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="9b575-114">Když je tato možnost zapnutá, cílový spustitelný soubor a všechny moduly, na kterých závisí, musí být schopné zpracovat hodnoty ukazatele, které jsou větší než 4 gigabajty (GB), když tyto moduly běží jako 64 procesy.</span><span class="sxs-lookup"><span data-stu-id="9b575-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b575-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b575-115">See also</span></span>

- [<span data-ttu-id="9b575-116">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="9b575-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="9b575-117">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="9b575-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
