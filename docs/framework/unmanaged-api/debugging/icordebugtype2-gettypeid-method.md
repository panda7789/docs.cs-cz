---
title: "ICorDebugType2::GetTypeID – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugType2.GetTypeID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d18aa8210ea90736c0757e2587aab4ff143dcdad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="48e8f-102">ICorDebugType2::GetTypeID – metoda</span><span class="sxs-lookup"><span data-stu-id="48e8f-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="48e8f-103">Získá [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento typ.</span><span class="sxs-lookup"><span data-stu-id="48e8f-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e8f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48e8f-104">Syntax</span></span>  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48e8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="48e8f-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="48e8f-106">[out] Ukazatel [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="48e8f-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48e8f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="48e8f-107">Return Value</span></span>  
 <span data-ttu-id="48e8f-108">Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kód při selhání.</span><span class="sxs-lookup"><span data-stu-id="48e8f-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="48e8f-109">`HRESULT` Kódy zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="48e8f-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="48e8f-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="48e8f-110">Return code</span></span>|<span data-ttu-id="48e8f-111">Popis</span><span class="sxs-lookup"><span data-stu-id="48e8f-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="48e8f-112">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="48e8f-112">Method succeeded.</span></span> <span data-ttu-id="48e8f-113">Metoda má načíst platná [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span><span class="sxs-lookup"><span data-stu-id="48e8f-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="48e8f-114">Typ nebyla načtena.</span><span class="sxs-lookup"><span data-stu-id="48e8f-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="48e8f-115">Typ není podporován.</span><span class="sxs-lookup"><span data-stu-id="48e8f-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48e8f-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48e8f-116">Remarks</span></span>  
 <span data-ttu-id="48e8f-117">Tato metoda poskytuje mapování z ICorDebugType, který představuje typ, který může nebo nemusí mít byla načtena do modulu runtime pro [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), která slouží jako neprůhledné zpracování, který identifikuje typu načíst do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="48e8f-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="48e8f-118">Pokud typ, který představuje ICorDebugType nebyl dosud bylo načteno, vrátí tato metoda `CORDBG_E_CLASS_NOT_LOADED`.</span><span class="sxs-lookup"><span data-stu-id="48e8f-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="48e8f-119">Pokud není podporován typ, vrátí `CORDBG_E_UNSUPPORTED`.</span><span class="sxs-lookup"><span data-stu-id="48e8f-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48e8f-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48e8f-120">Requirements</span></span>  
 <span data-ttu-id="48e8f-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48e8f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48e8f-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48e8f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48e8f-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48e8f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48e8f-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48e8f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e8f-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="48e8f-125">See Also</span></span>  
 [<span data-ttu-id="48e8f-126">ICorDebugType2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48e8f-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
