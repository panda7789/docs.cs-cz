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
ms.openlocfilehash: eca8cd7be8da1f6149dadf1e9edeab5e5225ab9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360667"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="c352b-102">Postupy: Převod řetězce na pole znaků v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c352b-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="c352b-103">Někdy je užitečné mít data o znacích v řetězci a umístění těchto znaků v rámci řetězce, například při analýze řetězce.</span><span class="sxs-lookup"><span data-stu-id="c352b-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="c352b-104">Tento příklad ukazuje, jak lze získat pole znaků v řetězci voláním <xref:System.String.ToCharArray%2A> metody řetězce.</span><span class="sxs-lookup"><span data-stu-id="c352b-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c352b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c352b-105">Example</span></span>  
 <span data-ttu-id="c352b-106">Tento příklad ukazuje, jak rozdělit řetězec do `Char` pole a jak rozdělit řetězec do `String` pole textových znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="c352b-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="c352b-107">Důvodem pro tento rozdíl je, že textové znaky Unicode mohou být složeny ze dvou nebo více `Char` znaků (například náhradní dvojice nebo kombinování znakových sekvencí).</span><span class="sxs-lookup"><span data-stu-id="c352b-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="c352b-108">Další informace najdete v tématu <xref:System.Globalization.TextElementEnumerator> a [standardu Unicode](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="c352b-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a><span data-ttu-id="c352b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c352b-109">Example</span></span>  
 <span data-ttu-id="c352b-110">Je obtížnější rozdělit řetězec na své textové znaky Unicode, ale to je nezbytné, pokud potřebujete informace o vizuálním znázornění řetězce.</span><span class="sxs-lookup"><span data-stu-id="c352b-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="c352b-111">Tento příklad používá <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodu k získání informací o textových znacích Unicode, které tvoří řetězec.</span><span class="sxs-lookup"><span data-stu-id="c352b-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a><span data-ttu-id="c352b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c352b-112">See also</span></span>

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [<span data-ttu-id="c352b-113">Postupy: Přístup ke znakům v řetězcích</span><span class="sxs-lookup"><span data-stu-id="c352b-113">How to: Access Characters in Strings</span></span>](how-to-access-characters-in-strings.md)
- [<span data-ttu-id="c352b-114">Převod mezi řetězci a ostatními datovými typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c352b-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="c352b-115">Řetězce</span><span class="sxs-lookup"><span data-stu-id="c352b-115">Strings</span></span>](index.md)
