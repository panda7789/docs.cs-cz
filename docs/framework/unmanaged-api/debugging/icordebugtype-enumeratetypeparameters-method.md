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
ms.openlocfilehash: dc6bf4f02c49788e640c6e230f864e3ca8e71b0d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379995"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="da061-102">ICorDebugType::EnumerateTypeParameters – metoda</span><span class="sxs-lookup"><span data-stu-id="da061-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="da061-103">Získá ukazatel rozhraní na ICorDebugTypeEnum, který obsahuje <xref:System.Type> parametry třídy, na kterou odkazuje tento ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="da061-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da061-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da061-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da061-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da061-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="da061-106">mimo Ukazatel na adresu `ICorDebugTypeEnum` , která obsahuje parametry typu.</span><span class="sxs-lookup"><span data-stu-id="da061-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da061-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da061-107">Remarks</span></span>  
 <span data-ttu-id="da061-108">Můžete použít, `EnumerateTypeParameters` Pokud hodnota CorElementType – vrácená funkcí [ICorDebugType:: GetType](icordebugtype-gettype-method.md) je ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR nebo ELEMENT_TYPE_FNPTR.</span><span class="sxs-lookup"><span data-stu-id="da061-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="da061-109">Počet parametrů a jejich pořadí závisí na typu:</span><span class="sxs-lookup"><span data-stu-id="da061-109">The number of parameters and their order depends on the type:</span></span>  
  
- <span data-ttu-id="da061-110">ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE: počet parametrů typu obsažených v `ICorDebugTypeEnum` metodě, kterou vrací tato metoda, bude záviset na počtu formálních parametrů typu pro odpovídající třídu.</span><span class="sxs-lookup"><span data-stu-id="da061-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="da061-111">Například pokud je typ `class Dict<String,int32>` , pak `EnumerateTypeParameters` vrátí objekt `ICorDebugTypeEnum` , který obsahuje objekty reprezentující `String` a `int32` v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="da061-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
- <span data-ttu-id="da061-112">ELEMENT_TYPE_FNPTR: počet parametrů typu obsažených v poli `ICorDebugTypeEnum` bude větší než počet argumentů přijatých funkcí.</span><span class="sxs-lookup"><span data-stu-id="da061-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="da061-113">První parametr typu obsažený v parametru `ICorDebugTypeEnum` je návratový typ pro funkci a následné parametry typu jsou parametry funkce.</span><span class="sxs-lookup"><span data-stu-id="da061-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
- <span data-ttu-id="da061-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF nebo ELEMENT_TYPE_PTR: vrátí se jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="da061-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="da061-115">Například pokud je typ pole typu `int32[]` , například, `EnumerateTypeParameters` vrátí `ICorDebugTypeEnum` objekt, který obsahuje objekt reprezentující `int32` .</span><span class="sxs-lookup"><span data-stu-id="da061-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da061-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da061-116">Requirements</span></span>  
 <span data-ttu-id="da061-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da061-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da061-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="da061-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da061-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="da061-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da061-120">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da061-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
