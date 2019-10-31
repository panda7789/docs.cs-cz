---
title: CorBindToRuntimeByCfg – funkce
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: 3802354bf52cd2aab2a4149d565993b9965e8312
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138290"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="1f0ab-102">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="1f0ab-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="1f0ab-103">Načte modul CLR (Common Language Runtime) do procesu pomocí informací o verzi načtených ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="1f0ab-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f0ab-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f0ab-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f0ab-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f0ab-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="1f0ab-107">pro Ukazatel na objekt `IStream`, který čte soubor XML.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="1f0ab-108">pro Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-108">[in] Reserved for future use.</span></span> <span data-ttu-id="1f0ab-109">Jako hodnotu použijte 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="1f0ab-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="1f0ab-110">pro Hodnota výčtu [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) , která určuje chování při spuštění modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="1f0ab-111">pro `CLSID` třídy coclass, která implementuje rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1f0ab-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="1f0ab-112">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="1f0ab-113">pro `IID` rozhraní `ICorRuntimeHost` nebo `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="1f0ab-114">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="1f0ab-115">mimo Ukazatel na adresu vráceného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f0ab-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f0ab-116">Remarks</span></span>  
 <span data-ttu-id="1f0ab-117">Formát souboru XML je modelován po standardní konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f0ab-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="1f0ab-118">Další informace o souborech XML najdete v tématu [Schéma konfiguračního souboru](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f0ab-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f0ab-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f0ab-119">Requirements</span></span>  
 <span data-ttu-id="1f0ab-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f0ab-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f0ab-121">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1f0ab-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f0ab-122">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1f0ab-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f0ab-123">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f0ab-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f0ab-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f0ab-124">See also</span></span>

- [<span data-ttu-id="1f0ab-125">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="1f0ab-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="1f0ab-126">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="1f0ab-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="1f0ab-127">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="1f0ab-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="1f0ab-128">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="1f0ab-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="1f0ab-129">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f0ab-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="1f0ab-130">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="1f0ab-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
