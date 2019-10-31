---
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
ms.openlocfilehash: 90474a61b16d65565889bd69ef75616804d8bc60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140879"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="d9d5d-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding – metoda</span><span class="sxs-lookup"><span data-stu-id="d9d5d-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="d9d5d-103">Vrátí rozhraní, které představuje modul runtime, ke kterému byly navázány zastaralé Zásady aktivace, například pomocí atributu `useLegacyV2RuntimeActivationPolicy` v položce konfiguračního souboru [\<po spuštění >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , a to přímým použitím starších aktivačních rozhraní API nebo voláním metody [ICLRRuntimeInfo:: bindaslegacyv2runtime –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d9d5d-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9d5d-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9d5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9d5d-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="d9d5d-106">pro Požadováno. v současné době je `IID_ICLRRuntimeInfo`jedinou platnou hodnotou tohoto parametru.</span><span class="sxs-lookup"><span data-stu-id="d9d5d-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="d9d5d-107">mimo Požadovanou.</span><span class="sxs-lookup"><span data-stu-id="d9d5d-107">[out] Required.</span></span> <span data-ttu-id="d9d5d-108">Až tato metoda vrátí, obsahuje ukazatel na rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , které představuje modul runtime, který je svázán se staršími zásadami aktivace.</span><span class="sxs-lookup"><span data-stu-id="d9d5d-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9d5d-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d9d5d-109">Return Value</span></span>  
 <span data-ttu-id="d9d5d-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="d9d5d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d9d5d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9d5d-111">HRESULT</span></span>|<span data-ttu-id="d9d5d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d9d5d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9d5d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9d5d-113">S_OK</span></span>|<span data-ttu-id="d9d5d-114">Metoda se úspěšně dokončila a vrátila modul runtime, který se váže k zásadám aktivace starší verze.</span><span class="sxs-lookup"><span data-stu-id="d9d5d-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="d9d5d-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d9d5d-115">S_FALSE</span></span>|<span data-ttu-id="d9d5d-116">Metoda se úspěšně dokončila, ale starší verze modulu runtime ještě není vázaná.</span><span class="sxs-lookup"><span data-stu-id="d9d5d-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="d9d5d-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="d9d5d-117">E_NOINTERFACE</span></span>|<span data-ttu-id="d9d5d-118">Metoda našla modul runtime, který byl vázán na starší Zásady aktivace, ale `riid` není tímto modulem runtime podporován.</span><span class="sxs-lookup"><span data-stu-id="d9d5d-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9d5d-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9d5d-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9d5d-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9d5d-120">Requirements</span></span>  
 <span data-ttu-id="d9d5d-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9d5d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9d5d-122">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d9d5d-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d9d5d-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d9d5d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9d5d-124">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9d5d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9d5d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9d5d-125">See also</span></span>

- [<span data-ttu-id="d9d5d-126">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9d5d-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="d9d5d-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="d9d5d-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
