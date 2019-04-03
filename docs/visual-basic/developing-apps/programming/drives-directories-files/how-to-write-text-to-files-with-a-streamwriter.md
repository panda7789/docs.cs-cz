---
title: 'Postupy: Zápis textu do souborů pomocí třídy StreamWriter v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: ca792106bdd341fa4be8f3554ce70cd7d3f22522
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816065"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="5c008-102">Postupy: Zápis textu do souborů pomocí třídy StreamWriter v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c008-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="5c008-103">Tento příklad otevře <xref:System.IO.StreamWriter> objekt s `My.Computer.FileSystem.OpenTextFileWriter` metody a použije ho k zápisu řetězce do textového souboru s <xref:System.IO.TextWriter.WriteLine%2A> metodu <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="5c008-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c008-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c008-104">Example</span></span>  
 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5c008-105">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="5c008-105">Robust Programming</span></span>  
 <span data-ttu-id="5c008-106">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="5c008-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="5c008-107">Soubor existuje a je jen pro čtení (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5c008-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="5c008-108">Disk je plný (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5c008-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="5c008-109">Cesta je moc dlouhý (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="5c008-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5c008-110">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5c008-110">.NET Framework Security</span></span>  
 <span data-ttu-id="5c008-111">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="5c008-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="5c008-112">Pokud aplikace potřebuje vytvořit soubor, pak tato aplikace potřebuje `Create` přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="5c008-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="5c008-113">Pokud soubor již existuje, aplikace potřebuje pouze `Write` přístup, a menší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5c008-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="5c008-114">Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze `Read` přístup do jednoho souboru, spíše než `Create` přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="5c008-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c008-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c008-115">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="5c008-116">Postupy: Čtení z textových souborů</span><span class="sxs-lookup"><span data-stu-id="5c008-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [<span data-ttu-id="5c008-117">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="5c008-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
