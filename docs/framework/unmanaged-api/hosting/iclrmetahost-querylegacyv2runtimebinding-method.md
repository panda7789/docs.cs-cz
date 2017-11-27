---
title: "ICLRMetaHost::QueryLegacyV2RuntimeBinding – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c273a1690828e37c8f7fcf5071e42e5bb2c58228
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="8c7bc-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding – metoda</span><span class="sxs-lookup"><span data-stu-id="8c7bc-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="8c7bc-103">Vrátí rozhraní, které představuje runtime, do které starší verze aktivace zásad byla svázána, například pomocí `useLegacyV2RuntimeActivationPolicy` atributu u [ \<spuštění > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) souboru položka konfigurace, pomocí přímých Aktivace starší verze rozhraní API nebo voláním [iclrruntimeinfo::bindaslegacyv2runtime –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="8c7bc-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c7bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c7bc-104">Syntax</span></span>  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c7bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c7bc-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="8c7bc-106">[v] Jedinou platnou hodnotou tohoto parametru je Required.Currently `IID_ICLRRuntimeInfo`.</span><span class="sxs-lookup"><span data-stu-id="8c7bc-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="8c7bc-107">[out] Vyžaduje se.</span><span class="sxs-lookup"><span data-stu-id="8c7bc-107">[out] Required.</span></span> <span data-ttu-id="8c7bc-108">Když tato metoda vrací výsledek, obsahuje odkazy [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, které představuje modul runtime, který bylo svázáno se starší verze aktivace zásad.</span><span class="sxs-lookup"><span data-stu-id="8c7bc-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c7bc-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8c7bc-109">Return Value</span></span>  
 <span data-ttu-id="8c7bc-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="8c7bc-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8c7bc-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c7bc-111">HRESULT</span></span>|<span data-ttu-id="8c7bc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8c7bc-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c7bc-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c7bc-113">S_OK</span></span>|<span data-ttu-id="8c7bc-114">Metoda byla úspěšně dokončena a vrátí modul runtime, který byl spojen starší verze aktivace zásad.</span><span class="sxs-lookup"><span data-stu-id="8c7bc-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="8c7bc-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8c7bc-115">S_FALSE</span></span>|<span data-ttu-id="8c7bc-116">Metoda byla úspěšně dokončena, ale starší verze modulu runtime nebyl ještě svázány.</span><span class="sxs-lookup"><span data-stu-id="8c7bc-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="8c7bc-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="8c7bc-117">E_NOINTERFACE</span></span>|<span data-ttu-id="8c7bc-118">Metoda nalezena modul runtime, který byl spojen starší verze aktivace zásad, ale `riid` nepodporuje tento modul runtime.</span><span class="sxs-lookup"><span data-stu-id="8c7bc-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c7bc-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c7bc-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c7bc-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c7bc-120">Requirements</span></span>  
 <span data-ttu-id="8c7bc-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c7bc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c7bc-122">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8c7bc-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8c7bc-123">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c7bc-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c7bc-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c7bc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c7bc-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c7bc-125">See Also</span></span>  
 [<span data-ttu-id="8c7bc-126">Iclrmetahost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c7bc-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="8c7bc-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="8c7bc-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
