---
title: "Postupy: Zápis textu do souborů v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4fbbe0ec007911460dc2bda8c681775da9a6cb91
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="c3dd2-102">Postupy: Zápis textu do souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3dd2-102">How to: Write Text to Files in Visual Basic</span></span>
<span data-ttu-id="c3dd2-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metoda slouží k zapsání textu do souborů.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="c3dd2-104">Pokud zadaný soubor neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="c3dd2-105">Postup</span><span class="sxs-lookup"><span data-stu-id="c3dd2-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="c3dd2-106">Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="c3dd2-106">To write text to a file</span></span>  
  
-   <span data-ttu-id="c3dd2-107">Použití `WriteAllText` metodu pro zápis textu do souboru, soubor a text, který má být zapsána.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="c3dd2-108">V tomto příkladu je zapsán řádek `"This is new text."` do souboru s názvem `test.txt`, přidání textu k existujícího textu v souboru.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="c3dd2-109">Pro zápis do souboru řad řetězců</span><span class="sxs-lookup"><span data-stu-id="c3dd2-109">To write a series of strings to a file</span></span>  
  
-   <span data-ttu-id="c3dd2-110">Projděte kolekci řetězec.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-110">Loop through the string collection.</span></span> <span data-ttu-id="c3dd2-111">Použití `WriteAllText` metodu pro zápis textu do souboru, cílový soubor a řetězec, který má být přidán a nastavení `append` k `True`.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="c3dd2-112">Zapíše názvy souborů v tomto příkladu `Documents and Settings` do adresáře `FileList.txt`, vkládání znaků CR vrátit mezi jednotlivými pro lepší čitelnost.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c3dd2-113">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c3dd2-113">Robust Programming</span></span>  
 <span data-ttu-id="c3dd2-114">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="c3dd2-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c3dd2-115">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="c3dd2-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="c3dd2-116">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="c3dd2-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="c3dd2-117">`File`odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="c3dd2-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="c3dd2-118">Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupní operace (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="c3dd2-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="c3dd2-119">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="c3dd2-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="c3dd2-120">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="c3dd2-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="c3dd2-121">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="c3dd2-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="c3dd2-122">Disk je plný a volání `WriteAllText` selže (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="c3dd2-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="c3dd2-123">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, kód může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c3dd2-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="c3dd2-124">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="c3dd2-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3dd2-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3dd2-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 [<span data-ttu-id="c3dd2-126">Postupy: čtení z textových souborů</span><span class="sxs-lookup"><span data-stu-id="c3dd2-126">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
