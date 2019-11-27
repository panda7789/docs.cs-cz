---
title: 'Postupy: Připojování k textovým souborům'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 97bcb5c511452e418df010f12d4b63f04251d021
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348874"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="d2f0e-102">Postupy: Připojování k textovým souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2f0e-102">How to: Append to Text Files in Visual Basic</span></span>

<span data-ttu-id="d2f0e-103">Metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> lze použít pro připojení k textovému souboru zadáním, že parametr `append` je nastaven na hodnotu `True`.</span><span class="sxs-lookup"><span data-stu-id="d2f0e-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="d2f0e-104">Připojení k textovému souboru</span><span class="sxs-lookup"><span data-stu-id="d2f0e-104">To append to a text file</span></span>  
  
- <span data-ttu-id="d2f0e-105">Použijte metodu `WriteAllText`, určete cílový soubor a řetězec, který se má připojit, a nastavte parametr `append` na `True`.</span><span class="sxs-lookup"><span data-stu-id="d2f0e-105">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="d2f0e-106">Tento příklad zapíše řetězec `"This is a test string."` do souboru s názvem `Testfile.txt`.</span><span class="sxs-lookup"><span data-stu-id="d2f0e-106">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d2f0e-107">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d2f0e-107">Robust Programming</span></span>  

 <span data-ttu-id="d2f0e-108">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="d2f0e-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d2f0e-109">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d2f0e-109">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="d2f0e-110">Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="d2f0e-110">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="d2f0e-111">`File` odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="d2f0e-111">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="d2f0e-112">Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="d2f0e-112">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="d2f0e-113">Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="d2f0e-113">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="d2f0e-114">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="d2f0e-114">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="d2f0e-115">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d2f0e-115">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f0e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2f0e-116">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="d2f0e-117">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="d2f0e-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
