---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21da325ee58df65ac449464f8292f2ba94d99338
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943299"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="b8ad7-102">ICorDebugProcess2::GetReferenceValueFromGCHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="b8ad7-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="b8ad7-103">Získá ukazatel odkazu na zadaný spravovaný objekt, který má popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b8ad7-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8ad7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8ad7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8ad7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8ad7-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="b8ad7-106">pro Ukazatel na spravovaný objekt, který má popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b8ad7-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="b8ad7-107">Tato hodnota je <xref:System.IntPtr> objekt, který lze načíst <xref:System.Runtime.InteropServices.GCHandle> z objektu pro spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="b8ad7-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="b8ad7-108">mimo Ukazatel na adresu objektu ICorDebugReferenceValue, který představuje odkaz na zadaný spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="b8ad7-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8ad7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8ad7-109">Remarks</span></span>  
 <span data-ttu-id="b8ad7-110">Nepleťte si vrácenou referenční hodnotu s referenční hodnotou uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b8ad7-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="b8ad7-111">Vrácený odkaz se chová jako normální reference.</span><span class="sxs-lookup"><span data-stu-id="b8ad7-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="b8ad7-112">Je zakázáno, pokud provádění kódu pokračuje po zarážce.</span><span class="sxs-lookup"><span data-stu-id="b8ad7-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="b8ad7-113">Doba života cílového objektu není ovlivněna životností referenční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b8ad7-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8ad7-114">`GetReferenceValueFromGCHandle` Metoda neověřuje popisovač.</span><span class="sxs-lookup"><span data-stu-id="b8ad7-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="b8ad7-115">`GetReferenceValueFromGCHandle` Proto metoda může potenciálně poškodit ladicí program i kód, který je laděn, pokud je předán neplatný popisovač.</span><span class="sxs-lookup"><span data-stu-id="b8ad7-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8ad7-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8ad7-116">Requirements</span></span>  
 <span data-ttu-id="b8ad7-117">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8ad7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8ad7-118">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b8ad7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8ad7-119">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8ad7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8ad7-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8ad7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
