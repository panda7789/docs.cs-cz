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
ms.openlocfilehash: 67e98750af589a3deb5e9d0d51f8b1204fdaad84
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240304"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="51075-102">Postupy: Čtení z textového souboru (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="51075-102">How to: Read From a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="51075-103">Tento příklad přečte obsah textového souboru s použitím statické metody <xref:System.IO.File.ReadAllText%2A> a <xref:System.IO.File.ReadAllLines%2A> z <xref:System.IO.File?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="51075-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
 <span data-ttu-id="51075-104">Příklad, který používá <xref:System.IO.StreamReader>, naleznete v tématu [jak: Přečíst textový soubor jeden řádek v čase](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="51075-104">For an example that uses <xref:System.IO.StreamReader>, see [How to: Read a Text File One Line at a Time](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51075-105">Soubory, které se používají v tomto příkladu se vytvoří v tématu [jak: Zápis do textového souboru](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="51075-105">The files that are used in this example are created in the topic [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51075-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="51075-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="51075-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="51075-107">Compiling the Code</span></span>  
 <span data-ttu-id="51075-108">Zkopírujte kód a vložte ho do konzolové aplikace jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="51075-108">Copy the code and paste it into a C# console application.</span></span>  
  
 <span data-ttu-id="51075-109">Pokud nepoužíváte textových souborů z [jak: Zápis do textového souboru](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), nahraďte argument `ReadAllText` a `ReadAllLines` s odpovídající název a cesta k souboru ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="51075-109">If you are not using the text files from [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="51075-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="51075-110">Robust Programming</span></span>  
 <span data-ttu-id="51075-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="51075-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="51075-112">Soubor neexistuje, nebo neexistuje v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="51075-112">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="51075-113">Zkontrolujte cestu a zadání názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="51075-113">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="51075-114">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="51075-114">.NET Framework Security</span></span>  
 <span data-ttu-id="51075-115">Nespoléhejte na název souboru můžete zjistit obsah souboru.</span><span class="sxs-lookup"><span data-stu-id="51075-115">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="51075-116">Například soubor `myFile.cs` nemusí být zdrojový soubor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="51075-116">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51075-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="51075-117">See Also</span></span>

- <xref:System.IO?displayProperty=nameWithType>  
- [<span data-ttu-id="51075-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="51075-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="51075-119">Systém souborů a registr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="51075-119">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
