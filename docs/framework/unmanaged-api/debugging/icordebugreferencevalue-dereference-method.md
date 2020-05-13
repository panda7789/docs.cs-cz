---
title: ICorDebugReferenceValue::Dereference – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
ms.openlocfilehash: 7c64823e1a5c519eb74b508af093afeb1132e608
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210082"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="ef03a-102">ICorDebugReferenceValue::Dereference – metoda</span><span class="sxs-lookup"><span data-stu-id="ef03a-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="ef03a-103">Načte objekt, na který je odkazováno.</span><span class="sxs-lookup"><span data-stu-id="ef03a-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef03a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef03a-104">Syntax</span></span>  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef03a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef03a-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="ef03a-106">mimo Ukazatel na adresu ICorDebugValue, která představuje objekt, na který odkazuje tento objekt ICorDebugReferenceValue.</span><span class="sxs-lookup"><span data-stu-id="ef03a-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef03a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef03a-107">Remarks</span></span>  
 <span data-ttu-id="ef03a-108">`ICorDebugValue`Objekt je platný pouze v případě, že jeho odkaz ještě není zakázán.</span><span class="sxs-lookup"><span data-stu-id="ef03a-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef03a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef03a-109">Requirements</span></span>  
 <span data-ttu-id="ef03a-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef03a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef03a-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ef03a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef03a-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ef03a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef03a-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef03a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
