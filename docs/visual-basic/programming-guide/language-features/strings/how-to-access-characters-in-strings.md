---
title: 'Postupy: Přístup znakům v řetězcích v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: f2831333008844c959c3625698fce6c485450683
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967552"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="4db77-102">Postupy: Přístup znakům v řetězcích v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4db77-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="4db77-103">Tento příklad ukazuje, jak používat <xref:System.String.Chars%2A> vlastnost přístup ke znakům v zadaném umístění v řetězci.</span><span class="sxs-lookup"><span data-stu-id="4db77-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4db77-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4db77-104">Example</span></span>  
 <span data-ttu-id="4db77-105">Někdy je užitečné mít data o znaky v váš řetězec a umístění těchto znaků v rámci vašeho řetězce.</span><span class="sxs-lookup"><span data-stu-id="4db77-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="4db77-106">Řetězec si můžete představit jako pole znaků (`Char` instance); určitý znak můžete načíst pomocí odkazu na index tohoto znaku prostřednictvím <xref:System.String.Chars%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4db77-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="4db77-107">`index` Parametr <xref:System.String.Chars%2A> vlastnost je založený na nule.</span><span class="sxs-lookup"><span data-stu-id="4db77-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4db77-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="4db77-108">Robust Programming</span></span>  
 <span data-ttu-id="4db77-109"><xref:System.String.Chars%2A> Vlastnost vrátí znak na zadané pozici.</span><span class="sxs-lookup"><span data-stu-id="4db77-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="4db77-110">Některé znaky Unicode však může být reprezentována více než jeden znak.</span><span class="sxs-lookup"><span data-stu-id="4db77-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="4db77-111">Další informace o tom, jak pracovat s znaků Unicode naleznete v tématu [jak: Převod řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="4db77-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="4db77-112"><xref:System.String.Chars%2A> Vlastnost vyvolá <xref:System.IndexOutOfRangeException> výjimka pokud `index` parametr je větší než nebo rovna délce řetězce, nebo pokud je menší než nula</span><span class="sxs-lookup"><span data-stu-id="4db77-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db77-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4db77-113">See also</span></span>
- <xref:System.String.Chars%2A>
- [<span data-ttu-id="4db77-114">Postupy: Převod řetězce na pole znaků</span><span class="sxs-lookup"><span data-stu-id="4db77-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="4db77-115">Převod mezi řetězci a ostatními datovými typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4db77-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="4db77-116">Řetězce</span><span class="sxs-lookup"><span data-stu-id="4db77-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
