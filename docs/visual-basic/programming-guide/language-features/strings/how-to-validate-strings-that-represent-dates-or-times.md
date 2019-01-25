---
title: 'Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 1a838d9d156ad9c05a70a4d4d72db1a288731c9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685396"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="aa5bd-102">Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa5bd-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="aa5bd-103">Následující příklad kódu nastaví `Boolean` hodnotu, která určuje, zda řetězec reprezentuje platné datum nebo čas.</span><span class="sxs-lookup"><span data-stu-id="aa5bd-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa5bd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa5bd-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aa5bd-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="aa5bd-105">Compiling the Code</span></span>  
 <span data-ttu-id="aa5bd-106">Nahraďte `("01/01/03")` a `"9:30 PM"` s datem a časem, kterou chcete ověřit.</span><span class="sxs-lookup"><span data-stu-id="aa5bd-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="aa5bd-107">Můžete nahradit řetězce jiným řetězcem pevně zakódované `String` proměnných, nebo s metodou, která vrátí řetězec, například `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="aa5bd-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="aa5bd-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="aa5bd-108">Robust Programming</span></span>  
 <span data-ttu-id="aa5bd-109">Tuto metodu použijte k ověření před pokusem o převod řetězce `String` k `DateTime` proměnné.</span><span class="sxs-lookup"><span data-stu-id="aa5bd-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="aa5bd-110">Nejprve zkontrolovat datum nebo čas, byste se vyhnout generuje výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="aa5bd-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa5bd-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa5bd-111">See also</span></span>
- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="aa5bd-112">Ověřování řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa5bd-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
