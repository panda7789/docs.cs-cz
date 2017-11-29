---
title: "CreateDebuggingInterfaceFromVersion – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CreateDebuggingInterfaceFromVersion
helpviewer_keywords: CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cc352603ef1c3610edf99f7bdd877c6bb0e5d9fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="fe0e2-102">CreateDebuggingInterfaceFromVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="fe0e2-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="fe0e2-103">Vytvoří [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objekt založený na informacích zadaná verze.</span><span class="sxs-lookup"><span data-stu-id="fe0e2-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="fe0e2-104">Tato funkce je v zastaralé [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe0e2-104">This function is obsolete in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="fe0e2-105">Místo toho použijte rozhraní common language runtime (CLR) 2.0 získáte [iclrruntimeinfo::getinterface –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metoda a zadejte identifikátor třídy CLSID_CLRDebuggingLegacy a identifikátor rozhraní IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="fe0e2-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="fe0e2-106">Pro získání rozhraní pro CLR 4 nebo novější, volání [clrcreateinstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkce a zadejte identifikátor třídy CLSID_CLRDebugging a identifikátor rozhraní IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="fe0e2-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe0e2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe0e2-107">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe0e2-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe0e2-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="fe0e2-109">[v] Verze `ICorDebug` je očekáváno ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="fe0e2-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="fe0e2-110">Najdete v článku [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) platné hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="fe0e2-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="fe0e2-111">[v] Běžné verzi modulu runtime jazyka přidružené aplikace nebo proces, který chcete ladit.</span><span class="sxs-lookup"><span data-stu-id="fe0e2-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="fe0e2-112">Najdete v článku [getversionfromprocess –](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) nebo [getrequestedruntimeversion –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metoda informace o načítání tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fe0e2-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="fe0e2-113">[out] Umístění, které obdrží ukazatel `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="fe0e2-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe0e2-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fe0e2-114">Return Value</span></span>  
 <span data-ttu-id="fe0e2-115">Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v souboru WinError.h vedle následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fe0e2-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="fe0e2-116">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="fe0e2-116">Return code</span></span>|<span data-ttu-id="fe0e2-117">Popis</span><span class="sxs-lookup"><span data-stu-id="fe0e2-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="fe0e2-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe0e2-118">S_OK</span></span>|<span data-ttu-id="fe0e2-119">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="fe0e2-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="fe0e2-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fe0e2-120">E_INVALIDARG</span></span>|<span data-ttu-id="fe0e2-121">`szDebuggeeVersion`nebo `ppCordb` má hodnotu null, nebo verze řetězec je nesprávný.</span><span class="sxs-lookup"><span data-stu-id="fe0e2-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe0e2-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe0e2-122">Remarks</span></span>  
 <span data-ttu-id="fe0e2-123">`szDebuggeeVersion` Parametr se mapuje na odpovídající verzi systému MSCorDbi.dll.</span><span class="sxs-lookup"><span data-stu-id="fe0e2-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe0e2-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe0e2-124">Requirements</span></span>  
 <span data-ttu-id="fe0e2-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe0e2-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe0e2-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fe0e2-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe0e2-127">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe0e2-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe0e2-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe0e2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0e2-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe0e2-129">See Also</span></span>  
 [<span data-ttu-id="fe0e2-130">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="fe0e2-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
