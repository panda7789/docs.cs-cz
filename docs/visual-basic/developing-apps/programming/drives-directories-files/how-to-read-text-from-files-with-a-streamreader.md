---
title: "Postupy: Čtení textu ze souborů pomocí třídy StreamReader (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8feefd401ad6064ff244ff9bc24abea08f001a2e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="cc951-102">Postupy: Čtení textu ze souborů pomocí třídy StreamReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc951-102">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>
<span data-ttu-id="cc951-103">`My.Computer.FileSystem` Objekt poskytuje metody pro otevření <xref:System.IO.TextReader> a <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="cc951-103">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="cc951-104">Tyto metody `OpenTextFileWriter` a `OpenTextFileReader`, jsou rozšířené metody, které se v technologii IntelliSense nezobrazí, dokud nevyberte **všechny** kartě.</span><span class="sxs-lookup"><span data-stu-id="cc951-104">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="cc951-105">Načíst řádek ze souboru s čtečku textu</span><span class="sxs-lookup"><span data-stu-id="cc951-105">To read a line from a file with a text reader</span></span>  
  
-   <span data-ttu-id="cc951-106">Použití `OpenTextFileReader` metoda otevřete <xref:System.IO.TextReader>, zadání souboru.</span><span class="sxs-lookup"><span data-stu-id="cc951-106">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="cc951-107">Tento příklad otevře soubor s názvem `testfile.txt`, přečte řádek z něj a zobrazí řádek v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="cc951-107">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cc951-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="cc951-108">Robust Programming</span></span>  
 <span data-ttu-id="cc951-109">Soubor, který je pro čtení musí být textového souboru.</span><span class="sxs-lookup"><span data-stu-id="cc951-109">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="cc951-110">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="cc951-110">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="cc951-111">Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cc951-111">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="cc951-112">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="cc951-112">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="cc951-113">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="cc951-113">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cc951-114">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cc951-114">.NET Framework Security</span></span>  
 <span data-ttu-id="cc951-115">Čtení ze souboru, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission> třídy.</span><span class="sxs-lookup"><span data-stu-id="cc951-115">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="cc951-116">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, kód může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="cc951-116">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="cc951-117">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="cc951-117">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span> <span data-ttu-id="cc951-118">Uživatel také potřebuje přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="cc951-118">The user also needs access to the file.</span></span> <span data-ttu-id="cc951-119">Další informace najdete v tématu [Přehled technologie ACL](http://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).</span><span class="sxs-lookup"><span data-stu-id="cc951-119">For more information, see [ACL Technology Overview](http://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc951-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc951-120">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>  
 [<span data-ttu-id="cc951-121">Komponenta SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="cc951-121">SaveFileDialog Component</span></span>](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)  
 [<span data-ttu-id="cc951-122">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="cc951-122">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
