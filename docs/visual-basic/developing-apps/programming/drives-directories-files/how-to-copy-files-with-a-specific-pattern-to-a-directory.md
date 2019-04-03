---
title: 'Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 184742ef03343eaff644c0f3f803e2acec8854eb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837101"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="bb950-102">Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb950-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>
<span data-ttu-id="bb950-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda vrátí kolekci řetězců, které představují názvy cest souborů jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="bb950-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="bb950-104">Můžete použít `wildCards` parametr k určení určitému vzoru.</span><span class="sxs-lookup"><span data-stu-id="bb950-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="bb950-105">Prázdná kolekce je vrácena, pokud nejsou nalezeny žádné odpovídající soubory.</span><span class="sxs-lookup"><span data-stu-id="bb950-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="bb950-106">Můžete použít <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> metoda kopírování souborů do jiného adresáře.</span><span class="sxs-lookup"><span data-stu-id="bb950-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="bb950-107">Pro kopírování souborů vyhovujících určitému vzoru do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="bb950-107">To copy files with a specific pattern to a directory</span></span>  
  
1.  <span data-ttu-id="bb950-108">Použití `GetFiles` metody, která vrátí seznam souborů.</span><span class="sxs-lookup"><span data-stu-id="bb950-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="bb950-109">V tomto příkladu vrátí všechny soubory ve formátu RTF v zadaném adresáři.</span><span class="sxs-lookup"><span data-stu-id="bb950-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2.  <span data-ttu-id="bb950-110">Použití `CopyFile` metoda kopírování souborů.</span><span class="sxs-lookup"><span data-stu-id="bb950-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="bb950-111">Tento příklad zkopíruje soubory do adresáře s názvem `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="bb950-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3.  <span data-ttu-id="bb950-112">Zavřít `For` příkazem `Next` příkazu.</span><span class="sxs-lookup"><span data-stu-id="bb950-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="bb950-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb950-113">Example</span></span>  
 <span data-ttu-id="bb950-114">Následujícím příkladu, který představuje výše uvedené fragmenty kódu v celý formulář, zkopíruje všechny soubory ve formátu RTF v zadaném adresáři k adresáři s názvem `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="bb950-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="bb950-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bb950-115">.NET Framework Security</span></span>  
 <span data-ttu-id="bb950-116">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="bb950-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="bb950-117">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="bb950-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="bb950-118">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="bb950-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="bb950-119">Adresáři neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="bb950-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="bb950-120">Adresář odkazuje na existující soubor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="bb950-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="bb950-121">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="bb950-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="bb950-122">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="bb950-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="bb950-123">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="bb950-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="bb950-124">Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="bb950-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb950-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb950-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="bb950-126">Postupy: Hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="bb950-126">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="bb950-127">Řešení potíží: Čtení a zápis do textových souborů</span><span class="sxs-lookup"><span data-stu-id="bb950-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="bb950-128">Postupy: Získání kolekce souborů v adresáři</span><span class="sxs-lookup"><span data-stu-id="bb950-128">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
