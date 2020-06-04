---
title: Erase – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 31aeaf822bc9c1de59a5c5f68406c6521216ae0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404716"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="b296e-102">Erase – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b296e-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="b296e-103">Slouží k uvolnění proměnných pole a navrácení paměti používané pro jejich elementy.</span><span class="sxs-lookup"><span data-stu-id="b296e-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b296e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b296e-104">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="b296e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b296e-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="b296e-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="b296e-106">Required.</span></span> <span data-ttu-id="b296e-107">Seznam proměnných pole, které mají být smazány.</span><span class="sxs-lookup"><span data-stu-id="b296e-107">List of array variables to be erased.</span></span> <span data-ttu-id="b296e-108">Více proměnných je odděleno čárkami.</span><span class="sxs-lookup"><span data-stu-id="b296e-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b296e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b296e-109">Remarks</span></span>  
 <span data-ttu-id="b296e-110">`Erase`Příkaz se může vyskytovat pouze na úrovni procedury.</span><span class="sxs-lookup"><span data-stu-id="b296e-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="b296e-111">To znamená, že můžete uvolnit pole v proceduře, ale ne na úrovni třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="b296e-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="b296e-112">`Erase`Příkaz je ekvivalentní k přiřazení `Nothing` každé proměnné pole.</span><span class="sxs-lookup"><span data-stu-id="b296e-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b296e-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b296e-113">Example</span></span>  
 <span data-ttu-id="b296e-114">Následující příklad používá `Erase` příkaz k vymazání dvou polí a uvolnění paměti 100 1000 (v uvedeném pořadí).</span><span class="sxs-lookup"><span data-stu-id="b296e-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="b296e-115">`ReDim`Příkaz následně přiřadí novou instanci pole trojrozměrnému poli.</span><span class="sxs-lookup"><span data-stu-id="b296e-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="b296e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b296e-116">See also</span></span>

- [<span data-ttu-id="b296e-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="b296e-117">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="b296e-118">ReDim – příkaz</span><span class="sxs-lookup"><span data-stu-id="b296e-118">ReDim Statement</span></span>](redim-statement.md)
