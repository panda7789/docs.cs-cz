---
title: 'Postupy: Připojování k textovým souborům'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 53b2e4c9030e9d1dd81a4121ad3f92aad796e3e1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359952"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="b784e-102">Postupy: Připojování k textovým souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b784e-102">How to: Append to Text Files in Visual Basic</span></span>

<span data-ttu-id="b784e-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>Metodu lze použít pro připojení k textovému souboru zadáním, zda `append` je parametr nastaven na hodnotu `True` .</span><span class="sxs-lookup"><span data-stu-id="b784e-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="b784e-104">Připojení k textovému souboru</span><span class="sxs-lookup"><span data-stu-id="b784e-104">To append to a text file</span></span>  
  
- <span data-ttu-id="b784e-105">Použijte `WriteAllText` metodu, určete cílový soubor a řetězec, který má být přidán a nastavte `append` parametr na `True` .</span><span class="sxs-lookup"><span data-stu-id="b784e-105">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="b784e-106">Tento příklad zapíše řetězec `"This is a test string."` do souboru s názvem `Testfile.txt` .</span><span class="sxs-lookup"><span data-stu-id="b784e-106">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b784e-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="b784e-107">Robust Programming</span></span>  

 <span data-ttu-id="b784e-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="b784e-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b784e-109">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b784e-109">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="b784e-110">Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="b784e-110">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="b784e-111">`File`odkazuje na cestu, která neexistuje ( <xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="b784e-111">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="b784e-112">Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="b784e-112">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="b784e-113">Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .</span><span class="sxs-lookup"><span data-stu-id="b784e-113">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="b784e-114">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="b784e-114">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="b784e-115">Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="b784e-115">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b784e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b784e-116">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="b784e-117">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="b784e-117">Writing to Files</span></span>](writing-to-files.md)
