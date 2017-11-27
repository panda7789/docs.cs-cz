---
title: "Postupy: Vyhledávání v řetězci (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c828d0b32fdf90e121e9d5da0bb60ab11c212f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="06304-102">Postupy: Vyhledávání v řetězci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06304-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="06304-103">Tento příklad volá <xref:System.String.IndexOf%2A> metodu <xref:System.String> objekt, který chcete nahlásit index prvního výskytu dílčí řetězec.</span><span class="sxs-lookup"><span data-stu-id="06304-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06304-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="06304-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="06304-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="06304-105">Compiling the Code</span></span>  
 <span data-ttu-id="06304-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="06304-106">This example requires:</span></span>  
  
-   <span data-ttu-id="06304-107">`Imports` Zadáním příkazu <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="06304-107">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="06304-108">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="06304-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="06304-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="06304-109">Robust Programming</span></span>  
 <span data-ttu-id="06304-110"><xref:System.String.IndexOf%2A> Metoda sestavy umístění první znak první výskyt dílčí řetězec.</span><span class="sxs-lookup"><span data-stu-id="06304-110">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="06304-111">Index je založen na 0, což znamená, že první znak řetězec má index 0.</span><span class="sxs-lookup"><span data-stu-id="06304-111">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="06304-112">Pokud <xref:System.String.IndexOf%2A> nebyl nalezen dílčí řetězec, vrátí hodnotu -1.</span><span class="sxs-lookup"><span data-stu-id="06304-112">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="06304-113"><xref:System.String.IndexOf%2A> Metoda je malá a velká písmena a používá aktuální jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="06304-113">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="06304-114">Pro optimální chyby řízení, můžete chtít uzavřete řetězec hledání v `Try` blokovat z [zkuste... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) konstrukce.</span><span class="sxs-lookup"><span data-stu-id="06304-114">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06304-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="06304-115">See Also</span></span>  
 <xref:System.String.IndexOf%2A>  
 [<span data-ttu-id="06304-116">Try... Catch... Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="06304-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="06304-117">Představení řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06304-117">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [<span data-ttu-id="06304-118">Řetězce</span><span class="sxs-lookup"><span data-stu-id="06304-118">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
