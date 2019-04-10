---
title: Příkazy '#Region' a '#End Region' nejsou platné uvnitř těla nebo víceřádkových výrazů lambda – metoda
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c41b95da7e3565ae7aaf332fe49361336e79f7c7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303905"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="b0619-102">Příkazy '#Region' a '#End Region' nejsou platné uvnitř těla metody nebo víceřádkových výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="b0619-102">'#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="b0619-103">`#Region` Bloku musí být deklarován na úrovni třídy, modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b0619-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="b0619-104">Sbalitelná oblast může zahrnovat jeden nebo více postupů, ale nesmí začínat ani končit v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="b0619-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="b0619-105">**ID chyby:** BC32025</span><span class="sxs-lookup"><span data-stu-id="b0619-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b0619-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b0619-106">To correct this error</span></span>  
  
1. <span data-ttu-id="b0619-107">Ujistěte se, že je správně ukončují předchozí postup `End Function` nebo `End Sub` příkazu.</span><span class="sxs-lookup"><span data-stu-id="b0619-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="b0619-108">Ujistěte se, `#Region` a `#End Region` direktivy jsou ve stejném bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="b0619-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0619-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0619-109">See also</span></span>

- [<span data-ttu-id="b0619-110">#Region – direktiva</span><span class="sxs-lookup"><span data-stu-id="b0619-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
