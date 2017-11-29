---
title: "ICLRRuntimeInfo::LoadLibrary – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.LoadLibrary
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1d943f45a4e665836f376bddf65d84329c1900e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="2d686-102">ICLRRuntimeInfo::LoadLibrary – metoda</span><span class="sxs-lookup"><span data-stu-id="2d686-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="2d686-103">Načte knihovnu rozhraní .NET Framework z common language runtime (CLR) reprezentována [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d686-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="2d686-104">Tato metoda nahrazuje [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="2d686-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d686-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d686-105">Syntax</span></span>  
  
```  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d686-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d686-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="2d686-107">[v] Název sestavení, které má být načten.</span><span class="sxs-lookup"><span data-stu-id="2d686-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="2d686-108">[out] Popisovač pro načíst sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d686-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d686-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2d686-109">Return Value</span></span>  
 <span data-ttu-id="2d686-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="2d686-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2d686-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d686-111">HRESULT</span></span>|<span data-ttu-id="2d686-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2d686-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d686-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d686-113">S_OK</span></span>|<span data-ttu-id="2d686-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="2d686-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="2d686-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2d686-115">E_POINTER</span></span>|<span data-ttu-id="2d686-116">`pwzDllName`nebo `phndModule` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="2d686-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="2d686-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2d686-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2d686-118">Je k dispozici pro zpracování požadavku není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="2d686-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d686-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d686-119">Remarks</span></span>  
 <span data-ttu-id="2d686-120">Tato metoda pouze načte knihovny DLL, které jsou součástí Distribuovatelný balíček .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d686-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="2d686-121">Sestavení uživatelem generovaný ho nelze načíst.</span><span class="sxs-lookup"><span data-stu-id="2d686-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d686-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d686-122">Requirements</span></span>  
 <span data-ttu-id="2d686-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d686-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d686-124">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2d686-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2d686-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d686-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d686-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d686-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d686-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d686-127">See Also</span></span>  
 [<span data-ttu-id="2d686-128">Iclrruntimeinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d686-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="2d686-129">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="2d686-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="2d686-130">Hostování</span><span class="sxs-lookup"><span data-stu-id="2d686-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
