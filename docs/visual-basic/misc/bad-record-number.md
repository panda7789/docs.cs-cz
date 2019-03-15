---
title: Chybné číslo záznamu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: c71d523406f3ffa420c36125847ab6d35a8f741c
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58037098"
---
# <a name="bad-record-number"></a><span data-ttu-id="fa324-102">Chybné číslo záznamu</span><span class="sxs-lookup"><span data-stu-id="fa324-102">Bad record number</span></span>
<span data-ttu-id="fa324-103">Číslo záznamu v `a FileGet`, `FilePut`, `FileGetObject`, nebo `FilePutObject` příkaz je menší než nebo rovna nule.</span><span class="sxs-lookup"><span data-stu-id="fa324-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa324-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fa324-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="fa324-105">Zkontrolujte výpočty použitého při generování číslo záznamu.</span><span class="sxs-lookup"><span data-stu-id="fa324-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="fa324-106">Zkontrolujte pravopis proměnné obsahující číslo záznamu nebo používají při výpočtu čísla záznamů.</span><span class="sxs-lookup"><span data-stu-id="fa324-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="fa324-107">Chybně napsaná název proměnné implicitně deklarovány a inicializovány na nulu, pokud jste použili `Option Explicit On` v modulu.</span><span class="sxs-lookup"><span data-stu-id="fa324-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa324-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa324-108">See also</span></span>

- [<span data-ttu-id="fa324-109">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="fa324-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
