---
title: CreateDebuggingInterfaceFromVersion – funkce
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176445"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="993d3-102">CreateDebuggingInterfaceFromVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="993d3-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="993d3-103">Vytvoří objekt [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) na základě informací o zadané verzi.</span><span class="sxs-lookup"><span data-stu-id="993d3-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="993d3-104">Tato funkce je v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="993d3-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="993d3-105">Místo toho chcete získat rozhraní pro modul CLR (CLR) 2.0, použijte metodu [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) a zadejte identifikátor třídy CLSID_CLRDebuggingLegacy a identifikátor rozhraní IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="993d3-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="993d3-106">Chcete-li získat rozhraní pro CLR 4 nebo novější, zavolejte funkci [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) a zadejte identifikátor třídy CLSID_CLRDebugging a identifikátor rozhraní IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="993d3-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="993d3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="993d3-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="993d3-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="993d3-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="993d3-109">[v] Verze, `ICorDebug` která je očekávána ladicí program.</span><span class="sxs-lookup"><span data-stu-id="993d3-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="993d3-110">Viz [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) výčet platné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="993d3-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="993d3-111">[v] Verze za běhu běžného jazyka přidružená k aplikaci nebo procesu, který má být laděn.</span><span class="sxs-lookup"><span data-stu-id="993d3-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="993d3-112">Informace o načtení této hodnoty naleznete v metodě [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) nebo [GetRequestedRuntimeVersion.](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="993d3-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="993d3-113">[out] Umístění, které přijímá ukazatel `ICorDebug` na objekt.</span><span class="sxs-lookup"><span data-stu-id="993d3-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="993d3-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="993d3-114">Return Value</span></span>  
 <span data-ttu-id="993d3-115">Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v souboru WinError.h kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="993d3-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="993d3-116">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="993d3-116">Return code</span></span>|<span data-ttu-id="993d3-117">Popis</span><span class="sxs-lookup"><span data-stu-id="993d3-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="993d3-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="993d3-118">S_OK</span></span>|<span data-ttu-id="993d3-119">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="993d3-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="993d3-120">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="993d3-120">E_INVALIDARG</span></span>|<span data-ttu-id="993d3-121">`szDebuggeeVersion`nebo `ppCordb` je null nebo je řetězec verze nesprávný.</span><span class="sxs-lookup"><span data-stu-id="993d3-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="993d3-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="993d3-122">Remarks</span></span>  
 <span data-ttu-id="993d3-123">Parametr `szDebuggeeVersion` se mapuje na odpovídající verzi souboru MSCorDbi.dll.</span><span class="sxs-lookup"><span data-stu-id="993d3-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="993d3-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="993d3-124">Requirements</span></span>  
 <span data-ttu-id="993d3-125">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="993d3-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="993d3-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="993d3-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="993d3-127">**Knihovna:** Soubor MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="993d3-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="993d3-128">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="993d3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="993d3-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="993d3-129">See also</span></span>

- [<span data-ttu-id="993d3-130">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="993d3-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
