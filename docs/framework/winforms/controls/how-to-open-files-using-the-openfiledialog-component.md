---
title: 'Postupy: Otevírání souborů pomocí komponenty OpenFileDialog'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 7f4e96f1714a182647665f12e29d38f2b8037478
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913455"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="cea50-102">Postupy: Otevřít soubory s OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="cea50-102">How to: Open files with the OpenFileDialog</span></span> 

<span data-ttu-id="cea50-103"><xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> Komponenty otevře dialogové okno Windows pro procházení a výběr souborů.</span><span class="sxs-lookup"><span data-stu-id="cea50-103">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="cea50-104">Otevřít a přečíst si vybrané soubory, můžete použít <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> metodu, nebo vytvořit instanci <xref:System.IO.StreamReader?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="cea50-104">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="cea50-105">Následující příklady ukazují oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="cea50-105">The following examples show both approaches.</span></span> 

<span data-ttu-id="cea50-106">V rozhraní .NET Framework pro získání nebo nastavení <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnost vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="cea50-106">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="cea50-107">Spuštění příkladů <xref:System.Security.Permissions.FileIOPermission> oprávnění Zkontrolujte a může vyvolat výjimku z důvodu nedostatečné oprávnění, pokud spuštění v kontextu částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="cea50-107">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="cea50-108">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="cea50-108">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="cea50-109">Můžete sestavit a spustit tyto příklady jako aplikace rozhraní .NET Framework C# nebo příkazového řádku jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cea50-109">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="cea50-110">Další informace najdete v tématu [příkazového řádku pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="cea50-110">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span> 

<span data-ttu-id="cea50-111">Od verze .NET Core 3.0, můžete také sestavit a spustit v příkladech jako Windows aplikace .NET Core ze složky, která má formulářů Windows .NET Core  *\<název složky > .csproj* souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="cea50-111">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span> 

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="cea50-112">Příklad: Čtení souboru jako datový proud pomocí třídy StreamReader</span><span class="sxs-lookup"><span data-stu-id="cea50-112">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="cea50-113">Následující příklad používá Windows Forms <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužná rutina události otevřete <xref:System.Windows.Forms.OpenFileDialog> s <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cea50-113">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="cea50-114">Poté, co uživatel vybere soubor a vybere **OK**, instance <xref:System.IO.StreamReader> třídy načte soubor a zobrazí jeho obsah v textovém poli formuláři.</span><span class="sxs-lookup"><span data-stu-id="cea50-114">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="cea50-115">Další informace o čtení ze souborů datových proudů, naleznete v tématu <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cea50-115">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="cea50-116">Příklad: Otevřete soubor z filtrovaný výběr s OpenFile</span><span class="sxs-lookup"><span data-stu-id="cea50-116">Example: Open a file from a filtered selection with OpenFile</span></span> 

<span data-ttu-id="cea50-117">V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužná rutina události otevřete <xref:System.Windows.Forms.OpenFileDialog> s filtrem, který zobrazuje pouze textové soubory.</span><span class="sxs-lookup"><span data-stu-id="cea50-117">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="cea50-118">Poté, co uživatel vybere textový soubor a vybere **OK**, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda se používá k otevření souboru v poznámkovém bloku.</span><span class="sxs-lookup"><span data-stu-id="cea50-118">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="cea50-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cea50-119">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="cea50-120">OpenFileDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="cea50-120">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
