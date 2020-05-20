---
title: CoUninitializeEE – funkce
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: fa6297e926d53c02bb0d1af7b59b45b8ee152399
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616460"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="a29dd-102">CoUninitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="a29dd-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="a29dd-103">`CoUninitializeEE`je zastaralá a neposkytuje žádné funkce.</span><span class="sxs-lookup"><span data-stu-id="a29dd-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a29dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a29dd-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="a29dd-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a29dd-105">Remarks</span></span>  
 <span data-ttu-id="a29dd-106">Modul pro spuštění společného jazykového modulu runtime nelze uvolnit z procesu.</span><span class="sxs-lookup"><span data-stu-id="a29dd-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="a29dd-107">Pro vypnutí volání prováděcího modulu [CorExitProcess –](corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="a29dd-107">To shut down the execution engine call [CorExitProcess](corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29dd-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="a29dd-108">See also</span></span>

- [<span data-ttu-id="a29dd-109">CoInitializeEE – funkce</span><span class="sxs-lookup"><span data-stu-id="a29dd-109">CoInitializeEE Function</span></span>](coinitializeee-function.md)
- [<span data-ttu-id="a29dd-110">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="a29dd-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
