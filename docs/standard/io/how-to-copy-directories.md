---
title: 'Postup: Kopírování adresářů'
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
ms.openlocfilehash: 5d40db7f902dac8bd6bbdc1510be8e56a321be30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159452"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="a1ac4-102">Postup: Kopírování adresářů</span><span class="sxs-lookup"><span data-stu-id="a1ac4-102">How to: Copy directories</span></span>
<span data-ttu-id="a1ac4-103">Toto téma ukazuje, jak používat vstupně-v třídy synchronně kopírovat obsah adresáře do jiného umístění.</span><span class="sxs-lookup"><span data-stu-id="a1ac4-103">This topic demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="a1ac4-104">Příklad asynchronní kopie souboru naleznete [v tématu V/V. asynchronního souboru](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="a1ac4-104">For an example of asynchronous file copy, see [Asynchronous file I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="a1ac4-105">Tento příklad zkopíruje podadresáře `DirectoryCopy` nastavením `true` `copySubDirs` metody na .</span><span class="sxs-lookup"><span data-stu-id="a1ac4-105">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="a1ac4-106">Metoda `DirectoryCopy` rekurzivně zkopíruje podadresáře voláním sebe sama v každém podadresáři, dokud nejsou k dispozici žádné další kopírování.</span><span class="sxs-lookup"><span data-stu-id="a1ac4-106">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1ac4-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1ac4-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="a1ac4-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1ac4-108">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="a1ac4-109">Vstupně-tono-videa</span><span class="sxs-lookup"><span data-stu-id="a1ac4-109">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="a1ac4-110">Běžné vstupně-no úkoly</span><span class="sxs-lookup"><span data-stu-id="a1ac4-110">Common I/O tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)
- [<span data-ttu-id="a1ac4-111">Vstupně-nosný soubor asynchronní soubor</span><span class="sxs-lookup"><span data-stu-id="a1ac4-111">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
