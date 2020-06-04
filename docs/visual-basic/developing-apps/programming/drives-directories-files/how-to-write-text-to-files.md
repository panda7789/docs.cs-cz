---
title: 'Postupy: Zápis textu do souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: f95a0c4df4a2eab0069a6dab0d4c3fa338d1d8ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411535"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="dd850-102">Postupy: Zápis textu do souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd850-102">How to: Write Text to Files in Visual Basic</span></span>

<span data-ttu-id="dd850-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>Metodu lze použít k zápisu textu do souborů.</span><span class="sxs-lookup"><span data-stu-id="dd850-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="dd850-104">Pokud zadaný soubor neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="dd850-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="dd850-105">Postup</span><span class="sxs-lookup"><span data-stu-id="dd850-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="dd850-106">Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="dd850-106">To write text to a file</span></span>  
  
- <span data-ttu-id="dd850-107">Použijte `WriteAllText` metodu k zápisu textu do souboru, zadání souboru a textu, který se má zapsat.</span><span class="sxs-lookup"><span data-stu-id="dd850-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="dd850-108">Tento příklad zapíše řádek `"This is new text."` do souboru s názvem `test.txt` a připojí text k jakémukoli existujícímu textu v souboru.</span><span class="sxs-lookup"><span data-stu-id="dd850-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="dd850-109">Zápis řady řetězců do souboru</span><span class="sxs-lookup"><span data-stu-id="dd850-109">To write a series of strings to a file</span></span>  
  
- <span data-ttu-id="dd850-110">Smyčka prostřednictvím kolekce řetězců.</span><span class="sxs-lookup"><span data-stu-id="dd850-110">Loop through the string collection.</span></span> <span data-ttu-id="dd850-111">Použijte `WriteAllText` metodu k zápisu textu do souboru, určení cílového souboru a řetězce, který chcete přidat a nastavení `append` na `True` .</span><span class="sxs-lookup"><span data-stu-id="dd850-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="dd850-112">Tento příklad zapíše názvy souborů v `Documents and Settings` adresáři do, do kterého se `FileList.txt` vloží znak pro lepší čitelnost.</span><span class="sxs-lookup"><span data-stu-id="dd850-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a><span data-ttu-id="dd850-113">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="dd850-113">Robust Programming</span></span>  

 <span data-ttu-id="dd850-114">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="dd850-114">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="dd850-115">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="dd850-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="dd850-116">Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="dd850-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="dd850-117">`File`odkazuje na cestu, která neexistuje ( <xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="dd850-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="dd850-118">Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="dd850-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="dd850-119">Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .</span><span class="sxs-lookup"><span data-stu-id="dd850-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="dd850-120">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="dd850-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="dd850-121">Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="dd850-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="dd850-122">Disk je plný a volání metody `WriteAllText` selžou ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="dd850-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="dd850-123">Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, může kód vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="dd850-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="dd850-124">Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="dd850-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd850-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd850-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [<span data-ttu-id="dd850-126">Postupy: čtení z textových souborů</span><span class="sxs-lookup"><span data-stu-id="dd850-126">How to: Read from Text Files</span></span>](how-to-read-from-text-files.md)
