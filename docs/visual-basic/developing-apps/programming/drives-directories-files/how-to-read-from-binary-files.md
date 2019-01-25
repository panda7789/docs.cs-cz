---
title: 'Postupy: Čtení z binárních souborů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 6594bd8180688ae453534207170a4befc96c5c37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647618"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="c4d54-102">Postupy: Čtení z binárních souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4d54-102">How to: Read From Binary Files in Visual Basic</span></span>
<span data-ttu-id="c4d54-103">`My.Computer.FileSystem` Objekt, který poskytuje `ReadAllBytes` metody pro čtení z binárních souborů.</span><span class="sxs-lookup"><span data-stu-id="c4d54-103">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="c4d54-104">Čtení z binárního souboru</span><span class="sxs-lookup"><span data-stu-id="c4d54-104">To read from a binary file</span></span>  
  
-   <span data-ttu-id="c4d54-105">Použití `ReadAllBytes` metoda, která vrátí obsah souboru jako bajtové pole.</span><span class="sxs-lookup"><span data-stu-id="c4d54-105">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="c4d54-106">V tomto příkladu načteme soubor `C:/Documents and Settings/selfportrait.jpg`.</span><span class="sxs-lookup"><span data-stu-id="c4d54-106">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_1.vb)]  
  
-   <span data-ttu-id="c4d54-107">Pro velké binární soubory, můžete použít <xref:System.IO.FileStream.Read%2A> metodu <xref:System.IO.FileStream> objektu určeného ke čtení ze souboru určenou dobu po jednom.</span><span class="sxs-lookup"><span data-stu-id="c4d54-107">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="c4d54-108">Můžete omezit, jak velká část souboru je načten do paměti pro každou operaci čtení.</span><span class="sxs-lookup"><span data-stu-id="c4d54-108">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="c4d54-109">Následující příklad kódu se zkopíruje soubor a umožňuje volajícímu zadat, jak velká část souboru je načíst do paměti za operace čtení.</span><span class="sxs-lookup"><span data-stu-id="c4d54-109">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c4d54-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c4d54-110">Robust Programming</span></span>  
 <span data-ttu-id="c4d54-111">Následující podmínky mohou způsobit výjimku, která je vyvolána:</span><span class="sxs-lookup"><span data-stu-id="c4d54-111">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="c4d54-112">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="c4d54-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="c4d54-113">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="c4d54-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="c4d54-114">Soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="c4d54-114">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="c4d54-115">Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupních operací (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="c4d54-115">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="c4d54-116">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="c4d54-116">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="c4d54-117">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="c4d54-117">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="c4d54-118">Není dostatek paměti k zápisu řetězce do vyrovnávací paměti (<xref:System.OutOfMemoryException>).</span><span class="sxs-lookup"><span data-stu-id="c4d54-118">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
-   <span data-ttu-id="c4d54-119">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="c4d54-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="c4d54-120">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="c4d54-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="c4d54-121">Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c4d54-121">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="c4d54-122">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="c4d54-122">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="c4d54-123">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="c4d54-123">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d54-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4d54-124">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="c4d54-125">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="c4d54-125">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="c4d54-126">Postupy: Čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="c4d54-126">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="c4d54-127">Ukládání dat do schránky a čtení ze schránky</span><span class="sxs-lookup"><span data-stu-id="c4d54-127">Storing Data to and Reading from the Clipboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
