---
title: CLRCreateInstance – funkce
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
ms.openlocfilehash: c1d796c6ef5f707f865a60023899d3b451c2085b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131956"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="5ff95-102">CLRCreateInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="5ff95-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="5ff95-103">Poskytuje jedno ze tří rozhraní: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)nebo [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5ff95-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ff95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ff95-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ff95-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ff95-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="5ff95-106">pro Jeden ze tří identifikátorů třídy: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy nebo CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="5ff95-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="5ff95-107">pro Jeden ze tří identifikátorů rozhraní (IID): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy nebo IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="5ff95-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="5ff95-108">mimo Jedno ze tří rozhraní: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)nebo [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5ff95-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ff95-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5ff95-109">Return Value</span></span>  
 <span data-ttu-id="5ff95-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="5ff95-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5ff95-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ff95-111">HRESULT</span></span>|<span data-ttu-id="5ff95-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5ff95-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ff95-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ff95-113">S_OK</span></span>|<span data-ttu-id="5ff95-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="5ff95-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5ff95-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5ff95-115">E_POINTER</span></span>|<span data-ttu-id="5ff95-116">`ppInterface` je null.</span><span class="sxs-lookup"><span data-stu-id="5ff95-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ff95-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ff95-117">Remarks</span></span>  
 <span data-ttu-id="5ff95-118">V následující tabulce jsou uvedeny podporované kombinace pro `clsid` a `riid`.</span><span class="sxs-lookup"><span data-stu-id="5ff95-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="5ff95-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="5ff95-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="5ff95-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="5ff95-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="5ff95-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="5ff95-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="5ff95-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="5ff95-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="5ff95-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="5ff95-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="5ff95-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="5ff95-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="5ff95-125">Následující kód ukazuje, jak použít `CLRCreateInstance` k získání všech tří rozhraní:</span><span class="sxs-lookup"><span data-stu-id="5ff95-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```cpp  
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
  
## <a name="requirements"></a><span data-ttu-id="5ff95-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ff95-126">Requirements</span></span>  
 <span data-ttu-id="5ff95-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ff95-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ff95-128">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="5ff95-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5ff95-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5ff95-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ff95-130">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ff95-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff95-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ff95-131">See also</span></span>

- [<span data-ttu-id="5ff95-132">Hostování</span><span class="sxs-lookup"><span data-stu-id="5ff95-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
