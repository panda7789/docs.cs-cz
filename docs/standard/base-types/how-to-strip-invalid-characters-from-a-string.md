---
title: 'Postupy: Odstranění neplatných znaků z řetězce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3bbd25e40607bd316f1bbab974174fe5433770f
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44510753"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="76aaa-102">Postupy: Odstranění neplatných znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="76aaa-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="76aaa-103">Následující příklad používá statickou <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodu k odstranění neplatných znaků z řetězce.</span><span class="sxs-lookup"><span data-stu-id="76aaa-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76aaa-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="76aaa-104">Example</span></span>  
 <span data-ttu-id="76aaa-105">Můžete použít `CleanInput` metody definované v tomto příkladu pro odstranění potenciálně nebezpečné znaky zadané do textového pole, která přijímá vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="76aaa-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="76aaa-106">V takovém případě `CleanInput` odstraní všechny nealfanumerické znaky s výjimkou tečky (.), symbolů (@), spojovníky (-) a vrátí zbývající řetězec.</span><span class="sxs-lookup"><span data-stu-id="76aaa-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="76aaa-107">Vzor regulárního výrazu, ale můžete upravit tak, aby se odstraní všechny znaky, které by neměly být obsažené ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="76aaa-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="76aaa-108">Vzor regulárního výrazu `[^\w\.@-]` odpovídá jakémukoli znaku, který není znakem slova, tečky, symbolu @ nebo pomlčkou.</span><span class="sxs-lookup"><span data-stu-id="76aaa-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="76aaa-109">Znak slova je libovolný písmeno, desítková číslice nebo interpunkční znaménka konektoru, jako je například podtržítko.</span><span class="sxs-lookup"><span data-stu-id="76aaa-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="76aaa-110">Libovolný znak, který odpovídá tomuto vzoru nahrazuje <xref:System.String.Empty?displayProperty=nameWithType>, což je řetězec určené vzor pro nahrazení.</span><span class="sxs-lookup"><span data-stu-id="76aaa-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="76aaa-111">Povolit další znaky ve vstupu uživatele, přidejte do třídy znak ve vzorku regulárního výrazu znaky.</span><span class="sxs-lookup"><span data-stu-id="76aaa-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="76aaa-112">Například vzor regulárního výrazu `[^\w\.@-\\%]` také umožňuje symbol procenta a zpětné lomítko ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="76aaa-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76aaa-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76aaa-113">See also</span></span>

- [<span data-ttu-id="76aaa-114">Regulárních výrazů .NET</span><span class="sxs-lookup"><span data-stu-id="76aaa-114">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
