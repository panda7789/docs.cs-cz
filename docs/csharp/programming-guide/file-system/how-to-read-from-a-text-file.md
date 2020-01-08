---
title: Jak číst z textového souboru – C# Průvodce programováním
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
ms.openlocfilehash: 4e15d82a303c1a92739c72a2ddffd411debf99d4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635324"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="59d92-102">Čtení z textového souboru (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="59d92-102">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="59d92-103">Tento příklad přečte obsah textového souboru pomocí statických metod <xref:System.IO.File.ReadAllText%2A> a <xref:System.IO.File.ReadAllLines%2A> z třídy <xref:System.IO.File?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59d92-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="59d92-104">Příklad, který používá <xref:System.IO.StreamReader>, najdete v tématu [jak číst textový soubor po jednom řádku](./how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="59d92-104">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="59d92-105">Soubory, které jsou použity v tomto příkladu, jsou vytvořeny v tématu [jak zapisovat do textového souboru](./how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="59d92-105">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="59d92-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="59d92-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59d92-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="59d92-107">Compiling the Code</span></span>  
 <span data-ttu-id="59d92-108">Zkopírujte kód a vložte ho do C# konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="59d92-108">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="59d92-109">Pokud nepoužíváte textové soubory z [postupu zápisu do textového souboru](./how-to-write-to-a-text-file.md), nahraďte argument `ReadAllText` a `ReadAllLines` odpovídající cestou a názvu souboru v počítači.</span><span class="sxs-lookup"><span data-stu-id="59d92-109">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="59d92-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="59d92-110">Robust Programming</span></span>  
 <span data-ttu-id="59d92-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="59d92-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="59d92-112">Soubor neexistuje nebo neexistuje v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="59d92-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="59d92-113">Zkontrolujte cestu a pravopis názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="59d92-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="59d92-114">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59d92-114">.NET Framework Security</span></span>  
 <span data-ttu-id="59d92-115">Nespoléhá na název souboru k určení obsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="59d92-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="59d92-116">Například soubor `myFile.cs` nemusí být C# zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="59d92-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59d92-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59d92-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="59d92-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="59d92-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="59d92-119">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="59d92-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
