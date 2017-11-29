---
title: "Postupy: Zápis textu do souborů pomocí třídy StreamWriter v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 874bb9cb88bbf25cb6208a0a33858855a7b26a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="f3920-102">Postupy: Zápis textu do souborů pomocí třídy StreamWriter v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3920-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="f3920-103">Tento příklad otevře <xref:System.IO.StreamWriter> objektu s `My.Computer.FileSystem.OpenTextFileWriter` metoda a použije k zápisu řetězec do textového souboru s <xref:System.IO.TextWriter.WriteLine%2A> metodu <xref:System.IO.StreamWriter> – třída.</span><span class="sxs-lookup"><span data-stu-id="f3920-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3920-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3920-104">Example</span></span>  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f3920-105">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f3920-105">Robust Programming</span></span>  
 <span data-ttu-id="f3920-106">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="f3920-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f3920-107">Soubor existuje a je jen pro čtení (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f3920-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="f3920-108">Disk je plný (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f3920-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="f3920-109">Cesta je příliš dlouhý (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="f3920-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f3920-110">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f3920-110">.NET Framework Security</span></span>  
 <span data-ttu-id="f3920-111">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f3920-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="f3920-112">Pokud aplikace potřebuje k vytvoření souboru, tato aplikace potřebuje `Create` přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="f3920-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="f3920-113">Pokud soubor již existuje, aplikace potřebuje pouze `Write` přístup nižší úrovní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="f3920-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="f3920-114">Pokud je to možné, je bezpečnější k vytvoření tohoto souboru během nasazení a udělit pouze `Read` přístup do jednoho souboru místo `Create` přístup pro složku.</span><span class="sxs-lookup"><span data-stu-id="f3920-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3920-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3920-115">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 [<span data-ttu-id="f3920-116">Postupy: čtení z textových souborů</span><span class="sxs-lookup"><span data-stu-id="f3920-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)  
 [<span data-ttu-id="f3920-117">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="f3920-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
