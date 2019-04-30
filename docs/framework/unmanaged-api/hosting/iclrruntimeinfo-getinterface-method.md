---
title: ICLRRuntimeInfo::GetInterface – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f229e421cc69f2ff45110233c4c6c36d7a1fc4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771758"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="8ec3c-102">ICLRRuntimeInfo::GetInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="8ec3c-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="8ec3c-103">Načte modul CLR do aktuální proces a vrátí runtime ukazatele rozhraní, jako například [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [iclrstrongname –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), a [imetadatadispenserex –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8ec3c-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="8ec3c-104">Tato metoda nahrazuje všechny `CorBindTo`\* funkce v [zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) oddílu.</span><span class="sxs-lookup"><span data-stu-id="8ec3c-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ec3c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ec3c-105">Syntax</span></span>  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ec3c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ec3c-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="8ec3c-107">[in] Identifikátor CLSID rozhraní pro coclass.</span><span class="sxs-lookup"><span data-stu-id="8ec3c-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="8ec3c-108">[in] Požadovaný identifikátor IID `rclsid` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8ec3c-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="8ec3c-109">[out] Ukazatel na rozhraní poslal dotaz.</span><span class="sxs-lookup"><span data-stu-id="8ec3c-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ec3c-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8ec3c-110">Return Value</span></span>  
 <span data-ttu-id="8ec3c-111">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="8ec3c-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8ec3c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ec3c-112">HRESULT</span></span>|<span data-ttu-id="8ec3c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8ec3c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ec3c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ec3c-114">S_OK</span></span>|<span data-ttu-id="8ec3c-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="8ec3c-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="8ec3c-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8ec3c-116">E_POINTER</span></span>|<span data-ttu-id="8ec3c-117">`ppUnk` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8ec3c-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="8ec3c-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8ec3c-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8ec3c-119">Nedostatek paměti je k dispozici pro zpracování požadavku.</span><span class="sxs-lookup"><span data-stu-id="8ec3c-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="8ec3c-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="8ec3c-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="8ec3c-121">Jiný modul runtime je již vázán na starší verze 2 Aktivace zásady CLR verze.</span><span class="sxs-lookup"><span data-stu-id="8ec3c-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ec3c-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ec3c-122">Remarks</span></span>  
 <span data-ttu-id="8ec3c-123">Tato metoda způsobí, že modul CLR do načtena, avšak nebyla inicializována.</span><span class="sxs-lookup"><span data-stu-id="8ec3c-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="8ec3c-124">V následující tabulce jsou uvedeny podporované kombinace pro `rclsid` a `riid`.</span><span class="sxs-lookup"><span data-stu-id="8ec3c-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="8ec3c-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="8ec3c-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="8ec3c-126">IID_IMetaDataDispenser IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="8ec3c-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="8ec3c-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="8ec3c-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="8ec3c-128">IID_IMetaDataDispenser IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="8ec3c-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="8ec3c-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="8ec3c-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="8ec3c-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="8ec3c-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="8ec3c-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="8ec3c-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="8ec3c-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="8ec3c-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="8ec3c-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="8ec3c-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="8ec3c-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="8ec3c-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="8ec3c-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="8ec3c-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="8ec3c-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="8ec3c-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="8ec3c-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="8ec3c-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="8ec3c-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="8ec3c-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ec3c-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ec3c-139">Requirements</span></span>  
 <span data-ttu-id="8ec3c-140">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ec3c-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ec3c-141">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8ec3c-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8ec3c-142">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ec3c-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ec3c-143">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ec3c-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec3c-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ec3c-144">See also</span></span>

- [<span data-ttu-id="8ec3c-145">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ec3c-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="8ec3c-146">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="8ec3c-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="8ec3c-147">Hostování</span><span class="sxs-lookup"><span data-stu-id="8ec3c-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
