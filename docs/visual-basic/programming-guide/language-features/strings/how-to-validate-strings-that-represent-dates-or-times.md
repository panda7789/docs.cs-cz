---
title: 'Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic).'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 411c8517783421b2472c3e4aa77287f8252f179b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647859"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="b0111-102">Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b0111-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="b0111-103">Následující příklad kódu nastaví `Boolean` hodnotu, která určuje, zda řetězec reprezentuje platné datum nebo čas.</span><span class="sxs-lookup"><span data-stu-id="b0111-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0111-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0111-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b0111-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b0111-105">Compiling the Code</span></span>  
 <span data-ttu-id="b0111-106">Nahraďte `("01/01/03")` a `"9:30 PM"` s datum a čas, kterou chcete ověřit.</span><span class="sxs-lookup"><span data-stu-id="b0111-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="b0111-107">Je řetězec s jiným řetězcem pevně nahradit `String` proměnnou, nebo pomocí metody, vrátí řetězec, například `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="b0111-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b0111-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="b0111-108">Robust Programming</span></span>  
 <span data-ttu-id="b0111-109">Použít tuto metodu ověření než se pokusíte převést řetězec `String` k `DateTime` proměnné.</span><span class="sxs-lookup"><span data-stu-id="b0111-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="b0111-110">Nejdřív kontrolou datum nebo čas, se můžete vyhnout generování výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="b0111-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0111-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0111-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [<span data-ttu-id="b0111-112">Ověřování řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0111-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
