---
title: 'Postupy: kopírování adresářů'
description: Podívejte se, jak kopírovat adresáře pomocí vstupně-výstupních tříd, které synchronně kopírují obsah adresáře do jiného umístění.
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
ms.openlocfilehash: 65fe28c90a6cd6f0b3c8c32da19c1d9603900670
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662586"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="13b2d-103">Postupy: kopírování adresářů</span><span class="sxs-lookup"><span data-stu-id="13b2d-103">How to: Copy directories</span></span>
<span data-ttu-id="13b2d-104">Toto téma ukazuje, jak použít třídy v/v k synchronnímu zkopírování obsahu adresáře do jiného umístění.</span><span class="sxs-lookup"><span data-stu-id="13b2d-104">This topic demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="13b2d-105">Příklad asynchronního kopírování souborů najdete v tématu [asynchronní vstupně-výstupní operace se soubory](asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="13b2d-105">For an example of asynchronous file copy, see [Asynchronous file I/O](asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="13b2d-106">Tento příklad kopíruje podadresáře nastavením `copySubDirs` `DirectoryCopy` metody na `true` .</span><span class="sxs-lookup"><span data-stu-id="13b2d-106">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="13b2d-107">`DirectoryCopy`Metoda rekurzivně kopíruje podadresáře tím, že zavolá sebe sama do každého podadresáře, dokud nebudete moci kopírovat.</span><span class="sxs-lookup"><span data-stu-id="13b2d-107">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13b2d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="13b2d-108">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="13b2d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="13b2d-109">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="13b2d-110">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="13b2d-110">File and stream I/O</span></span>](index.md)
- [<span data-ttu-id="13b2d-111">Obecné vstupně-výstupní úlohy</span><span class="sxs-lookup"><span data-stu-id="13b2d-111">Common I/O tasks</span></span>](common-i-o-tasks.md)
- [<span data-ttu-id="13b2d-112">Asynchronní souborový vstup-výstup</span><span class="sxs-lookup"><span data-stu-id="13b2d-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)
