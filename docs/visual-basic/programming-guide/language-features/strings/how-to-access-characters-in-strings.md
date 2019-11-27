---
title: 'Postupy: Přístup ke znakům v řetězcích'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 44a021ed3ce1d10613cf6ab7c959c62feec6046c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352460"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="6829b-102">Postupy: Přístup ke znakům v řetězcích v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6829b-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="6829b-103">Tento příklad ukazuje, jak použít vlastnost <xref:System.String.Chars%2A> pro přístup k znaku v zadaném umístění v řetězci.</span><span class="sxs-lookup"><span data-stu-id="6829b-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6829b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6829b-104">Example</span></span>  
 <span data-ttu-id="6829b-105">Někdy je užitečné mít data o znacích v řetězci a umístění těchto znaků v rámci řetězce.</span><span class="sxs-lookup"><span data-stu-id="6829b-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="6829b-106">Řetězec lze představit jako pole znaků (`Char` instance); můžete načíst konkrétní znak odkazem na index daného znaku prostřednictvím vlastnosti <xref:System.String.Chars%2A>.</span><span class="sxs-lookup"><span data-stu-id="6829b-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="6829b-107">Parametr `index` vlastnosti <xref:System.String.Chars%2A> je založený na nule.</span><span class="sxs-lookup"><span data-stu-id="6829b-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6829b-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="6829b-108">Robust Programming</span></span>  
 <span data-ttu-id="6829b-109">Vlastnost <xref:System.String.Chars%2A> vrací znak na zadané pozici.</span><span class="sxs-lookup"><span data-stu-id="6829b-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="6829b-110">Některé znaky Unicode však mohou být reprezentovány více než jedním znakem.</span><span class="sxs-lookup"><span data-stu-id="6829b-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="6829b-111">Další informace o tom, jak pracovat se znaky kódování Unicode, naleznete v tématu [How to: Convert String to Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="6829b-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="6829b-112">Vlastnost <xref:System.String.Chars%2A> vyvolá výjimku <xref:System.IndexOutOfRangeException>, pokud je parametr `index` větší nebo roven délce řetězce, nebo pokud je menší než nula.</span><span class="sxs-lookup"><span data-stu-id="6829b-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6829b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6829b-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="6829b-114">Postupy: Převod řetězce na pole znaků</span><span class="sxs-lookup"><span data-stu-id="6829b-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="6829b-115">Převod mezi řetězci a ostatními datovými typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6829b-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="6829b-116">Řetězce</span><span class="sxs-lookup"><span data-stu-id="6829b-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
