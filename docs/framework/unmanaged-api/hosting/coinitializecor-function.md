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
ms.openlocfilehash: e8d65e739504e01a7d11b37d1b34d7313b13a5e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138339"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="3ee90-102">CoInitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="3ee90-102">CoInitializeCor Function</span></span>
<span data-ttu-id="3ee90-103">`CoInitializeCor` je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="3ee90-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ee90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ee90-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="3ee90-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ee90-105">Remarks</span></span>  
 <span data-ttu-id="3ee90-106">Chcete-li inicializovat modul CLR (Common Language Runtime), použijte buď [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [CorBindToCurrentRuntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="3ee90-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ee90-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ee90-107">Requirements</span></span>  
 <span data-ttu-id="3ee90-108">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3ee90-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee90-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ee90-109">See also</span></span>

- [<span data-ttu-id="3ee90-110">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="3ee90-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
