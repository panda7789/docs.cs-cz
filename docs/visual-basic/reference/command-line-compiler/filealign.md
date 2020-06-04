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
ms.openlocfilehash: 3877757185030b0dba914a79d8c760fb8033ae5f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408644"
---
# <a name="-filealign"></a><span data-ttu-id="c909e-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="c909e-102">-filealign</span></span>
<span data-ttu-id="c909e-103">Určuje, kam se mají zarovnat oddíly výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="c909e-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c909e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c909e-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="c909e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c909e-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="c909e-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="c909e-106">Required.</span></span> <span data-ttu-id="c909e-107">Hodnota, která určuje zarovnání oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="c909e-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="c909e-108">Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192.</span><span class="sxs-lookup"><span data-stu-id="c909e-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="c909e-109">Tyto hodnoty jsou v bajtech.</span><span class="sxs-lookup"><span data-stu-id="c909e-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c909e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c909e-110">Remarks</span></span>  
 <span data-ttu-id="c909e-111">Pomocí `-filealign` Možnosti můžete určit zarovnání oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="c909e-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="c909e-112">Oddíly jsou bloky souvislé paměti v přenositelném spustitelném souboru (PE), který obsahuje buď kód, nebo data.</span><span class="sxs-lookup"><span data-stu-id="c909e-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="c909e-113">`-filealign`Možnost umožňuje zkompilovat aplikaci pomocí nestandardního zarovnání; většina vývojářů tuto možnost nepotřebuje.</span><span class="sxs-lookup"><span data-stu-id="c909e-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="c909e-114">Každý oddíl je zarovnán na hranici, která je násobkem `-filealign` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c909e-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="c909e-115">Neexistuje žádná pevná výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="c909e-115">There is no fixed default.</span></span> <span data-ttu-id="c909e-116">Pokud `-filealign` parametr není zadán, kompilátor vybere výchozí hodnotu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c909e-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="c909e-117">Zadáním velikosti oddílu můžete změnit velikost výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="c909e-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="c909e-118">Změna velikosti oddílu může být užitečná pro programy, které se spustí na menších zařízeních.</span><span class="sxs-lookup"><span data-stu-id="c909e-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c909e-119">Tato `-filealign` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c909e-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c909e-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c909e-120">See also</span></span>

- [<span data-ttu-id="c909e-121">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="c909e-121">Visual Basic Command-Line Compiler</span></span>](index.md)
