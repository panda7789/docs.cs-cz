---
title: Počet chybných záznamů
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 400879ba37c6b3215d9570ca6eb8eaa06edea03b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600802"
---
# <a name="bad-record-number"></a><span data-ttu-id="af7f2-102">Počet chybných záznamů</span><span class="sxs-lookup"><span data-stu-id="af7f2-102">Bad record number</span></span>
<span data-ttu-id="af7f2-103">Počet záznamů v `a FileGet`, `FilePut`, `FileGetObject`, nebo `FilePutObject` příkaz je menší než nebo rovna nule.</span><span class="sxs-lookup"><span data-stu-id="af7f2-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="af7f2-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="af7f2-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="af7f2-105">Zkontrolujte výpočty použité při vytváření číslo záznamu.</span><span class="sxs-lookup"><span data-stu-id="af7f2-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="af7f2-106">Zkontrolujte pravopis proměnné obsahující číslo záznamů nebo při výpočtu záznamu čísla.</span><span class="sxs-lookup"><span data-stu-id="af7f2-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="af7f2-107">Chybný název proměnné je implicitně deklarovaný a inicializovat na hodnotu nula, pokud jste použili `Option Explicit On` v modulu.</span><span class="sxs-lookup"><span data-stu-id="af7f2-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af7f2-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="af7f2-108">See Also</span></span>  
 [<span data-ttu-id="af7f2-109">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="af7f2-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
