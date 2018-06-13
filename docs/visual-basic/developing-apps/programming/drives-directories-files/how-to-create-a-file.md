---
title: 'Postupy: Vytvoření souboru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 6167ea0850308eec4b558a47dd881476325a8ea1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584843"
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="5b12a-102">Postupy: Vytvoření souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b12a-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="5b12a-103">Tento příklad vytvoří prázdný textový soubor v zadané cestě pomocí <xref:System.IO.File.Create%2A> metoda v <xref:System.IO.File> třídy.</span><span class="sxs-lookup"><span data-stu-id="5b12a-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b12a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b12a-104">Example</span></span>  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5b12a-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5b12a-105">Compiling the Code</span></span>  
 <span data-ttu-id="5b12a-106">Použití `file` proměnná k zápisu do souboru.</span><span class="sxs-lookup"><span data-stu-id="5b12a-106">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5b12a-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="5b12a-107">Robust Programming</span></span>  
 <span data-ttu-id="5b12a-108">Pokud soubor již existuje, je nahradit.</span><span class="sxs-lookup"><span data-stu-id="5b12a-108">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="5b12a-109">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="5b12a-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="5b12a-110">Název cesty je chybný.</span><span class="sxs-lookup"><span data-stu-id="5b12a-110">The path name is malformed.</span></span> <span data-ttu-id="5b12a-111">Například obsahuje neplatné znaky nebo je pouze mezera (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="5b12a-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="5b12a-112">Cesta je jen pro čtení (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5b12a-112">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="5b12a-113">Název cesty je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="5b12a-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="5b12a-114">Cesta je příliš dlouhý (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="5b12a-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="5b12a-115">Cesta je neplatná (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="5b12a-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="5b12a-116">Cesta je pouze dvojtečka ":" (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="5b12a-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5b12a-117">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5b12a-117">.NET Framework Security</span></span>  
 <span data-ttu-id="5b12a-118">A <xref:System.Security.SecurityException> může být vyvolána v prostředí s částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="5b12a-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="5b12a-119">Volání <xref:System.IO.File.Create%2A> metoda vyžaduje <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="5b12a-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="5b12a-120"><xref:System.UnauthorizedAccessException> Je vyvolána, pokud uživatel nemá oprávnění k vytvoření souboru.</span><span class="sxs-lookup"><span data-stu-id="5b12a-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b12a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b12a-121">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.IO.File.Create%2A>  
 [<span data-ttu-id="5b12a-122">Používání knihoven z částečně důvěryhodného kódu</span><span class="sxs-lookup"><span data-stu-id="5b12a-122">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)  
 [<span data-ttu-id="5b12a-123">Základy zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="5b12a-123">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
