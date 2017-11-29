---
title: "Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 40fd9f64b5702f5205b7817f3de1e0a8709c5a63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-plinq"></a><span data-ttu-id="23e67-102">Postupy: Procházení adresářů se soubory pomocí jazyka PLINQ</span><span class="sxs-lookup"><span data-stu-id="23e67-102">How to: Iterate File Directories with PLINQ</span></span>
<span data-ttu-id="23e67-103">Tento příklad ukazuje dva způsoby jednoduché učinit paralelní operací na souborové adresáře.</span><span class="sxs-lookup"><span data-stu-id="23e67-103">This example shows two simple ways to parallelize operations on file directories.</span></span> <span data-ttu-id="23e67-104">První dotaz používá <xref:System.IO.Directory.GetFiles%2A> metoda k vyplnění pole názvy souborů v adresáři a všechny podadresáře.</span><span class="sxs-lookup"><span data-stu-id="23e67-104">The first query uses the <xref:System.IO.Directory.GetFiles%2A> method to populate an array of file names in a directory and all subdirectories.</span></span> <span data-ttu-id="23e67-105">Tato metoda nevrátí, dokud se vyplní celé pole, a proto ho můžou představovat latence na začátku operaci.</span><span class="sxs-lookup"><span data-stu-id="23e67-105">This method does not return until the entire array is populated, and therefore it can introduce latency at the beginning of the operation.</span></span> <span data-ttu-id="23e67-106">Ale po naplnění pole PLINQ může zpracovat paralelní velmi rychle.</span><span class="sxs-lookup"><span data-stu-id="23e67-106">However, after the array is populated, PLINQ can process it in parallel very quickly.</span></span>  
  
 <span data-ttu-id="23e67-107">Druhý dotaz používá statickou <xref:System.IO.Directory.EnumerateDirectories%2A> a <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metody, které začít vracet výsledky okamžitě.</span><span class="sxs-lookup"><span data-stu-id="23e67-107">The second query uses the static <xref:System.IO.Directory.EnumerateDirectories%2A> and <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> methods which begin returning results immediately.</span></span> <span data-ttu-id="23e67-108">Tento přístup může být rychlejší při jsou iterování přes stromy velké adresáře, i když bude čas zpracování ve srovnání s prvním příkladu může záviset na mnoha faktorech.</span><span class="sxs-lookup"><span data-stu-id="23e67-108">This approach can be faster when you are iterating over large directory trees, although the processing time compared to the first example can depend on many factors.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="23e67-109">Tyto příklady jsou určeny k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu.</span><span class="sxs-lookup"><span data-stu-id="23e67-109">These examples are intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="23e67-110">Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="23e67-110">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23e67-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="23e67-111">Example</span></span>  
 <span data-ttu-id="23e67-112">Následující příklad ukazuje, jak Iterujte přes souborové adresáře v jednoduchého scénáře, když máte přístup do všech adresářů ve stromu, velikosti souborů nejsou velmi velké a čas přístupu nejsou důležité.</span><span class="sxs-lookup"><span data-stu-id="23e67-112">The following example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes are not very large, and the access times are not significant.</span></span> <span data-ttu-id="23e67-113">Tento postup zahrnuje období latence na začátku při je vytvářen pole názvy souborů.</span><span class="sxs-lookup"><span data-stu-id="23e67-113">This approach involves a period of latency at the beginning while the array of file names is being constructed.</span></span>  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a><span data-ttu-id="23e67-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="23e67-114">Example</span></span>  
 <span data-ttu-id="23e67-115">Následující příklad ukazuje, jak Iterujte přes souborové adresáře v jednoduchého scénáře, když máte přístup do všech adresářů ve stromu, velikosti souborů nejsou velmi velké a čas přístupu nejsou důležité.</span><span class="sxs-lookup"><span data-stu-id="23e67-115">The following example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes are not very large, and the access times are not significant.</span></span> <span data-ttu-id="23e67-116">Tento přístup začne generovala výsledky rychleji než předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="23e67-116">This approach begins producing results faster than the previous example.</span></span>  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 <span data-ttu-id="23e67-117">Při použití <xref:System.IO.Directory.GetFiles%2A>, ujistěte se, zda máte dostatečná oprávnění na všechny adresáře ve stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="23e67-117">When using <xref:System.IO.Directory.GetFiles%2A>, be sure that you have sufficient permissions on all directories in the tree.</span></span> <span data-ttu-id="23e67-118">V opačném případě bude vyvolána výjimka, které budou vráceny žádné výsledky.</span><span class="sxs-lookup"><span data-stu-id="23e67-118">Otherwise an exception will be thrown and no results will be returned.</span></span> <span data-ttu-id="23e67-119">Při použití <xref:System.IO.Directory.EnumerateDirectories%2A> v PLINQ dotazu, je problematické zpracování výjimek vstupně-výstupních operací řádně způsobem, který umožňuje pokračovat iterace.</span><span class="sxs-lookup"><span data-stu-id="23e67-119">When using the <xref:System.IO.Directory.EnumerateDirectories%2A> in a PLINQ query, it is problematic to handle I/O exceptions in a graceful way that enables you to continue iterating.</span></span> <span data-ttu-id="23e67-120">Pokud váš kód musí zpracovat vstupně-výstupních operací nebo výjimky neoprávněného přístupu, pak byste měli zvážit postupuje podle [postupy: procházení adresářů se soubory pomocí paralelní třídy](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).</span><span class="sxs-lookup"><span data-stu-id="23e67-120">If your code must handle I/O or unauthorized access exceptions, then you should consider the approach described in [How to: Iterate File Directories with the Parallel Class](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).</span></span>  
  
 <span data-ttu-id="23e67-121">Pokud je latence vstupně-výstupních operací problém, například souborem vstupně-výstupní operace přes síť, zvažte použití mezi asynchronní vstupně-výstupních operací technik popsaných v [TPL a tradiční rozhraní .NET Framework asynchronní programování](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) a v tomto [příspěvku na blogu ](http://go.microsoft.com/fwlink/?LinkID=186458).</span><span class="sxs-lookup"><span data-stu-id="23e67-121">If I/O latency is an issue, for example with file I/O over a network, consider using one of the asynchronous I/O techniques described in [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) and in this [blog post](http://go.microsoft.com/fwlink/?LinkID=186458).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e67-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="23e67-122">See Also</span></span>  
 [<span data-ttu-id="23e67-123">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="23e67-123">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
