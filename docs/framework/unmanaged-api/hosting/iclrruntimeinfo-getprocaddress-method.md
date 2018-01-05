---
title: "ICLRRuntimeInfo::GetProcAddress – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetProcAddress
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2878b23a2f848657e1d26b3bfb8395f8897c0632
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="47ee9-102">ICLRRuntimeInfo::GetProcAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="47ee9-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="47ee9-103">Získá adresu určenou funkci, která byla exportována z common language runtime (CLR) spojené s tímto rozhraním.</span><span class="sxs-lookup"><span data-stu-id="47ee9-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="47ee9-104">Tato metoda nahrazuje [getrealprocaddress –](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="47ee9-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47ee9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47ee9-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47ee9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="47ee9-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="47ee9-107">[v] Název exportované funkce.</span><span class="sxs-lookup"><span data-stu-id="47ee9-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="47ee9-108">[out] Adresa exportované funkce.</span><span class="sxs-lookup"><span data-stu-id="47ee9-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47ee9-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="47ee9-109">Return Value</span></span>  
 <span data-ttu-id="47ee9-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="47ee9-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="47ee9-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47ee9-111">HRESULT</span></span>|<span data-ttu-id="47ee9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="47ee9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47ee9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="47ee9-113">S_OK</span></span>|<span data-ttu-id="47ee9-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="47ee9-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="47ee9-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="47ee9-115">E_POINTER</span></span>|<span data-ttu-id="47ee9-116">`pszProcName`nebo `ppProc` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="47ee9-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="47ee9-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="47ee9-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="47ee9-118">Zadaná funkce není exportované funkce.</span><span class="sxs-lookup"><span data-stu-id="47ee9-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47ee9-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47ee9-119">Remarks</span></span>  
 <span data-ttu-id="47ee9-120">Tato metoda způsobí, že CLR do být načtena, avšak nebyla inicializována.</span><span class="sxs-lookup"><span data-stu-id="47ee9-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47ee9-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47ee9-121">Requirements</span></span>  
 <span data-ttu-id="47ee9-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47ee9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47ee9-123">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="47ee9-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="47ee9-124">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="47ee9-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47ee9-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47ee9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ee9-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="47ee9-126">See Also</span></span>  
 [<span data-ttu-id="47ee9-127">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47ee9-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="47ee9-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="47ee9-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="47ee9-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="47ee9-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
