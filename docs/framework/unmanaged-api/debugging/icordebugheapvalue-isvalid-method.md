---
title: "ICorDebugHeapValue::IsValid – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue.IsValid
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df7105c94a6f88c9c196f1d9d6be6f4a62f7c258
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="7c284-102">ICorDebugHeapValue::IsValid – metoda</span><span class="sxs-lookup"><span data-stu-id="7c284-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="7c284-103">Získá hodnotu, která určuje, zda je objekt reprezentovaný rozhraním tento icordebugheapvalue – platný.</span><span class="sxs-lookup"><span data-stu-id="7c284-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="7c284-104">Tato metoda je zastaralá v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="7c284-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c284-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c284-105">Syntax</span></span>  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c284-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c284-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="7c284-107">[out] Ukazatel na logickou hodnotu, která určuje, zda je tato hodnota v haldě platný.</span><span class="sxs-lookup"><span data-stu-id="7c284-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c284-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c284-108">Remarks</span></span>  
 <span data-ttu-id="7c284-109">Hodnota je neplatná, pokud má bylo uvolněno modulem garbage collector.</span><span class="sxs-lookup"><span data-stu-id="7c284-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="7c284-110">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="7c284-110">This method has been deprecated.</span></span> <span data-ttu-id="7c284-111">V rozhraní .NET Framework 2.0, všechny hodnoty jsou platné do [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) je volána, na kterých časové hodnoty jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="7c284-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c284-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c284-112">Requirements</span></span>  
 <span data-ttu-id="7c284-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c284-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c284-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c284-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c284-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c284-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c284-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c284-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
