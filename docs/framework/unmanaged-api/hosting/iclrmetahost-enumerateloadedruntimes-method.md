---
title: "ICLRMetaHost::EnumerateLoadedRuntimes – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.EnumerateLoadedRuntimes
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0724bf44eaf82b39262876ea4a44509b6c7d576
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="5bc27-102">ICLRMetaHost::EnumerateLoadedRuntimes – metoda</span><span class="sxs-lookup"><span data-stu-id="5bc27-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="5bc27-103">Vrátí výčet, který obsahuje platnou [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) ukazatel rozhraní pro každou verzi common language runtime (CLR), který je načten do daného procesu.</span><span class="sxs-lookup"><span data-stu-id="5bc27-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="5bc27-104">Tato metoda nahrazuje [getversionfromprocess –](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="5bc27-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc27-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bc27-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5bc27-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5bc27-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="5bc27-107">[v] Popisovač procesu Kontrola pro načíst moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="5bc27-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="5bc27-108">[out] <!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown` Výčet [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní odpovídající každé CLR, které se zavádějí procesem.</span><span class="sxs-lookup"><span data-stu-id="5bc27-108">[out] An <!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown` enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bc27-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5bc27-109">Return Value</span></span>  
 <span data-ttu-id="5bc27-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="5bc27-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5bc27-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5bc27-111">HRESULT</span></span>|<span data-ttu-id="5bc27-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5bc27-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5bc27-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5bc27-113">S_OK</span></span>|<span data-ttu-id="5bc27-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="5bc27-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5bc27-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5bc27-115">E_POINTER</span></span>|<span data-ttu-id="5bc27-116">`ppEnumerator`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5bc27-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bc27-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5bc27-117">Remarks</span></span>  
 <span data-ttu-id="5bc27-118">Tato metoda je runtimes zobrazí všechny načíst i v případě, že byly načteny s zastaralé funkce, jako [corbindtoruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="5bc27-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bc27-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5bc27-119">Requirements</span></span>  
 <span data-ttu-id="5bc27-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bc27-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bc27-121">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5bc27-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5bc27-122">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5bc27-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5bc27-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bc27-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc27-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5bc27-124">See Also</span></span>  
 [<span data-ttu-id="5bc27-125">Iclrmetahost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5bc27-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="5bc27-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="5bc27-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
