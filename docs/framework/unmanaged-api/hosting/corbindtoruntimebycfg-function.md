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
ms.openlocfilehash: 9326484c6a9f96d245e3c61a0ac3e3465a8a6dcd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616642"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="d4f5e-102">CorBindToRuntimeByCfg – funkce</span><span class="sxs-lookup"><span data-stu-id="d4f5e-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="d4f5e-103">Načte modul CLR (Common Language Runtime) do procesu pomocí informací o verzi načtených ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="d4f5e-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="d4f5e-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d4f5e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4f5e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4f5e-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d4f5e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4f5e-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="d4f5e-107">pro Ukazatel na `IStream` objekt, který čte soubor XML.</span><span class="sxs-lookup"><span data-stu-id="d4f5e-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="d4f5e-108">pro Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="d4f5e-108">[in] Reserved for future use.</span></span> <span data-ttu-id="d4f5e-109">Jako hodnotu použijte 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="d4f5e-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="d4f5e-110">pro Hodnota výčtu [STARTUP_FLAGS](startup-flags-enumeration.md) , která určuje chování při spuštění modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d4f5e-110">[in] A value of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="d4f5e-111">pro `CLSID`Třída typu coclass, která implementuje rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d4f5e-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="d4f5e-112">Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="d4f5e-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="d4f5e-113">pro `IID` `ICorRuntimeHost` `ICLRRuntimeHost` Rozhraní nebo.</span><span class="sxs-lookup"><span data-stu-id="d4f5e-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="d4f5e-114">Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="d4f5e-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="d4f5e-115">mimo Ukazatel na adresu vráceného rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d4f5e-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4f5e-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4f5e-116">Remarks</span></span>  
 <span data-ttu-id="d4f5e-117">Formát souboru XML je modelován po standardní konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="d4f5e-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="d4f5e-118">Další informace o souborech XML najdete v tématu [Schéma konfiguračního souboru](../../configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="d4f5e-118">For more information about XML files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4f5e-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4f5e-119">Requirements</span></span>  
 <span data-ttu-id="d4f5e-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4f5e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4f5e-121">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d4f5e-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4f5e-122">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d4f5e-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4f5e-123">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4f5e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f5e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4f5e-124">See also</span></span>

- [<span data-ttu-id="d4f5e-125">CorBindToCurrentRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="d4f5e-125">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="d4f5e-126">CorBindToRuntime – funkce</span><span class="sxs-lookup"><span data-stu-id="d4f5e-126">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="d4f5e-127">CorBindToRuntimeEx – funkce</span><span class="sxs-lookup"><span data-stu-id="d4f5e-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="d4f5e-128">CorBindToRuntimeHost – funkce</span><span class="sxs-lookup"><span data-stu-id="d4f5e-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="d4f5e-129">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4f5e-129">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="d4f5e-130">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="d4f5e-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
