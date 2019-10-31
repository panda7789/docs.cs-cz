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
ms.openlocfilehash: 295deeec2e8eb42ccaa4d0cfb8b08b32438d047c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120243"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="8aa04-102">ICLRRuntimeInfo::GetInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="8aa04-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="8aa04-103">Načte CLR do aktuálního procesu a vrátí ukazatele rozhraní Runtime, jako jsou [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)a [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8aa04-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="8aa04-104">Tato metoda nahrazuje všechny funkce `CorBindTo`\* v části [zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) .</span><span class="sxs-lookup"><span data-stu-id="8aa04-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aa04-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8aa04-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8aa04-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8aa04-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="8aa04-107">pro Rozhraní CLSID pro třídu typu coclass</span><span class="sxs-lookup"><span data-stu-id="8aa04-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="8aa04-108">pro IID požadovaného `rclsid` rozhraní</span><span class="sxs-lookup"><span data-stu-id="8aa04-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="8aa04-109">mimo Ukazatel na rozhraní dotazované přes dotaz.</span><span class="sxs-lookup"><span data-stu-id="8aa04-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8aa04-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8aa04-110">Return Value</span></span>  
 <span data-ttu-id="8aa04-111">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="8aa04-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8aa04-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8aa04-112">HRESULT</span></span>|<span data-ttu-id="8aa04-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8aa04-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8aa04-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8aa04-114">S_OK</span></span>|<span data-ttu-id="8aa04-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="8aa04-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="8aa04-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8aa04-116">E_POINTER</span></span>|<span data-ttu-id="8aa04-117">`ppUnk` je null.</span><span class="sxs-lookup"><span data-stu-id="8aa04-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="8aa04-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8aa04-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8aa04-119">Pro zpracování požadavku není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="8aa04-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="8aa04-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="8aa04-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="8aa04-121">Jiný modul runtime již byl svázán se staršími zásadami aktivace CLR verze 2.</span><span class="sxs-lookup"><span data-stu-id="8aa04-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8aa04-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8aa04-122">Remarks</span></span>  
 <span data-ttu-id="8aa04-123">Tato metoda způsobí, že se CLR načte, ale neinicializuje se.</span><span class="sxs-lookup"><span data-stu-id="8aa04-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="8aa04-124">V následující tabulce jsou uvedeny podporované kombinace pro `rclsid` a `riid`.</span><span class="sxs-lookup"><span data-stu-id="8aa04-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="8aa04-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="8aa04-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="8aa04-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="8aa04-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="8aa04-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="8aa04-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="8aa04-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="8aa04-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="8aa04-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="8aa04-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="8aa04-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="8aa04-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="8aa04-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="8aa04-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="8aa04-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="8aa04-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="8aa04-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="8aa04-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="8aa04-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="8aa04-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="8aa04-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="8aa04-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="8aa04-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="8aa04-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="8aa04-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="8aa04-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="8aa04-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="8aa04-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8aa04-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8aa04-139">Requirements</span></span>  
 <span data-ttu-id="8aa04-140">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aa04-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aa04-141">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="8aa04-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8aa04-142">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8aa04-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8aa04-143">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aa04-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa04-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8aa04-144">See also</span></span>

- [<span data-ttu-id="8aa04-145">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8aa04-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="8aa04-146">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="8aa04-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="8aa04-147">Hostování</span><span class="sxs-lookup"><span data-stu-id="8aa04-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
