---
title: ICorDebugReferenceValue::IsNull – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: e8b778c0880040f5ffd639a445fd5663ce493219
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379085"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="3a50c-102">ICorDebugReferenceValue::IsNull – metoda</span><span class="sxs-lookup"><span data-stu-id="3a50c-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="3a50c-103">Získá hodnotu, která označuje, zda je tato ICorDebugReferenceValue hodnotou null. v takovém případě neodkazuje `ICorDebugReferenceValue` na objekt.</span><span class="sxs-lookup"><span data-stu-id="3a50c-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a50c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a50c-104">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a50c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a50c-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="3a50c-106">mimo Ukazatel na logickou hodnotu, která je `true` v případě, že je tento `ICorDebugReferenceValue` objekt null. v opačném případě `pbNull` je `false` .</span><span class="sxs-lookup"><span data-stu-id="3a50c-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a50c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a50c-107">Requirements</span></span>  
 <span data-ttu-id="3a50c-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a50c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a50c-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a50c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a50c-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3a50c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a50c-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a50c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
