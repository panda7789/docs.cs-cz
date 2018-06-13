---
title: Erase – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 317e2a7dc5facb08388f3a3e635734e4daed5eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601790"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="bd2fd-102">Erase – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd2fd-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="bd2fd-103">Použít k vydání proměnné pole a navrátit paměť použitá pro jejich elementů.</span><span class="sxs-lookup"><span data-stu-id="bd2fd-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd2fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd2fd-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="bd2fd-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="bd2fd-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="bd2fd-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="bd2fd-106">Required.</span></span> <span data-ttu-id="bd2fd-107">Seznam proměnné pole, které chcete vymazat.</span><span class="sxs-lookup"><span data-stu-id="bd2fd-107">List of array variables to be erased.</span></span> <span data-ttu-id="bd2fd-108">Více proměnných jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="bd2fd-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd2fd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd2fd-109">Remarks</span></span>  
 <span data-ttu-id="bd2fd-110">`Erase` Příkaz může vyskytovat pouze na úrovni postupu.</span><span class="sxs-lookup"><span data-stu-id="bd2fd-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="bd2fd-111">To znamená, že můžete vydat pole uvnitř procedury, ale ne na úrovni třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="bd2fd-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="bd2fd-112">`Erase` Příkaz je ekvivalentní k přiřazení `Nothing` pro každou proměnnou pole.</span><span class="sxs-lookup"><span data-stu-id="bd2fd-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd2fd-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd2fd-113">Example</span></span>  
 <span data-ttu-id="bd2fd-114">Následující příklad používá `Erase` příkaz dvě pole vymazat a uvolnit paměť, jejich (elementy úložiště 1000 a 100, v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="bd2fd-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="bd2fd-115">`ReDim` Příkaz poté přiřadí novou instanci pole k poli trojrozměrné.</span><span class="sxs-lookup"><span data-stu-id="bd2fd-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bd2fd-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd2fd-116">See Also</span></span>  
 [<span data-ttu-id="bd2fd-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="bd2fd-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="bd2fd-118">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="bd2fd-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
