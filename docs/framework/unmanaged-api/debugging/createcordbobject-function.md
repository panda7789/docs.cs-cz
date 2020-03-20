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
ms.openlocfilehash: 2716adcc8c79c8003202561ea2011c2469a6bc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179234"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="7af65-102">CreateCordbObject – funkce</span><span class="sxs-lookup"><span data-stu-id="7af65-102">CreateCordbObject Function</span></span>
<span data-ttu-id="7af65-103">Vytvoří ladicí rozhraní ([ICorDebug](icordebug-interface.md)), které poskytuje funkce pro vytvoření instance spravované relace ladění ve vzdáleném procesu.</span><span class="sxs-lookup"><span data-stu-id="7af65-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7af65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7af65-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7af65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7af65-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="7af65-106">[v] Ladicí verze cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="7af65-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="7af65-107">Tento parametr musí být CorDebugVersion_2_0 pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="7af65-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="7af65-108">[out] Ukazatel na ukazatel na objekt, který bude přetypován do rozhraní [ICorDebug](icordebug-interface.md) a vrácen.</span><span class="sxs-lookup"><span data-stu-id="7af65-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7af65-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7af65-109">Return Value</span></span>  
 <span data-ttu-id="7af65-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7af65-110">S_OK</span></span>  
 <span data-ttu-id="7af65-111">Počet CLRs v procesu byl úspěšně určen a odpovídající popisovač a pole cesty byly správně vyplněny.</span><span class="sxs-lookup"><span data-stu-id="7af65-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="7af65-112">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="7af65-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="7af65-113">`ppCordb`je null `iDebuggerVersion` nebo není CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="7af65-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="7af65-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7af65-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="7af65-115">Nelze přidělit dostatek paměti pro`ppCordb`</span><span class="sxs-lookup"><span data-stu-id="7af65-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="7af65-116">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="7af65-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7af65-117">Další selhání.</span><span class="sxs-lookup"><span data-stu-id="7af65-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7af65-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7af65-118">Remarks</span></span>  
 <span data-ttu-id="7af65-119">Rozhraní [ICorDebug,](icordebug-interface.md) které `ppCordb` je vráceno v je nejvyšší úrovně ladění rozhraní pro všechny spravované ladicí služby.</span><span class="sxs-lookup"><span data-stu-id="7af65-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7af65-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7af65-120">Requirements</span></span>  
 <span data-ttu-id="7af65-121">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7af65-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7af65-122">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="7af65-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="7af65-123">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="7af65-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="7af65-124">**Verze rozhraní .NET Framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="7af65-124">**.NET Framework Versions:** 3.5 SP1</span></span>
