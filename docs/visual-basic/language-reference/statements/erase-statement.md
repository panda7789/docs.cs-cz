---
title: Erase – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 7dec2a859f664ee8dcbb305082ec33aeacbaccb4
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583391"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="840b3-102">Erase – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="840b3-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="840b3-103">Slouží k uvolnění proměnných pole a navrácení paměti používané pro jejich elementy.</span><span class="sxs-lookup"><span data-stu-id="840b3-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="840b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="840b3-104">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="840b3-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="840b3-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="840b3-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="840b3-106">Required.</span></span> <span data-ttu-id="840b3-107">Seznam proměnných pole, které mají být smazány.</span><span class="sxs-lookup"><span data-stu-id="840b3-107">List of array variables to be erased.</span></span> <span data-ttu-id="840b3-108">Více proměnných je odděleno čárkami.</span><span class="sxs-lookup"><span data-stu-id="840b3-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="840b3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="840b3-109">Remarks</span></span>  
 <span data-ttu-id="840b3-110">Příkaz `Erase` se může vyskytovat pouze na úrovni procedury.</span><span class="sxs-lookup"><span data-stu-id="840b3-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="840b3-111">To znamená, že můžete uvolnit pole v proceduře, ale ne na úrovni třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="840b3-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="840b3-112">Příkaz `Erase` je ekvivalentní k přiřazování `Nothing` na každou proměnnou pole.</span><span class="sxs-lookup"><span data-stu-id="840b3-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="840b3-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="840b3-113">Example</span></span>  
 <span data-ttu-id="840b3-114">V následujícím příkladu je použit příkaz `Erase` pro vymazání dvou polí a uvolnění paměti (v uvedeném pořadí) paměti (1000 a 100 prvků úložiště).</span><span class="sxs-lookup"><span data-stu-id="840b3-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="840b3-115">Příkaz `ReDim` potom přiřadí novou instanci pole k trojrozměrnému poli.</span><span class="sxs-lookup"><span data-stu-id="840b3-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="840b3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="840b3-116">See also</span></span>

- [<span data-ttu-id="840b3-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="840b3-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="840b3-118">Příkaz ReDim</span><span class="sxs-lookup"><span data-stu-id="840b3-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
