---
title: '&#39;#Region&#39; a &#39;#End Region&#39; příkazy nejsou platné uvnitř těla nebo víceřádkových výrazů lambda – metoda'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 55399cd123ce4d67cc833f2eabe3230acdafc0bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737212"
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="4450c-102">&#39;#Region&#39; a &#39;#End Region&#39; příkazy nejsou platné uvnitř těla nebo víceřádkových výrazů lambda – metoda</span><span class="sxs-lookup"><span data-stu-id="4450c-102">&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="4450c-103">`#Region` Bloku musí být deklarován na úrovni třídy, modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4450c-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="4450c-104">Sbalitelná oblast může zahrnovat jeden nebo více postupů, ale nesmí začínat ani končit v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="4450c-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="4450c-105">**ID chyby:** BC32025</span><span class="sxs-lookup"><span data-stu-id="4450c-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4450c-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4450c-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="4450c-107">Ujistěte se, že je správně ukončují předchozí postup `End Function` nebo `End Sub` příkazu.</span><span class="sxs-lookup"><span data-stu-id="4450c-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="4450c-108">Ujistěte se, `#Region` a `#End Region` direktivy jsou ve stejném bloku kódu.</span><span class="sxs-lookup"><span data-stu-id="4450c-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4450c-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4450c-109">See also</span></span>
- [<span data-ttu-id="4450c-110">Direktiva #Region</span><span class="sxs-lookup"><span data-stu-id="4450c-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
