---
title: ICorDebugType2::GetTypeID Method
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b19efdedc21f66e4692ce1850eb3947f856e436
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083748"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="b6ce2-102">ICorDebugType2::GetTypeID Method</span><span class="sxs-lookup"><span data-stu-id="b6ce2-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="b6ce2-103">Získá [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) u tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="b6ce2-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ce2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6ce2-104">Syntax</span></span>  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6ce2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6ce2-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="b6ce2-106">[out] Ukazatel [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="b6ce2-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6ce2-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b6ce2-107">Return Value</span></span>  
 <span data-ttu-id="b6ce2-108">Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kódu při selhání.</span><span class="sxs-lookup"><span data-stu-id="b6ce2-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="b6ce2-109">`HRESULT` Kódy patří následující:</span><span class="sxs-lookup"><span data-stu-id="b6ce2-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="b6ce2-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="b6ce2-110">Return code</span></span>|<span data-ttu-id="b6ce2-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b6ce2-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="b6ce2-112">Metoda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="b6ce2-112">Method succeeded.</span></span> <span data-ttu-id="b6ce2-113">Metoda byla načtena platný [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span><span class="sxs-lookup"><span data-stu-id="b6ce2-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="b6ce2-114">Typ se nenačetl.</span><span class="sxs-lookup"><span data-stu-id="b6ce2-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="b6ce2-115">Tento typ není podporovaný.</span><span class="sxs-lookup"><span data-stu-id="b6ce2-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6ce2-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6ce2-116">Remarks</span></span>  
 <span data-ttu-id="b6ce2-117">Tato metoda poskytuje mapování z ICorDebugType, který představuje typ, který může nebo nemusí byla načtena do modulu runtime, na [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), která slouží jako neprůhledným zpracování, který identifikuje typ zavedeny do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b6ce2-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="b6ce2-118">Pokud typ, který představuje ICorDebugType nebyl dosud bylo načteno, vrátí tato metoda `CORDBG_E_CLASS_NOT_LOADED`.</span><span class="sxs-lookup"><span data-stu-id="b6ce2-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="b6ce2-119">Pokud typ není podporován, vrátí `CORDBG_E_UNSUPPORTED`.</span><span class="sxs-lookup"><span data-stu-id="b6ce2-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ce2-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6ce2-120">Requirements</span></span>  
 <span data-ttu-id="b6ce2-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6ce2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ce2-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6ce2-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6ce2-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6ce2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6ce2-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6ce2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ce2-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6ce2-125">See also</span></span>

- [<span data-ttu-id="b6ce2-126">ICorDebugType2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6ce2-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
