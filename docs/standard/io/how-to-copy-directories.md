---
title: 'Postupy: kopírování adresářů'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: 132ce0b887f7c314311e294567c546bded9a89a0
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627388"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="763cc-102">Postupy: kopírování adresářů</span><span class="sxs-lookup"><span data-stu-id="763cc-102">How to: Copy directories</span></span>
<span data-ttu-id="763cc-103">Toto téma ukazuje, jak použít třídy v/v k synchronnímu zkopírování obsahu adresáře do jiného umístění.</span><span class="sxs-lookup"><span data-stu-id="763cc-103">This topic demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> 

<span data-ttu-id="763cc-104">Příklad asynchronního kopírování souborů najdete v tématu [asynchronní vstupně-výstupní operace se soubory](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="763cc-104">For an example of asynchronous file copy, see [Asynchronous file I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span> 

<span data-ttu-id="763cc-105">Tento příklad kopíruje podadresáře nastavením `copySubDirs` metody `DirectoryCopy` na `true`.</span><span class="sxs-lookup"><span data-stu-id="763cc-105">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="763cc-106">Metoda `DirectoryCopy` rekurzivně kopíruje podadresáře tím, že se zavolá sám na každý podadresář, dokud nebudete moci kopírovat.</span><span class="sxs-lookup"><span data-stu-id="763cc-106">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="763cc-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="763cc-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="763cc-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="763cc-108">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="763cc-109">Vstupně-výstupní operace se soubory a datovým proudem</span><span class="sxs-lookup"><span data-stu-id="763cc-109">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="763cc-110">Běžné vstupně-výstupní úlohy</span><span class="sxs-lookup"><span data-stu-id="763cc-110">Common I/O tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)
- [<span data-ttu-id="763cc-111">I/O asynchronní soubory</span><span class="sxs-lookup"><span data-stu-id="763cc-111">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
