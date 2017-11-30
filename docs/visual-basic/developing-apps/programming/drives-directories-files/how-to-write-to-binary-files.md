---
title: "Postupy: Zápis do binárních souborů v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4d8f908822dbcb865f427bee082b8bc4e22ca7fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="0848f-102">Postupy: Zápis do binárních souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0848f-102">How to: Write to Binary Files in Visual Basic</span></span>
<span data-ttu-id="0848f-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> Metoda zapisuje data do binárního souboru.</span><span class="sxs-lookup"><span data-stu-id="0848f-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="0848f-104">Pokud `append` parametr `True`, připojí data k souboru; v opačném případě se data v souboru přepíše.</span><span class="sxs-lookup"><span data-stu-id="0848f-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>  
  
 <span data-ttu-id="0848f-105">Pokud zadaná cesta není platná, <xref:System.IO.DirectoryNotFoundException> dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="0848f-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="0848f-106">Pokud je cesta platná, ale soubor neexistuje, vytvoří se soubor.</span><span class="sxs-lookup"><span data-stu-id="0848f-106">If the path is valid but the file does not exist, the file will be created.</span></span>  
  
### <a name="to-write-to-a-binary-file"></a><span data-ttu-id="0848f-107">Zápis do binárního souboru</span><span class="sxs-lookup"><span data-stu-id="0848f-107">To write to a binary file</span></span>  
  
-   <span data-ttu-id="0848f-108">Použití `WriteAllBytes` metodu cesta k souboru, název a bajtů, které mají být zapsána.</span><span class="sxs-lookup"><span data-stu-id="0848f-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="0848f-109">Tento příklad přidáno pole data `CustomerData` do souboru s názvem `CollectedData.dat`.</span><span class="sxs-lookup"><span data-stu-id="0848f-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0848f-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="0848f-110">Robust Programming</span></span>  
 <span data-ttu-id="0848f-111">Následujících podmínek může vytvořit výjimku:</span><span class="sxs-lookup"><span data-stu-id="0848f-111">The following conditions may create an exception:</span></span>  
  
-   <span data-ttu-id="0848f-112">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky; obsahuje jenom prázdné znaky; nebo obsahuje neplatné znaky.</span><span class="sxs-lookup"><span data-stu-id="0848f-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="0848f-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0848f-113">(<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="0848f-114">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="0848f-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="0848f-115">`File`odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="0848f-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="0848f-116">Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupní operace (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="0848f-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="0848f-117">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="0848f-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="0848f-118">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="0848f-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="0848f-119">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0848f-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0848f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="0848f-120">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>  
 [<span data-ttu-id="0848f-121">Postupy: zápis textu do souborů</span><span class="sxs-lookup"><span data-stu-id="0848f-121">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
