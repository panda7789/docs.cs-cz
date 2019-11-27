---
title: 'Postupy: Čtení textu ze souborů pomocí třídy StreamReader'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 572463d1f03d768fb133f2dac59b012051f053bb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334565"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="4c25a-102">Postupy: Čtení textu ze souborů pomocí třídy StreamReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c25a-102">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>

<span data-ttu-id="4c25a-103">Objekt `My.Computer.FileSystem` poskytuje metody pro otevření <xref:System.IO.TextReader> a <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="4c25a-103">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="4c25a-104">Tyto metody, `OpenTextFileWriter` a `OpenTextFileReader`, jsou pokročilé metody, které se nezobrazují v IntelliSense, pokud nevyberete kartu **vše** .</span><span class="sxs-lookup"><span data-stu-id="4c25a-104">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="4c25a-105">Načtení řádku ze souboru pomocí čtecího modulu textu</span><span class="sxs-lookup"><span data-stu-id="4c25a-105">To read a line from a file with a text reader</span></span>  
  
- <span data-ttu-id="4c25a-106">Pomocí metody `OpenTextFileReader` otevřete <xref:System.IO.TextReader>a zadejte soubor.</span><span class="sxs-lookup"><span data-stu-id="4c25a-106">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="4c25a-107">Tento příklad otevře soubor s názvem `testfile.txt`, přečte z něj řádek a zobrazí řádek v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="4c25a-107">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="4c25a-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="4c25a-108">Robust Programming</span></span>  

 <span data-ttu-id="4c25a-109">Soubor, který je čten, musí být textový soubor.</span><span class="sxs-lookup"><span data-stu-id="4c25a-109">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="4c25a-110">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="4c25a-110">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="4c25a-111">Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="4c25a-111">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="4c25a-112">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="4c25a-112">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="4c25a-113">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="4c25a-113">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4c25a-114">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4c25a-114">.NET Framework Security</span></span>  

 <span data-ttu-id="4c25a-115">Aby bylo možné číst ze souboru, vaše sestavení vyžaduje úroveň oprávnění udělené třídou <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="4c25a-115">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="4c25a-116">Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, může kód vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="4c25a-116">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="4c25a-117">Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="4c25a-117">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span> <span data-ttu-id="4c25a-118">Uživatel také potřebuje přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="4c25a-118">The user also needs access to the file.</span></span> <span data-ttu-id="4c25a-119">Další informace najdete v tématu [Přehled technologie ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4c25a-119">For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c25a-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c25a-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [<span data-ttu-id="4c25a-121">Komponenta SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="4c25a-121">SaveFileDialog Component</span></span>](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [<span data-ttu-id="4c25a-122">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="4c25a-122">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
