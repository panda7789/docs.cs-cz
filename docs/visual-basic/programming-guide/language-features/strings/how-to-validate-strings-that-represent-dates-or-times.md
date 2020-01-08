---
title: 'Postupy: Ověření řetězců, které představují data nebo časy.'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5321e7a85c45ddb6ce17433bd25ce9ca2165f0a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348405"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="70cfa-102">Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="70cfa-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="70cfa-103">Následující příklad kódu nastaví `Boolean` hodnotu, která označuje, zda řetězec představuje platné datum nebo čas.</span><span class="sxs-lookup"><span data-stu-id="70cfa-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70cfa-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="70cfa-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="70cfa-105">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="70cfa-105">Compile the code</span></span>  
 <span data-ttu-id="70cfa-106">Nahraďte `("01/01/03")` a `"9:30 PM"` datem a časem, který chcete ověřit.</span><span class="sxs-lookup"><span data-stu-id="70cfa-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="70cfa-107">Řetězec lze nahradit jiným pevně zakódovaným řetězcem s `String` proměnnou nebo metodou, která vrací řetězec, například `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="70cfa-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="70cfa-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="70cfa-108">Robust Programming</span></span>  
 <span data-ttu-id="70cfa-109">Tuto metodu použijte, chcete-li před pokusem o převedení `String` na `DateTime` proměnnou ověřit řetězec.</span><span class="sxs-lookup"><span data-stu-id="70cfa-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="70cfa-110">Kontrolou prvního data nebo času se můžete vyhnout generování výjimky v době běhu.</span><span class="sxs-lookup"><span data-stu-id="70cfa-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70cfa-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70cfa-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="70cfa-112">Ověřování řetězců v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70cfa-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
