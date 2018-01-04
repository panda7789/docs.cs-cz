---
title: "ICorDebugAppDomain2::GetArrayOrPointerType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2.GetArrayOrPointerType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6beb75638ccbf81149fd7fa1682acca3e7673dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="de021-102">ICorDebugAppDomain2::GetArrayOrPointerType – metoda</span><span class="sxs-lookup"><span data-stu-id="de021-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="de021-103">Získá zadaný typ, nebo ukazatel nebo odkaz na zadaný typ pole.</span><span class="sxs-lookup"><span data-stu-id="de021-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de021-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de021-104">Syntax</span></span>  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de021-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de021-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="de021-106">[v] Hodnota CorElementType – výčet, který určuje základní typ nativní (pole, ukazatel nebo odkaz) má být vytvořen.</span><span class="sxs-lookup"><span data-stu-id="de021-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="de021-107">[v] Pořadí (to znamená, počet dimenzí) pole.</span><span class="sxs-lookup"><span data-stu-id="de021-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="de021-108">Tato hodnota musí být 0, pokud `elementType` Určuje typ ukazatele nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="de021-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="de021-109">[v] Ukazatel na ICorDebugType objekt, který představuje typ pole, ukazatel nebo odkaz, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="de021-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="de021-110">[out] Ukazatel na adresu `ICorDebugType` typ objektu, který reprezentuje sestavené pole, ukazatel typu nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="de021-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de021-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de021-111">Remarks</span></span>  
 <span data-ttu-id="de021-112">Hodnota *elementType* musí mít jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="de021-112">The value of *elementType* must be one of the following:</span></span>  
  
-   <span data-ttu-id="de021-113">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="de021-113">ELEMENT_TYPE_PTR</span></span>  
  
-   <span data-ttu-id="de021-114">TYPU ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="de021-114">ELEMENT_TYPE_BYREF</span></span>  
  
-   <span data-ttu-id="de021-115">ELEMENT_TYPE_ARRAY nebo ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="de021-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="de021-116">Pokud hodnota *elementType* ELEMENT_TYPE_PTR nebo typu ELEMENT_TYPE_BYREF, *nRank* musí být nula.</span><span class="sxs-lookup"><span data-stu-id="de021-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de021-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de021-117">Requirements</span></span>  
 <span data-ttu-id="de021-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de021-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de021-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de021-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de021-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de021-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de021-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de021-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
