---
title: "Soubor již je otevřen."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3305831e840510e3f0b5bcb8bf847e39ea3ee4ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="file-already-open"></a><span data-ttu-id="a94e6-102">Soubor již je otevřen.</span><span class="sxs-lookup"><span data-stu-id="a94e6-102">File already open</span></span>
<span data-ttu-id="a94e6-103">Někdy soubor musí být uzavřeny před jiné `FileOpen` nebo může dojít, jiná operace.</span><span class="sxs-lookup"><span data-stu-id="a94e6-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="a94e6-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="a94e6-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="a94e6-105">Režim sekvenční výstup `FileOpen` byla provedena operace pro soubor, který je již otevřeno</span><span class="sxs-lookup"><span data-stu-id="a94e6-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="a94e6-106">Příkaz odkazuje na soubor otevřený.</span><span class="sxs-lookup"><span data-stu-id="a94e6-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a94e6-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a94e6-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="a94e6-108">Zavřete soubor před provedením příkazu.</span><span class="sxs-lookup"><span data-stu-id="a94e6-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a94e6-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a94e6-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
