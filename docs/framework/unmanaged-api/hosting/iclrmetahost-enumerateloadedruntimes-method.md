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
ms.openlocfilehash: db10b5c67a098cc34292a2680bd832f9cef2861b
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323399"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="59560-102">ICLRMetaHost::EnumerateLoadedRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="59560-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="59560-103">Vrátí výčet, který obsahuje platné [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ukazatel rozhraní pro jednotlivé verze common language runtime (CLR), který je načten v daném procesu.</span><span class="sxs-lookup"><span data-stu-id="59560-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="59560-104">Tato metoda nahrazuje [getversionfromprocess –](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="59560-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59560-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59560-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59560-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="59560-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="59560-107">[in] Popisovač procesu ke kontrole pro načtené moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="59560-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="59560-108">[out] <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> Výčet [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní odpovídající každé CLR, který je načten v procesu.</span><span class="sxs-lookup"><span data-stu-id="59560-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59560-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="59560-109">Return Value</span></span>  
 <span data-ttu-id="59560-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="59560-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="59560-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="59560-111">HRESULT</span></span>|<span data-ttu-id="59560-112">Popis</span><span class="sxs-lookup"><span data-stu-id="59560-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="59560-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="59560-113">S_OK</span></span>|<span data-ttu-id="59560-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="59560-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="59560-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="59560-115">E_POINTER</span></span>|<span data-ttu-id="59560-116">`ppEnumerator` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="59560-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59560-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59560-117">Remarks</span></span>  
 <span data-ttu-id="59560-118">Tato metoda je načtena zobrazí všechny moduly runtime, i v případě, že nebyly načteny pomocí zastaralé funkce, jako [corbindtoruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="59560-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59560-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59560-119">Requirements</span></span>  
 <span data-ttu-id="59560-120">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59560-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59560-121">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="59560-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="59560-122">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="59560-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59560-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59560-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59560-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="59560-124">See Also</span></span>  
 [<span data-ttu-id="59560-125">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="59560-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="59560-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="59560-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
