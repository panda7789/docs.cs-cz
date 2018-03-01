---
title: "ICorDebugType::EnumerateTypeParameters – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d4b864b2b5fd4f2a6ed03218ce6e7b6f3bf62202
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="6c634-102">ICorDebugType::EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="6c634-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="6c634-103">Získá ukazatele rozhraní k ICorDebugTypeEnum, který obsahuje <xref:System.Type> parametry třídy odkazuje tento ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="6c634-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c634-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c634-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c634-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c634-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="6c634-106">[out] Ukazatel na adresu `ICorDebugTypeEnum` obsahující parametry typu.</span><span class="sxs-lookup"><span data-stu-id="6c634-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c634-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c634-107">Remarks</span></span>  
 <span data-ttu-id="6c634-108">Můžete použít `EnumerateTypeParameters` Pokud je hodnota CorElementType vrácené [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) je ELEMENT_TYPE_CLASS, Typ ELEMENT_TYPE_VALUETYPE, který, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, typu ELEMENT_TYPE_BYREF, typ ELEMENT_TYPE_ PTR, nebo ELEMENT_TYPE_FNPTR.</span><span class="sxs-lookup"><span data-stu-id="6c634-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="6c634-109">Počet parametrů a jejich pořadí, závisí na typu:</span><span class="sxs-lookup"><span data-stu-id="6c634-109">The number of parameters and their order depends on the type:</span></span>  
  
-   <span data-ttu-id="6c634-110">ELEMENT_TYPE_CLASS nebo Typ ELEMENT_TYPE_VALUETYPE, který: počet parametrů typů, které jsou součástí `ICorDebugTypeEnum` , tato metoda vrátí, bude záviset na počtu formální typ parametrů pro odpovídající třídu.</span><span class="sxs-lookup"><span data-stu-id="6c634-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="6c634-111">Například, pokud je typ `class Dict<String,int32>`, pak `EnumerateTypeParameters` vrátí `ICorDebugTypeEnum` obsahující objekty, které představují `String` a `int32` v pořadí.</span><span class="sxs-lookup"><span data-stu-id="6c634-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
-   <span data-ttu-id="6c634-112">ELEMENT_TYPE_FNPTR: Počet parametrů typů, které jsou součástí `ICorDebugTypeEnum` bude jeden větší než počet argumentů přijímány funkcí.</span><span class="sxs-lookup"><span data-stu-id="6c634-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="6c634-113">První parametr typu obsažené v `ICorDebugTypeEnum` je návratový typ funkce a následné typ parametry jsou parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="6c634-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
-   <span data-ttu-id="6c634-114">ELEMENT_TYPE_ARRAY ELEMENT_TYPE_SZARRAY, typu ELEMENT_TYPE_BYREF nebo ELEMENT_TYPE_PTR: jeden typ parametr bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="6c634-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="6c634-115">Pokud typ je typ pole, jako například `int32[]`,`EnumerateTypeParameters` vrátí `ICorDebugTypeEnum` obsahující k objekt reprezentující `int32`.</span><span class="sxs-lookup"><span data-stu-id="6c634-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c634-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c634-116">Requirements</span></span>  
 <span data-ttu-id="6c634-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c634-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c634-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c634-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c634-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c634-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c634-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c634-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
