---
title: "CLRCreateInstance – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type: COM
f1_keywords: CLRCreateInstance
helpviewer_keywords: CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d95815dd0b2a1cdbddcb28a2e176bc12d3270ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="decfd-102">CLRCreateInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="decfd-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="decfd-103">Poskytuje jedno z tři rozhraní: [iclrmetahost –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [iclrmetahostpolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), nebo [iclrdebugging –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="decfd-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="decfd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="decfd-104">Syntax</span></span>  
  
```  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="decfd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="decfd-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="decfd-106">[v] Mezi tři identifikátory třídy: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy nebo CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="decfd-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="decfd-107">[v] Mezi tři identifikátorů rozhraní (IID): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy nebo IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="decfd-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="decfd-108">[out] Mezi tři rozhraní: [iclrmetahost –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [iclrmetahostpolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), nebo [iclrdebugging –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="decfd-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="decfd-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="decfd-109">Return Value</span></span>  
 <span data-ttu-id="decfd-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="decfd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="decfd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="decfd-111">HRESULT</span></span>|<span data-ttu-id="decfd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="decfd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="decfd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="decfd-113">S_OK</span></span>|<span data-ttu-id="decfd-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="decfd-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="decfd-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="decfd-115">E_POINTER</span></span>|<span data-ttu-id="decfd-116">`ppInterface`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="decfd-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="decfd-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="decfd-117">Remarks</span></span>  
 <span data-ttu-id="decfd-118">Následující tabulka uvádí podporované kombinace pro `clsid` a `riid`.</span><span class="sxs-lookup"><span data-stu-id="decfd-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="decfd-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="decfd-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="decfd-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="decfd-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="decfd-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="decfd-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="decfd-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="decfd-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="decfd-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="decfd-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="decfd-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="decfd-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="decfd-125">Následující kód ukazuje, jak používat `CLRCreateInstance` získat všechna tři rozhraní:</span><span class="sxs-lookup"><span data-stu-id="decfd-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="decfd-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="decfd-126">Requirements</span></span>  
 <span data-ttu-id="decfd-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="decfd-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="decfd-128">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="decfd-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="decfd-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="decfd-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="decfd-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="decfd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="decfd-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="decfd-131">See Also</span></span>  
 [<span data-ttu-id="decfd-132">Hostování</span><span class="sxs-lookup"><span data-stu-id="decfd-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
