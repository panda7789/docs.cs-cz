---
title: /filealign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbabc19c85501b97ef5443a6f6e12524f8de7d91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="filealign"></a><span data-ttu-id="d4369-102">/filealign</span><span class="sxs-lookup"><span data-stu-id="d4369-102">/filealign</span></span>
<span data-ttu-id="d4369-103">Určuje, kde chcete-li zarovnat na části výstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="d4369-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4369-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4369-104">Syntax</span></span>  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="d4369-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d4369-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="d4369-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d4369-106">Required.</span></span> <span data-ttu-id="d4369-107">Hodnota, která určuje zarovnání oddílů, které jsou ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="d4369-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="d4369-108">Platné hodnoty jsou 512, 1024, 2048, 4096 až 8192.</span><span class="sxs-lookup"><span data-stu-id="d4369-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="d4369-109">Tyto hodnoty jsou v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d4369-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4369-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4369-110">Remarks</span></span>  
 <span data-ttu-id="d4369-111">Můžete použít `/filealign` možnost určení zarovnání oddílů, které jsou ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="d4369-111">You can use the `/filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="d4369-112">Oddíly jsou bloky souvislé paměti v souboru přenosné spustitelný soubor (PE), který obsahuje kód nebo data.</span><span class="sxs-lookup"><span data-stu-id="d4369-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="d4369-113">`/filealign` Možnost umožňuje kompilovat vaší aplikace pomocí nestandardní zarovnání; není nutné tuto možnost použijte, Většina vývojářů.</span><span class="sxs-lookup"><span data-stu-id="d4369-113">The `/filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="d4369-114">Každá část je zarovnán na hranici, která je násobkem `/filealign` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d4369-114">Each section is aligned on a boundary that is a multiple of the `/filealign` value.</span></span> <span data-ttu-id="d4369-115">Neexistuje žádná pevná výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="d4369-115">There is no fixed default.</span></span> <span data-ttu-id="d4369-116">Pokud `/filealign` není zadán, kompilátor zvolí výchozí v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="d4369-116">If `/filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="d4369-117">Zadáním velikost oddílu, můžete změnit velikost výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="d4369-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="d4369-118">Změna velikosti oddílu může být užitečné pro programy, které se spustí na menší zařízení.</span><span class="sxs-lookup"><span data-stu-id="d4369-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4369-119">`/filealign` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d4369-119">The `/filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4369-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4369-120">See Also</span></span>  
 [<span data-ttu-id="d4369-121">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="d4369-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
