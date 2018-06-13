---
title: 'Postupy: Kopírování adresářů'
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1cfe07af216da1c35b093a1ca23e4d48c60a7bfe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571232"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="61fd7-102">Postupy: Kopírování adresářů</span><span class="sxs-lookup"><span data-stu-id="61fd7-102">How to: Copy Directories</span></span>
<span data-ttu-id="61fd7-103">Tento příklad znázorňuje, jakým způsobem lze pomocí vstupně-výstupních tříd synchronně zkopírovat obsah adresáře do jiného umístění.</span><span class="sxs-lookup"><span data-stu-id="61fd7-103">This example demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> <span data-ttu-id="61fd7-104">V tomto příkladu může uživatel zadat, zda se mají kopírovat také podadresáře.</span><span class="sxs-lookup"><span data-stu-id="61fd7-104">In this example, the user can specify whether to also copy the subdirectories.</span></span> <span data-ttu-id="61fd7-105">Při kopírování podadresářů kopíruje metoda uvedená v tomto příkladu rekurzivně podadresáře voláním sebe sama pro jednotlivé následné podadresáře, jsou-li k dispozici.</span><span class="sxs-lookup"><span data-stu-id="61fd7-105">If the subdirectories are copied, the method in this example recursively copies them by calling itself on each subsequent subdirectory until there are no more to copy.</span></span>  
  
 <span data-ttu-id="61fd7-106">Příklad asynchronně kopírování souborů naleznete v části [asynchronní vstup-výstup souboru](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="61fd7-106">For an example of copying files asynchronously, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="61fd7-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="61fd7-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="61fd7-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="61fd7-108">See Also</span></span>  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [<span data-ttu-id="61fd7-109">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="61fd7-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="61fd7-110">Obecné vstupně-výstupní úlohy</span><span class="sxs-lookup"><span data-stu-id="61fd7-110">Common I/O Tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)  
 [<span data-ttu-id="61fd7-111">Asynchronní vstupně-výstupní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="61fd7-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
