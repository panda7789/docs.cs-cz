---
title: "Postupy: Kopírování adresářů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a5602a4e227f3cd17e4a7c9a086bee69d3e3e506
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="4eef4-102">Postupy: Kopírování adresářů</span><span class="sxs-lookup"><span data-stu-id="4eef4-102">How to: Copy Directories</span></span>
<span data-ttu-id="4eef4-103">Tento příklad znázorňuje, jakým způsobem lze pomocí vstupně-výstupních tříd synchronně zkopírovat obsah adresáře do jiného umístění.</span><span class="sxs-lookup"><span data-stu-id="4eef4-103">This example demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> <span data-ttu-id="4eef4-104">V tomto příkladu může uživatel zadat, zda se mají kopírovat také podadresáře.</span><span class="sxs-lookup"><span data-stu-id="4eef4-104">In this example, the user can specify whether to also copy the subdirectories.</span></span> <span data-ttu-id="4eef4-105">Při kopírování podadresářů kopíruje metoda uvedená v tomto příkladu rekurzivně podadresáře voláním sebe sama pro jednotlivé následné podadresáře, jsou-li k dispozici.</span><span class="sxs-lookup"><span data-stu-id="4eef4-105">If the subdirectories are copied, the method in this example recursively copies them by calling itself on each subsequent subdirectory until there are no more to copy.</span></span>  
  
 <span data-ttu-id="4eef4-106">Příklad asynchronně kopírování souborů naleznete v části [asynchronní vstup-výstup souboru](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="4eef4-106">For an example of copying files asynchronously, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4eef4-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4eef4-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4eef4-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="4eef4-108">See Also</span></span>  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [<span data-ttu-id="4eef4-109">Vstupně-výstupních souborů a proudů</span><span class="sxs-lookup"><span data-stu-id="4eef4-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="4eef4-110">Běžné vstupně-výstupní úlohy</span><span class="sxs-lookup"><span data-stu-id="4eef4-110">Common I/O Tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)  
 [<span data-ttu-id="4eef4-111">Asynchronní I/O soubory</span><span class="sxs-lookup"><span data-stu-id="4eef4-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
