---
title: 'Postup: Otevření souborů pomocí komponenty OpenFileDialog'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: ca69de19ab1b9ae387002898145fe99e35a7b6b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182135"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="6f8b7-102">Postup: Otevření souborů pomocí dialogu OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="6f8b7-102">How to: Open files with the OpenFileDialog</span></span>

<span data-ttu-id="6f8b7-103">Komponenta <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> otevře dialogové okno Systému Windows pro procházení a výběr souborů.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-103">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="6f8b7-104">Chcete-li otevřít a číst vybrané <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> soubory, můžete použít metodu nebo vytvořit instanci třídy. <xref:System.IO.StreamReader?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6f8b7-104">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="6f8b7-105">Následující příklady ukazují oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-105">The following examples show both approaches.</span></span>

<span data-ttu-id="6f8b7-106">V rozhraní .NET Framework vyžaduje <xref:System.Windows.Forms.FileDialog.FileName%2A> získání nebo nastavení vlastnosti úroveň oprávnění udělenou třídou. <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6f8b7-106">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="6f8b7-107">Příklady spustit <xref:System.Security.Permissions.FileIOPermission> kontrolu oprávnění a může vyvolat výjimku z důvodu nedostatečných oprávnění, pokud jsou spuštěny v kontextu částečné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-107">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="6f8b7-108">Další informace naleznete v [tématu Základy zabezpečení přístupu kódu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="6f8b7-108">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="6f8b7-109">Tyto příklady můžete vytvořit a spustit jako aplikace rozhraní .NET Framework z příkazového řádku jazyka C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-109">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="6f8b7-110">Další informace naleznete v [tématu Vytváření příkazového řádku s csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [Sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="6f8b7-110">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="6f8b7-111">Počínaje rozhraním .NET Core 3.0 můžete také vytvářet a spouštět příklady jako aplikace Windows .NET Core ze složky, která má název složky .NET Core Windows Forms \* \<>.csproj\* soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-111">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="6f8b7-112">Příklad: Čtení souboru jako datového proudu pomocí streamreaderu</span><span class="sxs-lookup"><span data-stu-id="6f8b7-112">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="6f8b7-113">Následující příklad používá obslužnou rutinu <xref:System.Windows.Forms.OpenFileDialog> události <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> ovládacího <xref:System.Windows.Forms.Control.Click> prvku Windows Forms <xref:System.Windows.Forms.Button> k otevření metody s.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-113">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="6f8b7-114">Poté, co uživatel vybere soubor **OK**a vybere OK <xref:System.IO.StreamReader> , instance třídy přečte soubor a zobrazí jeho obsah v textovém poli formuláře.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-114">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="6f8b7-115">Další informace o čtení z datových proudů souborů naleznete v tématu <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-115">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="6f8b7-116">Příklad: Otevření souboru z filtrovaného výběru pomocí openfile</span><span class="sxs-lookup"><span data-stu-id="6f8b7-116">Example: Open a file from a filtered selection with OpenFile</span></span>

<span data-ttu-id="6f8b7-117">Následující příklad používá <xref:System.Windows.Forms.Button> obslužnou rutinu události ovládacího <xref:System.Windows.Forms.Control.Click> prvku k otevření <xref:System.Windows.Forms.OpenFileDialog> filtru, který zobrazuje pouze textové soubory.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-117">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="6f8b7-118">Poté, co uživatel vybere textový **OK**soubor a <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> vybere OK , metoda se používá k otevření souboru v poznámkovém bloku.</span><span class="sxs-lookup"><span data-stu-id="6f8b7-118">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="6f8b7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f8b7-119">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="6f8b7-120">Komponenta OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="6f8b7-120">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
