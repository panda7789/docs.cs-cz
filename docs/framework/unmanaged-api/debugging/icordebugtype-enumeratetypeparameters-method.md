---
title: ICorDebugType::EnumerateTypeParameters – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: b2c381d093069f5ee86be1b19d75f5c2d69ad9fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791314"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="facff-102">ICorDebugType::EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="facff-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="facff-103">Získá ukazatel rozhraní na ICorDebugTypeEnum, který obsahuje parametry <xref:System.Type> třídy, na kterou odkazuje tento ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="facff-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="facff-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="facff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="facff-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="facff-106">mimo Ukazatel na adresu `ICorDebugTypeEnum`, která obsahuje parametry typu.</span><span class="sxs-lookup"><span data-stu-id="facff-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="facff-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="facff-107">Remarks</span></span>  
 <span data-ttu-id="facff-108">Pokud je hodnota CorElementType – vrácená funkcí [ICorDebugType:: GetType](icordebugtype-gettype-method.md) ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR nebo ELEMENT_TYPE_FNPTR, můžete použít `EnumerateTypeParameters`.</span><span class="sxs-lookup"><span data-stu-id="facff-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="facff-109">Počet parametrů a jejich pořadí závisí na typu:</span><span class="sxs-lookup"><span data-stu-id="facff-109">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="facff-110">ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE: počet parametrů typu obsažených v `ICorDebugTypeEnum`, které tato metoda vrátí, bude záviset na počtu formálních parametrů typu pro odpovídající třídu.</span><span class="sxs-lookup"><span data-stu-id="facff-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="facff-111">Například pokud je typ `class Dict<String,int32>`, `EnumerateTypeParameters` vrátí `ICorDebugTypeEnum`, který obsahuje objekty reprezentující `String` a `int32` v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="facff-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="facff-112">ELEMENT_TYPE_FNPTR: počet parametrů typu obsažených v `ICorDebugTypeEnum` bude o jeden větší než počet argumentů přijatých funkcí.</span><span class="sxs-lookup"><span data-stu-id="facff-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="facff-113">První parametr typu obsažený v `ICorDebugTypeEnum` je návratový typ pro funkci a následné parametry typu jsou parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="facff-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="facff-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF nebo ELEMENT_TYPE_PTR: vrátí se jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="facff-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="facff-115">Například pokud je typ pole typ, například `int32[]`,`EnumerateTypeParameters` vrátí `ICorDebugTypeEnum` obsahující objekt reprezentující `int32`.</span><span class="sxs-lookup"><span data-stu-id="facff-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="facff-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="facff-116">Requirements</span></span>  
 <span data-ttu-id="facff-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="facff-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="facff-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="facff-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="facff-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="facff-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="facff-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="facff-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
