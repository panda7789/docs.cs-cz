---
title: "ICorDebugProcess6::GetExportStepInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3c69bbc904f54636e56be6d235d1070b9fecf1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="cbfa4-102">ICorDebugProcess6::GetExportStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="cbfa4-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="cbfa4-103">Obsahuje informace o modulu runtime exportované funkce, které umožňují krok prostřednictvím spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="cbfa4-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbfa4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbfa4-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbfa4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbfa4-105">Parameters</span></span>  
 <span data-ttu-id="cbfa4-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="cbfa4-106">pszExportName</span></span>  
 <span data-ttu-id="cbfa4-107">[v] Název funkce exportu runtime zapsaný v tabulce PE export.</span><span class="sxs-lookup"><span data-stu-id="cbfa4-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="cbfa4-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="cbfa4-108">invokeKind</span></span>  
 <span data-ttu-id="cbfa4-109">[out] Ukazatel na členem [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) výčet, který popisuje, jak bude exportované funkce vyvolání spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="cbfa4-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="cbfa4-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="cbfa4-110">invokePurpose</span></span>  
 <span data-ttu-id="cbfa4-111">[out] Ukazatel na členem [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) výčet, který popisuje, proč exportované funkce zavolá spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="cbfa4-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbfa4-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cbfa4-112">Return Value</span></span>  
 <span data-ttu-id="cbfa4-113">Metoda může vrátit hodnoty uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="cbfa4-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="cbfa4-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cbfa4-114">Return value</span></span>|<span data-ttu-id="cbfa4-115">Popis</span><span class="sxs-lookup"><span data-stu-id="cbfa4-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="cbfa4-116">Volání metody, které bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="cbfa4-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="cbfa4-117">`pInvokeKind`nebo `pInvokePurpose` je **null**.</span><span class="sxs-lookup"><span data-stu-id="cbfa4-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="cbfa4-118">Další selhání `HRESULT` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cbfa4-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="cbfa4-119">Podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="cbfa4-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbfa4-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cbfa4-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbfa4-121">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="cbfa4-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbfa4-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cbfa4-122">Requirements</span></span>  
 <span data-ttu-id="cbfa4-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbfa4-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbfa4-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cbfa4-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbfa4-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbfa4-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbfa4-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbfa4-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbfa4-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="cbfa4-127">See Also</span></span>  
 [<span data-ttu-id="cbfa4-128">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cbfa4-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="cbfa4-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cbfa4-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
