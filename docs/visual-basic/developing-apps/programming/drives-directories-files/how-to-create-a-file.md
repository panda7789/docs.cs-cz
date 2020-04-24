---
title: 'Postupy: Vytvoření souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 20533ec01d3198d499312ed0c15ec8cca2ff70bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348798"
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="1a78b-102">Postupy: Vytvoření souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a78b-102">How to: Create a File in Visual Basic</span></span>

<span data-ttu-id="1a78b-103">Tento příklad vytvoří prázdný textový soubor v zadané cestě pomocí <xref:System.IO.File.Create%2A> metody ve <xref:System.IO.File> třídě.</span><span class="sxs-lookup"><span data-stu-id="1a78b-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a78b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a78b-104">Example</span></span>  

 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1a78b-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1a78b-105">Compiling the Code</span></span>  

 <span data-ttu-id="1a78b-106">Použijte `file` proměnnou k zápisu do souboru.</span><span class="sxs-lookup"><span data-stu-id="1a78b-106">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1a78b-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1a78b-107">Robust Programming</span></span>  

 <span data-ttu-id="1a78b-108">Pokud soubor již existuje, je nahrazen.</span><span class="sxs-lookup"><span data-stu-id="1a78b-108">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="1a78b-109">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="1a78b-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="1a78b-110">Název cesty je poškozen.</span><span class="sxs-lookup"><span data-stu-id="1a78b-110">The path name is malformed.</span></span> <span data-ttu-id="1a78b-111">Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="1a78b-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="1a78b-112">Cesta je určena jen pro čtení (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="1a78b-112">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="1a78b-113">Název cesty je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="1a78b-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="1a78b-114">Název cesty je příliš dlouhý (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="1a78b-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="1a78b-115">Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="1a78b-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="1a78b-116">Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="1a78b-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1a78b-117">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1a78b-117">.NET Framework Security</span></span>  

 <span data-ttu-id="1a78b-118"><xref:System.Security.SecurityException> Může být vyvolána v prostředích s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="1a78b-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="1a78b-119">Volání <xref:System.IO.File.Create%2A> metody vyžaduje <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="1a78b-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="1a78b-120">Pokud <xref:System.UnauthorizedAccessException> uživatel nemá oprávnění k vytvoření souboru, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1a78b-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a78b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a78b-121">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [<span data-ttu-id="1a78b-122">Používání knihoven z částečně důvěryhodného kódu</span><span class="sxs-lookup"><span data-stu-id="1a78b-122">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [<span data-ttu-id="1a78b-123">Základy zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="1a78b-123">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
