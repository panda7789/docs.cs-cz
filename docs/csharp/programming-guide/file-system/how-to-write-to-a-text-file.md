---
title: 'Postupy: Zápis do textového souboru (Průvodce programováním v C#)'
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: ca08651bfce1a92f65a3e6fec7da3411a22bffb2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43780072"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="ae600-102">Postupy: Zápis do textového souboru (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ae600-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="ae600-103">Tyto příklady znázorňují různé způsoby zápisu textu do souboru.</span><span class="sxs-lookup"><span data-stu-id="ae600-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="ae600-104">První dva příklady používají statické pohodlí metody <xref:System.IO.File?displayProperty=nameWithType> třídu pro zápis každý prvek žádné `IEnumerable<string>` a řetězce do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="ae600-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="ae600-105">Příklad 3 ukazuje, jak přidat text do souboru, když máte při psaní do souboru zpracovávat každý řádek zvlášť.</span><span class="sxs-lookup"><span data-stu-id="ae600-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="ae600-106">Příklady 1 – 3 přepisují veškerý existující obsah v souboru, ale příkladu 4 se dozvíte, jak lze připojit text k existujícímu souboru.</span><span class="sxs-lookup"><span data-stu-id="ae600-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="ae600-107">Všechny tyto příklady zapisují řetězcové literály do souborů.</span><span class="sxs-lookup"><span data-stu-id="ae600-107">These examples all write string literals to files.</span></span> <span data-ttu-id="ae600-108">Pokud chcete k formátování textu zapsána do souboru, použijte <xref:System.String.Format%2A> metody nebo C# [interpolace](../../../csharp/language-reference/tokens/interpolated.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="ae600-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../../csharp/language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae600-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae600-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ae600-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ae600-110">Robust Programming</span></span>  
 <span data-ttu-id="ae600-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="ae600-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ae600-112">Soubor existuje a je určen jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="ae600-112">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="ae600-113">Název cesty je pravděpodobně příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="ae600-113">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="ae600-114">Disk je pravděpodobně plný.</span><span class="sxs-lookup"><span data-stu-id="ae600-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae600-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae600-115">See Also</span></span>

- [<span data-ttu-id="ae600-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ae600-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ae600-117">Systém souborů a registr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="ae600-117">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
- [<span data-ttu-id="ae600-118">Ukázka: Ukládání kolekce do úložiště aplikací</span><span class="sxs-lookup"><span data-stu-id="ae600-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
