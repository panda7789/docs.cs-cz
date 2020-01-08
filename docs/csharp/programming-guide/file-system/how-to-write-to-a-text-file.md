---
title: Postup zápisu do textového souboru – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: c0b6646e0d7f453dc9021a7470a3671f11ea0653
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635415"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="13da0-102">Zápis do textového souboru (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="13da0-102">How to write to a text file (C# Programming Guide)</span></span>
<span data-ttu-id="13da0-103">Tyto příklady znázorňují různé způsoby zápisu textu do souboru.</span><span class="sxs-lookup"><span data-stu-id="13da0-103">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="13da0-104">První dva příklady používají statické praktické metody pro třídu <xref:System.IO.File?displayProperty=nameWithType> k zápisu každého prvku `IEnumerable<string>` a řetězce do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="13da0-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="13da0-105">Příklad 3 ukazuje, jak přidat text do souboru, když je potřeba zpracovat jednotlivé řádky jednotlivě při zápisu do souboru.</span><span class="sxs-lookup"><span data-stu-id="13da0-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="13da0-106">Příklady 1-3 přepisují veškerý existující obsah v souboru, ale příklad 4 ukazuje, jak připojit text k existujícímu souboru.</span><span class="sxs-lookup"><span data-stu-id="13da0-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="13da0-107">Tyto příklady všechny zapisují řetězcové literály do souborů.</span><span class="sxs-lookup"><span data-stu-id="13da0-107">These examples all write string literals to files.</span></span> <span data-ttu-id="13da0-108">Pokud chcete naformátovat text zapsaný do souboru, použijte funkci <xref:System.String.Format%2A> nebo C# [řetězcové interpolace](../../language-reference/tokens/interpolated.md) .</span><span class="sxs-lookup"><span data-stu-id="13da0-108">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13da0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="13da0-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="13da0-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="13da0-110">Robust Programming</span></span>  
 <span data-ttu-id="13da0-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="13da0-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="13da0-112">Soubor existuje a je určen jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="13da0-112">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="13da0-113">Název cesty je pravděpodobně příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="13da0-113">The path name may be too long.</span></span>  
  
- <span data-ttu-id="13da0-114">Disk je pravděpodobně plný.</span><span class="sxs-lookup"><span data-stu-id="13da0-114">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13da0-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13da0-115">See also</span></span>

- [<span data-ttu-id="13da0-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="13da0-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="13da0-117">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="13da0-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="13da0-118">Ukázka: uložení kolekce do úložiště aplikace</span><span class="sxs-lookup"><span data-stu-id="13da0-118">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
