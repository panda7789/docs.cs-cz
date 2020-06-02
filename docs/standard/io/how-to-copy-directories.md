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
ms.openlocfilehash: f71f428037f33fdbc692ca2f02a4c767998d684e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288573"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="ba7e1-102">Postupy: kopírování adresářů</span><span class="sxs-lookup"><span data-stu-id="ba7e1-102">How to: Copy directories</span></span>
<span data-ttu-id="ba7e1-103">Toto téma ukazuje, jak použít třídy v/v k synchronnímu zkopírování obsahu adresáře do jiného umístění.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-103">This topic demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="ba7e1-104">Příklad asynchronního kopírování souborů najdete v tématu [asynchronní vstupně-výstupní operace se soubory](asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="ba7e1-104">For an example of asynchronous file copy, see [Asynchronous file I/O](asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="ba7e1-105">Tento příklad kopíruje podadresáře nastavením `copySubDirs` `DirectoryCopy` metody na `true` .</span><span class="sxs-lookup"><span data-stu-id="ba7e1-105">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="ba7e1-106">`DirectoryCopy`Metoda rekurzivně kopíruje podadresáře tím, že zavolá sebe sama do každého podadresáře, dokud nebudete moci kopírovat.</span><span class="sxs-lookup"><span data-stu-id="ba7e1-106">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba7e1-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba7e1-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="ba7e1-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba7e1-108">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="ba7e1-109">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="ba7e1-109">File and stream I/O</span></span>](index.md)
- [<span data-ttu-id="ba7e1-110">Obecné vstupně-výstupní úlohy</span><span class="sxs-lookup"><span data-stu-id="ba7e1-110">Common I/O tasks</span></span>](common-i-o-tasks.md)
- [<span data-ttu-id="ba7e1-111">Asynchronní souborový vstup-výstup</span><span class="sxs-lookup"><span data-stu-id="ba7e1-111">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)
