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
ms.openlocfilehash: f38f9a3ebd88e0a5abb7a6bc8cb4026dc7d0f068
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736934"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="3639f-102">ICorDebugProcess2::GetReferenceValueFromGCHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="3639f-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="3639f-103">Získá odkaz na ukazatel na zadaný spravovaný objekt, který má uvolňování paměti zpracovávají.</span><span class="sxs-lookup"><span data-stu-id="3639f-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3639f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3639f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3639f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3639f-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="3639f-106">[in] Ukazatel na spravovaný objekt, který má popisovač kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="3639f-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="3639f-107">Tato hodnota je <xref:System.IntPtr> objektu a je možné načíst z <xref:System.Runtime.InteropServices.GCHandle> pro spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="3639f-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="3639f-108">[out] Ukazatel na adresu icordebugreferencevalue – objekt, který představuje odkaz na zadaný spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="3639f-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3639f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3639f-109">Remarks</span></span>  
 <span data-ttu-id="3639f-110">Nezaměňujte hodnotu vráceného odkazu s hodnotou odkaz kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="3639f-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="3639f-111">Vrácený odkaz se chová jako normální odkaz.</span><span class="sxs-lookup"><span data-stu-id="3639f-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="3639f-112">Při provádění kódu pokračuje po zarážku je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="3639f-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="3639f-113">Životnost cílový objekt nemá vliv životnost hodnota odkazu.</span><span class="sxs-lookup"><span data-stu-id="3639f-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3639f-114">`GetReferenceValueFromGCHandle` Popisovač metody nelze ověřit.</span><span class="sxs-lookup"><span data-stu-id="3639f-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="3639f-115">Proto `GetReferenceValueFromGCHandle` metoda může potenciálně poškodit ladicího programu a kódu, který se právě ladí, pokud je předán neplatný popisovač.</span><span class="sxs-lookup"><span data-stu-id="3639f-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3639f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3639f-116">Requirements</span></span>  
 <span data-ttu-id="3639f-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3639f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3639f-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3639f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3639f-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3639f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3639f-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3639f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
