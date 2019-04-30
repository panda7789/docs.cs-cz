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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58a39771bd89fc9c4947f80a3c87b4d340b5461c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934872"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="5209f-102">ICorDebugAppDomain2::GetArrayOrPointerType – metoda</span><span class="sxs-lookup"><span data-stu-id="5209f-102">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>
<span data-ttu-id="5209f-103">Získá pole objektů zadaného typu nebo ukazatel nebo odkaz na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="5209f-103">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5209f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5209f-104">Syntax</span></span>  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5209f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5209f-105">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="5209f-106">[in] Hodnota corelementtype – výčet, který určuje základní nativní typ (pole, ukazatel nebo odkaz) který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="5209f-106">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="5209f-107">[in] Pořadí (to znamená, počet rozměrů) v poli.</span><span class="sxs-lookup"><span data-stu-id="5209f-107">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="5209f-108">Tato hodnota musí být 0, pokud `elementType` Určuje typ ukazatele nebo odkazu.</span><span class="sxs-lookup"><span data-stu-id="5209f-108">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="5209f-109">[in] Ukazatel na objekt ICorDebugType, který představuje typ pole, ukazatel nebo odkaz, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="5209f-109">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="5209f-110">[out] Ukazatel na adresu `ICorDebugType` typ objektu, který představuje konstruovaná pole, typ ukazatele nebo odkazu.</span><span class="sxs-lookup"><span data-stu-id="5209f-110">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5209f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5209f-111">Remarks</span></span>  
 <span data-ttu-id="5209f-112">Hodnota *elementType* musí být jedna z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="5209f-112">The value of *elementType* must be one of the following:</span></span>  
  
- <span data-ttu-id="5209f-113">TYP ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="5209f-113">ELEMENT_TYPE_PTR</span></span>  
  
- <span data-ttu-id="5209f-114">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="5209f-114">ELEMENT_TYPE_BYREF</span></span>  
  
- <span data-ttu-id="5209f-115">ELEMENT_TYPE_ARRAY nebo ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="5209f-115">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="5209f-116">Pokud hodnota *elementType* ELEMENT_TYPE_PTR nebo ELEMENT_TYPE_BYREF, *nRank* musí být nula.</span><span class="sxs-lookup"><span data-stu-id="5209f-116">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5209f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5209f-117">Requirements</span></span>  
 <span data-ttu-id="5209f-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5209f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5209f-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5209f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5209f-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5209f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5209f-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5209f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
