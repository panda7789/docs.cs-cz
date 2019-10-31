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
ms.openlocfilehash: cc90e6609f9335b7e2f08271e5540b182901e8c9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127656"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="bcaf3-102">Postupy: Odstranění neplatných znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="bcaf3-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="bcaf3-103">Následující příklad používá metodu static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> k odstranění neplatných znaků z řetězce.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcaf3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcaf3-104">Example</span></span>  
 <span data-ttu-id="bcaf3-105">Metodu `CleanInput` definovanou v tomto příkladu můžete použít k odstranění potenciálně škodlivých znaků, které byly zadány do textového pole, které přijímá vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="bcaf3-106">V tomto případě `CleanInput` vydělení všech nealfanumerických znaků s výjimkou teček (.), symbolem (@) a spojovníky (-) a vrátí zbývající řetězec.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="bcaf3-107">Můžete však upravit vzor regulárního výrazu tak, aby vyčerpal všechny znaky, které by neměly být zahrnuty ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="bcaf3-108">Vzor regulárního výrazu `[^\w\.@-]` odpovídá jakémukoli znaku, který není znakem slova, tečku, symbolem @ nebo spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="bcaf3-109">Znak slova je jakékoli písmeno, desítkovou číslici nebo konektor interpunkce, například podtržítko.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="bcaf3-110">Libovolný znak, který odpovídá tomuto vzoru, je nahrazen <xref:System.String.Empty?displayProperty=nameWithType>, což je řetězec definovaný vzorem pro nahrazení.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="bcaf3-111">Chcete-li v uživatelském vstupu připustit další znaky, přidejte tyto znaky do třídy znaků ve vzoru regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="bcaf3-112">Například vzor regulárního výrazu `[^\w\.@-\\%]` také umožňuje ve vstupním řetězci symbol procenta a zpětné lomítko.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcaf3-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcaf3-113">See also</span></span>

- [<span data-ttu-id="bcaf3-114">Regulární výrazy .NET</span><span class="sxs-lookup"><span data-stu-id="bcaf3-114">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
