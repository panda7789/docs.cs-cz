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
ms.openlocfilehash: 3fe1f93c621fd567471b9a49e4aa75cb90e6e0e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771641"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="0b508-102">ICLRRuntimeInfo::LoadLibrary – metoda</span><span class="sxs-lookup"><span data-stu-id="0b508-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="0b508-103">Načte knihovna rozhraní .NET Framework z common language runtime (CLR) reprezentována [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0b508-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="0b508-104">Tato metoda nahrazuje [LoadLibraryShim –](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="0b508-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b508-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b508-105">Syntax</span></span>  
  
```  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b508-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b508-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="0b508-107">[in] Název sestavení, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="0b508-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="0b508-108">[out] Popisovač pro načtené sestavení.</span><span class="sxs-lookup"><span data-stu-id="0b508-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b508-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0b508-109">Return Value</span></span>  
 <span data-ttu-id="0b508-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="0b508-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0b508-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b508-111">HRESULT</span></span>|<span data-ttu-id="0b508-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0b508-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b508-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b508-113">S_OK</span></span>|<span data-ttu-id="0b508-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="0b508-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="0b508-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0b508-115">E_POINTER</span></span>|<span data-ttu-id="0b508-116">`pwzDllName` nebo `phndModule` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="0b508-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="0b508-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0b508-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0b508-118">Nedostatek paměti je k dispozici pro zpracování požadavku.</span><span class="sxs-lookup"><span data-stu-id="0b508-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b508-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b508-119">Remarks</span></span>  
 <span data-ttu-id="0b508-120">Tato metoda načte pouze knihovny DLL, které jsou součástí Distribuovatelný balíček rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0b508-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="0b508-121">Jej nelze načíst sestavení pro generovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="0b508-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b508-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b508-122">Requirements</span></span>  
 <span data-ttu-id="0b508-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b508-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b508-124">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0b508-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0b508-125">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0b508-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b508-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b508-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b508-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b508-127">See also</span></span>

- [<span data-ttu-id="0b508-128">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b508-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="0b508-129">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="0b508-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="0b508-130">Hostování</span><span class="sxs-lookup"><span data-stu-id="0b508-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
