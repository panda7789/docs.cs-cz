---
title: "Postupy: Zápis do textového souboru (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c576536947cdb4984d6e5ce67c8377fe23b354c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="a8654-102">Postupy: Zápis do textového souboru (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a8654-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="a8654-103">Tyto příklady znázorňují různé způsoby zápisu textu do souboru.</span><span class="sxs-lookup"><span data-stu-id="a8654-103">These examples show various ways to write text to a file.</span></span>  <span data-ttu-id="a8654-104">První dva příklady používají statické usnadňující metody na <xref:System.IO.File?displayProperty=nameWithType> třída pro psaní každý prvek žádné rozhraní IEnumerable\<řetězec > a řetězec do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="a8654-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any IEnumerable\<string> and a string to a text file.</span></span>  <span data-ttu-id="a8654-105">Příklad 3 ukazuje, jak přidat text do souboru při každém řádku jednotlivě zpracovat, protože zapisovat do souboru.</span><span class="sxs-lookup"><span data-stu-id="a8654-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span>  <span data-ttu-id="a8654-106">Příklady 1 – 3 přepsat všechny existující obsah v souboru, ale příklad 4 ukazuje, jak přidat text do existující soubor.</span><span class="sxs-lookup"><span data-stu-id="a8654-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="a8654-107">Tyto příklady všechny textové literály zápis do souborů, ale více pravděpodobně budete chtít použít <xref:System.String.Format%2A> metoda, která má mnoho ovládacích prvků pro zápis různé typy hodnot zarovnané vlevo nebo vpravo v poli, s nebo bez odsazení a tak dále.</span><span class="sxs-lookup"><span data-stu-id="a8654-107">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="a8654-108">Můžete také použít jazyka C# [řetězec interpolace](../../../csharp/language-reference/keywords/interpolated-strings.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="a8654-108">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8654-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8654-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 <span data-ttu-id="a8654-110">Tyto příklady všechny textové literály zápis do souborů, ale více pravděpodobně budete chtít použít <xref:System.String.Format%2A> metoda, která má mnoho ovládacích prvků pro zápis různé typy hodnot zarovnané vlevo nebo vpravo v poli, s nebo bez odsazení a tak dále.</span><span class="sxs-lookup"><span data-stu-id="a8654-110">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="a8654-111">Můžete také použít jazyka C# [řetězec interpolace](../../../csharp/language-reference/keywords/interpolated-strings.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="a8654-111">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a8654-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="a8654-112">Robust Programming</span></span>  
 <span data-ttu-id="a8654-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="a8654-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="a8654-114">Soubor existuje a je určen jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="a8654-114">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="a8654-115">Název cesty je pravděpodobně příliš dlouhý.</span><span class="sxs-lookup"><span data-stu-id="a8654-115">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="a8654-116">Disk je pravděpodobně plný.</span><span class="sxs-lookup"><span data-stu-id="a8654-116">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8654-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8654-117">See Also</span></span>  
 [<span data-ttu-id="a8654-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a8654-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a8654-119">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="a8654-119">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="a8654-120">Ukázka: Uložit kolekci do úložiště aplikací</span><span class="sxs-lookup"><span data-stu-id="a8654-120">Sample: Save a collection to Application Storage</span></span>](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
