---
title: 'Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 7e263e2c9035db54dbb58c6c78c0647d5442504e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401703"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="b1c67-102">Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1c67-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>

<span data-ttu-id="b1c67-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>Metoda vrátí kolekci řetězců jen pro čtení, které představují názvy cest pro soubory.</span><span class="sxs-lookup"><span data-stu-id="b1c67-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="b1c67-104">`wildCards`K určení konkrétního vzoru můžete použít parametr.</span><span class="sxs-lookup"><span data-stu-id="b1c67-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="b1c67-105">Je-li nalezena žádná vyhovující soubory, je vrácena prázdná kolekce.</span><span class="sxs-lookup"><span data-stu-id="b1c67-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="b1c67-106">Můžete použít <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> metodu ke zkopírování souborů do adresáře.</span><span class="sxs-lookup"><span data-stu-id="b1c67-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="b1c67-107">Kopírování souborů s určitým vzorem do adresáře</span><span class="sxs-lookup"><span data-stu-id="b1c67-107">To copy files with a specific pattern to a directory</span></span>  
  
1. <span data-ttu-id="b1c67-108">`GetFiles`K vrácení seznamu souborů použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="b1c67-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="b1c67-109">Tento příklad vrátí všechny soubory. RTF v zadaném adresáři.</span><span class="sxs-lookup"><span data-stu-id="b1c67-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. <span data-ttu-id="b1c67-110">`CopyFile`K kopírování souborů použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="b1c67-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="b1c67-111">V tomto příkladu se zkopírují soubory do adresáře s názvem `testdirectory` .</span><span class="sxs-lookup"><span data-stu-id="b1c67-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. <span data-ttu-id="b1c67-112">Uzavřete `For` příkaz s `Next` příkazem.</span><span class="sxs-lookup"><span data-stu-id="b1c67-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="b1c67-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1c67-113">Example</span></span>  

 <span data-ttu-id="b1c67-114">Následující příklad, který prezentuje výše uvedené fragmenty kódu v úplné podobě, zkopíruje všechny soubory. RTF v zadaném adresáři do adresáře s názvem `testdirectory` .</span><span class="sxs-lookup"><span data-stu-id="b1c67-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="b1c67-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b1c67-115">.NET Framework Security</span></span>  

 <span data-ttu-id="b1c67-116">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="b1c67-116">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b1c67-117">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b1c67-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="b1c67-118">Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="b1c67-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="b1c67-119">Adresář neexistuje ( <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="b1c67-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="b1c67-120">Adresář odkazuje na existující soubor ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="b1c67-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="b1c67-121">Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .</span><span class="sxs-lookup"><span data-stu-id="b1c67-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="b1c67-122">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="b1c67-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="b1c67-123">Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="b1c67-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="b1c67-124">Uživatel nemá potřebná oprávnění ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="b1c67-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c67-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1c67-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="b1c67-126">Postupy: Hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="b1c67-126">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="b1c67-127">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="b1c67-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="b1c67-128">Postupy: Získání kolekce souborů z adresáře</span><span class="sxs-lookup"><span data-stu-id="b1c67-128">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
