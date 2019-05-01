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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f546d7707c40f7f26a46177ae972a988e54e1e45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965825"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="42fdf-102">CreateCordbObject – funkce</span><span class="sxs-lookup"><span data-stu-id="42fdf-102">CreateCordbObject Function</span></span>
<span data-ttu-id="42fdf-103">Vytvoří rozhraní ladicího programu ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)), která poskytuje funkce pro vytvoření instance spravované ladicí relace na vzdálený proces.</span><span class="sxs-lookup"><span data-stu-id="42fdf-103">Creates a debugger interface ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42fdf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42fdf-104">Syntax</span></span>  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42fdf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42fdf-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="42fdf-106">[in] Ladicí verze cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="42fdf-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="42fdf-107">Tento parametr musí být CorDebugVersion_2_0 pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="42fdf-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="42fdf-108">[out] Ukazatel na ukazatel na objekt, který bude převeden [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní a vrátí.</span><span class="sxs-lookup"><span data-stu-id="42fdf-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42fdf-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="42fdf-109">Return Value</span></span>  
 <span data-ttu-id="42fdf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="42fdf-110">S_OK</span></span>  
 <span data-ttu-id="42fdf-111">Úspěšně bylo zjištěno číslo CLRs v procesu a odpovídající popisovač a pole cesty byly správně vyplněné.</span><span class="sxs-lookup"><span data-stu-id="42fdf-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="42fdf-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="42fdf-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="42fdf-113">`ppCordb` má hodnotu null, nebo `iDebuggerVersion` není CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="42fdf-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="42fdf-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="42fdf-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="42fdf-115">Nepovedlo se přidělit dostatek paměti pro `ppCordb`</span><span class="sxs-lookup"><span data-stu-id="42fdf-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="42fdf-116">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="42fdf-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="42fdf-117">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="42fdf-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42fdf-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42fdf-118">Remarks</span></span>  
 <span data-ttu-id="42fdf-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní, které se vrátí v `ppCordb` pro všechny spravované ladění služby je rozhraní pro ladění nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="42fdf-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42fdf-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42fdf-120">Requirements</span></span>  
 <span data-ttu-id="42fdf-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42fdf-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42fdf-122">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="42fdf-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="42fdf-123">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="42fdf-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="42fdf-124">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="42fdf-124">**.NET Framework Versions:** 3.5 SP1</span></span>
