---
title: Příkazy '#Region' a '#End Region' nejsou platné uvnitř těla metody nebo víceřádkových výrazů lambda.
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 5652139ab139ea93258eb116f97ba21b76986a24
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400380"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="f89a8-102">Příkazy '#Region' a '#End Region' nejsou platné uvnitř těla metody nebo víceřádkových výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="f89a8-102">'#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="f89a8-103">`#Region`Blok musí být deklarován na úrovni třídy, modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f89a8-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="f89a8-104">Sbalitelná oblast může zahrnovat jeden nebo více procedur, ale nemůže začínat ani končit uvnitř procedury.</span><span class="sxs-lookup"><span data-stu-id="f89a8-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="f89a8-105">**ID chyby:** BC32025</span><span class="sxs-lookup"><span data-stu-id="f89a8-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f89a8-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f89a8-106">To correct this error</span></span>  
  
1. <span data-ttu-id="f89a8-107">Zajistěte, aby byl předchozí postup správně ukončen `End Function` pomocí `End Sub` příkazu nebo.</span><span class="sxs-lookup"><span data-stu-id="f89a8-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="f89a8-108">Ujistěte se, `#Region` že `#End Region` direktivy a jsou ve stejném bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="f89a8-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f89a8-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="f89a8-109">See also</span></span>

- [<span data-ttu-id="f89a8-110">#Region direktiva</span><span class="sxs-lookup"><span data-stu-id="f89a8-110">#Region Directive</span></span>](../directives/region-directive.md)
