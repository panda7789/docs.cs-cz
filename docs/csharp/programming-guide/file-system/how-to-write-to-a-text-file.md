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
ms.openlocfilehash: 6d3f1bc238bd3129a25d4af29341c27d52b71ed8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333840"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="6d0f0-102">Postupy: Zápis do textového souboru (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6d0f0-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="6d0f0-103">Tyto příklady znázorňují různé způsoby zápisu textu do souboru.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="6d0f0-104">První dva příklady používají statické usnadňující metody na <xref:System.IO.File?displayProperty=nameWithType> třída pro psaní každý prvek všech `IEnumerable<string>` a řetězec do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="6d0f0-105">Příklad 3 ukazuje, jak přidat text do souboru při každém řádku jednotlivě zpracovat, protože zapisovat do souboru.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="6d0f0-106">Příklady 1 – 3 přepsat všechny existující obsah v souboru, ale příklad 4 ukazuje, jak přidat text do existující soubor.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="6d0f0-107">Tyto příklady všechny textové literály zápis do souborů.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-107">These examples all write string literals to files.</span></span> <span data-ttu-id="6d0f0-108">Pokud chcete k formátování textu zapisují do souboru, použijte <xref:System.String.Format%2A> metoda nebo C# [řetězec interpolace](../../../csharp/language-reference/tokens/interpolated.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../../csharp/language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d0f0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d0f0-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6d0f0-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="6d0f0-110">Robust Programming</span></span>  
 <span data-ttu-id="6d0f0-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="6d0f0-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="6d0f0-112">Soubor existuje a je určen jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-112">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="6d0f0-113">Název cesty je pravděpodobně příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-113">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="6d0f0-114">Disk je pravděpodobně plný.</span><span class="sxs-lookup"><span data-stu-id="6d0f0-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d0f0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d0f0-115">See Also</span></span>  
 [<span data-ttu-id="6d0f0-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6d0f0-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6d0f0-117">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="6d0f0-117">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="6d0f0-118">Ukázka: Uložit kolekci do úložiště aplikací</span><span class="sxs-lookup"><span data-stu-id="6d0f0-118">Sample: Save a collection to Application Storage</span></span>](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
