---
title: 'Postupy: Zápis textu do souborů pomocí třídy StreamWriter'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 373f3bd07ea61263ddd81037d8cbbb06f789e599
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411574"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="2e3fd-102">Postupy: Zápis textu do souborů pomocí třídy StreamWriter v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e3fd-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>

<span data-ttu-id="2e3fd-103">Tento příklad otevře <xref:System.IO.StreamWriter> objekt s `My.Computer.FileSystem.OpenTextFileWriter` metodou a použije ho k zápisu řetězce do textového souboru s <xref:System.IO.TextWriter.WriteLine%2A> metodou <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="2e3fd-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e3fd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e3fd-104">Example</span></span>  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2e3fd-105">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="2e3fd-105">Robust Programming</span></span>  

 <span data-ttu-id="2e3fd-106">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="2e3fd-106">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2e3fd-107">Soubor existuje a je určen jen pro čtení ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="2e3fd-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2e3fd-108">Disk je plný ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="2e3fd-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2e3fd-109">Cesta je příliš dlouhá ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="2e3fd-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2e3fd-110">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2e3fd-110">.NET Framework Security</span></span>  

 <span data-ttu-id="2e3fd-111">Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="2e3fd-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="2e3fd-112">Pokud aplikace potřebuje vytvořit soubor, tato aplikace potřebuje `Create` ke složce přístup.</span><span class="sxs-lookup"><span data-stu-id="2e3fd-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="2e3fd-113">Pokud soubor již existuje, aplikace potřebuje `Write` přístup pouze k menšímu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="2e3fd-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="2e3fd-114">Je-li to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` přístup pouze k jedinému souboru, nikoli ke `Create` složce.</span><span class="sxs-lookup"><span data-stu-id="2e3fd-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e3fd-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e3fd-115">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="2e3fd-116">Postupy: čtení z textových souborů</span><span class="sxs-lookup"><span data-stu-id="2e3fd-116">How to: Read from Text Files</span></span>](how-to-read-from-text-files.md)
- [<span data-ttu-id="2e3fd-117">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="2e3fd-117">Writing to Files</span></span>](writing-to-files.md)
