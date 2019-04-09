---
title: ICLRMetaHost::EnumerateLoadedRuntimes – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0e1213128f5728f17225fbf6906d877dc64e86d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106610"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="0a4ae-102">ICLRMetaHost::EnumerateLoadedRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="0a4ae-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="0a4ae-103">Vrátí výčet, který obsahuje platné [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ukazatel rozhraní pro jednotlivé verze common language runtime (CLR), který je načten v daném procesu.</span><span class="sxs-lookup"><span data-stu-id="0a4ae-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="0a4ae-104">Tato metoda nahrazuje [getversionfromprocess –](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="0a4ae-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a4ae-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a4ae-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a4ae-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a4ae-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="0a4ae-107">[in] Popisovač procesu ke kontrole pro načtené moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="0a4ae-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="0a4ae-108">[out] <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> Výčet [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní odpovídající každé CLR, který je načten v procesu.</span><span class="sxs-lookup"><span data-stu-id="0a4ae-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a4ae-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0a4ae-109">Return Value</span></span>  
 <span data-ttu-id="0a4ae-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="0a4ae-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0a4ae-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a4ae-111">HRESULT</span></span>|<span data-ttu-id="0a4ae-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0a4ae-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a4ae-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a4ae-113">S_OK</span></span>|<span data-ttu-id="0a4ae-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="0a4ae-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="0a4ae-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0a4ae-115">E_POINTER</span></span>|`ppEnumerator` <span data-ttu-id="0a4ae-116">má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="0a4ae-116">is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a4ae-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a4ae-117">Remarks</span></span>  
 <span data-ttu-id="0a4ae-118">Tato metoda je načtena zobrazí všechny moduly runtime, i v případě, že nebyly načteny pomocí zastaralé funkce, jako [corbindtoruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="0a4ae-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a4ae-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a4ae-119">Requirements</span></span>  
 <span data-ttu-id="0a4ae-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a4ae-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a4ae-121">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0a4ae-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0a4ae-122">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a4ae-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0a4ae-123">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0a4ae-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a4ae-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a4ae-124">See also</span></span>

- [<span data-ttu-id="0a4ae-125">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a4ae-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="0a4ae-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="0a4ae-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
