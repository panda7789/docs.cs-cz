---
title: 'Postupy: Vytvoření řetězce z pole znakových hodnot'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: d9ec897467f0caac0afc089a028516c0316a2bda
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410590"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="3711b-102">Postupy: Vytvoření řetězce z pole znakových hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3711b-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="3711b-103">Tento příklad vytvoří řetězec "abcd" z jednotlivých znaků.</span><span class="sxs-lookup"><span data-stu-id="3711b-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3711b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3711b-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="3711b-105">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="3711b-105">Compile the code</span></span>  
 <span data-ttu-id="3711b-106">Tato metoda nemá žádné zvláštní požadavky.</span><span class="sxs-lookup"><span data-stu-id="3711b-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="3711b-107">Syntaxe `"a"c` , kde jedna následuje za `c` jedním znakem v uvozovkách, se používá k vytvoření znakového literálu.</span><span class="sxs-lookup"><span data-stu-id="3711b-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3711b-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="3711b-108">Robust Programming</span></span>  
 <span data-ttu-id="3711b-109">Znaky null (stejné jako `Chr(0)` ) v řetězci mají za následek neočekávané výsledky při použití řetězce.</span><span class="sxs-lookup"><span data-stu-id="3711b-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="3711b-110">Znak null bude zahrnut spolu s řetězcem, ale v některých situacích se nezobrazí znaky, které následují za znakem null.</span><span class="sxs-lookup"><span data-stu-id="3711b-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3711b-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="3711b-111">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="3711b-112">Char – datový typ</span><span class="sxs-lookup"><span data-stu-id="3711b-112">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="3711b-113">Datové typy</span><span class="sxs-lookup"><span data-stu-id="3711b-113">Data Types</span></span>](../data-types/index.md)
