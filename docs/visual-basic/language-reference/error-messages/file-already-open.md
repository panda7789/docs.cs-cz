---
title: Soubor již je otevřen.
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 75a08b411a4afd7ea8e11953f1d465b082faa712
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586667"
---
# <a name="file-already-open"></a><span data-ttu-id="7bd38-102">Soubor již je otevřen.</span><span class="sxs-lookup"><span data-stu-id="7bd38-102">File already open</span></span>
<span data-ttu-id="7bd38-103">Někdy soubor musí být uzavřeny před jiné `FileOpen` nebo může dojít, jiná operace.</span><span class="sxs-lookup"><span data-stu-id="7bd38-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="7bd38-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="7bd38-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="7bd38-105">Režim sekvenční výstup `FileOpen` byla provedena operace pro soubor, který je již otevřeno</span><span class="sxs-lookup"><span data-stu-id="7bd38-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="7bd38-106">Příkaz odkazuje na soubor otevřený.</span><span class="sxs-lookup"><span data-stu-id="7bd38-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7bd38-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7bd38-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="7bd38-108">Zavřete soubor před provedením příkazu.</span><span class="sxs-lookup"><span data-stu-id="7bd38-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd38-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="7bd38-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
