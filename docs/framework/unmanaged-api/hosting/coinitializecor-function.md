---
title: CoInitializeCor – funkce
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
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
ms.openlocfilehash: 91315e8af0cc46a3450a7515b885988cffe34927
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429985"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="c7951-102">CoInitializeCor – funkce</span><span class="sxs-lookup"><span data-stu-id="c7951-102">CoInitializeCor Function</span></span>
<span data-ttu-id="c7951-103">`CoInitializeCor` je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="c7951-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7951-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7951-104">Syntax</span></span>  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c7951-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7951-105">Remarks</span></span>  
 <span data-ttu-id="c7951-106">K chybě při inicializaci modulu CLR, použijte buď [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [corbindtocurrentruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="c7951-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7951-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7951-107">Requirements</span></span>  
 <span data-ttu-id="c7951-108">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c7951-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7951-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7951-109">See Also</span></span>  
 [<span data-ttu-id="c7951-110">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="c7951-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
