---
title: 'Postupy: Ověření řetězců, které představují data nebo časy.'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5d153ac29039375386b3cd5f03609b1e4bd1d5bf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410564"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="267f4-102">Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="267f4-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="267f4-103">Následující příklad kódu nastaví `Boolean` hodnotu, která označuje, zda řetězec představuje platné datum nebo čas.</span><span class="sxs-lookup"><span data-stu-id="267f4-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="267f4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="267f4-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="267f4-105">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="267f4-105">Compile the code</span></span>  
 <span data-ttu-id="267f4-106">Nahraďte `("01/01/03")` a `"9:30 PM"` datem a časem, který chcete ověřit.</span><span class="sxs-lookup"><span data-stu-id="267f4-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="267f4-107">Řetězec lze nahradit jiným pevně zakódovaným řetězcem s `String` proměnnou nebo s metodou, která vrací řetězec, například `InputBox` .</span><span class="sxs-lookup"><span data-stu-id="267f4-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="267f4-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="267f4-108">Robust Programming</span></span>  
 <span data-ttu-id="267f4-109">Tuto metodu použijte k ověření řetězce před pokusem o převod na `String` `DateTime` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="267f4-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="267f4-110">Kontrolou prvního data nebo času se můžete vyhnout generování výjimky v době běhu.</span><span class="sxs-lookup"><span data-stu-id="267f4-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="267f4-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="267f4-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="267f4-112">Ověřování řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="267f4-112">Validating Strings in Visual Basic</span></span>](validating-strings.md)
