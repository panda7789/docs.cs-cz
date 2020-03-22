---
title: 'Postupy: Zápis do binárních souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 72d019f5f49868bd84d0507535e8ebc547b50e25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334434"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="be10c-102">Postupy: Zápis do binárních souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be10c-102">How to: Write to Binary Files in Visual Basic</span></span>

<span data-ttu-id="be10c-103">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> zapisuje data do binárního souboru.</span><span class="sxs-lookup"><span data-stu-id="be10c-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="be10c-104">Pokud `append` je `True`parametr , připojí data k souboru; v opačném případě jsou data v souboru přepsána.</span><span class="sxs-lookup"><span data-stu-id="be10c-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>

<span data-ttu-id="be10c-105">Pokud zadaná cesta bez názvu souboru <xref:System.IO.DirectoryNotFoundException> není platná, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="be10c-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="be10c-106">Pokud je cesta platná, ale soubor neexistuje, soubor bude vytvořen.</span><span class="sxs-lookup"><span data-stu-id="be10c-106">If the path is valid but the file does not exist, the file will be created.</span></span>

## <a name="to-write-to-a-binary-file"></a><span data-ttu-id="be10c-107">Zápis do binárního souboru</span><span class="sxs-lookup"><span data-stu-id="be10c-107">To write to a binary file</span></span>

<span data-ttu-id="be10c-108">Použijte `WriteAllBytes` metodu, která poskytuje cestu k souboru a název a bajty, které mají být zapsány.</span><span class="sxs-lookup"><span data-stu-id="be10c-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="be10c-109">Tento příklad připojí datové `CustomerData` pole k `CollectedData.dat`souboru s názvem .</span><span class="sxs-lookup"><span data-stu-id="be10c-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a><span data-ttu-id="be10c-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="be10c-110">Robust Programming</span></span>

<span data-ttu-id="be10c-111">Následující podmínky mohou vytvořit výjimku:</span><span class="sxs-lookup"><span data-stu-id="be10c-111">The following conditions may create an exception:</span></span>

- <span data-ttu-id="be10c-112">Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky; obsahuje pouze prázdné místo; nebo obsahuje neplatné znaky.</span><span class="sxs-lookup"><span data-stu-id="be10c-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="be10c-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="be10c-113">(<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="be10c-114">Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).</span><span class="sxs-lookup"><span data-stu-id="be10c-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="be10c-115">`File`odkazuje na cestu, která<xref:System.IO.FileNotFoundException> neexistuje <xref:System.IO.DirectoryNotFoundException>( nebo ).</span><span class="sxs-lookup"><span data-stu-id="be10c-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="be10c-116">Soubor je používán jiným procesem nebo dojde k chybě<xref:System.IO.IOException>vstupně-out ( ).</span><span class="sxs-lookup"><span data-stu-id="be10c-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="be10c-117">Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).</span><span class="sxs-lookup"><span data-stu-id="be10c-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="be10c-118">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="be10c-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="be10c-119">Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).</span><span class="sxs-lookup"><span data-stu-id="be10c-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="be10c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="be10c-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="be10c-121">Postupy: Zápis textu do souborů</span><span class="sxs-lookup"><span data-stu-id="be10c-121">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
