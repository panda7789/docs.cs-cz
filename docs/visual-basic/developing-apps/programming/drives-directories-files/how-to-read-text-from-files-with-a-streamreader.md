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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334565"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="db830-102">Postupy: Čtení textu ze souborů pomocí třídy StreamReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db830-102">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>

<span data-ttu-id="db830-103">`My.Computer.FileSystem` Objekt poskytuje metody pro otevření <xref:System.IO.TextReader> a <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="db830-103">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="db830-104">Tyto metody `OpenTextFileWriter` a `OpenTextFileReader`, jsou pokročilé metody, které se nezobrazí v technologii IntelliSense, pokud nevyberete kartu **vše** .</span><span class="sxs-lookup"><span data-stu-id="db830-104">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="db830-105">Načtení řádku ze souboru pomocí čtecího modulu textu</span><span class="sxs-lookup"><span data-stu-id="db830-105">To read a line from a file with a text reader</span></span>  
  
- <span data-ttu-id="db830-106">Použijte `OpenTextFileReader` metodu k otevření <xref:System.IO.TextReader>a určení souboru.</span><span class="sxs-lookup"><span data-stu-id="db830-106">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="db830-107">Tento příklad otevře soubor s názvem `testfile.txt`, přečte z něj čáru a zobrazí řádek v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="db830-107">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="db830-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="db830-108">Robust Programming</span></span>  

 <span data-ttu-id="db830-109">Soubor, který je čten, musí být textový soubor.</span><span class="sxs-lookup"><span data-stu-id="db830-109">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="db830-110">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="db830-110">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="db830-111">Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="db830-111">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="db830-112">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="db830-112">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="db830-113">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="db830-113">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="db830-114">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="db830-114">.NET Framework Security</span></span>  

 <span data-ttu-id="db830-115">Aby bylo možné číst ze souboru, vaše sestavení vyžaduje úroveň oprávnění udělené <xref:System.Security.Permissions.FileIOPermission> třídou.</span><span class="sxs-lookup"><span data-stu-id="db830-115">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="db830-116">Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, může kód vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="db830-116">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="db830-117">Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="db830-117">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span> <span data-ttu-id="db830-118">Uživatel také potřebuje přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="db830-118">The user also needs access to the file.</span></span> <span data-ttu-id="db830-119">Další informace najdete v tématu [Přehled technologie ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="db830-119">For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db830-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="db830-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [<span data-ttu-id="db830-121">Komponenta SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="db830-121">SaveFileDialog Component</span></span>](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [<span data-ttu-id="db830-122">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="db830-122">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
