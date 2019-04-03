---
title: Chybný název souboru nebo číslo
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: b6da1031b60a4cd73c53588cf18992797c3fddab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839064"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="879d5-102">Chybný název souboru nebo číslo</span><span class="sxs-lookup"><span data-stu-id="879d5-102">Bad file name or number</span></span>
<span data-ttu-id="879d5-103">Při pokusu o přístup k zadanému souboru došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="879d5-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="879d5-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="879d5-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="879d5-105">Příkaz odkazuje na soubor s názvem souboru nebo číslo, který nebyl zadán v `FileOpen` příkazu nebo, který byl zadán v `FileOpen` prohlášení, avšak byla následně uzavřen.</span><span class="sxs-lookup"><span data-stu-id="879d5-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="879d5-106">Příkaz odkazuje na soubor s číslo, které je mimo rozsah čísel souborů.</span><span class="sxs-lookup"><span data-stu-id="879d5-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="879d5-107">Příkaz odkazuje na název souboru nebo číslo, které není platný.</span><span class="sxs-lookup"><span data-stu-id="879d5-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="879d5-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="879d5-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="879d5-109">Ujistěte se, že byl zadán název souboru `FileOpen` příkazu.</span><span class="sxs-lookup"><span data-stu-id="879d5-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="879d5-110">Poznámka: Pokud jste vyvolali `FileClose` příkaz bez argumentů, mohou neúmyslně neukončíte všechny otevřené soubory.</span><span class="sxs-lookup"><span data-stu-id="879d5-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="879d5-111">Pokud váš kód algorithmically generuje soubor čísla, zkontrolujte, zda že jsou čísla platné.</span><span class="sxs-lookup"><span data-stu-id="879d5-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="879d5-112">Zkontrolujte názvy souborů, abyste měli jistotu, že jsou v souladu s konvencí operačního systému.</span><span class="sxs-lookup"><span data-stu-id="879d5-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="879d5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="879d5-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="879d5-114">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="879d5-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
