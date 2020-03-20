---
title: ICorDebugProcess6::GetExportStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 6580fdaacaea17fcf886bfd7ac5e236925acf453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178534"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="79b03-102">ICorDebugProcess6::GetExportStepInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="79b03-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="79b03-103">Obsahuje informace o funkcích exportovaných za běhu, které vám pomohou krokovat spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="79b03-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79b03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79b03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79b03-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79b03-105">Parameters</span></span>  
 <span data-ttu-id="79b03-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="79b03-106">pszExportName</span></span>  
 <span data-ttu-id="79b03-107">[v] Název funkce exportu za běhu, jak je napsáno v tabulce exportu PE.</span><span class="sxs-lookup"><span data-stu-id="79b03-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="79b03-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="79b03-108">invokeKind</span></span>  
 <span data-ttu-id="79b03-109">[out] Ukazatel na člen a [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) výčet, který popisuje, jak exportované funkce vyvolá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="79b03-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="79b03-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="79b03-110">invokePurpose</span></span>  
 <span data-ttu-id="79b03-111">[out] Ukazatel na člena výčtu [CorDebugCodeInvokePurpose,](cordebugcodeinvokepurpose-enumeration.md) který popisuje, proč exportovaná funkce bude volat spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="79b03-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79b03-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="79b03-112">Return Value</span></span>  
 <span data-ttu-id="79b03-113">Metoda může vrátit hodnoty uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="79b03-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="79b03-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="79b03-114">Return value</span></span>|<span data-ttu-id="79b03-115">Popis</span><span class="sxs-lookup"><span data-stu-id="79b03-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="79b03-116">Volání metody bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="79b03-116">The method call was successful.</span></span>|  
|`E_POINTER`|<span data-ttu-id="79b03-117">`pInvokeKind`nebo `pInvokePurpose` je **null**.</span><span class="sxs-lookup"><span data-stu-id="79b03-117">`pInvokeKind` or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="79b03-118">Jiné `HRESULT` selhávající hodnoty.</span><span class="sxs-lookup"><span data-stu-id="79b03-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="79b03-119">Podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="79b03-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79b03-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79b03-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79b03-121">Tato metoda je k dispozici pouze s nativní .NET.</span><span class="sxs-lookup"><span data-stu-id="79b03-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79b03-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79b03-122">Requirements</span></span>  
 <span data-ttu-id="79b03-123">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79b03-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79b03-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79b03-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79b03-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79b03-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79b03-126">**Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79b03-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79b03-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="79b03-127">See also</span></span>

- [<span data-ttu-id="79b03-128">Rozhraní ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="79b03-128">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="79b03-129">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79b03-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
