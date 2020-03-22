---
title: 'Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: ee3951e967436a1b8aec09b8e42dc6d1b547bc02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348842"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="e1205-102">Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1205-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>

<span data-ttu-id="e1205-103">Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> vrátí kolekci řetězců jen pro čtení představující názvy cest pro soubory.</span><span class="sxs-lookup"><span data-stu-id="e1205-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="e1205-104">`wildCards` Parametr můžete použít k určení určitého vzoru.</span><span class="sxs-lookup"><span data-stu-id="e1205-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="e1205-105">Prázdná kolekce je vrácena, pokud nejsou nalezeny žádné odpovídající soubory.</span><span class="sxs-lookup"><span data-stu-id="e1205-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="e1205-106">Tuto metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> můžete použít ke kopírování souborů do adresáře.</span><span class="sxs-lookup"><span data-stu-id="e1205-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="e1205-107">Kopírování souborů s určitým vzorkem do adresáře</span><span class="sxs-lookup"><span data-stu-id="e1205-107">To copy files with a specific pattern to a directory</span></span>  
  
1. <span data-ttu-id="e1205-108">Pomocí `GetFiles` této metody vraťte seznam souborů.</span><span class="sxs-lookup"><span data-stu-id="e1205-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="e1205-109">Tento příklad vrátí všechny soubory RTF v zadaném adresáři.</span><span class="sxs-lookup"><span data-stu-id="e1205-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. <span data-ttu-id="e1205-110">Pomocí `CopyFile` metody zkopírujte soubory.</span><span class="sxs-lookup"><span data-stu-id="e1205-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="e1205-111">Tento příklad zkopíruje soubory `testdirectory`do adresáře s názvem .</span><span class="sxs-lookup"><span data-stu-id="e1205-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. <span data-ttu-id="e1205-112">Zavřete `For` příkaz `Next` příkazem.</span><span class="sxs-lookup"><span data-stu-id="e1205-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="e1205-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1205-113">Example</span></span>  

 <span data-ttu-id="e1205-114">Následující příklad, který představuje výše uvedené výstřižky v úplné podobě, zkopíruje všechny `testdirectory`soubory RTF v zadaném adresáři do adresáře s názvem .</span><span class="sxs-lookup"><span data-stu-id="e1205-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="e1205-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e1205-115">.NET Framework Security</span></span>  

 <span data-ttu-id="e1205-116">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="e1205-116">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="e1205-117">Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="e1205-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="e1205-118">Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).</span><span class="sxs-lookup"><span data-stu-id="e1205-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="e1205-119">Adresář neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="e1205-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="e1205-120">Adresář odkazuje na existující<xref:System.IO.IOException>soubor ( ).</span><span class="sxs-lookup"><span data-stu-id="e1205-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="e1205-121">Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).</span><span class="sxs-lookup"><span data-stu-id="e1205-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="e1205-122">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="e1205-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="e1205-123">Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).</span><span class="sxs-lookup"><span data-stu-id="e1205-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="e1205-124">Uživatel nemá potřebná<xref:System.UnauthorizedAccessException>oprávnění ( ).</span><span class="sxs-lookup"><span data-stu-id="e1205-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1205-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1205-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="e1205-126">Postupy: Hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="e1205-126">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="e1205-127">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="e1205-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="e1205-128">Postupy: Získání kolekce souborů z adresáře</span><span class="sxs-lookup"><span data-stu-id="e1205-128">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
