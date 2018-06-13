---
title: ICLRRuntimeInfo::GetProcAddress – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8e50a018016b885a3513cbd885b8e5115f18113
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432918"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="99ae7-102">ICLRRuntimeInfo::GetProcAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="99ae7-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="99ae7-103">Získá adresu určenou funkci, která byla exportována z common language runtime (CLR) spojené s tímto rozhraním.</span><span class="sxs-lookup"><span data-stu-id="99ae7-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="99ae7-104">Tato metoda nahrazuje [getrealprocaddress –](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="99ae7-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99ae7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99ae7-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99ae7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="99ae7-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="99ae7-107">[v] Název exportované funkce.</span><span class="sxs-lookup"><span data-stu-id="99ae7-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="99ae7-108">[out] Adresa exportované funkce.</span><span class="sxs-lookup"><span data-stu-id="99ae7-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99ae7-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="99ae7-109">Return Value</span></span>  
 <span data-ttu-id="99ae7-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="99ae7-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="99ae7-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99ae7-111">HRESULT</span></span>|<span data-ttu-id="99ae7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="99ae7-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99ae7-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="99ae7-113">S_OK</span></span>|<span data-ttu-id="99ae7-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="99ae7-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="99ae7-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="99ae7-115">E_POINTER</span></span>|<span data-ttu-id="99ae7-116">`pszProcName` nebo `ppProc` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="99ae7-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="99ae7-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="99ae7-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="99ae7-118">Zadaná funkce není exportované funkce.</span><span class="sxs-lookup"><span data-stu-id="99ae7-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99ae7-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99ae7-119">Remarks</span></span>  
 <span data-ttu-id="99ae7-120">Tato metoda způsobí, že CLR do být načtena, avšak nebyla inicializována.</span><span class="sxs-lookup"><span data-stu-id="99ae7-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99ae7-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99ae7-121">Requirements</span></span>  
 <span data-ttu-id="99ae7-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99ae7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99ae7-123">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="99ae7-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="99ae7-124">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99ae7-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99ae7-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99ae7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ae7-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="99ae7-126">See Also</span></span>  
 [<span data-ttu-id="99ae7-127">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99ae7-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="99ae7-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="99ae7-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="99ae7-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="99ae7-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
