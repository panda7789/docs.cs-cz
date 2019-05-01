---
title: 'Postupy: Vyhledávání v řetězci (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: b690aa78a2cf07b0db5bdd28d7d71ed4a79fbf61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032081"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="498a0-102">Postupy: Vyhledávání v řetězci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="498a0-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="498a0-103">Tento příklad příkladu volá <xref:System.String.IndexOf%2A> metoda <xref:System.String> objektu oznámit index prvního výskytu podřetězce.</span><span class="sxs-lookup"><span data-stu-id="498a0-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="498a0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="498a0-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="498a0-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="498a0-105">Compiling the Code</span></span>  
 <span data-ttu-id="498a0-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="498a0-106">This example requires:</span></span>  
  
- <span data-ttu-id="498a0-107">`Imports` Zadáním příkazu <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="498a0-107">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="498a0-108">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="498a0-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="498a0-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="498a0-109">Robust Programming</span></span>  
 <span data-ttu-id="498a0-110"><xref:System.String.IndexOf%2A> Metoda umístění prvního znaku prvního výskytu podřetězce sestav.</span><span class="sxs-lookup"><span data-stu-id="498a0-110">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="498a0-111">Index je založen na 0, což znamená, že první znak řetězce má index 0.</span><span class="sxs-lookup"><span data-stu-id="498a0-111">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="498a0-112">Pokud <xref:System.String.IndexOf%2A> nebyl nalezen dílčí řetězec, vrátí hodnotu -1.</span><span class="sxs-lookup"><span data-stu-id="498a0-112">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="498a0-113"><xref:System.String.IndexOf%2A> Metoda velká a malá písmena a použije aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="498a0-113">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="498a0-114">Pro řízení optimální chyb, můžete chtít uzavřít řetězec hledání v `Try` bloku [zkuste... Catch... Příkaz finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) konstrukce.</span><span class="sxs-lookup"><span data-stu-id="498a0-114">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="498a0-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="498a0-115">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="498a0-116">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="498a0-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="498a0-117">Úvod do řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="498a0-117">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="498a0-118">Řetězce</span><span class="sxs-lookup"><span data-stu-id="498a0-118">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
