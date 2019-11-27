---
title: 'Postupy: Převod řetězce na pole znaků'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: d2f7128f97e576d37216d3aa9736921f13f77004
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352450"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="81a86-102">Postupy: Převod řetězce na pole znaků v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81a86-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="81a86-103">Někdy je užitečné mít data o znacích v řetězci a umístění těchto znaků v rámci řetězce, například při analýze řetězce.</span><span class="sxs-lookup"><span data-stu-id="81a86-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="81a86-104">Tento příklad ukazuje, jak lze získat pole znaků v řetězci voláním metody <xref:System.String.ToCharArray%2A> řetězce.</span><span class="sxs-lookup"><span data-stu-id="81a86-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81a86-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="81a86-105">Example</span></span>  
 <span data-ttu-id="81a86-106">Tento příklad ukazuje, jak rozdělit řetězec do `Char` pole a jak rozdělit řetězec do `String` pole textových znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="81a86-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="81a86-107">Důvodem pro tento rozdíl je, že textové znaky Unicode mohou být složeny ze dvou nebo více `Char`ch znaků (například náhradní pár nebo kombinace znakových sekvencí).</span><span class="sxs-lookup"><span data-stu-id="81a86-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="81a86-108">Další informace najdete v tématu <xref:System.Globalization.TextElementEnumerator> a [standardu Unicode](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="81a86-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a><span data-ttu-id="81a86-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="81a86-109">Example</span></span>  
 <span data-ttu-id="81a86-110">Je obtížnější rozdělit řetězec na své textové znaky Unicode, ale to je nezbytné, pokud potřebujete informace o vizuálním znázornění řetězce.</span><span class="sxs-lookup"><span data-stu-id="81a86-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="81a86-111">Tento příklad používá metodu <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> k získání informací o textových znacích Unicode, které tvoří řetězec.</span><span class="sxs-lookup"><span data-stu-id="81a86-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a><span data-ttu-id="81a86-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81a86-112">See also</span></span>

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [<span data-ttu-id="81a86-113">Postupy: Přístup ke znakům v řetězcích</span><span class="sxs-lookup"><span data-stu-id="81a86-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [<span data-ttu-id="81a86-114">Převod mezi řetězci a ostatními datovými typy v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81a86-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="81a86-115">Řetězce</span><span class="sxs-lookup"><span data-stu-id="81a86-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
