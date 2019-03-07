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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b21b86e9f5866626f72562f5105b214777e3d5bd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486900"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="310e6-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding – metoda</span><span class="sxs-lookup"><span data-stu-id="310e6-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="310e6-103">Vrátí rozhraní, která představuje modul runtime, ke kterému zásady aktivace starší verze byl vázán, například pomocí `useLegacyV2RuntimeActivationPolicy` atribut na [ \<spuštění > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) položka souboru konfigurace s přímým přístupem pomocí Aktivace starší verze rozhraní API, nebo pomocí volání [iclrruntimeinfo::bindaslegacyv2runtime –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="310e6-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="310e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="310e6-104">Syntax</span></span>  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="310e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="310e6-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="310e6-106">[in] Jediná platná hodnota pro tento parametr je Required.Currently `IID_ICLRRuntimeInfo`.</span><span class="sxs-lookup"><span data-stu-id="310e6-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="310e6-107">[out] Povinné.</span><span class="sxs-lookup"><span data-stu-id="310e6-107">[out] Required.</span></span> <span data-ttu-id="310e6-108">Po návratu metody obsahuje ukazatel [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, které představuje modul runtime, který bylo svázáno se zásady aktivace starší verze.</span><span class="sxs-lookup"><span data-stu-id="310e6-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="310e6-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="310e6-109">Return Value</span></span>  
 <span data-ttu-id="310e6-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="310e6-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="310e6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="310e6-111">HRESULT</span></span>|<span data-ttu-id="310e6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="310e6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="310e6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="310e6-113">S_OK</span></span>|<span data-ttu-id="310e6-114">Metoda byla úspěšně dokončena a vrátí modulu runtime, která byla vázána na starší verzi Aktivace zásady.</span><span class="sxs-lookup"><span data-stu-id="310e6-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="310e6-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="310e6-115">S_FALSE</span></span>|<span data-ttu-id="310e6-116">Metoda byla úspěšně dokončena, ale starší verzi modulu runtime nebyl dosud byl svázán.</span><span class="sxs-lookup"><span data-stu-id="310e6-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="310e6-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="310e6-117">E_NOINTERFACE</span></span>|<span data-ttu-id="310e6-118">Metoda najít modul runtime, který je vázán na zásady aktivace starší verze, ale `riid` nepodporuje tento modul runtime.</span><span class="sxs-lookup"><span data-stu-id="310e6-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="310e6-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="310e6-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="310e6-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="310e6-120">Requirements</span></span>  
 <span data-ttu-id="310e6-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="310e6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="310e6-122">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="310e6-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="310e6-123">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="310e6-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="310e6-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="310e6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310e6-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="310e6-125">See also</span></span>
- [<span data-ttu-id="310e6-126">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="310e6-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="310e6-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="310e6-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
