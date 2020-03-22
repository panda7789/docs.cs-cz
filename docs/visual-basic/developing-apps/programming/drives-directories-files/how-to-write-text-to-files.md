---
title: 'Postupy: Zápis textu do souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: ce1ee59ba71af6bb13e05a5bce37a2f7eee37712
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334464"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="268b6-102">Postupy: Zápis textu do souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="268b6-102">How to: Write Text to Files in Visual Basic</span></span>

<span data-ttu-id="268b6-103">Metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> lze použít k zápisu textu do souborů.</span><span class="sxs-lookup"><span data-stu-id="268b6-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="268b6-104">Pokud zadaný soubor neexistuje, je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="268b6-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="268b6-105">Postup</span><span class="sxs-lookup"><span data-stu-id="268b6-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="268b6-106">Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="268b6-106">To write text to a file</span></span>  
  
- <span data-ttu-id="268b6-107">Pomocí `WriteAllText` metody zapište text do souboru a zadejte soubor a text, který se má zapsat.</span><span class="sxs-lookup"><span data-stu-id="268b6-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="268b6-108">Tento příklad zapíše řádek `"This is new text."` `test.txt`do souboru s názvem , připojí text k existujícímu textu v souboru.</span><span class="sxs-lookup"><span data-stu-id="268b6-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="268b6-109">Zápis řady řetězců do souboru</span><span class="sxs-lookup"><span data-stu-id="268b6-109">To write a series of strings to a file</span></span>  
  
- <span data-ttu-id="268b6-110">Smyčka prostřednictvím kolekce řetězce.</span><span class="sxs-lookup"><span data-stu-id="268b6-110">Loop through the string collection.</span></span> <span data-ttu-id="268b6-111">Pomocí `WriteAllText` metody zapište text do souboru, určete cílový soubor `append` a `True`řetězec, který má být přidán, a nastavení na soubor .</span><span class="sxs-lookup"><span data-stu-id="268b6-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="268b6-112">Tento příklad zapisuje `Documents and Settings` názvy `FileList.txt`souborů v adresáři do , vložení matný návrat mezi každý pro lepší čitelnost.</span><span class="sxs-lookup"><span data-stu-id="268b6-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a><span data-ttu-id="268b6-113">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="268b6-113">Robust Programming</span></span>  

 <span data-ttu-id="268b6-114">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="268b6-114">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="268b6-115">Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="268b6-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="268b6-116">Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).</span><span class="sxs-lookup"><span data-stu-id="268b6-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="268b6-117">`File`odkazuje na cestu, která<xref:System.IO.FileNotFoundException> neexistuje <xref:System.IO.DirectoryNotFoundException>( nebo ).</span><span class="sxs-lookup"><span data-stu-id="268b6-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="268b6-118">Soubor je používán jiným procesem nebo dojde k chybě<xref:System.IO.IOException>vstupně-out ( ).</span><span class="sxs-lookup"><span data-stu-id="268b6-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="268b6-119">Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).</span><span class="sxs-lookup"><span data-stu-id="268b6-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="268b6-120">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="268b6-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="268b6-121">Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).</span><span class="sxs-lookup"><span data-stu-id="268b6-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="268b6-122">Disk je plný a volání `WriteAllText` nezdaří (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="268b6-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="268b6-123">Pokud jsou spuštěny v kontextu částečné důvěryhodnosti, kód může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="268b6-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="268b6-124">Další informace naleznete v [tématu Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="268b6-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="268b6-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="268b6-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [<span data-ttu-id="268b6-126">Postup: Čtení z textových souborů</span><span class="sxs-lookup"><span data-stu-id="268b6-126">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
