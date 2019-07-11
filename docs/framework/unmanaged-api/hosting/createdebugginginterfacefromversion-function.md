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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe34ffded73e8305e4ade3bb9b402b1d8e1bcc49
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764673"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="63959-102">CreateDebuggingInterfaceFromVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="63959-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="63959-103">Vytvoří [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objektu na základě zadané verze informací.</span><span class="sxs-lookup"><span data-stu-id="63959-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="63959-104">Tato funkce je zastaralé v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="63959-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="63959-105">Místo toho rozhraní pro modul common language runtime (CLR) 2.0, použijte [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metodu a zadejte identifikátor třídy CLSID_CLRDebuggingLegacy a IID_ICorDebug identifikátoru rozhraní.</span><span class="sxs-lookup"><span data-stu-id="63959-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="63959-106">K získání rozhraní pro modul CLR 4 nebo novější, zavolejte [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) fungovat a zadejte identifikátor třídy CLSID_CLRDebugging a IID_ICLRDebugging identifikátoru rozhraní.</span><span class="sxs-lookup"><span data-stu-id="63959-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63959-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63959-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63959-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="63959-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="63959-109">[in] Verze `ICorDebug` to je očekáváno ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="63959-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="63959-110">Zobrazit [cordebuginterfaceversion –](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) platné hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="63959-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="63959-111">[in] Verze společného běhového jazykového přidružené aplikace nebo proces, který chcete ladit.</span><span class="sxs-lookup"><span data-stu-id="63959-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="63959-112">Zobrazit [getversionfromprocess –](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) nebo [getrequestedruntimeversion –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metoda informace o načtení tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="63959-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="63959-113">[out] Umístění, které přijímá ukazatel `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="63959-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63959-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="63959-114">Return Value</span></span>  
 <span data-ttu-id="63959-115">Tato metoda vrací standardní kódy chyb modelu COM, jak jsou definovány v souboru WinError.h kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="63959-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="63959-116">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="63959-116">Return code</span></span>|<span data-ttu-id="63959-117">Popis</span><span class="sxs-lookup"><span data-stu-id="63959-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="63959-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="63959-118">S_OK</span></span>|<span data-ttu-id="63959-119">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="63959-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="63959-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="63959-120">E_INVALIDARG</span></span>|<span data-ttu-id="63959-121">`szDebuggeeVersion` nebo `ppCordb` má hodnotu null nebo verze řetězce je nesprávný.</span><span class="sxs-lookup"><span data-stu-id="63959-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63959-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63959-122">Remarks</span></span>  
 <span data-ttu-id="63959-123">`szDebuggeeVersion` Parametr mapují na odpovídající verzi knihovna MSCorDbi.dll.</span><span class="sxs-lookup"><span data-stu-id="63959-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63959-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63959-124">Requirements</span></span>  
 <span data-ttu-id="63959-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63959-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63959-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63959-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63959-127">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63959-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63959-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63959-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63959-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63959-129">See also</span></span>

- [<span data-ttu-id="63959-130">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="63959-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
