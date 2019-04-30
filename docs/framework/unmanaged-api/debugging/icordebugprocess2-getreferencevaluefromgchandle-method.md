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
ms.openlocfilehash: 08bf4022f7cd7f85ffe7939c16fd47950e131a77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948886"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="dc4e5-102">ICorDebugProcess2::GetReferenceValueFromGCHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="dc4e5-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="dc4e5-103">Získá odkaz na ukazatel na zadaný spravovaný objekt, který má uvolňování paměti zpracovávají.</span><span class="sxs-lookup"><span data-stu-id="dc4e5-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc4e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc4e5-104">Syntax</span></span>  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc4e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc4e5-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="dc4e5-106">[in] Ukazatel na spravovaný objekt, který má popisovač kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="dc4e5-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="dc4e5-107">Tato hodnota je <xref:System.IntPtr> objektu a je možné načíst z <xref:System.Runtime.InteropServices.GCHandle> pro spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="dc4e5-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="dc4e5-108">[out] Ukazatel na adresu icordebugreferencevalue – objekt, který představuje odkaz na zadaný spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="dc4e5-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc4e5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc4e5-109">Remarks</span></span>  
 <span data-ttu-id="dc4e5-110">Nezaměňujte hodnotu vráceného odkazu s hodnotou odkaz kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="dc4e5-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="dc4e5-111">Vrácený odkaz se chová jako normální odkaz.</span><span class="sxs-lookup"><span data-stu-id="dc4e5-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="dc4e5-112">Při provádění kódu pokračuje po zarážku je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="dc4e5-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="dc4e5-113">Životnost cílový objekt nemá vliv životnost hodnota odkazu.</span><span class="sxs-lookup"><span data-stu-id="dc4e5-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc4e5-114">`GetReferenceValueFromGCHandle` Popisovač metody nelze ověřit.</span><span class="sxs-lookup"><span data-stu-id="dc4e5-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="dc4e5-115">Proto `GetReferenceValueFromGCHandle` metoda může potenciálně poškodit ladicího programu a kódu, který se právě ladí, pokud je předán neplatný popisovač.</span><span class="sxs-lookup"><span data-stu-id="dc4e5-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc4e5-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc4e5-116">Requirements</span></span>  
 <span data-ttu-id="dc4e5-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc4e5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc4e5-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc4e5-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc4e5-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc4e5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc4e5-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc4e5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
