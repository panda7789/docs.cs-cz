---
title: "Erase – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a2b439cf5ad04d59cea59bb21d345d0057b322
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="fd1e4-102">Erase – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd1e4-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="fd1e4-103">Použít k vydání proměnné pole a navrátit paměť použitá pro jejich elementů.</span><span class="sxs-lookup"><span data-stu-id="fd1e4-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd1e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd1e4-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="fd1e4-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="fd1e4-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="fd1e4-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fd1e4-106">Required.</span></span> <span data-ttu-id="fd1e4-107">Seznam proměnné pole, které chcete vymazat.</span><span class="sxs-lookup"><span data-stu-id="fd1e4-107">List of array variables to be erased.</span></span> <span data-ttu-id="fd1e4-108">Více proměnných jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="fd1e4-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd1e4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd1e4-109">Remarks</span></span>  
 <span data-ttu-id="fd1e4-110">`Erase` Příkaz může vyskytovat pouze na úrovni postupu.</span><span class="sxs-lookup"><span data-stu-id="fd1e4-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="fd1e4-111">To znamená, že můžete vydat pole uvnitř procedury, ale ne na úrovni třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="fd1e4-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="fd1e4-112">`Erase` Příkaz je ekvivalentní k přiřazení `Nothing` pro každou proměnnou pole.</span><span class="sxs-lookup"><span data-stu-id="fd1e4-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd1e4-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd1e4-113">Example</span></span>  
 <span data-ttu-id="fd1e4-114">Následující příklad používá `Erase` příkaz dvě pole vymazat a uvolnit paměť, jejich (elementy úložiště 1000 a 100, v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="fd1e4-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="fd1e4-115">`ReDim` Příkaz poté přiřadí novou instanci pole k poli trojrozměrné.</span><span class="sxs-lookup"><span data-stu-id="fd1e4-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fd1e4-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd1e4-116">See Also</span></span>  
 [<span data-ttu-id="fd1e4-117">Nic</span><span class="sxs-lookup"><span data-stu-id="fd1e4-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="fd1e4-118">ReDim – příkaz</span><span class="sxs-lookup"><span data-stu-id="fd1e4-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
