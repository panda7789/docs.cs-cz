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
ms.openlocfilehash: fef2652f591e713140c651a9cb0df1ea9e6236c8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005595"
---
# <a name="-filealign"></a><span data-ttu-id="0b889-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="0b889-102">-filealign</span></span>
<span data-ttu-id="0b889-103">Určuje, kam se mají zarovnat oddíly výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="0b889-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b889-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b889-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="0b889-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0b889-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="0b889-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0b889-106">Required.</span></span> <span data-ttu-id="0b889-107">Hodnota, která určuje zarovnání oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="0b889-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="0b889-108">Platné hodnoty jsou 512, 1024, 2048, 4096 a 8192.</span><span class="sxs-lookup"><span data-stu-id="0b889-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="0b889-109">Tyto hodnoty jsou v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0b889-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b889-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b889-110">Remarks</span></span>  
 <span data-ttu-id="0b889-111">Pomocí možnosti `-filealign` můžete určit zarovnání oddílů ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="0b889-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="0b889-112">Oddíly jsou bloky souvislé paměti v přenositelném spustitelném souboru (PE), který obsahuje buď kód, nebo data.</span><span class="sxs-lookup"><span data-stu-id="0b889-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="0b889-113">Možnost `-filealign` umožňuje kompilovat aplikaci pomocí nestandardního zarovnání; většinu vývojářů tuto možnost nepotřebují použít.</span><span class="sxs-lookup"><span data-stu-id="0b889-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="0b889-114">Každý oddíl je zarovnán na hranici, která je násobkem hodnoty `-filealign`.</span><span class="sxs-lookup"><span data-stu-id="0b889-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="0b889-115">Neexistuje žádná pevná výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="0b889-115">There is no fixed default.</span></span> <span data-ttu-id="0b889-116">Pokud není zadán `-filealign`, kompilátor vybere výchozí hodnotu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0b889-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="0b889-117">Zadáním velikosti oddílu můžete změnit velikost výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="0b889-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="0b889-118">Změna velikosti oddílu může být užitečná pro programy, které se spustí na menších zařízeních.</span><span class="sxs-lookup"><span data-stu-id="0b889-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b889-119">Možnost `-filealign` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0b889-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b889-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b889-120">See also</span></span>

- [<span data-ttu-id="0b889-121">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="0b889-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
