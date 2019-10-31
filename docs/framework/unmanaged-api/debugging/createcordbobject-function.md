---
title: CreateCordbObject – funkce
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: d21e0d3d0370ec7c1b223be29099f6b99822463b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132108"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="5f321-102">CreateCordbObject – funkce</span><span class="sxs-lookup"><span data-stu-id="5f321-102">CreateCordbObject Function</span></span>
<span data-ttu-id="5f321-103">Vytvoří rozhraní ladicího programu ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)), které poskytuje funkce pro vytvoření instance spravované relace ladění na vzdáleném procesu.</span><span class="sxs-lookup"><span data-stu-id="5f321-103">Creates a debugger interface ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f321-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f321-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f321-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f321-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="5f321-106">pro Verze ladicího programu cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="5f321-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="5f321-107">Tento parametr musí být CorDebugVersion_2_0 pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="5f321-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="5f321-108">mimo Ukazatel na ukazatel na objekt, který bude převeden na rozhraní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) a vráceno.</span><span class="sxs-lookup"><span data-stu-id="5f321-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f321-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5f321-109">Return Value</span></span>  
 <span data-ttu-id="5f321-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f321-110">S_OK</span></span>  
 <span data-ttu-id="5f321-111">Počet CLRs v procesu byl úspěšně zjištěn a odpovídající pole popisovače a cesty byly správně vyplněny.</span><span class="sxs-lookup"><span data-stu-id="5f321-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="5f321-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5f321-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="5f321-113">`ppCordb` je null nebo `iDebuggerVersion` není CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="5f321-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="5f321-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5f321-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="5f321-115">Nelze přidělit dostatek paměti pro `ppCordb`</span><span class="sxs-lookup"><span data-stu-id="5f321-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="5f321-116">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="5f321-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="5f321-117">Další chyby.</span><span class="sxs-lookup"><span data-stu-id="5f321-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f321-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f321-118">Remarks</span></span>  
 <span data-ttu-id="5f321-119">Rozhraní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , které je vráceno v `ppCordb`, je rozhraní ladění nejvyšší úrovně pro všechny spravované služby ladění.</span><span class="sxs-lookup"><span data-stu-id="5f321-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f321-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f321-120">Requirements</span></span>  
 <span data-ttu-id="5f321-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f321-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f321-122">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="5f321-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="5f321-123">**Knihovna:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="5f321-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="5f321-124">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="5f321-124">**.NET Framework Versions:** 3.5 SP1</span></span>
