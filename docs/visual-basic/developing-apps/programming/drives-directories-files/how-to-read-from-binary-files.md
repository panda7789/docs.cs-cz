---
title: 'Postupy: Čtení z binárních souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 3b4108034b86d99143fff6943e68ca0077ebd21b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359926"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="1cff5-102">Postupy: Čtení z binárních souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1cff5-102">How to: Read From Binary Files in Visual Basic</span></span>

<span data-ttu-id="1cff5-103">`My.Computer.FileSystem`Objekt poskytuje `ReadAllBytes` metodu pro čtení z binárních souborů.</span><span class="sxs-lookup"><span data-stu-id="1cff5-103">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="1cff5-104">Čtení z binárního souboru</span><span class="sxs-lookup"><span data-stu-id="1cff5-104">To read from a binary file</span></span>  
  
- <span data-ttu-id="1cff5-105">Použijte `ReadAllBytes` metodu, která vrátí obsah souboru jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="1cff5-105">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="1cff5-106">Tento příklad čte ze souboru `C:/Documents and Settings/selfportrait.jpg` .</span><span class="sxs-lookup"><span data-stu-id="1cff5-106">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- <span data-ttu-id="1cff5-107">U velkých binárních souborů lze použít <xref:System.IO.FileStream.Read%2A> metodu <xref:System.IO.FileStream> objektu pro čtení ze souboru pouze v zadané velikosti.</span><span class="sxs-lookup"><span data-stu-id="1cff5-107">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="1cff5-108">Pak můžete omezit, kolik souborů je načteno do paměti pro každou operaci čtení.</span><span class="sxs-lookup"><span data-stu-id="1cff5-108">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="1cff5-109">Následující příklad kódu zkopíruje soubor a umožňuje volajícímu určit, jak velká část souboru je načtena do paměti na operaci čtení.</span><span class="sxs-lookup"><span data-stu-id="1cff5-109">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1cff5-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1cff5-110">Robust Programming</span></span>  

 <span data-ttu-id="1cff5-111">Následující podmínky mohou způsobit vyvolání výjimky:</span><span class="sxs-lookup"><span data-stu-id="1cff5-111">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="1cff5-112">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="1cff5-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="1cff5-113">Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="1cff5-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="1cff5-114">Soubor neexistuje ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="1cff5-114">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="1cff5-115">Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="1cff5-115">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="1cff5-116">Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .</span><span class="sxs-lookup"><span data-stu-id="1cff5-116">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="1cff5-117">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="1cff5-117">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="1cff5-118">K zápisu řetězce do vyrovnávací paměti () není dostatek paměti <xref:System.OutOfMemoryException> .</span><span class="sxs-lookup"><span data-stu-id="1cff5-118">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
- <span data-ttu-id="1cff5-119">Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="1cff5-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="1cff5-120">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="1cff5-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="1cff5-121">Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="1cff5-121">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="1cff5-122">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="1cff5-122">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="1cff5-123">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="1cff5-123">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cff5-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cff5-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="1cff5-125">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="1cff5-125">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="1cff5-126">Postupy: Čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="1cff5-126">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="1cff5-127">Ukládání dat do schránky a čtení ze schránky</span><span class="sxs-lookup"><span data-stu-id="1cff5-127">Storing Data to and Reading from the Clipboard</span></span>](../computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
