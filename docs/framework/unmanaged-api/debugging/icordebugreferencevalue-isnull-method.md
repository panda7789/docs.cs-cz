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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 972df4613255dc1b71801e02d387a735dfc632c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782932"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="9d4a7-102">ICorDebugReferenceValue::IsNull – metoda</span><span class="sxs-lookup"><span data-stu-id="9d4a7-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="9d4a7-103">Získá hodnotu určující, zda tento icordebugreferencevalue – v takovém případě je hodnota null, `ICorDebugReferenceValue` neukazuje na objekt.</span><span class="sxs-lookup"><span data-stu-id="9d4a7-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d4a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d4a7-104">Syntax</span></span>  
  
```  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d4a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d4a7-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="9d4a7-106">[out] Ukazatel na logickou hodnotu, která je `true` tato `ICorDebugReferenceValue` objekt je null; v opačném případě `pbNull` je `false`.</span><span class="sxs-lookup"><span data-stu-id="9d4a7-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d4a7-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d4a7-107">Requirements</span></span>  
 <span data-ttu-id="9d4a7-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d4a7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d4a7-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d4a7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d4a7-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d4a7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d4a7-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d4a7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
