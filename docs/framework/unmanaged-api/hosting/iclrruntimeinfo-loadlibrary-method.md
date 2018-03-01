---
title: "ICLRRuntimeInfo::LoadLibrary – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8b688a4f2557c5ab2ef112e13b411e25ad47b8c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="b6162-102">ICLRRuntimeInfo::LoadLibrary – metoda</span><span class="sxs-lookup"><span data-stu-id="b6162-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="b6162-103">Načte knihovnu rozhraní .NET Framework z common language runtime (CLR) reprezentována [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b6162-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="b6162-104">Tato metoda nahrazuje [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="b6162-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6162-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6162-105">Syntax</span></span>  
  
```  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6162-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6162-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="b6162-107">[v] Název sestavení, které má být načten.</span><span class="sxs-lookup"><span data-stu-id="b6162-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="b6162-108">[out] Popisovač pro načíst sestavení.</span><span class="sxs-lookup"><span data-stu-id="b6162-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6162-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b6162-109">Return Value</span></span>  
 <span data-ttu-id="b6162-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="b6162-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b6162-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6162-111">HRESULT</span></span>|<span data-ttu-id="b6162-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b6162-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6162-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6162-113">S_OK</span></span>|<span data-ttu-id="b6162-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="b6162-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="b6162-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="b6162-115">E_POINTER</span></span>|<span data-ttu-id="b6162-116">`pwzDllName`nebo `phndModule` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b6162-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="b6162-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b6162-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b6162-118">Je k dispozici pro zpracování požadavku není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="b6162-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6162-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6162-119">Remarks</span></span>  
 <span data-ttu-id="b6162-120">Tato metoda pouze načte knihovny DLL, které jsou součástí Distribuovatelný balíček .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b6162-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="b6162-121">Sestavení uživatelem generovaný ho nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="b6162-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6162-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6162-122">Requirements</span></span>  
 <span data-ttu-id="b6162-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6162-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6162-124">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b6162-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b6162-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6162-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6162-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6162-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6162-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6162-127">See Also</span></span>  
 [<span data-ttu-id="b6162-128">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6162-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="b6162-129">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="b6162-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="b6162-130">Hostování</span><span class="sxs-lookup"><span data-stu-id="b6162-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
