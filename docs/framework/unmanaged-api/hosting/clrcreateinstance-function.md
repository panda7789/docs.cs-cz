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
ms.openlocfilehash: c3011149b9b23e776ad3baac9e41f3c42213654d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616824"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="b4cbd-102">CLRCreateInstance – funkce</span><span class="sxs-lookup"><span data-stu-id="b4cbd-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="b4cbd-103">Poskytuje jedno ze tří rozhraní: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)nebo [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b4cbd-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4cbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4cbd-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4cbd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4cbd-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="b4cbd-106">pro Jeden ze tří identifikátorů třídy: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy nebo CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="b4cbd-107">pro Jeden ze tří identifikátorů rozhraní (IID): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy nebo IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="b4cbd-108">mimo Jedno ze tří rozhraní: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)nebo [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b4cbd-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4cbd-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b4cbd-109">Return Value</span></span>  
 <span data-ttu-id="b4cbd-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b4cbd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4cbd-111">HRESULT</span></span>|<span data-ttu-id="b4cbd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b4cbd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4cbd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4cbd-113">S_OK</span></span>|<span data-ttu-id="b4cbd-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="b4cbd-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="b4cbd-115">E_POINTER</span></span>|<span data-ttu-id="b4cbd-116">`ppInterface`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b4cbd-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4cbd-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4cbd-117">Remarks</span></span>  
 <span data-ttu-id="b4cbd-118">V následující tabulce jsou uvedeny podporované kombinace pro `clsid` a `riid` .</span><span class="sxs-lookup"><span data-stu-id="b4cbd-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="b4cbd-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="b4cbd-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="b4cbd-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="b4cbd-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="b4cbd-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="b4cbd-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="b4cbd-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="b4cbd-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="b4cbd-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="b4cbd-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="b4cbd-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="b4cbd-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="b4cbd-125">Následující kód ukazuje, jak použít `CLRCreateInstance` k získání všech tří rozhraní:</span><span class="sxs-lookup"><span data-stu-id="b4cbd-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="b4cbd-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4cbd-126">Requirements</span></span>  
 <span data-ttu-id="b4cbd-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4cbd-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4cbd-128">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="b4cbd-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b4cbd-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b4cbd-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4cbd-130">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4cbd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4cbd-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4cbd-131">See also</span></span>

- [<span data-ttu-id="b4cbd-132">Hostování</span><span class="sxs-lookup"><span data-stu-id="b4cbd-132">Hosting</span></span>](index.md)
