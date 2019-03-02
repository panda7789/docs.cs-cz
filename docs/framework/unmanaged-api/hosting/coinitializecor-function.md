---
title: CoInitializeCor – funkce
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 556d26ac7e4fb8847f132d19bd2e749aff345abf
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211842"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="e6438-102">CoInitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="e6438-102">CoInitializeCor Function</span></span>
<span data-ttu-id="e6438-103">`CoInitializeCor` je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="e6438-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6438-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6438-104">Syntax</span></span>  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="e6438-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6438-105">Remarks</span></span>  
 <span data-ttu-id="e6438-106">Pokud chcete inicializovat modul common language runtime, použijte buď [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [corbindtocurrentruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="e6438-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6438-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6438-107">Requirements</span></span>  
 <span data-ttu-id="e6438-108">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e6438-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6438-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6438-109">See also</span></span>
- [<span data-ttu-id="e6438-110">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="e6438-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
