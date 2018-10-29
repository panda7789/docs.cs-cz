---
title: 'Postupy: Převod řetězce na pole znaků v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: cc12b70cddcb93a72b4421a8ddd93542ef84f55b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202759"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="c2044-102">Postupy: Převod řetězce na pole znaků v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2044-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="c2044-103">Někdy je užitečné mít data o znaky v váš řetězec a umístění těchto znaků v řetězci, například když je analýza řetězce.</span><span class="sxs-lookup"><span data-stu-id="c2044-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="c2044-104">Tento příklad ukazuje, jak získat pole znaků v řetězci pomocí volání řetězce <xref:System.String.ToCharArray%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c2044-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2044-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2044-105">Example</span></span>  
 <span data-ttu-id="c2044-106">Tento příklad ukazuje, jak rozdělit řetězec do `Char` pole a jak rozdělit řetězec do `String` pole jeho textové znaky kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="c2044-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="c2044-107">Důvod pro tento rozdíl je, že znaky kódování Unicode se může skládat ze dvou nebo více `Char` znaky (například náhradní pár nebo kombinování posloupnosti znaků).</span><span class="sxs-lookup"><span data-stu-id="c2044-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="c2044-108">Další informace najdete v tématu <xref:System.Globalization.TextElementEnumerator> a [standardu Unicode](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="c2044-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="c2044-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2044-109">Example</span></span>  
 <span data-ttu-id="c2044-110">Je obtížnější rozdělit řetězec na jeho textové znaky Unicode, ale to je nezbytné, pokud potřebujete informace o bude obsahovat vizuální reprezentaci řetězce.</span><span class="sxs-lookup"><span data-stu-id="c2044-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="c2044-111">V tomto příkladu <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodu k získání informací o textové znaky Unicode, které společně tvoří řetězec.</span><span class="sxs-lookup"><span data-stu-id="c2044-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c2044-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2044-112">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [<span data-ttu-id="c2044-113">Postupy: Přístup ke znakům v řetězcích</span><span class="sxs-lookup"><span data-stu-id="c2044-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [<span data-ttu-id="c2044-114">Převod mezi řetězci a ostatními datovými typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2044-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="c2044-115">Řetězce</span><span class="sxs-lookup"><span data-stu-id="c2044-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
