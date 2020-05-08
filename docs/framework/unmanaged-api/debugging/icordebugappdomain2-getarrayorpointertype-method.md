---
title: ICorDebugAppDomain2::GetArrayOrPointerType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: bbf43f3936823b9a8e562cb32cfa2eef08840033
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895191"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="0044f-102">ICorDebugAppDomain2::GetArrayOrPointerType – metoda</span><span class="sxs-lookup"><span data-stu-id="0044f-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="0044f-103">Získá pole zadaného typu nebo ukazatel nebo odkaz na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="0044f-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0044f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0044f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0044f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0044f-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="0044f-106">pro Hodnota výčtu CorElementType –, která určuje podkladový nativní typ (pole, ukazatel nebo odkaz), který má být vytvořen.</span><span class="sxs-lookup"><span data-stu-id="0044f-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="0044f-107">pro Rozměr (tj. počet rozměrů) pole.</span><span class="sxs-lookup"><span data-stu-id="0044f-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="0044f-108">Tato hodnota musí být 0, `elementType` Pokud určuje typ ukazatele nebo odkazu.</span><span class="sxs-lookup"><span data-stu-id="0044f-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="0044f-109">pro Ukazatel na objekt ICorDebugType, který představuje typ pole, ukazatel nebo odkaz, který má být vytvořen.</span><span class="sxs-lookup"><span data-stu-id="0044f-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="0044f-110">mimo Ukazatel na adresu `ICorDebugType` objektu, který představuje konstruované pole, typ ukazatele nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="0044f-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0044f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0044f-111">Remarks</span></span>  
 <span data-ttu-id="0044f-112">Hodnota typu *ElementType* musí být jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="0044f-112">The value of *elementType* must be one of the following:</span></span>  
  
- <span data-ttu-id="0044f-113">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="0044f-113">ELEMENT_TYPE_PTR</span></span>  
  
- <span data-ttu-id="0044f-114">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="0044f-114">ELEMENT_TYPE_BYREF</span></span>  
  
- <span data-ttu-id="0044f-115">ELEMENT_TYPE_ARRAY nebo ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="0044f-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="0044f-116">Pokud je hodnota typu *elementType* ELEMENT_TYPE_PTR nebo ELEMENT_TYPE_BYREF, *nRank* musí být nula.</span><span class="sxs-lookup"><span data-stu-id="0044f-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0044f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0044f-117">Requirements</span></span>  
 <span data-ttu-id="0044f-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0044f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0044f-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0044f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0044f-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0044f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0044f-121">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0044f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
