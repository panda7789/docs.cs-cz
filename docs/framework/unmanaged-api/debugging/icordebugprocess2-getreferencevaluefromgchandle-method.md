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
ms.openlocfilehash: 47647bf0460507b4c88b47bf87bfcc3bf620aecc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137212"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="01ebf-102">ICorDebugProcess2::GetReferenceValueFromGCHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="01ebf-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="01ebf-103">Získá ukazatel odkazu na zadaný spravovaný objekt, který má popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="01ebf-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01ebf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01ebf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01ebf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01ebf-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="01ebf-106">pro Ukazatel na spravovaný objekt, který má popisovač uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="01ebf-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="01ebf-107">Tato hodnota je objekt <xref:System.IntPtr> a lze ho načíst z <xref:System.Runtime.InteropServices.GCHandle> pro spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="01ebf-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="01ebf-108">mimo Ukazatel na adresu objektu ICorDebugReferenceValue, který představuje odkaz na zadaný spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="01ebf-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01ebf-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01ebf-109">Remarks</span></span>  
 <span data-ttu-id="01ebf-110">Nepleťte si vrácenou referenční hodnotu s referenční hodnotou uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="01ebf-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="01ebf-111">Vrácený odkaz se chová jako normální reference.</span><span class="sxs-lookup"><span data-stu-id="01ebf-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="01ebf-112">Je zakázáno, pokud provádění kódu pokračuje po zarážce.</span><span class="sxs-lookup"><span data-stu-id="01ebf-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="01ebf-113">Doba života cílového objektu není ovlivněna životností referenční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01ebf-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01ebf-114">Metoda `GetReferenceValueFromGCHandle` neověřuje popisovač.</span><span class="sxs-lookup"><span data-stu-id="01ebf-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="01ebf-115">Proto metoda `GetReferenceValueFromGCHandle` může potenciálně poškodit ladicí program i kód, který je laděn, pokud je předán neplatný popisovač.</span><span class="sxs-lookup"><span data-stu-id="01ebf-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01ebf-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01ebf-116">Requirements</span></span>  
 <span data-ttu-id="01ebf-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01ebf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01ebf-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="01ebf-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01ebf-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="01ebf-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01ebf-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01ebf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
