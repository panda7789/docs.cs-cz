---
title: "CorBindToRuntimeByCfg – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeByCfg
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeByCfg
helpviewer_keywords: CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dccd777ef20f68d091cfdd7939c57a1f8d42ad5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="2b9d1-102">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="2b9d1-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="2b9d1-103">Načte modul CLR (CLR) do procesu pomocí informací o verzi, která je pro čtení ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="2b9d1-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="2b9d1-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b9d1-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b9d1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b9d1-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b9d1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b9d1-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="2b9d1-107">[v] Ukazatel na `IStream` objekt, který načte soubor XML.</span><span class="sxs-lookup"><span data-stu-id="2b9d1-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="2b9d1-108">[v] Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="2b9d1-108">[in] Reserved for future use.</span></span> <span data-ttu-id="2b9d1-109">Jako hodnotu, použijte hodnotu 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="2b9d1-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="2b9d1-110">[v] Hodnota [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu, která určuje chování při spouštění modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="2b9d1-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="2b9d1-111">[v] `CLSID` Coclass, který implementuje buď [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2b9d1-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="2b9d1-112">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="2b9d1-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="2b9d1-113">[v] `IID` Buď `ICorRuntimeHost` nebo `ICLRRuntimeHost` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2b9d1-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="2b9d1-114">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="2b9d1-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="2b9d1-115">[out] Ukazatel na adresu vrácený rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2b9d1-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b9d1-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b9d1-116">Remarks</span></span>  
 <span data-ttu-id="2b9d1-117">Formát souboru XML je Modelováno podle konfiguračního souboru standardní aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b9d1-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="2b9d1-118">Další informace o souborech XML, najdete v části [schéma konfiguračního souboru](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="2b9d1-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b9d1-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b9d1-119">Requirements</span></span>  
 <span data-ttu-id="2b9d1-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b9d1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b9d1-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2b9d1-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b9d1-122">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b9d1-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b9d1-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b9d1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b9d1-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b9d1-124">See Also</span></span>  
 [<span data-ttu-id="2b9d1-125">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="2b9d1-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="2b9d1-126">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="2b9d1-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="2b9d1-127">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="2b9d1-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="2b9d1-128">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="2b9d1-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="2b9d1-129">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b9d1-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="2b9d1-130">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="2b9d1-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
