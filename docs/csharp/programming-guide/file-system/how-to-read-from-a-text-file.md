---
title: 'Postupy: Čtení z textového souboru – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 2b98f24da7f13ae752f248eb8f26c75c1d47a824
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923956"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="60561-102">Postupy: Čtení z textového souboru (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="60561-102">How to: Read From a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="60561-103">Tento příklad přečte obsah textového souboru pomocí statických metod <xref:System.IO.File.ReadAllText%2A> a <xref:System.IO.File.ReadAllLines%2A> od <xref:System.IO.File?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="60561-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
 <span data-ttu-id="60561-104">Příklad použití <xref:System.IO.StreamReader>naleznete v tématu [How to: Přečtěte si textový soubor po](./how-to-read-a-text-file-one-line-at-a-time.md)jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="60561-104">For an example that uses <xref:System.IO.StreamReader>, see [How to: Read a Text File One Line at a Time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60561-105">Soubory, které jsou použity v tomto příkladu, jsou vytvořeny v tématu [How to: Zápis do textového souboru](./how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="60561-105">The files that are used in this example are created in the topic [How to: Write to a Text File](./how-to-write-to-a-text-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60561-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="60561-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="60561-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="60561-107">Compiling the Code</span></span>  
 <span data-ttu-id="60561-108">Zkopírujte kód a vložte ho do C# konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="60561-108">Copy the code and paste it into a C# console application.</span></span>  
  
 <span data-ttu-id="60561-109">Pokud nepoužíváte textové soubory z [tématu Postupy: Zapište do textového souboru](./how-to-write-to-a-text-file.md), nahraďte `ReadAllText` argument a `ReadAllLines` odpovídající cestou a názvem souboru v počítači.</span><span class="sxs-lookup"><span data-stu-id="60561-109">If you are not using the text files from [How to: Write to a Text File](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="60561-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="60561-110">Robust Programming</span></span>  
 <span data-ttu-id="60561-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="60561-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="60561-112">Soubor neexistuje nebo neexistuje v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="60561-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="60561-113">Zkontrolujte cestu a pravopis názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="60561-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="60561-114">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="60561-114">.NET Framework Security</span></span>  
 <span data-ttu-id="60561-115">Nespoléhá na název souboru k určení obsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="60561-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="60561-116">Soubor `myFile.cs` může být například C# zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="60561-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60561-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60561-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="60561-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="60561-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="60561-119">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="60561-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
