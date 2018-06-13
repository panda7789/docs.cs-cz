---
title: 'Postupy: Přístup ke znakům v řetězcích v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 48507cade639660e6ce36697975d09fb29206c20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649149"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="ee1fa-102">Postupy: Přístup ke znakům v řetězcích v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee1fa-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="ee1fa-103">Tento příklad ukazuje, jak používat <xref:System.String.Chars%2A> vlastnost, která má přístup ke znakům v zadaném umístění v řetězci.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee1fa-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee1fa-104">Example</span></span>  
 <span data-ttu-id="ee1fa-105">Někdy je užitečné používat data o znaky v řetězec vašeho a pozice z těchto znaků v rámci vaší řetězec.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="ee1fa-106">Řetězce si můžete představit jako pole znaků (`Char` instance); určitý znak můžete načíst odkazem index tento znak prostřednictvím <xref:System.String.Chars%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 <span data-ttu-id="ee1fa-107">`index` Parametr <xref:System.String.Chars%2A> vlastnost je počítáno od nuly.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ee1fa-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ee1fa-108">Robust Programming</span></span>  
 <span data-ttu-id="ee1fa-109"><xref:System.String.Chars%2A> Vlastnost vrátí znak na zadané pozici.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="ee1fa-110">Některé znaky kódování Unicode však může být reprezentovaný více než jeden znak.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="ee1fa-111">Další informace o tom, jak pracovat s znaky znakové sady Unicode, najdete v části [postupy: převedení řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="ee1fa-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="ee1fa-112"><xref:System.String.Chars%2A> Vlastnost vyvolává <xref:System.IndexOutOfRangeException> výjimka pokud `index` parametr je větší než nebo rovna hodnotě délky řetězce, nebo pokud ji je menší než nula</span><span class="sxs-lookup"><span data-stu-id="ee1fa-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee1fa-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee1fa-113">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 [<span data-ttu-id="ee1fa-114">Postupy: Převod řetězce na pole znaků</span><span class="sxs-lookup"><span data-stu-id="ee1fa-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [<span data-ttu-id="ee1fa-115">Převod mezi řetězci a ostatními typy dat v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee1fa-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="ee1fa-116">Řetězce</span><span class="sxs-lookup"><span data-stu-id="ee1fa-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
