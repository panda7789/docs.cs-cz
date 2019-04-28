---
title: Erase – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: bf3eb6476dc1485faeddab475f29e508175d3378
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638184"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="58146-102">Erase – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58146-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="58146-103">Slouží k uvolnění proměnných pole a navrácení paměti používané pro jejich elementy.</span><span class="sxs-lookup"><span data-stu-id="58146-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58146-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58146-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="58146-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="58146-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="58146-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="58146-106">Required.</span></span> <span data-ttu-id="58146-107">Seznam proměnných jsou vymazány.</span><span class="sxs-lookup"><span data-stu-id="58146-107">List of array variables to be erased.</span></span> <span data-ttu-id="58146-108">Více proměnných jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="58146-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58146-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58146-109">Remarks</span></span>  
 <span data-ttu-id="58146-110">`Erase` Příkaz se může zobrazit jenom na úroveň procedury.</span><span class="sxs-lookup"><span data-stu-id="58146-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="58146-111">To znamená, že můžete uvolnit pole uvnitř procedury, ale ne na úrovni třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="58146-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="58146-112">`Erase` Příkaz je ekvivalentní k přiřazení `Nothing` pro každou proměnnou pole.</span><span class="sxs-lookup"><span data-stu-id="58146-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58146-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="58146-113">Example</span></span>  
 <span data-ttu-id="58146-114">V následujícím příkladu `Erase` příkaz dvě pole vymazat a uvolnit paměť, jejich (1 000 až 100 elementů úložiště, v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="58146-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="58146-115">`ReDim` Příkaz pak přiřadí nové pole instance na trojrozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="58146-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="58146-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58146-116">See also</span></span>

- [<span data-ttu-id="58146-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="58146-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="58146-118">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="58146-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
