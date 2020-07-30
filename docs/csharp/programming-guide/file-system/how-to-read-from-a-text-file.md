---
title: Jak číst z textového souboru – Průvodce programováním v C#
description: Naučte se číst z textového souboru pomocí statických metod z třídy File. Podívejte se na příklad kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 80ac6f8412f456b23d05ee87882dca8e16a132c3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301655"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="88926-104">Jak číst z textového souboru (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="88926-104">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="88926-105">Tento příklad přečte obsah textového souboru pomocí statických metod <xref:System.IO.File.ReadAllText%2A> a <xref:System.IO.File.ReadAllLines%2A> od <xref:System.IO.File?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="88926-105">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="88926-106">Příklad, který používá <xref:System.IO.StreamReader> , najdete v tématu [jak číst textový soubor po jednom řádku](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="88926-106">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="88926-107">Soubory, které jsou použity v tomto příkladu, jsou vytvořeny v tématu [jak zapisovat do textového souboru](./how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="88926-107">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="88926-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="88926-108">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="88926-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="88926-109">Compiling the Code</span></span>  
 <span data-ttu-id="88926-110">Zkopírujte kód a vložte ho do konzolové aplikace v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="88926-110">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="88926-111">Pokud nepoužíváte textové soubory z [postupu zápisu do textového souboru](./how-to-write-to-a-text-file.md), nahraďte argument `ReadAllText` a `ReadAllLines` odpovídající cestou a názvem souboru v počítači.</span><span class="sxs-lookup"><span data-stu-id="88926-111">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="88926-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="88926-112">Robust Programming</span></span>  
 <span data-ttu-id="88926-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="88926-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="88926-114">Soubor neexistuje nebo neexistuje v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="88926-114">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="88926-115">Zkontrolujte cestu a pravopis názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="88926-115">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="88926-116">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="88926-116">.NET Security</span></span>  
 <span data-ttu-id="88926-117">Nespoléhá na název souboru k určení obsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="88926-117">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="88926-118">Například soubor nemusí `myFile.cs` být zdrojový soubor C#.</span><span class="sxs-lookup"><span data-stu-id="88926-118">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88926-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88926-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="88926-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="88926-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="88926-121">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="88926-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
