---
title: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
ms.openlocfilehash: 57eb284bfe39ce92b2d6c03a2aeb4ae84d6aba91
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788668"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="8ad40-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack – metoda</span><span class="sxs-lookup"><span data-stu-id="8ad40-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="8ad40-103">Načte enumerátor do zásobníku volání vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="8ad40-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ad40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ad40-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ad40-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ad40-105">Parameters</span></span>  
 <span data-ttu-id="8ad40-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="8ad40-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="8ad40-107">mimo Ukazatel na adresu objektu rozhraní [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) , který je enumerátor trasování zásobníku pro objekt spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="8ad40-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ad40-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ad40-108">Remarks</span></span>  
 <span data-ttu-id="8ad40-109">Pokud nejsou k dispozici žádné informace zásobníku volání, vrátí metoda `S_OK`a [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) je platný enumerátor s délkou 0.</span><span class="sxs-lookup"><span data-stu-id="8ad40-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="8ad40-110">Pokud metoda nemůže načíst informace o trasování zásobníku, návratová hodnota je `E_FAIL` a není vrácen žádný enumerátor.</span><span class="sxs-lookup"><span data-stu-id="8ad40-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="8ad40-111">Objekt [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) zodpovídá za dekódování dat trasování zásobníku z pole `_stackTrace` objektu Exception.</span><span class="sxs-lookup"><span data-stu-id="8ad40-111">The [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ad40-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ad40-112">Requirements</span></span>  
 <span data-ttu-id="8ad40-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ad40-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ad40-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8ad40-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ad40-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8ad40-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ad40-116">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ad40-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad40-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ad40-117">See also</span></span>

- [<span data-ttu-id="8ad40-118">ICorDebugExceptionObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ad40-118">ICorDebugExceptionObjectValue Interface</span></span>](icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="8ad40-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8ad40-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
