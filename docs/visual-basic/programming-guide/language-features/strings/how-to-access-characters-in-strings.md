---
title: 'Postupy: Přístup znakům v řetězcích v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 9833b562fc0b4115448ebefb8631f0d73eb15f6f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618919"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="1d51b-102">Postupy: Přístup znakům v řetězcích v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1d51b-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="1d51b-103">Tento příklad ukazuje, jak používat <xref:System.String.Chars%2A> vlastnost přístup ke znakům v zadaném umístění v řetězci.</span><span class="sxs-lookup"><span data-stu-id="1d51b-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d51b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d51b-104">Example</span></span>  
 <span data-ttu-id="1d51b-105">Někdy je užitečné mít data o znaky v váš řetězec a umístění těchto znaků v rámci vašeho řetězce.</span><span class="sxs-lookup"><span data-stu-id="1d51b-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="1d51b-106">Řetězec si můžete představit jako pole znaků (`Char` instance); určitý znak můžete načíst pomocí odkazu na index tohoto znaku prostřednictvím <xref:System.String.Chars%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1d51b-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 <span data-ttu-id="1d51b-107">`index` Parametr <xref:System.String.Chars%2A> vlastnost je založený na nule.</span><span class="sxs-lookup"><span data-stu-id="1d51b-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1d51b-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1d51b-108">Robust Programming</span></span>  
 <span data-ttu-id="1d51b-109"><xref:System.String.Chars%2A> Vlastnost vrátí znak na zadané pozici.</span><span class="sxs-lookup"><span data-stu-id="1d51b-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="1d51b-110">Některé znaky Unicode však může být reprezentována více než jeden znak.</span><span class="sxs-lookup"><span data-stu-id="1d51b-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="1d51b-111">Další informace o tom, jak pracovat s znaků Unicode naleznete v tématu [jak: Převod řetězce na pole znaků](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="1d51b-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="1d51b-112"><xref:System.String.Chars%2A> Vlastnost vyvolá <xref:System.IndexOutOfRangeException> výjimka pokud `index` parametr je větší než nebo rovna délce řetězce, nebo pokud je menší než nula</span><span class="sxs-lookup"><span data-stu-id="1d51b-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d51b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d51b-113">See also</span></span>
- <xref:System.String.Chars%2A>
- [<span data-ttu-id="1d51b-114">Postupy: Převod řetězce na pole znaků</span><span class="sxs-lookup"><span data-stu-id="1d51b-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="1d51b-115">Převod mezi řetězci a ostatními datovými typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1d51b-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="1d51b-116">Řetězce</span><span class="sxs-lookup"><span data-stu-id="1d51b-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
