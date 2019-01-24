---
title: Soubor již je otevřen.
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: cda72e03eb5c2469b8106957a0c50fbfa5314549
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567032"
---
# <a name="file-already-open"></a><span data-ttu-id="63626-102">Soubor již je otevřen.</span><span class="sxs-lookup"><span data-stu-id="63626-102">File already open</span></span>
<span data-ttu-id="63626-103">Někdy musí zavřít soubor před jiný `FileOpen` nebo může dojít k jiné operace.</span><span class="sxs-lookup"><span data-stu-id="63626-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="63626-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="63626-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="63626-105">Režim sekvenční výstupu `FileOpen` byla provedena operace pro soubor, který je již otevřen</span><span class="sxs-lookup"><span data-stu-id="63626-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="63626-106">Příkaz odkazuje na otevřený soubor.</span><span class="sxs-lookup"><span data-stu-id="63626-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="63626-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="63626-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="63626-108">Zavřete soubor před provedením příkazu.</span><span class="sxs-lookup"><span data-stu-id="63626-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63626-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63626-109">See also</span></span>
- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
