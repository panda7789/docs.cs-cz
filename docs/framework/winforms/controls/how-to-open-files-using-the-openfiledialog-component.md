---
title: 'Postupy: otevření souborů pomocí komponenty OpenFileDialog'
ms.date: 02/11/2019
description: Naučte se používat komponentu OpenFileDialog k otevření dialogového okna Windows pro procházení a výběr souborů.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: d571885011b0f0c723c73a417f294f30f96952f4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904426"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="a1c3e-103">Postupy: otevření souborů pomocí OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="a1c3e-103">How to: Open files with the OpenFileDialog</span></span>

<span data-ttu-id="a1c3e-104"><xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType>Komponenta otevře dialogové okno Windows pro procházení a výběr souborů.</span><span class="sxs-lookup"><span data-stu-id="a1c3e-104">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="a1c3e-105">Chcete-li otevřít a číst vybrané soubory, můžete použít <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> metodu nebo vytvořit instanci <xref:System.IO.StreamReader?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="a1c3e-105">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="a1c3e-106">Následující příklady znázorňují oba přístupy.</span><span class="sxs-lookup"><span data-stu-id="a1c3e-106">The following examples show both approaches.</span></span>

<span data-ttu-id="a1c3e-107">V .NET Framework pro získání nebo nastavení <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnosti vyžaduje úroveň oprávnění udělené <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídou.</span><span class="sxs-lookup"><span data-stu-id="a1c3e-107">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="a1c3e-108">Příklady spouštějí <xref:System.Security.Permissions.FileIOPermission> kontrolu oprávnění a mohou vyvolat výjimku z důvodu nedostatečných oprávnění, pokud jsou spuštěny v kontextu s částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="a1c3e-108">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="a1c3e-109">Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="a1c3e-109">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="a1c3e-110">Tyto příklady můžete sestavit a spustit jako aplikace .NET Framework z příkazového řádku jazyka C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a1c3e-110">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="a1c3e-111">Další informace naleznete v tématu [sestavování z příkazového řádku pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="a1c3e-111">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="a1c3e-112">Počínaje rozhraním .NET Core 3,0 můžete také sestavit a spustit příklady jako aplikace Windows .NET Core ze složky, která obsahuje soubor projektu .NET Core model Windows Forms \* \<folder name> . csproj\* .</span><span class="sxs-lookup"><span data-stu-id="a1c3e-112">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="a1c3e-113">Příklad: čtení souboru jako datového proudu pomocí StreamReader</span><span class="sxs-lookup"><span data-stu-id="a1c3e-113">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="a1c3e-114">V následujícím příkladu je použita <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> obslužná rutina události model Windows Forms ovládacího prvku pro otevření <xref:System.Windows.Forms.OpenFileDialog> s <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="a1c3e-114">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="a1c3e-115">Poté, co uživatel zvolí soubor a vybere **OK**, instance <xref:System.IO.StreamReader> třídy načte soubor a zobrazí jeho obsah v textovém poli formuláře.</span><span class="sxs-lookup"><span data-stu-id="a1c3e-115">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="a1c3e-116">Další informace o čtení z datových proudů souborů naleznete v tématu <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a1c3e-116">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="a1c3e-117">Příklad: otevření souboru z filtrovaného výběru pomocí OpenFile</span><span class="sxs-lookup"><span data-stu-id="a1c3e-117">Example: Open a file from a filtered selection with OpenFile</span></span>

<span data-ttu-id="a1c3e-118">Následující příklad používá <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> obslužnou rutinu události ovládacího prvku pro otevření <xref:System.Windows.Forms.OpenFileDialog> s filtrem, který zobrazuje pouze textové soubory.</span><span class="sxs-lookup"><span data-stu-id="a1c3e-118">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="a1c3e-119">Když uživatel zvolí textový soubor a vybere **OK**, <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> použije se k otevření souboru v poznámkovém bloku metoda.</span><span class="sxs-lookup"><span data-stu-id="a1c3e-119">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="a1c3e-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1c3e-120">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="a1c3e-121">OpenFileDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="a1c3e-121">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
