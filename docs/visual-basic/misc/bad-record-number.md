---
title: Počet chybných záznamů
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be04987353498775ec7dcef50b6acc1e6b4ec149
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="bad-record-number"></a><span data-ttu-id="b0ca0-102">Počet chybných záznamů</span><span class="sxs-lookup"><span data-stu-id="b0ca0-102">Bad record number</span></span>
<span data-ttu-id="b0ca0-103">Počet záznamů v `a FileGet`, `FilePut`, `FileGetObject`, nebo `FilePutObject` příkaz je menší než nebo rovna nule.</span><span class="sxs-lookup"><span data-stu-id="b0ca0-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b0ca0-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b0ca0-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="b0ca0-105">Zkontrolujte výpočty použité při vytváření číslo záznamu.</span><span class="sxs-lookup"><span data-stu-id="b0ca0-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="b0ca0-106">Zkontrolujte pravopis proměnné obsahující číslo záznamů nebo při výpočtu záznamu čísla.</span><span class="sxs-lookup"><span data-stu-id="b0ca0-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="b0ca0-107">Chybný název proměnné je implicitně deklarovaný a inicializovat na hodnotu nula, pokud jste použili `Option Explicit On` v modulu.</span><span class="sxs-lookup"><span data-stu-id="b0ca0-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ca0-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0ca0-108">See Also</span></span>  
 [<span data-ttu-id="b0ca0-109">Option Explicit – příkaz</span><span class="sxs-lookup"><span data-stu-id="b0ca0-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
