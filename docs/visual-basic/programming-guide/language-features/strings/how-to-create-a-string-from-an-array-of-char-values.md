---
title: 'Postupy: Vytvoření řetězce z pole znakových hodnot (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 0d3a4caf0967ab77de7d91470e43e52521dbd2da
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975508"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="bbe10-102">Postupy: Vytvoření řetězce z pole znakových hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbe10-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="bbe10-103">Tento příklad vytvoří řetězec "abcd" z jednotlivých znaků.</span><span class="sxs-lookup"><span data-stu-id="bbe10-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbe10-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bbe10-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bbe10-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bbe10-105">Compiling the Code</span></span>  
 <span data-ttu-id="bbe10-106">Tato metoda nemá žádné zvláštní požadavky.</span><span class="sxs-lookup"><span data-stu-id="bbe10-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="bbe10-107">Syntaxe `"a"c`, kde jeden `c` následující jeden znak do uvozovek, je použít k vytvoření znak literálu.</span><span class="sxs-lookup"><span data-stu-id="bbe10-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bbe10-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="bbe10-108">Robust Programming</span></span>  
 <span data-ttu-id="bbe10-109">Znaky s hodnotou Null (ekvivalentní `Chr(0)`) v řetězci vést k neočekávaným výsledkům při použití řetězce.</span><span class="sxs-lookup"><span data-stu-id="bbe10-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="bbe10-110">Znak null bude součástí řetězce, ale v některých situacích se nezobrazí znaky následující po znaku null.</span><span class="sxs-lookup"><span data-stu-id="bbe10-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe10-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bbe10-111">See also</span></span>
- <xref:System.String>
- [<span data-ttu-id="bbe10-112">Datový typ Char</span><span class="sxs-lookup"><span data-stu-id="bbe10-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="bbe10-113">Datové typy</span><span class="sxs-lookup"><span data-stu-id="bbe10-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
