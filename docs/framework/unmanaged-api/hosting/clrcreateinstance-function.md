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
ms.openlocfilehash: f10fe48bc2b61a9de5d0703720629f31531c1ea1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="ce1e8-102">CLRCreateInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="ce1e8-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="ce1e8-103">Poskytuje jedno z tři rozhraní: [iclrmetahost –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [iclrmetahostpolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), nebo [iclrdebugging –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ce1e8-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce1e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce1e8-104">Syntax</span></span>  
  
```  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce1e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce1e8-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="ce1e8-106">[v] Mezi tři identifikátory třídy: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy nebo CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="ce1e8-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="ce1e8-107">[v] Mezi tři identifikátorů rozhraní (IID): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy nebo IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="ce1e8-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="ce1e8-108">[out] Mezi tři rozhraní: [iclrmetahost –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [iclrmetahostpolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), nebo [iclrdebugging –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ce1e8-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce1e8-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ce1e8-109">Return Value</span></span>  
 <span data-ttu-id="ce1e8-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="ce1e8-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ce1e8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce1e8-111">HRESULT</span></span>|<span data-ttu-id="ce1e8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ce1e8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce1e8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce1e8-113">S_OK</span></span>|<span data-ttu-id="ce1e8-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="ce1e8-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="ce1e8-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ce1e8-115">E_POINTER</span></span>|<span data-ttu-id="ce1e8-116">`ppInterface`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ce1e8-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce1e8-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce1e8-117">Remarks</span></span>  
 <span data-ttu-id="ce1e8-118">Následující tabulka uvádí podporované kombinace pro `clsid` a `riid`.</span><span class="sxs-lookup"><span data-stu-id="ce1e8-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="ce1e8-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="ce1e8-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="ce1e8-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="ce1e8-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="ce1e8-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="ce1e8-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="ce1e8-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="ce1e8-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="ce1e8-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="ce1e8-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="ce1e8-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="ce1e8-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="ce1e8-125">Následující kód ukazuje, jak používat `CLRCreateInstance` získat všechna tři rozhraní:</span><span class="sxs-lookup"><span data-stu-id="ce1e8-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="ce1e8-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce1e8-126">Requirements</span></span>  
 <span data-ttu-id="ce1e8-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce1e8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce1e8-128">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ce1e8-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ce1e8-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ce1e8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce1e8-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce1e8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce1e8-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce1e8-131">See Also</span></span>  
 [<span data-ttu-id="ce1e8-132">Hostování</span><span class="sxs-lookup"><span data-stu-id="ce1e8-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
