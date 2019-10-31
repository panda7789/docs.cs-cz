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
ms.openlocfilehash: e23dfb86c2129a02a0ca95de8c89d8294e97ad81
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136840"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="7c501-102">CreateDebuggingInterfaceFromVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="7c501-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="7c501-103">Vytvoří objekt [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) na základě zadaných informací o verzi.</span><span class="sxs-lookup"><span data-stu-id="7c501-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="7c501-104">Tato funkce je zastaralá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7c501-104">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="7c501-105">Místo toho chcete-li získat rozhraní pro modul CLR (Common Language Runtime) 2,0, použijte metodu [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) a určete identifikátor třídy CLSID_CLRDebuggingLegacy a identifikátor rozhraní IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="7c501-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="7c501-106">Chcete-li získat rozhraní pro CLR 4 nebo novější, zavolejte funkci [CLRCreateInstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) a určete identifikátor třídy CLSID_CLRDebugging a identifikátor rozhraní IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="7c501-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c501-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c501-107">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c501-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c501-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="7c501-109">pro Verze `ICorDebug`, kterou očekává ladicí program.</span><span class="sxs-lookup"><span data-stu-id="7c501-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="7c501-110">Platné hodnoty najdete ve výčtu [CorDebugInterfaceVersion –](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="7c501-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="7c501-111">pro Verze společného jazykového modulu runtime přidružená k aplikaci nebo procesu, který se má ladit.</span><span class="sxs-lookup"><span data-stu-id="7c501-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="7c501-112">Informace o načtení této hodnoty naleznete v metodě [GetVersionFromProcess –](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) nebo [GetRequestedRuntimeVersion –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="7c501-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="7c501-113">mimo Umístění, které přijímá ukazatel na objekt `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="7c501-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c501-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7c501-114">Return Value</span></span>  
 <span data-ttu-id="7c501-115">Tato metoda vrací standardní chybové kódy modelu COM, jak jsou definovány v souboru WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="7c501-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="7c501-116">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="7c501-116">Return code</span></span>|<span data-ttu-id="7c501-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7c501-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7c501-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c501-118">S_OK</span></span>|<span data-ttu-id="7c501-119">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="7c501-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="7c501-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7c501-120">E_INVALIDARG</span></span>|<span data-ttu-id="7c501-121">`szDebuggeeVersion` nebo `ppCordb` je null nebo je řetězec verze nesprávný.</span><span class="sxs-lookup"><span data-stu-id="7c501-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c501-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c501-122">Remarks</span></span>  
 <span data-ttu-id="7c501-123">Parametr `szDebuggeeVersion` se mapuje na odpovídající verzi MSCorDbi. dll.</span><span class="sxs-lookup"><span data-stu-id="7c501-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c501-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c501-124">Requirements</span></span>  
 <span data-ttu-id="7c501-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c501-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c501-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7c501-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c501-127">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7c501-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c501-128">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c501-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c501-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c501-129">See also</span></span>

- [<span data-ttu-id="7c501-130">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="7c501-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
