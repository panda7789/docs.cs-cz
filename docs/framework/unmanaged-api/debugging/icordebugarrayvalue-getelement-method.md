---
title: ICorDebugArrayValue::GetElement – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1be7eaeccb53e8b180aeb9492cd887f952bbaea5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645640"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="5eb3a-102">ICorDebugArrayValue::GetElement – metoda</span><span class="sxs-lookup"><span data-stu-id="5eb3a-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="5eb3a-103">Získá hodnotu prvku daného pole.</span><span class="sxs-lookup"><span data-stu-id="5eb3a-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eb3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5eb3a-104">Syntax</span></span>  
  
```  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5eb3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5eb3a-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="5eb3a-106">[in] Počet dimenzí tohoto `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="5eb3a-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="5eb3a-107">Tato hodnota je také velikost `indices` pole, protože jeho velikost se rovná počet rozměrů `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="5eb3a-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="5eb3a-108">[in] Pole hodnot indexu, z nichž každý určuje pozici v rámci dimenze sady `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="5eb3a-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="5eb3a-109">Tato hodnota nesmí být null.</span><span class="sxs-lookup"><span data-stu-id="5eb3a-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5eb3a-110">[out] Ukazatel na adresu ICorDebugValue objekt, který představuje hodnotu zadaného prvku.</span><span class="sxs-lookup"><span data-stu-id="5eb3a-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5eb3a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5eb3a-111">Requirements</span></span>  
 <span data-ttu-id="5eb3a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5eb3a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5eb3a-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5eb3a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5eb3a-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5eb3a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5eb3a-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5eb3a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
