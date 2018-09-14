---
title: 'Postupy: Zápis textu do souborů v adresáři MyDocuments v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: 894458ad6d69b8bb2836518b90723703733208b6
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617075"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="d1e46-102">Postupy: Zápis textu do souborů v adresáři MyDocuments v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d1e46-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="d1e46-103">`My.Computer.FileSystem.SpecialDirectories` Objekt umožňuje přístup k adresářům speciální, například **MyDocuments** adresáře.</span><span class="sxs-lookup"><span data-stu-id="d1e46-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="d1e46-104">Postup</span><span class="sxs-lookup"><span data-stu-id="d1e46-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="d1e46-105">Psaní nové textové soubory v adresáři Moje dokumenty</span><span class="sxs-lookup"><span data-stu-id="d1e46-105">To write new text files in the My Documents directory</span></span>  
  
1.  <span data-ttu-id="d1e46-106">Použití `My.Computer.FileSystem.SpecialDirectories.MyDocuments` vlastnost zadat cestu.</span><span class="sxs-lookup"><span data-stu-id="d1e46-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  <span data-ttu-id="d1e46-107">Použití `WriteAllText` způsob zápisu textu do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="d1e46-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="d1e46-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1e46-108">Example</span></span>  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d1e46-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d1e46-109">Compiling the Code</span></span>  
 <span data-ttu-id="d1e46-110">Nahraďte `test.txt` s názvem souboru chcete zapsat.</span><span class="sxs-lookup"><span data-stu-id="d1e46-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d1e46-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d1e46-111">Robust Programming</span></span>  
 <span data-ttu-id="d1e46-112">Tento kód znovu vyvolá všechny výjimky, které mohou nastat při zápisu textu do souboru.</span><span class="sxs-lookup"><span data-stu-id="d1e46-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="d1e46-113">Snížíte pravděpodobnost, že výjimky pomocí ovládacích prvků Windows Forms, jako [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) a [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) součásti, které omezují výběr uživatele na platný název souboru.</span><span class="sxs-lookup"><span data-stu-id="d1e46-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="d1e46-114">Pomocí těchto ovládacích prvků není spolehlivá, ale.</span><span class="sxs-lookup"><span data-stu-id="d1e46-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="d1e46-115">Systém souborů můžete změnit mezi časem uživatel vybere soubor a čas, který spouští kód.</span><span class="sxs-lookup"><span data-stu-id="d1e46-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="d1e46-116">Zpracování výjimek je proto téměř vždy nezbytné při práci se soubory.</span><span class="sxs-lookup"><span data-stu-id="d1e46-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d1e46-117">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d1e46-117">.NET Framework Security</span></span>  
 <span data-ttu-id="d1e46-118">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, kód může vyvolat výjimku, protože nedostatečná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="d1e46-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="d1e46-119">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="d1e46-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="d1e46-120">Tento příklad vytvoří nový soubor.</span><span class="sxs-lookup"><span data-stu-id="d1e46-120">This example creates a new file.</span></span> <span data-ttu-id="d1e46-121">Pokud aplikace potřebuje vytvořit soubor, tato aplikace potřebuje vytvořit oprávnění pro složku.</span><span class="sxs-lookup"><span data-stu-id="d1e46-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="d1e46-122">Oprávnění se nastavují pomocí seznamů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="d1e46-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="d1e46-123">Pokud soubor již existuje, aplikace potřebuje pouze oprávnění, a menší oprávnění k zápisu.</span><span class="sxs-lookup"><span data-stu-id="d1e46-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="d1e46-124">Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze oprávnění ke čtení pro jeden soubor, nikoli k udělení oprávnění vytvořit pro složku.</span><span class="sxs-lookup"><span data-stu-id="d1e46-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="d1e46-125">Navíc je bezpečnější zapsat data do uživatelské složky než do kořenové složky nebo **Program Files** složky.</span><span class="sxs-lookup"><span data-stu-id="d1e46-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="d1e46-126">Další informace najdete v tématu [Přehled technologie ACL](https://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).</span><span class="sxs-lookup"><span data-stu-id="d1e46-126">For more information, see [ACL Technology Overview](https://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e46-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1e46-127">See Also</span></span>  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
