---
title: "ICorDebugProcess2::GetReferenceValueFromGCHandle – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d40d1799a7c1572e8213fda3a163fb9a84060f92
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="72cab-102">ICorDebugProcess2::GetReferenceValueFromGCHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="72cab-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="72cab-103">Získá odkaz na ukazatel na zadaný spravovaný objekt, který je uvolnění paměti zpracovat.</span><span class="sxs-lookup"><span data-stu-id="72cab-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72cab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72cab-104">Syntax</span></span>  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72cab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72cab-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="72cab-106">[v] Ukazatel na spravovaný objekt, který má kolekci popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="72cab-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="72cab-107">Tato hodnota je <xref:System.IntPtr> objektu a je možné načíst z <xref:System.Runtime.InteropServices.GCHandle> pro spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="72cab-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="72cab-108">[out] Ukazatel na adresu ICorDebugReferenceValue objekt, který reprezentuje odkaz na zadaný spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="72cab-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72cab-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72cab-109">Remarks</span></span>  
 <span data-ttu-id="72cab-110">Nezaměňujte hodnota vrácená odkazu s hodnotou odkaz na kolekci paměti.</span><span class="sxs-lookup"><span data-stu-id="72cab-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="72cab-111">Odkaz na vrácený se chová jako normální odkaz.</span><span class="sxs-lookup"><span data-stu-id="72cab-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="72cab-112">Při provádění kódu pokračovat po zarážku je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="72cab-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="72cab-113">Životnost cílový objekt není ovlivněn životnost hodnota odkazu.</span><span class="sxs-lookup"><span data-stu-id="72cab-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72cab-114">`GetReferenceValueFromGCHandle` Metoda neověřuje popisovač.</span><span class="sxs-lookup"><span data-stu-id="72cab-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="72cab-115">Proto `GetReferenceValueFromGCHandle` metoda může potenciálně dojít k poškození ladicího programu a kód laděné, pokud je předán neplatný popisovač.</span><span class="sxs-lookup"><span data-stu-id="72cab-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72cab-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72cab-116">Requirements</span></span>  
 <span data-ttu-id="72cab-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72cab-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72cab-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72cab-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72cab-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72cab-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72cab-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72cab-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
