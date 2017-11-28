---
title: "Postupy: Převod řetězce na pole znaků v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59d0da52c8f78b93c76325e6242156c106deeaf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="7c247-102">Postupy: Převod řetězce na pole znaků v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7c247-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="7c247-103">Někdy je užitečné používat data o znaky v řetězec vašeho a pozice z těchto znaků v řetězci, například když analyzujete řetězec.</span><span class="sxs-lookup"><span data-stu-id="7c247-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="7c247-104">Tento příklad ukazuje, jak můžete získat pole znaky v řetězci voláním řetězec <xref:System.String.ToCharArray%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="7c247-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c247-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c247-105">Example</span></span>  
 <span data-ttu-id="7c247-106">Tento příklad ukazuje, jak rozdělit řetězec do `Char` pole a jak rozdělit řetězec do `String` pole jeho textových znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="7c247-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="7c247-107">Důvody, proč tento rozdíl je, že znaky znakové sady Unicode text může skládat ze dvou nebo více `Char` znaků (například náhradní pár nebo kombinování sekvenci znaků).</span><span class="sxs-lookup"><span data-stu-id="7c247-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="7c247-108">Další informace najdete v tématu <xref:System.Globalization.TextElementEnumerator> a "Ve standardu Unicode" na http://www.unicode.org.</span><span class="sxs-lookup"><span data-stu-id="7c247-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and "The Unicode Standard" at http://www.unicode.org.</span></span>  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="7c247-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c247-109">Example</span></span>  
 <span data-ttu-id="7c247-110">Je obtížné rozdělit řetězec na jeho text znaky znakové sady Unicode, ale to je nezbytné, pokud potřebujete informace o vizuální reprezentace řetězec.</span><span class="sxs-lookup"><span data-stu-id="7c247-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="7c247-111">Tento příklad používá <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> metodu za účelem získání informací o textových znaků Unicode, které tvoří řetězec.</span><span class="sxs-lookup"><span data-stu-id="7c247-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7c247-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c247-112">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [<span data-ttu-id="7c247-113">Postupy: přístup ke znakům v řetězcích</span><span class="sxs-lookup"><span data-stu-id="7c247-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [<span data-ttu-id="7c247-114">Převod mezi řetězci a ostatními typy dat v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7c247-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="7c247-115">Řetězce</span><span class="sxs-lookup"><span data-stu-id="7c247-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
