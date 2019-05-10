---
title: 'Postupy: Vyhledávání v řetězci (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 57a3d9650ad78e1c8580fd46839c9a1cbc7794c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665344"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="1db0e-102">Postupy: Vyhledávání v řetězci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1db0e-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="1db0e-103">Tento příklad příkladu volá <xref:System.String.IndexOf%2A> metoda <xref:System.String> objektu oznámit index prvního výskytu podřetězce.</span><span class="sxs-lookup"><span data-stu-id="1db0e-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1db0e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1db0e-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1db0e-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1db0e-105">Compiling the Code</span></span>  
 <span data-ttu-id="1db0e-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1db0e-106">This example requires:</span></span>  
  
- <span data-ttu-id="1db0e-107">`Imports` Zadáním příkazu <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1db0e-107">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="1db0e-108">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="1db0e-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1db0e-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1db0e-109">Robust Programming</span></span>  
 <span data-ttu-id="1db0e-110"><xref:System.String.IndexOf%2A> Metoda umístění prvního znaku prvního výskytu podřetězce sestav.</span><span class="sxs-lookup"><span data-stu-id="1db0e-110">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="1db0e-111">Index je založen na 0, což znamená, že první znak řetězce má index 0.</span><span class="sxs-lookup"><span data-stu-id="1db0e-111">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="1db0e-112">Pokud <xref:System.String.IndexOf%2A> nebyl nalezen dílčí řetězec, vrátí hodnotu -1.</span><span class="sxs-lookup"><span data-stu-id="1db0e-112">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="1db0e-113"><xref:System.String.IndexOf%2A> Metoda velká a malá písmena a použije aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="1db0e-113">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="1db0e-114">Pro řízení optimální chyb, můžete chtít uzavřít řetězec hledání v `Try` bloku [zkuste... Catch... Příkaz finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) konstrukce.</span><span class="sxs-lookup"><span data-stu-id="1db0e-114">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db0e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1db0e-115">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="1db0e-116">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="1db0e-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="1db0e-117">Úvod do řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1db0e-117">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="1db0e-118">Řetězce</span><span class="sxs-lookup"><span data-stu-id="1db0e-118">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
