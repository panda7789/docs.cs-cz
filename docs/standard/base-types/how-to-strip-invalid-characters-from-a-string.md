---
title: "Postupy: Odstranění neplatných znaků z řetězce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f676ca9121498da7c88cdec8b49586bde91b181
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="990cc-102">Postupy: Odstranění neplatných znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="990cc-102">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="990cc-103">Následující příklad používá statické <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> metoda pro odstranění neplatných znaků z řetězce.</span><span class="sxs-lookup"><span data-stu-id="990cc-103">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="990cc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="990cc-104">Example</span></span>  
 <span data-ttu-id="990cc-105">Můžete použít `CleanInput` metoda definované v tomto příkladu pro odstranění potenciálně škodlivých znaků, které byly zadány do textového pole, které přijímá vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="990cc-105">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="990cc-106">V takovém případě `CleanInput` odstraní všechny nealfanumerické znaky s výjimkou tečky (.) a symboly (@), pomlčky (-) a vrátí zbývající řetězec.</span><span class="sxs-lookup"><span data-stu-id="990cc-106">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="990cc-107">Regulární výraz však můžete upravit tak, aby se odstraní všechny znaky, které by neměly být obsažené ve vstupní řetězec.</span><span class="sxs-lookup"><span data-stu-id="990cc-107">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="990cc-108">Regulární výraz `[^\w\.@-]` odpovídá jakémukoliv znaku, který není písmenem, tečky, @ symbol nebo pomlčky.</span><span class="sxs-lookup"><span data-stu-id="990cc-108">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="990cc-109">Jakékoli písmeno, číslici desítkové soustavy nebo interpunkce konektoru třeba podtržítko je znak aplikace word.</span><span class="sxs-lookup"><span data-stu-id="990cc-109">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="990cc-110">Libovolný znak, který odpovídá tomuto vzoru nahrazuje <xref:System.String.Empty?displayProperty=nameWithType>, což je řetězec definované vzor nahrazení.</span><span class="sxs-lookup"><span data-stu-id="990cc-110">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="990cc-111">Povolit další znaky ve vstupu uživatele, přidejte do třídy znaků v regulární výraz tyto znaky.</span><span class="sxs-lookup"><span data-stu-id="990cc-111">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="990cc-112">Například vzor regulárního výrazu `[^\w\.@-\\%]` také umožňuje symbol procenta a zpětné lomítko ve vstupním řetězci.</span><span class="sxs-lookup"><span data-stu-id="990cc-112">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="990cc-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="990cc-113">See Also</span></span>  
 [<span data-ttu-id="990cc-114">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="990cc-114">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
