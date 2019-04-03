---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: 9a844515a4596064937762ac05b850463f1b5e14
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819174"
---
# <a name="-filealign"></a><span data-ttu-id="d5917-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="d5917-102">-filealign</span></span>
<span data-ttu-id="d5917-103">Určuje, kam chcete zarovnat oddíly výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="d5917-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5917-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5917-104">Syntax</span></span>  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="d5917-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d5917-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="d5917-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="d5917-106">Required.</span></span> <span data-ttu-id="d5917-107">Hodnota, která určuje zarovnání oddílů v souboru výstupu.</span><span class="sxs-lookup"><span data-stu-id="d5917-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="d5917-108">Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192.</span><span class="sxs-lookup"><span data-stu-id="d5917-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="d5917-109">Tyto hodnoty jsou v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d5917-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5917-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5917-110">Remarks</span></span>  
 <span data-ttu-id="d5917-111">Můžete použít `-filealign` možnost určení zarovnání oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="d5917-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="d5917-112">Oddíly jsou bloky souvislé paměti v souboru Portable Executable (PE), který obsahuje kód nebo data.</span><span class="sxs-lookup"><span data-stu-id="d5917-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="d5917-113">`-filealign` Možnost umožňuje zkompilovat aplikaci s nestandardní zarovnání; není potřeba tuto možnost použijte, Většina vývojářů.</span><span class="sxs-lookup"><span data-stu-id="d5917-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="d5917-114">Každý oddíl je zarovnáno na hranici, která je násobkem `-filealign` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d5917-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="d5917-115">Neexistuje žádná pevná výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="d5917-115">There is no fixed default.</span></span> <span data-ttu-id="d5917-116">Pokud `-filealign` není zadán, kompilátor zvolí výchozí v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="d5917-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="d5917-117">Tak, že určíte velikost oddílu, můžete změnit velikost výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="d5917-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="d5917-118">Změna velikosti oddílu může být užitečné pro programy, které poběží na menších zařízeních.</span><span class="sxs-lookup"><span data-stu-id="d5917-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5917-119">`-filealign` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d5917-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5917-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5917-120">See also</span></span>

- [<span data-ttu-id="d5917-121">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="d5917-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
