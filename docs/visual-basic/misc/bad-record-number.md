---
title: Chybné číslo záznamu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: abd0a1467c0991a40b93e74a1d7a7889367fb8ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340799"
---
# <a name="bad-record-number"></a><span data-ttu-id="5c73f-102">Chybné číslo záznamu</span><span class="sxs-lookup"><span data-stu-id="5c73f-102">Bad record number</span></span>
<span data-ttu-id="5c73f-103">Číslo záznamu v `a FileGet`, `FilePut`, `FileGetObject`, nebo `FilePutObject` příkaz je menší než nebo rovna nule.</span><span class="sxs-lookup"><span data-stu-id="5c73f-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c73f-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5c73f-104">To correct this error</span></span>  
  
1. <span data-ttu-id="5c73f-105">Zkontrolujte výpočty použitého při generování číslo záznamu.</span><span class="sxs-lookup"><span data-stu-id="5c73f-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="5c73f-106">Zkontrolujte pravopis proměnné obsahující číslo záznamu nebo používají při výpočtu čísla záznamů.</span><span class="sxs-lookup"><span data-stu-id="5c73f-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="5c73f-107">Chybně napsaná název proměnné implicitně deklarovány a inicializovány na nulu, pokud jste použili `Option Explicit On` v modulu.</span><span class="sxs-lookup"><span data-stu-id="5c73f-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c73f-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c73f-108">See also</span></span>

- [<span data-ttu-id="5c73f-109">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="5c73f-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
