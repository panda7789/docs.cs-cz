---
title: 'Postupy: Vytvoření řetězce z pole znakových hodnot'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 03138a851afc55f735cc66edeb345817428a0452
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344389"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="c6e99-102">Postupy: Vytvoření řetězce z pole znakových hodnot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6e99-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="c6e99-103">Tento příklad vytvoří řetězec "abcd" z jednotlivých znaků.</span><span class="sxs-lookup"><span data-stu-id="c6e99-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6e99-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6e99-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c6e99-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c6e99-105">Compiling the Code</span></span>  
 <span data-ttu-id="c6e99-106">Tato metoda nemá žádné zvláštní požadavky.</span><span class="sxs-lookup"><span data-stu-id="c6e99-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="c6e99-107">Syntaxe `"a"c`, kde jedna `c` sleduje jeden znak v uvozovkách, slouží k vytvoření znakového literálu.</span><span class="sxs-lookup"><span data-stu-id="c6e99-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c6e99-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c6e99-108">Robust Programming</span></span>  
 <span data-ttu-id="c6e99-109">Znaky null (ekvivalentní `Chr(0)`) v řetězci mají za následek neočekávané výsledky při použití řetězce.</span><span class="sxs-lookup"><span data-stu-id="c6e99-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="c6e99-110">Znak null bude zahrnut spolu s řetězcem, ale v některých situacích se nezobrazí znaky, které následují za znakem null.</span><span class="sxs-lookup"><span data-stu-id="c6e99-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6e99-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6e99-111">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="c6e99-112">Datový typ Char</span><span class="sxs-lookup"><span data-stu-id="c6e99-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="c6e99-113">Datové typy</span><span class="sxs-lookup"><span data-stu-id="c6e99-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
