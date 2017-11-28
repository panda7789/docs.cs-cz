---
title: "Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed3201ef2bbef97eebbafa5ef128ca015adac013
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="34343-102">Postupy: Ověření řetězců, které představují data nebo časy (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="34343-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="34343-103">Následující příklad kódu nastaví `Boolean` hodnotu, která určuje, zda řetězec reprezentuje platné datum nebo čas.</span><span class="sxs-lookup"><span data-stu-id="34343-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34343-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="34343-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="34343-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="34343-105">Compiling the Code</span></span>  
 <span data-ttu-id="34343-106">Nahraďte `("01/01/03")` a `"9:30 PM"` s datum a čas, kterou chcete ověřit.</span><span class="sxs-lookup"><span data-stu-id="34343-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="34343-107">Je řetězec s jiným řetězcem pevně nahradit `String` proměnnou, nebo pomocí metody, vrátí řetězec, například `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="34343-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="34343-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="34343-108">Robust Programming</span></span>  
 <span data-ttu-id="34343-109">Použít tuto metodu ověření než se pokusíte převést řetězec `String` k `DateTime` proměnné.</span><span class="sxs-lookup"><span data-stu-id="34343-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="34343-110">Nejdřív kontrolou datum nebo čas, se můžete vyhnout generování výjimku za běhu.</span><span class="sxs-lookup"><span data-stu-id="34343-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34343-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="34343-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [<span data-ttu-id="34343-112">Ověřování řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34343-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
