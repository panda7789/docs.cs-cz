---
title: CoUninitializeCor – funkce
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3ce0b9a40d5375f563662d73964d28724209dcd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758291"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="fb128-102">CoUninitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="fb128-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="fb128-103">`CoUninitializeCor` je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="fb128-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb128-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb128-104">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="fb128-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb128-105">Remarks</span></span>  
 <span data-ttu-id="fb128-106">Modul common language runtime nemůže být uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="fb128-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="fb128-107">Modul runtime úplně odebrat ze spuštěného procesu, je nutné vypnout tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="fb128-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb128-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb128-108">See also</span></span>

- [<span data-ttu-id="fb128-109">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="fb128-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
