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
ms.openlocfilehash: 4924f373270a30b593e27c334d383963fc4a7cf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435848"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="23ed7-102">ICLRRuntimeInfo::GetInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="23ed7-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="23ed7-103">Načte modul CLR do aktuální proces a vrátí runtime ukazatele rozhraní, jako například [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [iclrstrongname –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), a [imetadatadispenserex –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="23ed7-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="23ed7-104">Tato metoda nahrazuje všechny `CorBindTo`\* funkce [zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) části.</span><span class="sxs-lookup"><span data-stu-id="23ed7-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ed7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23ed7-105">Syntax</span></span>  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23ed7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="23ed7-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="23ed7-107">[v] Rozhraní CLSID coclass.</span><span class="sxs-lookup"><span data-stu-id="23ed7-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="23ed7-108">[v] Identifikátory IID požadované `rclsid` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="23ed7-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="23ed7-109">[out] Ukazatel rozhraní předmětem dotazu.</span><span class="sxs-lookup"><span data-stu-id="23ed7-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23ed7-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="23ed7-110">Return Value</span></span>  
 <span data-ttu-id="23ed7-111">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="23ed7-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="23ed7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23ed7-112">HRESULT</span></span>|<span data-ttu-id="23ed7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="23ed7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23ed7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="23ed7-114">S_OK</span></span>|<span data-ttu-id="23ed7-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="23ed7-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="23ed7-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="23ed7-116">E_POINTER</span></span>|<span data-ttu-id="23ed7-117">`ppUnk` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="23ed7-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="23ed7-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="23ed7-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="23ed7-119">Je k dispozici pro zpracování požadavku není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="23ed7-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="23ed7-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="23ed7-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="23ed7-121">Jiný modul runtime byl již vázána na starší verzi zásad 2 aktivace verze CLR.</span><span class="sxs-lookup"><span data-stu-id="23ed7-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23ed7-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23ed7-122">Remarks</span></span>  
 <span data-ttu-id="23ed7-123">Tato metoda způsobí, že CLR do být načtena, avšak nebyla inicializována.</span><span class="sxs-lookup"><span data-stu-id="23ed7-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="23ed7-124">Následující tabulka uvádí podporované kombinace pro `rclsid` a `riid`.</span><span class="sxs-lookup"><span data-stu-id="23ed7-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="23ed7-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="23ed7-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="23ed7-126">IID_IMetaDataDispenser IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="23ed7-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="23ed7-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="23ed7-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="23ed7-128">IID_IMetaDataDispenser IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="23ed7-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="23ed7-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="23ed7-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="23ed7-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="23ed7-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="23ed7-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="23ed7-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="23ed7-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="23ed7-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="23ed7-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="23ed7-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="23ed7-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="23ed7-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="23ed7-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="23ed7-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="23ed7-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="23ed7-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="23ed7-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="23ed7-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="23ed7-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="23ed7-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23ed7-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23ed7-139">Requirements</span></span>  
 <span data-ttu-id="23ed7-140">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23ed7-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23ed7-141">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="23ed7-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="23ed7-142">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="23ed7-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23ed7-143">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23ed7-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ed7-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="23ed7-144">See Also</span></span>  
 [<span data-ttu-id="23ed7-145">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23ed7-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="23ed7-146">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="23ed7-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="23ed7-147">Hostování</span><span class="sxs-lookup"><span data-stu-id="23ed7-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
