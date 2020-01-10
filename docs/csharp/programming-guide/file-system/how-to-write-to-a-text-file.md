---
title: Postup zápisu do textového souboru – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: ac16fb971eae5654a55e2f1753d78a6458f03315
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712244"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="8fc83-102">Zápis do textového souboru (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="8fc83-102">How to write to a text file (C# Programming Guide)</span></span>
<span data-ttu-id="8fc83-103">Tyto příklady znázorňují různé způsoby zápisu textu do souboru.</span><span class="sxs-lookup"><span data-stu-id="8fc83-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="8fc83-104">První dva příklady používají statické praktické metody pro třídu <xref:System.IO.File?displayProperty=nameWithType> k zápisu každého prvku `IEnumerable<string>` a řetězce do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="8fc83-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="8fc83-105">Příklad 3 ukazuje, jak přidat text do souboru, když je potřeba zpracovat jednotlivé řádky jednotlivě při zápisu do souboru.</span><span class="sxs-lookup"><span data-stu-id="8fc83-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="8fc83-106">Příklady 1-3 přepisují veškerý existující obsah v souboru, ale příklad 4 ukazuje, jak připojit text k existujícímu souboru.</span><span class="sxs-lookup"><span data-stu-id="8fc83-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="8fc83-107">Tyto příklady všechny zapisují řetězcové literály do souborů.</span><span class="sxs-lookup"><span data-stu-id="8fc83-107">These examples all write string literals to files.</span></span> <span data-ttu-id="8fc83-108">Pokud chcete naformátovat text zapsaný do souboru, použijte funkci <xref:System.String.Format%2A> nebo C# [řetězcové interpolace](../../language-reference/tokens/interpolated.md) .</span><span class="sxs-lookup"><span data-stu-id="8fc83-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fc83-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8fc83-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8fc83-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="8fc83-110">Robust Programming</span></span>  
 <span data-ttu-id="8fc83-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="8fc83-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="8fc83-112">Soubor existuje a je určen jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="8fc83-112">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="8fc83-113">Název cesty je pravděpodobně příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="8fc83-113">The path name may be too long.</span></span>  
  
- <span data-ttu-id="8fc83-114">Disk je pravděpodobně plný.</span><span class="sxs-lookup"><span data-stu-id="8fc83-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc83-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fc83-115">See also</span></span>

- [<span data-ttu-id="8fc83-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8fc83-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8fc83-117">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="8fc83-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="8fc83-118">Ukázka: uložení kolekce do úložiště aplikace</span><span class="sxs-lookup"><span data-stu-id="8fc83-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
