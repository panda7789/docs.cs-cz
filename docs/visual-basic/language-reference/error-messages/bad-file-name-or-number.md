---
title: Chybný název souboru nebo číslo
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 11e866d9a8da7ad1ecc5f788fc31f6ac96d32f2c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409826"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="7b3d4-102">Chybný název souboru nebo číslo</span><span class="sxs-lookup"><span data-stu-id="7b3d4-102">Bad file name or number</span></span>
<span data-ttu-id="7b3d4-103">Při pokusu o přístup k zadanému souboru došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="7b3d4-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="7b3d4-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="7b3d4-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="7b3d4-105">Příkaz odkazuje na soubor s názvem nebo číslem souboru, který nebyl zadán v `FileOpen` příkazu nebo který byl zadán v `FileOpen` příkazu, ale byl následně uzavřen.</span><span class="sxs-lookup"><span data-stu-id="7b3d4-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="7b3d4-106">Příkaz odkazuje na soubor s číslem, který se nachází mimo rozsah čísel souborů.</span><span class="sxs-lookup"><span data-stu-id="7b3d4-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="7b3d4-107">Příkaz odkazuje na název souboru nebo číslo, které není platné.</span><span class="sxs-lookup"><span data-stu-id="7b3d4-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7b3d4-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7b3d4-108">To correct this error</span></span>  
  
1. <span data-ttu-id="7b3d4-109">Přesvědčte se, zda je název souboru zadán v `FileOpen` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7b3d4-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="7b3d4-110">Všimněte si, že pokud jste příkaz vyvolali `FileClose` bez argumentů, možná jste omylem zavřeli všechny otevřené soubory.</span><span class="sxs-lookup"><span data-stu-id="7b3d4-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="7b3d4-111">Pokud kód generuje čísla souborů algorithmically, ujistěte se, že jsou čísla platná.</span><span class="sxs-lookup"><span data-stu-id="7b3d4-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="7b3d4-112">Zkontrolujte názvy souborů a ujistěte se, že odpovídají konvencím operačního systému.</span><span class="sxs-lookup"><span data-stu-id="7b3d4-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b3d4-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b3d4-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="7b3d4-114">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b3d4-114">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
