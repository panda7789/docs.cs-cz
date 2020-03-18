---
title: Jak psát do textového souboru - C# Programovací průvodce
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: ac16fb971eae5654a55e2f1753d78a6458f03315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712244"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="98e6f-102">Jak psát do textového souboru (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="98e6f-102">How to write to a text file (C# Programming Guide)</span></span>
<span data-ttu-id="98e6f-103">Tyto příklady znázorňují různé způsoby zápisu textu do souboru.</span><span class="sxs-lookup"><span data-stu-id="98e6f-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="98e6f-104">První dva příklady používají statické <xref:System.IO.File?displayProperty=nameWithType> metody pohodlí na třídě `IEnumerable<string>` zapsat každý prvek any a řetězec do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="98e6f-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="98e6f-105">Příklad 3 ukazuje, jak přidat text do souboru, když je třeba zpracovat každý řádek jednotlivě při zápisu do souboru.</span><span class="sxs-lookup"><span data-stu-id="98e6f-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="98e6f-106">Příklady 1-3 přepsat veškerý existující obsah v souboru, ale příklad 4 ukazuje, jak připojit text k existujícímu souboru.</span><span class="sxs-lookup"><span data-stu-id="98e6f-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="98e6f-107">Tyto příklady všechny zápis y řetězcové literály do souborů.</span><span class="sxs-lookup"><span data-stu-id="98e6f-107">These examples all write string literals to files.</span></span> <span data-ttu-id="98e6f-108">Pokud chcete formátovat text napsaný do <xref:System.String.Format%2A> souboru, použijte metodu nebo funkci [interpolace řetězce](../../language-reference/tokens/interpolated.md) C#.</span><span class="sxs-lookup"><span data-stu-id="98e6f-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98e6f-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="98e6f-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="98e6f-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="98e6f-110">Robust Programming</span></span>  
 <span data-ttu-id="98e6f-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="98e6f-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="98e6f-112">Soubor existuje a je určen jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="98e6f-112">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="98e6f-113">Název cesty je pravděpodobně příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="98e6f-113">The path name may be too long.</span></span>  
  
- <span data-ttu-id="98e6f-114">Disk je pravděpodobně plný.</span><span class="sxs-lookup"><span data-stu-id="98e6f-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e6f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="98e6f-115">See also</span></span>

- [<span data-ttu-id="98e6f-116">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="98e6f-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="98e6f-117">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="98e6f-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="98e6f-118">Ukázka: Uložení kolekce do úložiště aplikací</span><span class="sxs-lookup"><span data-stu-id="98e6f-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
