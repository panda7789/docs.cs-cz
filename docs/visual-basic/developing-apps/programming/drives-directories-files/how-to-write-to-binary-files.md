---
title: 'Postupy: Zápis do binárních souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: b36da82060b930101cb54dd852d050ac0155bd10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411548"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="06c4c-102">Postupy: Zápis do binárních souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06c4c-102">How to: Write to Binary Files in Visual Basic</span></span>

<span data-ttu-id="06c4c-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>Metoda zapisuje data do binárního souboru.</span><span class="sxs-lookup"><span data-stu-id="06c4c-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="06c4c-104">Pokud `append` je parametr `True` , připojí data do souboru; v opačném případě se data v souboru přepíše.</span><span class="sxs-lookup"><span data-stu-id="06c4c-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>

<span data-ttu-id="06c4c-105">Pokud zadaná cesta s výjimkou názvu souboru není platná, <xref:System.IO.DirectoryNotFoundException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="06c4c-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="06c4c-106">Pokud je cesta platná, ale soubor neexistuje, vytvoří se soubor.</span><span class="sxs-lookup"><span data-stu-id="06c4c-106">If the path is valid but the file does not exist, the file will be created.</span></span>

## <a name="to-write-to-a-binary-file"></a><span data-ttu-id="06c4c-107">Zápis do binárního souboru</span><span class="sxs-lookup"><span data-stu-id="06c4c-107">To write to a binary file</span></span>

<span data-ttu-id="06c4c-108">Použijte `WriteAllBytes` metodu a zadejte cestu k souboru a název a bajty, které mají být zapsány.</span><span class="sxs-lookup"><span data-stu-id="06c4c-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="06c4c-109">Tento příklad připojí datové pole `CustomerData` k souboru s názvem `CollectedData.dat` .</span><span class="sxs-lookup"><span data-stu-id="06c4c-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a><span data-ttu-id="06c4c-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="06c4c-110">Robust Programming</span></span>

<span data-ttu-id="06c4c-111">Následující podmínky mohou vytvořit výjimku:</span><span class="sxs-lookup"><span data-stu-id="06c4c-111">The following conditions may create an exception:</span></span>

- <span data-ttu-id="06c4c-112">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce; obsahuje pouze prázdné znaky; nebo obsahuje neplatné znaky.</span><span class="sxs-lookup"><span data-stu-id="06c4c-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="06c4c-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="06c4c-113">(<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="06c4c-114">Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="06c4c-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="06c4c-115">`File`odkazuje na cestu, která neexistuje ( <xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="06c4c-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="06c4c-116">Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="06c4c-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="06c4c-117">Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .</span><span class="sxs-lookup"><span data-stu-id="06c4c-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="06c4c-118">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="06c4c-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="06c4c-119">Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="06c4c-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="06c4c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="06c4c-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="06c4c-121">Postupy: Zápis textu do souborů</span><span class="sxs-lookup"><span data-stu-id="06c4c-121">How to: Write Text to Files</span></span>](how-to-write-text-to-files.md)
