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
ms.openlocfilehash: da9ae70056e3ef5d6d9e03fde1dcf8775e5d118e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498949"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="ec9ae-102">ICLRRuntimeInfo::GetProcAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="ec9ae-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="ec9ae-103">Získá adresu zadané funkce, která byla exportována z common language runtime (CLR) přidružené k tomuto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ec9ae-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="ec9ae-104">Tato metoda nahrazuje [getrealprocaddress –](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="ec9ae-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec9ae-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec9ae-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec9ae-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec9ae-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="ec9ae-107">[in] Název exportované funkce.</span><span class="sxs-lookup"><span data-stu-id="ec9ae-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="ec9ae-108">[out] Adresu exportované funkce.</span><span class="sxs-lookup"><span data-stu-id="ec9ae-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec9ae-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ec9ae-109">Return Value</span></span>  
 <span data-ttu-id="ec9ae-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="ec9ae-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ec9ae-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec9ae-111">HRESULT</span></span>|<span data-ttu-id="ec9ae-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ec9ae-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec9ae-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec9ae-113">S_OK</span></span>|<span data-ttu-id="ec9ae-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="ec9ae-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="ec9ae-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ec9ae-115">E_POINTER</span></span>|<span data-ttu-id="ec9ae-116">`pszProcName` nebo `ppProc` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ec9ae-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="ec9ae-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="ec9ae-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="ec9ae-118">Zadaná funkce není exportované funkce.</span><span class="sxs-lookup"><span data-stu-id="ec9ae-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec9ae-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec9ae-119">Remarks</span></span>  
 <span data-ttu-id="ec9ae-120">Tato metoda způsobí, že modul CLR do načtena, avšak nebyla inicializována.</span><span class="sxs-lookup"><span data-stu-id="ec9ae-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec9ae-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec9ae-121">Requirements</span></span>  
 <span data-ttu-id="ec9ae-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec9ae-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec9ae-123">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ec9ae-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ec9ae-124">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ec9ae-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec9ae-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec9ae-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec9ae-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec9ae-126">See also</span></span>
- [<span data-ttu-id="ec9ae-127">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ec9ae-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ec9ae-128">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ec9ae-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ec9ae-129">Hostování</span><span class="sxs-lookup"><span data-stu-id="ec9ae-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
