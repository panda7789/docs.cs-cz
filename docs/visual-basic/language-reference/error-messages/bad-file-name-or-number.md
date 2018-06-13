---
title: Chybný název souboru nebo číslo
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 903be68e71ad590b4b669545afd077175534ef4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585564"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="7937f-102">Chybný název souboru nebo číslo</span><span class="sxs-lookup"><span data-stu-id="7937f-102">Bad file name or number</span></span>
<span data-ttu-id="7937f-103">Došlo k chybě při pokusu o přístup k zadanému souboru.</span><span class="sxs-lookup"><span data-stu-id="7937f-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="7937f-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="7937f-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="7937f-105">Příkaz odkazuje na soubor s názvem souboru nebo číslo, který nebyl specifikován v `FileOpen` v byl zadán příkaz nebo který `FileOpen` příkaz ale byl následně uzavřen.</span><span class="sxs-lookup"><span data-stu-id="7937f-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="7937f-106">Příkaz odkazuje na soubor s číslo, které je mimo rozsah čísel souboru.</span><span class="sxs-lookup"><span data-stu-id="7937f-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="7937f-107">Příkaz odkazuje na název souboru nebo číslo, který není platný.</span><span class="sxs-lookup"><span data-stu-id="7937f-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7937f-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7937f-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="7937f-109">Ujistěte se, že v je zadán název souboru `FileOpen` příkaz.</span><span class="sxs-lookup"><span data-stu-id="7937f-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="7937f-110">Všimněte si, že pokud je volána `FileClose` příkaz bez argumentů, může nechtěně ukončení všech otevřených souborů.</span><span class="sxs-lookup"><span data-stu-id="7937f-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="7937f-111">Pokud váš kód je algorithmically generování čísel soubor, zkontrolujte, zda že jsou čísla platné.</span><span class="sxs-lookup"><span data-stu-id="7937f-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="7937f-112">Zkontrolujte názvy souborů a ujistěte se, že jsou v souladu s konvence operačního systému.</span><span class="sxs-lookup"><span data-stu-id="7937f-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7937f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7937f-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [<span data-ttu-id="7937f-114">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7937f-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
