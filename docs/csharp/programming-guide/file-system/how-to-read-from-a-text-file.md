---
title: 'Postupy: Čtení z textového souboru (Průvodce programováním v C#)'
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: cb7f5c0239273c04f9f89b4e63335e67fdf5419a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084114"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="6296d-102">Postupy: Čtení z textového souboru (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6296d-102">How to: Read From a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="6296d-103">Tento příklad přečte obsah textového souboru s použitím statické metody <xref:System.IO.File.ReadAllText%2A> a <xref:System.IO.File.ReadAllLines%2A> z <xref:System.IO.File?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="6296d-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
 <span data-ttu-id="6296d-104">Příklad, který používá <xref:System.IO.StreamReader>, naleznete v tématu [postupy: čtení jeden řádek textu souboru současně](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="6296d-104">For an example that uses <xref:System.IO.StreamReader>, see [How to: Read a Text File One Line at a Time](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6296d-105">Soubory, které se používají v tomto příkladu se vytvoří v tématu [postupy: zápis do textového souboru](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="6296d-105">The files that are used in this example are created in the topic [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6296d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6296d-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6296d-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6296d-107">Compiling the Code</span></span>  
 <span data-ttu-id="6296d-108">Zkopírujte kód a vložte ho do konzolové aplikace jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="6296d-108">Copy the code and paste it into a C# console application.</span></span>  
  
 <span data-ttu-id="6296d-109">Pokud nepoužíváte textových souborů z [postupy: zápis do textového souboru](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), nahraďte argument `ReadAllText` a `ReadAllLines` s odpovídající název a cesta k souboru ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="6296d-109">If you are not using the text files from [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6296d-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="6296d-110">Robust Programming</span></span>  
 <span data-ttu-id="6296d-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="6296d-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="6296d-112">Soubor neexistuje, nebo neexistuje v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="6296d-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="6296d-113">Zkontrolujte cestu a zadání názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="6296d-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6296d-114">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6296d-114">.NET Framework Security</span></span>  
 <span data-ttu-id="6296d-115">Nespoléhejte na název souboru můžete zjistit obsah souboru.</span><span class="sxs-lookup"><span data-stu-id="6296d-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="6296d-116">Například soubor `myFile.cs` nemusí být zdrojový soubor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="6296d-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6296d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6296d-117">See Also</span></span>

- <xref:System.IO?displayProperty=nameWithType>  
- [<span data-ttu-id="6296d-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6296d-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6296d-119">Systém souborů a registr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="6296d-119">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
