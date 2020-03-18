---
title: Jak číst z textového souboru - C# Programovací průvodce
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: d401a1d1bb2c6fccb203c440f367bd14c80e70e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705012"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="5fdcc-102">Jak číst z textového souboru (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="5fdcc-102">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="5fdcc-103">Tento příklad přečte obsah textového souboru <xref:System.IO.File.ReadAllText%2A> <xref:System.IO.File.ReadAllLines%2A> pomocí <xref:System.IO.File?displayProperty=nameWithType> statických metod a z třídy.</span><span class="sxs-lookup"><span data-stu-id="5fdcc-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="5fdcc-104">Příklad, který <xref:System.IO.StreamReader>používá , naleznete [v tématu Jak číst textový soubor po jednom řádku](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="5fdcc-104">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="5fdcc-105">Soubory, které jsou použity v tomto příkladu jsou vytvořeny v tématu [Jak zapisovat do textového souboru](./how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="5fdcc-105">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="5fdcc-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fdcc-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5fdcc-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5fdcc-107">Compiling the Code</span></span>  
 <span data-ttu-id="5fdcc-108">Zkopírujte kód a vložte jej do aplikace konzoly C#.</span><span class="sxs-lookup"><span data-stu-id="5fdcc-108">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="5fdcc-109">Pokud nepoužíváte textové soubory z [jak zapisovat do textového souboru](./how-to-write-to-a-text-file.md), nahraďte argument `ReadAllText` a `ReadAllLines` příslušnou cestou a názvem souboru v počítači.</span><span class="sxs-lookup"><span data-stu-id="5fdcc-109">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="5fdcc-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="5fdcc-110">Robust Programming</span></span>  
 <span data-ttu-id="5fdcc-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="5fdcc-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5fdcc-112">Soubor neexistuje nebo neexistuje v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="5fdcc-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="5fdcc-113">Zkontrolujte cestu a pravopis názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="5fdcc-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5fdcc-114">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5fdcc-114">.NET Framework Security</span></span>  
 <span data-ttu-id="5fdcc-115">Při určování obsahu souboru nespoléhejte na název souboru.</span><span class="sxs-lookup"><span data-stu-id="5fdcc-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="5fdcc-116">Například soubor `myFile.cs` nemusí být zdrojový soubor Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="5fdcc-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fdcc-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fdcc-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="5fdcc-118">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5fdcc-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5fdcc-119">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5fdcc-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
