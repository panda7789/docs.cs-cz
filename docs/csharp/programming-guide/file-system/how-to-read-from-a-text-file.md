---
title: Jak číst z textového souboru – Průvodce programováním v C#
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 8f79d22a86390ca931b05262e50865d852c154c7
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241744"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="ec550-102">Jak číst z textového souboru (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ec550-102">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="ec550-103">Tento příklad přečte obsah textového souboru pomocí statických metod <xref:System.IO.File.ReadAllText%2A> a <xref:System.IO.File.ReadAllLines%2A> od <xref:System.IO.File?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="ec550-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="ec550-104">Příklad, který používá <xref:System.IO.StreamReader> , najdete v tématu [jak číst textový soubor po jednom řádku](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="ec550-104">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="ec550-105">Soubory, které jsou použity v tomto příkladu, jsou vytvořeny v tématu [jak zapisovat do textového souboru](./how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="ec550-105">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="ec550-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec550-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ec550-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ec550-107">Compiling the Code</span></span>  
 <span data-ttu-id="ec550-108">Zkopírujte kód a vložte ho do konzolové aplikace v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="ec550-108">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="ec550-109">Pokud nepoužíváte textové soubory z [postupu zápisu do textového souboru](./how-to-write-to-a-text-file.md), nahraďte argument `ReadAllText` a `ReadAllLines` odpovídající cestou a názvem souboru v počítači.</span><span class="sxs-lookup"><span data-stu-id="ec550-109">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="ec550-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ec550-110">Robust Programming</span></span>  
 <span data-ttu-id="ec550-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="ec550-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ec550-112">Soubor neexistuje nebo neexistuje v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="ec550-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="ec550-113">Zkontrolujte cestu a pravopis názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="ec550-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="ec550-114">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="ec550-114">.NET Security</span></span>  
 <span data-ttu-id="ec550-115">Nespoléhá na název souboru k určení obsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="ec550-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="ec550-116">Například soubor nemusí `myFile.cs` být zdrojový soubor C#.</span><span class="sxs-lookup"><span data-stu-id="ec550-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec550-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec550-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="ec550-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ec550-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ec550-119">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ec550-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
