---
title: ICorDebugType::GetFirstTypeParameter – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: da0097daea183c76f97f0b1966b313e1cb5a557b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379955"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a><span data-ttu-id="7df6e-102">ICorDebugType::GetFirstTypeParameter – metoda</span><span class="sxs-lookup"><span data-stu-id="7df6e-102">ICorDebugType::GetFirstTypeParameter Method</span></span>
<span data-ttu-id="7df6e-103">Získá ukazatel rozhraní na ICorDebugType, který představuje první <xref:System.Type> parametr typu reprezentovaného tímto `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="7df6e-103">Gets an interface pointer to an ICorDebugType that represents the first <xref:System.Type> parameter of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7df6e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7df6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7df6e-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="7df6e-106">mimo Ukazatel na adresu `ICorDebugType` objektu, který představuje první parametr.</span><span class="sxs-lookup"><span data-stu-id="7df6e-106">[out] A pointer to the address of an `ICorDebugType` object that represents the first parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7df6e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7df6e-107">Remarks</span></span>  
 <span data-ttu-id="7df6e-108">`GetFirstTypeParameter`lze ji volat v případech, kde další informace o typu zahrnují, maximálně jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="7df6e-108">`GetFirstTypeParameter` can be called in cases where the additional information about the type involves, at most, one type parameter.</span></span> <span data-ttu-id="7df6e-109">Konkrétně lze použít, pokud je typ ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF nebo ELEMENT_TYPE_PTR, jak je uvedeno v metodě [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7df6e-109">In particular, it can be used if the type is an ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7df6e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7df6e-110">Requirements</span></span>  
 <span data-ttu-id="7df6e-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7df6e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7df6e-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7df6e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7df6e-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7df6e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7df6e-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7df6e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
