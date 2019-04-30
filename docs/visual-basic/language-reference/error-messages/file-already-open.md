---
title: Soubor již je otevřen.
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 401801c7c9072ce11f9eafdb84f2b377669ae545
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802645"
---
# <a name="file-already-open"></a><span data-ttu-id="4cfac-102">Soubor již je otevřen.</span><span class="sxs-lookup"><span data-stu-id="4cfac-102">File already open</span></span>
<span data-ttu-id="4cfac-103">Někdy musí zavřít soubor před jiný `FileOpen` nebo může dojít k jiné operace.</span><span class="sxs-lookup"><span data-stu-id="4cfac-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="4cfac-104">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="4cfac-104">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="4cfac-105">Režim sekvenční výstupu `FileOpen` byla provedena operace pro soubor, který je již otevřen</span><span class="sxs-lookup"><span data-stu-id="4cfac-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
- <span data-ttu-id="4cfac-106">Příkaz odkazuje na otevřený soubor.</span><span class="sxs-lookup"><span data-stu-id="4cfac-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4cfac-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4cfac-107">To correct this error</span></span>  
  
1. <span data-ttu-id="4cfac-108">Zavřete soubor před provedením příkazu.</span><span class="sxs-lookup"><span data-stu-id="4cfac-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cfac-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cfac-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
