---
title: ICorDebugProcess6::GetExportStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24c3c46a1f347093061983b9185234cc9959b68d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656138"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="6b61f-102">ICorDebugProcess6::GetExportStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="6b61f-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="6b61f-103">Obsahuje informace o modulu runtime exportované funkce, které umožňují krokovat spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6b61f-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b61f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b61f-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b61f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b61f-105">Parameters</span></span>  
 <span data-ttu-id="6b61f-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="6b61f-106">pszExportName</span></span>  
 <span data-ttu-id="6b61f-107">[in] Název exportu funkce modulu runtime, jak je uvedená v tabulce exportu PE.</span><span class="sxs-lookup"><span data-stu-id="6b61f-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="6b61f-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="6b61f-108">invokeKind</span></span>  
 <span data-ttu-id="6b61f-109">[out] Ukazatel na člen [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) výčet, který popisuje, jak exportované funkce vyvolá spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6b61f-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="6b61f-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="6b61f-110">invokePurpose</span></span>  
 <span data-ttu-id="6b61f-111">[out] Ukazatel na člen [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) výčet, který popisuje, proč exportované funkce bude volat spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6b61f-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b61f-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6b61f-112">Return Value</span></span>  
 <span data-ttu-id="6b61f-113">Metoda může vrátit hodnoty uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="6b61f-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="6b61f-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6b61f-114">Return value</span></span>|<span data-ttu-id="6b61f-115">Popis</span><span class="sxs-lookup"><span data-stu-id="6b61f-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="6b61f-116">Volání metody bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="6b61f-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="6b61f-117">`pInvokeKind` nebo `pInvokePurpose` je **null**.</span><span class="sxs-lookup"><span data-stu-id="6b61f-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="6b61f-118">Další selhání `HRESULT` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6b61f-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="6b61f-119">Podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="6b61f-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b61f-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b61f-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b61f-121">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6b61f-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b61f-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b61f-122">Requirements</span></span>  
 <span data-ttu-id="6b61f-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b61f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b61f-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b61f-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b61f-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b61f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b61f-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b61f-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b61f-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b61f-127">See also</span></span>
- [<span data-ttu-id="6b61f-128">ICorDebugProcess6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b61f-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="6b61f-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6b61f-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
