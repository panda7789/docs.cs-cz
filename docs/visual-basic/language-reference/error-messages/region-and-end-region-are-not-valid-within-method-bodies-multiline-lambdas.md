---
title: "& č. 39; #Region & č. 39; a & č. 39; #End Region & č. 39; příkazy nejsou platné uvnitř těla víceřádkových výrazů lambda – metoda"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 614d0c7324bfbf07bc5736c799e8b54937ead081
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="18203-102">& č. 39; #Region & č. 39; a & č. 39; #End Region & č. 39; příkazy nejsou platné uvnitř těla nebo víceřádkových výrazů lambda – metoda</span><span class="sxs-lookup"><span data-stu-id="18203-102">&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="18203-103">`#Region` Bloku musí být deklarován na úrovni třídy, modul nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="18203-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="18203-104">Sbalitelné oblast může obsahovat jednu nebo více procedur, ale nesmí začínat ani končit v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="18203-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="18203-105">**ID chyby:** BC32025</span><span class="sxs-lookup"><span data-stu-id="18203-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18203-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="18203-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="18203-107">Ujistěte se, že předchozí postup je správně byla ukončena s `End Function` nebo `End Sub` příkaz.</span><span class="sxs-lookup"><span data-stu-id="18203-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="18203-108">Ujistěte se, že `#Region` a `#End Region` direktivy jsou ve stejné blok kódu.</span><span class="sxs-lookup"><span data-stu-id="18203-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18203-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="18203-109">See Also</span></span>  
 [<span data-ttu-id="18203-110">#Region – direktiva</span><span class="sxs-lookup"><span data-stu-id="18203-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
