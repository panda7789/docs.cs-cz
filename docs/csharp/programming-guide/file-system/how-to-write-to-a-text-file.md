---
title: Jak zapisovat do textového souboru – Průvodce programováním v C#
description: Naučte se, jak napsat textový soubor pomocí jazyka C#. Podívejte se na několik příkladů kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: 4108163121d56268b810121ca3ae2b2c1338aeab
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301642"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="9cb89-104">Zápis do textového souboru (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9cb89-104">How to write to a text file (C# Programming Guide)</span></span>
<span data-ttu-id="9cb89-105">Tyto příklady znázorňují různé způsoby zápisu textu do souboru.</span><span class="sxs-lookup"><span data-stu-id="9cb89-105">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="9cb89-106">První dva příklady používají statické pohodlí pro <xref:System.IO.File?displayProperty=nameWithType> třídu pro zápis každého prvku libovolného `IEnumerable<string>` a řetězce do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="9cb89-106">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="9cb89-107">Příklad 3 ukazuje, jak přidat text do souboru, když je potřeba zpracovat jednotlivé řádky jednotlivě při zápisu do souboru.</span><span class="sxs-lookup"><span data-stu-id="9cb89-107">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="9cb89-108">Příklady 1-3 přepisují veškerý existující obsah v souboru, ale příklad 4 ukazuje, jak připojit text k existujícímu souboru.</span><span class="sxs-lookup"><span data-stu-id="9cb89-108">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="9cb89-109">Tyto příklady všechny zapisují řetězcové literály do souborů.</span><span class="sxs-lookup"><span data-stu-id="9cb89-109">These examples all write string literals to files.</span></span> <span data-ttu-id="9cb89-110">Pokud chcete naformátovat text zapsaný do souboru, použijte <xref:System.String.Format%2A> funkci nebo [řetězcové interpolace](../../language-reference/tokens/interpolated.md) v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="9cb89-110">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cb89-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="9cb89-111">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9cb89-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="9cb89-112">Robust Programming</span></span>  
 <span data-ttu-id="9cb89-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="9cb89-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="9cb89-114">Soubor existuje a je určen jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="9cb89-114">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="9cb89-115">Název cesty je pravděpodobně příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="9cb89-115">The path name may be too long.</span></span>  
  
- <span data-ttu-id="9cb89-116">Disk je pravděpodobně plný.</span><span class="sxs-lookup"><span data-stu-id="9cb89-116">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb89-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9cb89-117">See also</span></span>

- [<span data-ttu-id="9cb89-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="9cb89-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9cb89-119">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9cb89-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="9cb89-120">Ukázka: uložení kolekce do úložiště aplikace</span><span class="sxs-lookup"><span data-stu-id="9cb89-120">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
