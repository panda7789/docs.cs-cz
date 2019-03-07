---
title: ICLRRuntimeInfo::LoadLibrary – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 878d68dd690a8764ef26f5f180fabd6c22841a25
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466830"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="bc9bd-102">ICLRRuntimeInfo::LoadLibrary – metoda</span><span class="sxs-lookup"><span data-stu-id="bc9bd-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="bc9bd-103">Načte knihovna rozhraní .NET Framework z common language runtime (CLR) reprezentována [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bc9bd-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="bc9bd-104">Tato metoda nahrazuje [LoadLibraryShim –](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="bc9bd-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc9bd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc9bd-105">Syntax</span></span>  
  
```  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc9bd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc9bd-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="bc9bd-107">[in] Název sestavení, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="bc9bd-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="bc9bd-108">[out] Popisovač pro načtené sestavení.</span><span class="sxs-lookup"><span data-stu-id="bc9bd-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc9bd-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bc9bd-109">Return Value</span></span>  
 <span data-ttu-id="bc9bd-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="bc9bd-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bc9bd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc9bd-111">HRESULT</span></span>|<span data-ttu-id="bc9bd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bc9bd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc9bd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc9bd-113">S_OK</span></span>|<span data-ttu-id="bc9bd-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="bc9bd-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="bc9bd-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="bc9bd-115">E_POINTER</span></span>|<span data-ttu-id="bc9bd-116">`pwzDllName` nebo `phndModule` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="bc9bd-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="bc9bd-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bc9bd-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="bc9bd-118">Nedostatek paměti je k dispozici pro zpracování požadavku.</span><span class="sxs-lookup"><span data-stu-id="bc9bd-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc9bd-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc9bd-119">Remarks</span></span>  
 <span data-ttu-id="bc9bd-120">Tato metoda načte pouze knihovny DLL, které jsou součástí Distribuovatelný balíček rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bc9bd-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="bc9bd-121">Jej nelze načíst sestavení pro generovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="bc9bd-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc9bd-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc9bd-122">Requirements</span></span>  
 <span data-ttu-id="bc9bd-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc9bd-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc9bd-124">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bc9bd-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bc9bd-125">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bc9bd-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc9bd-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc9bd-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc9bd-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc9bd-127">See also</span></span>
- [<span data-ttu-id="bc9bd-128">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc9bd-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="bc9bd-129">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="bc9bd-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="bc9bd-130">Hostování</span><span class="sxs-lookup"><span data-stu-id="bc9bd-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
