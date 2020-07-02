---
title: 'Postupy: Odstranění neplatných znaků z řetězce'
description: Přečtěte si příklad, který ukazuje, jak odstranit potenciálně škodlivé znaky z řetězce pomocí metody static Regex. Replace.
ms.date: 06/30/2020
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
ms.openlocfilehash: 5e0cd423df7fce03cdefb3da7bc192f3045e8f9c
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803986"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="8660f-103">Postupy: Odstranění neplatných znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="8660f-103">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="8660f-104">Následující příklad používá statickou <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metodu k odstranění neplatných znaků z řetězce.</span><span class="sxs-lookup"><span data-stu-id="8660f-104">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="8660f-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="8660f-105">Example</span></span>  
 <span data-ttu-id="8660f-106">`CleanInput`Metodu definovanou v tomto příkladu můžete použít k odstranění potenciálně škodlivých znaků, které byly zadány do textového pole, které přijímá vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="8660f-106">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="8660f-107">V tomto případě `CleanInput` vyčerpá všechny nealfanumerické znaky kromě teček (.), symbolů (@) a spojovníky (-) a vrátí zbývající řetězec.</span><span class="sxs-lookup"><span data-stu-id="8660f-107">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="8660f-108">Můžete však upravit vzor regulárního výrazu tak, aby vyčerpal všechny znaky, které by neměly být zahrnuty ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="8660f-108">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="8660f-109">Vzor regulárního výrazu `[^\w\.@-]` odpovídá jakémukoli znaku, který není znakem slova, tečku, symbolem @ nebo spojovníkem.</span><span class="sxs-lookup"><span data-stu-id="8660f-109">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="8660f-110">Znak slova je jakékoli písmeno, desítkovou číslici nebo konektor interpunkce, například podtržítko.</span><span class="sxs-lookup"><span data-stu-id="8660f-110">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="8660f-111">Libovolný znak, který odpovídá tomuto vzoru, je nahrazen <xref:System.String.Empty?displayProperty=nameWithType> řetězcem, což je řetězec definovaný vzorem pro nahrazení.</span><span class="sxs-lookup"><span data-stu-id="8660f-111">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="8660f-112">Chcete-li v uživatelském vstupu připustit další znaky, přidejte tyto znaky do třídy znaků ve vzoru regulárního výrazu.</span><span class="sxs-lookup"><span data-stu-id="8660f-112">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="8660f-113">Například vzor regulárního výrazu `[^\w\.@-\\%]` také umožňuje symbol procenta a zpětné lomítko ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="8660f-113">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8660f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8660f-114">See also</span></span>

- [<span data-ttu-id="8660f-115">Regulární výrazy .NET</span><span class="sxs-lookup"><span data-stu-id="8660f-115">.NET Regular Expressions</span></span>](regular-expressions.md)
