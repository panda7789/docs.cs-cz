---
title: Chybné číslo záznamu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 44a11d95d33041de9d637684f41cb003dcc36b97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84367539"
---
# <a name="bad-record-number"></a><span data-ttu-id="e7f6a-102">Chybné číslo záznamu</span><span class="sxs-lookup"><span data-stu-id="e7f6a-102">Bad record number</span></span>
<span data-ttu-id="e7f6a-103">Číslo záznamu v `a FileGet` příkazu, `FilePut` , `FileGetObject` nebo `FilePutObject` je menší nebo rovno nule.</span><span class="sxs-lookup"><span data-stu-id="e7f6a-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e7f6a-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e7f6a-104">To correct this error</span></span>  
  
1. <span data-ttu-id="e7f6a-105">Zkontroluje výpočty použité při generování čísla záznamu.</span><span class="sxs-lookup"><span data-stu-id="e7f6a-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="e7f6a-106">Ověřte pravopis proměnných, které obsahují číslo záznamu nebo které se používají při výpočtu čísel záznamů.</span><span class="sxs-lookup"><span data-stu-id="e7f6a-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="e7f6a-107">Nesprávně napsaný název proměnné se implicitně deklaruje a inicializuje na nulu, pokud se v modulu nepoužíváte `Option Explicit On` .</span><span class="sxs-lookup"><span data-stu-id="e7f6a-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f6a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7f6a-108">See also</span></span>

- [<span data-ttu-id="e7f6a-109">Option Explicit – příkaz</span><span class="sxs-lookup"><span data-stu-id="e7f6a-109">Option Explicit Statement</span></span>](../language-reference/statements/option-explicit-statement.md)
