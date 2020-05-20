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
ms.openlocfilehash: c8ac959c192814562488ab916c8462b0baa0d8e6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703645"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="6b1b8-102">ICLRRuntimeInfo::GetInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="6b1b8-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="6b1b8-103">Načte CLR do aktuálního procesu a vrátí ukazatele rozhraní Runtime, jako jsou [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)a [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="6b1b8-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="6b1b8-104">Tato metoda nahrazuje všechny `CorBindTo` funkce \* v sekci [zastaralých hostujících funkcí CLR](deprecated-clr-hosting-functions.md) .</span><span class="sxs-lookup"><span data-stu-id="6b1b8-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b1b8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b1b8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b1b8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b1b8-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="6b1b8-107">pro Rozhraní CLSID pro třídu typu coclass</span><span class="sxs-lookup"><span data-stu-id="6b1b8-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="6b1b8-108">pro IID požadovaného `rclsid` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6b1b8-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="6b1b8-109">mimo Ukazatel na rozhraní dotazované přes dotaz.</span><span class="sxs-lookup"><span data-stu-id="6b1b8-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b1b8-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6b1b8-110">Return Value</span></span>  
 <span data-ttu-id="6b1b8-111">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="6b1b8-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6b1b8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b1b8-112">HRESULT</span></span>|<span data-ttu-id="6b1b8-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6b1b8-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b1b8-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b1b8-114">S_OK</span></span>|<span data-ttu-id="6b1b8-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="6b1b8-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="6b1b8-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6b1b8-116">E_POINTER</span></span>|<span data-ttu-id="6b1b8-117">`ppUnk`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="6b1b8-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="6b1b8-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6b1b8-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6b1b8-119">Pro zpracování požadavku není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="6b1b8-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="6b1b8-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="6b1b8-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="6b1b8-121">Jiný modul runtime již byl svázán se staršími zásadami aktivace CLR verze 2.</span><span class="sxs-lookup"><span data-stu-id="6b1b8-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b1b8-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b1b8-122">Remarks</span></span>  
 <span data-ttu-id="6b1b8-123">Tato metoda způsobí, že se CLR načte, ale neinicializuje se.</span><span class="sxs-lookup"><span data-stu-id="6b1b8-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="6b1b8-124">V následující tabulce jsou uvedeny podporované kombinace pro `rclsid` a `riid` .</span><span class="sxs-lookup"><span data-stu-id="6b1b8-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="6b1b8-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="6b1b8-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="6b1b8-126">IID_IMetaDataDispenser IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="6b1b8-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="6b1b8-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="6b1b8-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="6b1b8-128">IID_IMetaDataDispenser IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="6b1b8-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="6b1b8-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6b1b8-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="6b1b8-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6b1b8-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="6b1b8-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6b1b8-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="6b1b8-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6b1b8-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="6b1b8-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="6b1b8-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="6b1b8-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="6b1b8-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="6b1b8-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="6b1b8-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="6b1b8-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="6b1b8-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="6b1b8-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="6b1b8-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="6b1b8-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="6b1b8-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b1b8-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b1b8-139">Requirements</span></span>  
 <span data-ttu-id="6b1b8-140">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b1b8-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b1b8-141">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="6b1b8-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6b1b8-142">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6b1b8-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b1b8-143">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b1b8-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b1b8-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b1b8-144">See also</span></span>

- [<span data-ttu-id="6b1b8-145">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b1b8-145">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="6b1b8-146">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="6b1b8-146">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6b1b8-147">Hostování</span><span class="sxs-lookup"><span data-stu-id="6b1b8-147">Hosting</span></span>](index.md)
