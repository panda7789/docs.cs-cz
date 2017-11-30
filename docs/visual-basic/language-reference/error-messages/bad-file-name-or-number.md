---
title: "Chybný název souboru nebo číslo"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="dd9ca-102">Chybný název souboru nebo číslo</span><span class="sxs-lookup"><span data-stu-id="dd9ca-102">Bad file name or number</span></span>
<span data-ttu-id="dd9ca-103">Došlo k chybě při pokusu o přístup k zadanému souboru.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="dd9ca-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="dd9ca-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="dd9ca-105">Příkaz odkazuje na soubor s názvem souboru nebo číslo, který nebyl specifikován v `FileOpen` v byl zadán příkaz nebo který `FileOpen` příkaz ale byl následně uzavřen.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="dd9ca-106">Příkaz odkazuje na soubor s číslo, které je mimo rozsah čísel souboru.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="dd9ca-107">Příkaz odkazuje na název souboru nebo číslo, který není platný.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dd9ca-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="dd9ca-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="dd9ca-109">Ujistěte se, že v je zadán název souboru `FileOpen` příkaz.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="dd9ca-110">Všimněte si, že pokud je volána `FileClose` příkaz bez argumentů, může nechtěně ukončení všech otevřených souborů.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="dd9ca-111">Pokud váš kód je algorithmically generování čísel soubor, zkontrolujte, zda že jsou čísla platné.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="dd9ca-112">Zkontrolujte názvy souborů a ujistěte se, že jsou v souladu s konvence operačního systému.</span><span class="sxs-lookup"><span data-stu-id="dd9ca-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd9ca-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd9ca-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [<span data-ttu-id="dd9ca-114">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd9ca-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
